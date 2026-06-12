---
title: "ndiswrapper can't connect until it is reloaded"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by swinky on 2008-11-12
Last night I decided to switch from 32 bit Ubuntu (8.10) to 64 bit on my Toshiba L305. Just about everything went smoothly (more or less) except for the wireless networking. After many searches across the internet, I managed to get ndiswrapper working from this post:[http://ubuntuforums.org/showthread.php?t=921589]("http://ubuntuforums.org/showthread.php?t=921589") in the reply from user peterwil.

I rejoiced in what was most likely a comical little display on my part, but it was short lived. The next time I booted my computer, the network manager icon started the connecting animation but refused to connect, and after a short while it pops up with the dialog saying that it could not connect. No matter how many times I try it always fails. Also, if I am attempting to connect on a protected network it will ask for the password before failing. 

I messed around with a few things and discovered that removing the ndiswrapper module and then reloading it causes everything to work almost instantly. So while I have functioning wireless internet, I would rather not have to reload it every time I boot.

Using lsmod does show that ndiswrapper is loaded on boot. It just don't work, and I am clueless as to why.

Ubuntu 8.10 amd64 
Atheros AR242x for WiFi.

---

### Post by pacco on 2008-11-21
did you have any problems with the grub bootloader freezing after restarting,if so how did you fix it?
i have searched everywhere and i used supergrub disk,it worked a couple of times and then the same old freeze.
i did have windows vista installed,and then i told ubuntu installer to erase and use entire disk.

Any help would be appreciated.
Thank You

---

