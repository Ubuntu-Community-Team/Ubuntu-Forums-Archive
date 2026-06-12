---
title: "HOST setting, ndiswrapper, and wireless prob"
date: 2008-01-13
forum: Networking &amp; Wireless
---

### Post by johngonewbie on 2008-01-13
Breathing is a good thing.

anyhoo, I am runing xubuntu on an hp omnibook with a linksys w300bn - ithink that is the model - I spent three days trying to get the wireless to work. Finally, with the help of the Ubuntu community the wireless network is running. However, on startup the host setting is clearly wrong. Also, I have sudo modprobe ndiswrapper everytime in order to get the wireless surfin'.

What is the host name? is there a simple web site or file I need to edit so ndiswrapper can detect the usb wireless at boot.

=johngo

---

### Post by sqrt2 on 2008-01-13
I've never used ndiswrapper (PowerPC user here), but if it's only about loading the kernel module, add "ndiswrapper" to /etc/modules.

I don't what you mean by "the host setting is clearly wrong". What host, what setting?

---

### Post by johngonewbie on 2008-01-14
I resolved part of the problem with the host name by changing it under the manual configuration general tab for wireless networking. The problem is I have to
type sudo modprobe ndiswapper everytime to get the USB wireless card to function.

---

### Post by johngonewbie on 2008-01-14
Never edited that file. hmmm... do I simply type ndiswrapper and save it.

The module is a plaintext file that looks as such:

fuse
lp

Also, I forget the command to edit the file.
last time I edited the interfaces file I used the command
gksudo and the mousepad program to get permissions to change it.

(newbie!!)

---

### Post by sqrt2 on 2008-01-14
Open a terminal, type "sudo nano /etc/modules" and enter your password. Using nano is pretty much straightforward. When you're finished editing, press Control-O to save the file and Control-X to exit.

---

### Post by johngonewbie on 2008-01-14
Thanks for the info. It is running now after I reboot. I used gksudo thunar and opened and edited it with mousepad. Very simple.

---

