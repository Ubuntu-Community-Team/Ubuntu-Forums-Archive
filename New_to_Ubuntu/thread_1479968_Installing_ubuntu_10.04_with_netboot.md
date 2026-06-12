---
title: "Installing ubuntu 10.04 with netboot"
date: 2010-05-11
forum: New to Ubuntu
---

### Post by W.Kruger on 2010-05-11
Hi I am a newbe at linux so please be gentle.
I had to install ubuntu 9.04 alternate on 200 pc's so I did a 
lot of googeling and it worked. I used tftpboot on a dhcp server
and got it to install ubuntu on all pc's over the network with no probs.
But now I have to do the same with Ubuntu 10.04 alternate, but it just won't work the same as 9.04.
It just won't install the os, I had a look at my default cfg and can't find any thing wrong, It's the same as the one for 9.04 exept the target dir.

Can anyone please help.

---

### Post by Nxion on 2010-05-12
> **W.Kruger said:**
> Hi I am a newbe at linux so please be gentle.
I had to install ubuntu 9.04 alternate on 200 pc's so I did a 
lot of googeling and it worked. I used tftpboot on a dhcp server
and got it to install ubuntu on all pc's over the network with no probs.
But now I have to do the same with Ubuntu 10.04 alternate, but it just won't work the same as 9.04.
It just won't install the os, I had a look at my default cfg and can't find any thing wrong, It's the same as the one for 9.04 exept the target dir.

Can anyone please help.

Can you give us any errors your getting? When does the install stop? Does it even start?

---

### Post by W.Kruger on 2010-06-22
Thanks for taking intrest in my problem but I looked around and fink I may have found the problem, the vertual box that I was using was just for all older ubuntu's and not for 10.04.
but now I have a nother problem, 10.04 installes but won't boot after install, something to do with a corupt grub or something, now I did take in concederation that it may be the disk so I made a usb boot and it still did the same.......O and Im still learning linux so please be gentle. As for my timming in responce Im very sorry, was away for a wile.

---

### Post by HuckBerry on 2010-10-27
Any Luck Getting 10.04 to work?

I'm learning netboot and so I started with a simple install. Netinstalling Jaunty (9.04) Desktop interactively via this tutorial: [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

This has been successful so far (base image installing right now) and I'd like to move on to something harder. First I'd like to install Lucid (10.04) because it's LTS and I'd like to do it unattended via preseeding.

In this tutorial it mentions the appended kernel options are different between ubuntu versions and I was wondering if you knew the options for 10.04. Currently I have this:
append url=http://192.168.1.137/10.04.preseed initrd=/10.04.initrd.gz vga=normal locale=en_US setup/layoutcode=en_US console-setup/layoutcode=us netcfg/get_hostname= -- quiet

Finally, which ISO did you use. I'd like to install server edition and would like to take as much off of the ISO as possible to reduce excess network traffic fetching from the repos. I believe the 10.04 server alternative would be the correct ISO?

---

