### **Project Description: ¥enOS**

**¥enOS** is a minimalist, lightweight operating system based on Slax Linux, designed to be easily customized and run on both desktop and mobile devices. It is highly portable and runs smoothly on Android via **Termux**, without the need for root access. 

This project allows you to experience a complete Linux environment with both graphical and command-line interfaces, on devices such as Android, and also works as a desktop system for more traditional use.

---

### **How to Install ¥enOS on Android via Termux:**

Follow these steps to install and run **¥enOS** on your Android device using **Termux**.

#### **Step 1: Install Termux**

1. Open the [Play Store](https://play.google.com/store/apps/details?id=com.termux) on your Android device and install **Termux**.
2. Open **Termux** and run the following commands to update the environment:

   ```bash
   pkg update
   pkg upgrade
   ```

#### **Step 2: Install Required Packages and Tools**

1. In **Termux**, install the necessary tools to run **¥enOS**:

   ```bash
   pkg install proot wget git vim curl x11-repo
   pkg install xterm pulseaudio
   ```

   This installs **proot**, **X11**, **xterm** (a lightweight graphical terminal), and **pulseaudio** for managing audio, if needed.

#### **Step 3: Install Graphical Environment (Optional)**

1. To run the **¥enOS** with a graphical interface, install **XServer XSDL** (an X11 server for Android):

   - Download **XServer XSDL** from the [Play Store](https://play.google.com/store/apps/details?id=x.org.server.xserver).
   
2. Install the necessary graphical dependencies for **¥enOS**:

   ```bash
   apt-get update
   apt-get install -y xorg fluxbox
   ```

   This will install **Xorg** (X server) and **Fluxbox** (a lightweight window manager).

#### **Step 4: Download and Prepare ¥enOS**

1. Download the **¥enOS** ISO or files:

   ```bash
   wget https://link.to/your-yenos.iso
   ```

   **Replace the link above with the actual link to your **¥enOS** ISO or files.**

2. Create a directory to prepare **¥enOS**:

   ```bash
   mkdir ~/yenos
   ```

#### **Step 5: Mount the Environment with proot**

1. Use **proot** to mount the environment:

   ```bash
   proot --link2symlink -0 -r ~/yenos -b /dev -b /proc -b /sys -b /data -w /root /bin/bash
   ```

   - **Explanation**:
     - `-r ~/yenos`: Directory where **¥enOS** will be mounted.
     - `-b /dev -b /proc -b /sys -b /data`: Bind mounts for necessary directories.
     - `-w /root`: Set the working directory to `/root`.
     - `/bin/bash`: Start a Bash shell inside the mounted environment.

#### **Step 6: Set Up and Start the Graphical Environment (X11)**

1. Open **XServer XSDL** and note the display screen (usually `:0` or `localhost:0`).

2. In **Termux**, set the environment variable to use the **XServer XSDL** display:

   ```bash
   export DISPLAY=localhost:0
   ```

3. Start the graphical environment with **Fluxbox**:

   ```bash
   startx
   ```

   This will launch **Xorg** and **Fluxbox** within **X11**, providing a graphical interface on your Android device.

#### **Step 7: Using ¥enOS**

You can now use **¥enOS** directly on your Android device! Inside the proot environment, you can run Linux commands and use the system just as you would on a desktop system, but on your mobile device with a graphical interface.

---

### **How to Install ¥enOS on Desktop**

For desktop installation, follow the standard installation steps for **¥enOS** on a regular PC. You can either create a bootable USB drive or use virtualization tools to run the system.

1. Download the **¥enOS** ISO file.
2. Create a bootable USB using tools like **Rufus** or **Balena Etcher**.
3. Boot from the USB drive and follow the installation instructions to set up **¥enOS** on your desktop or laptop.

---

### **Conclusion**

With these steps, you can install and run **¥enOS** both on your Android mobile device via **Termux** and on your desktop. On Android, you can enjoy a full Linux environment with graphical and command-line interfaces, all without needing root access. On your desktop, you can follow standard installation procedures for a full desktop experience.

If you need more help or run into any issues, feel free to open an issue in the repository!
