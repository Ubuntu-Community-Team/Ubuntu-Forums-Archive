---
title: "Big Time Novice - Wants Wireless Working"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by Phluxed on 2007-08-02
Hello there,
This is my first linux Distro and it was recommended to me by a co-worker. I have since managed to get it to dual boot with vista, and everything seems to work great, however, I am completely unable to get wireless working. 

I have a WG121 USB wireless adaptor that I am trying to connect with. As far as I understand I will need Ndiswrapper to get it working. However, the computer does not have internet access at all through a land line and being a large novice, I have been unable to figure out how the heck to install it. I have looked through guides etc but have been unable to find any novice instructions on how to install. Could anyone please give me some assistance on this matter. It would be greatly appreciated.

---

### Post by noob12 on 2007-08-02
If possible you should really try to find a location where you can plug into hard-wired ethernet.  Otherwise, your only real hope is if you have a USB jump drive handy, you can hope to boot into Windows, download the packages you need, and use the jump drive on the linux side.  This works, but will get painful if you have to do multiple iterations of that.  Alternately, if you have a separate computer that is connected you can keep doing the sneaker-net thing with the USB drive.

The other thing is that you'll probably want to interact with some helpers on the forum to guide you through the process, and you'll need some connection for that.

---

### Post by Phluxed on 2007-08-02
Hi there, 
I managed to get the darn thing installed by downloading it to another hard drive with windows and copying it over. I then compiled and installed it.

However, when I add a driver to it, it doesn't list it in the left and doesn't have the device working. I use ndiswrapper -l and it shows the device as connected and working. I can't seem to remove the software and try reinstalling either... how do I uninstall and how can I get this working?

---

### Post by noob12 on 2007-08-02
Can you post the output from these commands.  We need to understand the situation a bit more.  

```

lsusb

lshw -C network

ndiswrapper -v

ndiswrapper -l

```

---

### Post by Phluxed on 2007-08-02
As soon as I did lshw -C network
the USB device lit up.

I then manually configured the IP information and it connected.

---

### Post by noob12 on 2007-08-02
Um.  That little miracle was not expected.   

May have triggered a modprobe.  Not sure.  If you have trouble after reboots, post for help.

---

