---
title: "[SOLVED] Trying to connect to the internet...."
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by M787M on 2008-03-14
Hi.

I'm running an install of Feisty and I'm really new to all of this.  I've been trying to install my linksys WUSB54Gv4 wireless card (chipset , and have been following all of the threads I could find here, and nothing I've tried has worked. I *think* I installed ndiswrapper, and I successfully installed the driver rt2570.

But, nothing will connect, whether it is a manual connection or not. When I choose to connect to the network, it says I'm connected and displays some percentage, but then I can't go to the internet or view the network at all.  I can't tell if this means that the driver is working, but something else isn't, or if I need to disable something?

Thank you for anyone who can help, I'm tearing my hair out.

---

### Post by mrpixels0 on 2008-03-14
hey there M787M,

Do you have a password on your router ?, if so you will need to tell the network config manager what it is.

for example I use a PSK (WPA) meaning that I use a simple 8 Char password for the router so if want to connect to it, it asks me once for it after that it will remember it and i can connect with no prblems.

if your router does not use a password then did you issue a command like this:

sudo ndiswrapper -ma 

      or  like this 

sudo ndiswrapper -mi

these commands write config info to your modprobe.d config file so linux knows to use them when it boots up.

if you could give me more specific info I or someone else could be of more help to you.

MP0

---

### Post by M787M on 2008-03-14
Thank you for replying!

It does have a password, it's a WEP hexadecimal code, and the computer accepts the password, and says that it is connected, but I can't view the network or go on the internet.

What information would be helpful?

---

### Post by superprash2003 on 2008-03-14
are you getting an ip address from your router.. please type ifconfig in your ubuntu terminal and post results here

---

### Post by mrpixels0 on 2008-03-15
Hey there M787

mine did the same thing, here is what I had to do

goto system->Administration->netowork tools click on it once.

In the dialig that comes up see if your wireless device is there, if it says loop back then click on the arrow next to it and select your wireless device from there once that is done, click on the config button next to it and give it your hex code password again and click ok.

After that you should be abe to surf the net, this should work since we are using the same wireless device. :)

MP0

---

### Post by M787M on 2008-03-18
Thank you everyone who replied! It's working now!

---

### Post by Eiríkr on 2008-03-18
Great to hear!  Since your issue is fixed, please remember to mark this thread as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Thank you,

Eiríkr

---

