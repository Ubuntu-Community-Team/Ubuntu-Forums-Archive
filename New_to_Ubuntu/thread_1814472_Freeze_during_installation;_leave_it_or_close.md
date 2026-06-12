---
title: "Freeze during installation; leave it or close?"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by WubiAR on 2011-07-29
Hello there,

I am trying to install Xubuntu 11.04 whilst running the "try Xubuntu without installing mode". The bar was about 3/4 full when it suddenly froze.

It says the following at the bottom

```

Copying files...
Jul 29 16:53:27 ubuntu kernel: [ 7790.522229]  [<fffffff81087750] ? kthread+0x0/0xa0
Jul 29 16:53:27 ubuntu kernel: [ 7790.522231]  [<fffffff8100ce20>] ? kernel_thread_helper+0x0/0x10

```

What should I do? I left the installation screen, currently frozen where I described. Should I reboot and try installation again? This from a CD by the way.

---

### Post by ~!geek!~ on 2011-07-29
If you r still waiting for the frozen ubuntu install to resume, I would suggest you to just start whole installation process again.

---

### Post by ajgreeny on 2011-07-29
Did you get to the live xubuntu xfce desktop or did the freeze occur when trying to boot to that?

Either way, it is worth checking the md5sum of the iso file you used to burn the CD or make the USB with the published md5sums you can get from [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

 f1b224166bea923042e53b0e9d5ff63f 
    xubuntu-11.04-desktop-amd64.iso 
     78719bfee11576729a62b4a241d40b19 
    xubuntu-11.04-desktop-i386.iso 



If the md5sum does not correspond exactly, download it again, preferably with a torrent client.  If the hash is correct, burn the CD again as slow as possible, and then check the CD/USB with the menu that appears if you hit the enter key after the first screen appears at bootup.

---

