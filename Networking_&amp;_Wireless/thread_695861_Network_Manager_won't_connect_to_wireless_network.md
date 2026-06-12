---
title: "Network Manager won't connect to wireless network"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by sharpnotflat on 2008-02-13
Hi all, I am a new user to Linux/Ubuntu.

I just installed it on the family computer last night, and it worked out nicely and swiftly. 

However, I am having trouble connecting to my unprotected wireless network. It works for my other laptop, which has a built in wireless adapter (Windows XP). The computer with the newly installed Ubuntu uses a Linksys adapter, but I don't know if it is working.

First, I installed ndiswrapper (there were two, so I installed both) using the Synaptic Package Manager. I then downloaded ndisgtk from my other computer and put it onto the Ubuntu computer. I installed it, and tried installing the windows driver for my linksys, but I don't think it installed. It does not show up on the List, there is nothing on the list at all, but when I try to install again, it says that it is already installed (inf file). I tried both .inf files on the installation cd for linksys. 

However, I rebooted the computer and clicked on the Network Manager, and it showed a list of networks (including my network). I clicked on it and it was spinning to connect, but it stopped after a while and remained disconnected. I tried numerous times, rebooting the computer and restarting my router. Two times, when I was rebooting, the screen went black and had some text about some wireless thing. It was like DOS or something, and it let me type. I tried typing restart and exit but it just stayed at that window. I had to manually shut  down the computer, and turn it on again. The networks did not show this time, so I rebooted. The networks then started showing up, but still would not connect.

Is it because I don't have my drivers installed correctly? Please help me out.

---

### Post by Hightide on 2008-02-14
Hi sharpnotflat

Can you have a look at Kevdog's wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571194")  and post the ouptut of

lshw -C network:)

regards

:)

---

### Post by spiffwalker on 2008-02-14
I am also new to linux, and im also a computer noob.  I have just installed ubuntu and i have not really done anything, but i know that i have no network driver.  I have tested my usb drive and found out that it works without a driver.  I was wondering if there were any files that i could download from another computer that has internet, and then transfer them over to ubuntu via the usb, and then run it there?

---

### Post by sharpnotflat on 2008-02-16
Thank you, but I solved the problem. I had the wrong drivers, ndiswrapper didn't seem to work for me. However, I downloaded the this driver: [http://at76c503a.berlios.de/](http://at76c503a.berlios.de/) and installed it. I rebooted, and the internet worked perfectly. Thanks for all the help though.

---

