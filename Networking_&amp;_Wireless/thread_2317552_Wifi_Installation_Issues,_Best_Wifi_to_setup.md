---
title: "Wifi Installation Issues, Best Wifi to setup"
date: 2016-03-17
forum: Networking &amp; Wireless
---

### Post by NotWindows on 2016-03-17
I have moved and need to run wifi, I purchased a small usb wifi adapter but doesn't get recognised by Ubuntu 15. What is the best way to do wifi with Ubuntu?

Thanks,
Kevin

---

### Post by chili555 on 2016-03-17
Perhaps we can get it recognized. Please insert the device and run and post:```
lsusb
```

---

### Post by NotWindows on 2016-03-18
It comes up as Realtek Semiconductor Corp.

---

### Post by chili555 on 2016-03-18
> **NotWindows said:**
> It comes up as Realtek Semiconductor Corp.If you want to post the details, we may be able to help you. However, with "Realtek Semiconductor Corp." there aren't enough details to help us find and propose a solution.

Sorry.

---

### Post by NotWindows on 2016-03-18
Realtek 11N

What other info should I get and how from the terminal?

This may not even be a great WiFi adapter.

---

### Post by chili555 on 2016-03-18
```
lsusb
```On my machine, it produces a lot of data, but for my wireless device, it says:> Bus 001 Device 007: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11nWe asked for this information because we can't possibly guess what you have. Realtek has made dozens, maybe hundreds of devices over the years and there is no way, without these details, that we can figure out what you have and try to tell you how to get it going.

---

### Post by NotWindows on 2016-03-18
Mine doesn't list the model#. The only thing I could find was the 11n.

Is there a way for me to get more info from it via the terminal for you?

---

### Post by chili555 on 2016-03-18
> **NotWindows said:**
> Mine doesn't list the model#. The only thing I could find was the 11n.

Is there a way for me to get more info from it via the terminal for you?Do you have a pencil and paper?

---

### Post by NotWindows on 2016-03-18
Yes

---

### Post by NotWindows on 2016-03-19
I have discovered this is a Realtek RTL8192EU  USB wifi

---

### Post by NotWindows on 2016-03-19
Ok I used the terminal and lsusb this is what I got.

Bus 004  Device 002: ID 0BDA:818B Realtek Semiconductor Corp.

---

### Post by chili555 on 2016-03-19
There are two methods to install the necessary driver. The first is the five minute method.

NotWin: "Hey, friend, can I borrow your ethernet connection for just a few minutes? I brought along six of your favorite beverage."

Friend: "Sure, NotWin, glad to help you! Let me put a couple of those beverages on ice."

You then open a terminal and do:

```
sudo apt-get update
sudo apt-get install linux-headers-generic build-essential git
git clone https://github.com/Mange/rtl8192eu-linux-driver.git
cd rtl8192eu-linux-driver
make
sudo make install
sudo modprobe 8192eu

```
Your wireless should now be working. Detach the ethernet, thank the friend and enjoy!

Here is how to do it in about five days...maybe.

Go here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) Select your Ubuntu version in the dropdown; find out with:

```
lsb_release -c

```
You may have the prerequisites already installed. Find out:

```
sudo dpkg -s build-essential
sudo dpkg -s linux-headers-generic
```

If both are installed, please proceed to the next step. If not, search for linux-headers-generic and build-essential or whichever is not installed. Be sure to locate their dependencies and the dependencies of the dependencies. Be sure to download the correct version, either 32- or 64-bit. Find out:```
arch
```Once you've download about fifteen or so packages on another computer, transfer them with a USB stick or similar to the desktop of your Ubuntu computer. Open a terminal and install them:

```
cd ~/Desktop
```

If your installation is not in English, your desktop may be named something else, for example, Escritorio or something else. Substitute here.

```
sudo dpkg -i *.deb
```

It may complain that a package is missing a dependency. If so, download that and add it to the desktop and try again.

Write many posts on the forum to tell old Chili how you're stuck. Rinse and repeat.

Once that's all done, get this: [https://github.com/Mange/rtl8192eu-linux-driver/archive/master.zip](https://github.com/Mange/rtl8192eu-linux-driver/archive/master.zip) Download it and then transfer it to your desktop, too. Right-click it and select 'Extract Here.' Now, back to the terminal.

```
cd ~/Desktop/rtl8192eu-linux-driver
make
sudo make install
sudo modprobe 8192eu
```

In either event, when Update Manager installs a later kernel, known as linux-image, after the requested reboot, you must recompile:

```
cd ~/Desktop/rtl8192-linux-driver
make clean
make
sudo make install
sudo modprobe 8192eu
```

Please retain the files and these instructions for that time.

---

### Post by jeremy31 on 2016-03-19
If NotWindows posts the result of ```
uname -a
``` I probably have that kernel installed on one laptop or another and can compile it, and put it my dropbox account so they can download it

---

### Post by NotWindows on 2016-03-20
Your first quick example did the trick! THANKS A LOT!

Kevin

---

### Post by NotWindows on 2016-03-20
I have a problem. Everything worked fine until I rebooted from doing updates and now it isn't recognizing the modem.

---

### Post by jeremy31 on 2016-03-20
Do the second part of Chili's post, you likely got a kernel update

---

### Post by NotWindows on 2016-04-02
That did the trick! I think it was from a Kernal upgrade.

Not sure how to close the thread as solved.

---

### Post by jeremy31 on 2016-04-02
The thread tools dropdown menu near the top  of the page will allow you to mark as solved

---

