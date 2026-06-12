---
title: "Install a Ralink RT5592sta PCI-e Wireless Card with Kernel 3.x"
date: 2015-02-27
forum: Networking &amp; Wireless
---

### Post by Macbuntu-Windows-7-User on 2015-02-27
Hello everyone:

If you're like me and had problems installing a newer wireless card with a Ralink RT5592sta Chipset, and tried different methods, like using NDIS Wrapper for the wireless card installation, look no further.  I recently found a link to solve the issue and to get the RT5592sta chipset wireless card (Ex. ASUS PCE-N53); this might work with any wireless card with that specific chipset.  It is called [ASUS-PCE-N53-Linux]("https://github.com/mareksuscak/asus-pce-n53-linux") and the instructions for the installation are on that site, however, I'll setup the instructions on here.

The first step would be to have a temporary Wired (Ethernet) connection, and administrative rights.

Install the following components (if required):

```

sudo apt-get install build-essential linux-headers-generic linux-headers-$(uname -r) -y

```

If you get this message when running the command above:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-3.16.0-31-generic is already the newest version.
linux-headers-generic is already the newest version.

```

Then the following are installed.  If not, the installation should take a few minutes, depending on your Internet connection.

Run the other commands for the driver installation process:

```

cd ~
sudo apt-get install git -y
git clone https://github.com/mareksuscak/asus-pce-n53-linux.git
cd asus-pce-n53-linux
sudo make
sudo make install
sudo modprobe rt5592sta

```

Add the following line in the /etc/modules file at the end:

```

sudo nano /etc/modules

```

```

rt5592sta

```

Connect to your wireless network and enjoy!

Hope this helps.  Feel free to discuss if the installation was a success or a failure.  We'll help you out if the installation was a failure...

---

