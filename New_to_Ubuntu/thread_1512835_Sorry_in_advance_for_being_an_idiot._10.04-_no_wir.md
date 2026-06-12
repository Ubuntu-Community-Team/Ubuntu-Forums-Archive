---
title: "Sorry in advance for being an idiot. 10.04- no wireless device found"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by rspos330 on 2010-06-18
As the title explains, I am fairly new to Ubuntu and for the past month I have been running my laptop through a ethernet cable and everything has been running smoothly; however, I have now been trying to connect to wireless internet but I am showing no device Found.
Thanks in advance for the help.
Please let me know if you need anymore information to help.

---

### Post by anewguy on 2010-06-18
Please do the following:

- open a terminal window (Applications/Accessories/Terminal)

- type:

lspci -C network <press enter>

lsusb <press enter>


Copy and paste the output in a reply here.  What we're doing is asking linux to list any pci network devices and to list all USB devices (the internal wireless on some laptops is actually connected to internal USB).

These outputs will allow us to see what type of wireless adapter you have so we can help you get it working.

Dave ;)

---

### Post by k3lt01 on 2010-06-18
Do you know what your wireless device is? Have you used it with Windows previously?

You may need to install ndiswrapper-common and ndiswrapper-utils-1.9 then follow this guide to install Windows drivers

If this is what you will need to do you will need your wired connection, or your Ubuntu installation disk, open a terminal and paste
```
 sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
``` and follow the prompts. You will need to type in your password and if you haven't done anything in the terminal like this before you will notice your password doesn't look like it is being typed in, don't worry it is.

Now you will need your Windows wireless drivers and then follow this advice.
```
# Notes. Make sure drivers are visible on the Desktop then copy and paste each command into a terminal to install the wireless network drivers for yout wireless card. replace xxxxx.inf with your inf file.

cd Desktop

sudo ndiswrapper -i xxxxx.inf

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

echo "ndiswrapper"|sudo tee -a /etc/modules

sudo shutdown -r now
```

---

### Post by rspos330 on 2010-06-18
Thanks a lot for the fast replies guys. I figured it out though. I didn't have my drivers activated. Sorry for not checking on that first!

---

