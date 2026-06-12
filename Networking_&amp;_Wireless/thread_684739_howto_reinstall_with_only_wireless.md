---
title: "howto reinstall with only wireless?"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by Xbehave on 2008-02-01
i live in a flat the landlord only offers wireless, Ive messed up my gutsy install and need to reinstall my system with an alternate CD

* i have a wired connection at uni but its quite hard to get running as i need to install cisco VPN to get out bound access, which is to say the least a pain. (tried connecting wirelessly today and it just wasnt working . )
* i have ndiswrapper and bcm43xx working with no problems
* ive got patched drivers but if its too hard to copy them over then it doesn't matter

what files should i save on a memory pen to be able to get my system working?

---

### Post by HermanAB on 2008-02-01
The short answer is that you can't re-install over a Wireless link.

Cheers,

Herman

---

### Post by Xbehave on 2008-02-01
the OS installs of the disk, and surely i can just save the files that are needed to a usb pen and install ndiswrapper or the firmware files or whatever i installed of the internet from the pen instead!

---

### Post by HermanAB on 2008-02-01
Well, there you got the long answer...

BTW, I won't even try - I'll just find a friend with wired internet.

---

### Post by SactoBob on 2008-02-01
Get a wireless bridge to convert the wireless signal into a wired input.  For all intents and purposes, you will have a wired connection, and a faster and more reliable connection.
[http://ubuntuforums.org/showthread.php?t=387871](http://ubuntuforums.org/showthread.php?t=387871)

---

### Post by jmcnaught on 2008-02-02
You can do this, it isn't hard.  The files you need to copy to your USB disk can be found in /var/cache/apt/archives

You want anything that starts with ndis.  If they're not there, you could simply reinstall them with Synaptic.  I don't use ndiswrapper myself so I don't remember which exact packages you need, but this should do the trick:

```

cp /var/cache/apt/archives/ndis* /media/disk
```

Also make sure to put the Windows driver for your wireless card on the USB disk.  If it's in a .zip file, unzip it first or make sure to include the unzip package (also in /var/cache/apt/archives if you've installed it on the current system).

Once you've reinstalled, you should be able to pop the USB disk in and install the ndis packages with dpkg or simply clicking on them in Nautilus to use GDebi. If you get an error about a dependency, try installing the other one first.  

Once you've done that, you should be able to use the same ndiswrapper commands that you used last time.  If you don't know them, you might also want to print/save them to disk beforehand too.

Hope that helps.

---

### Post by ginge on 2008-02-02
You beat me to the punch. As you have most of what I was going to put there, here are some more addition bits of info that might help. If you are worried about dependancies, you might want to use a massive USB disk and copy *.deb to it. Best way to be sure.

you can copy the current install for your wireless drivers from the folder /etc/ndiswrapper/bcm* to your usb disk

The files you will need are ndiswrapper-common*.deb and ndiswrapper-utils*.deb

to install the deb files manually you can use

dpkg -i ndiswrapper-common*.deb

you install the drivers from the usb disk using

ndiswrapper -i bcmwl5.inf

You can check to see if it worked using ndiswrapper -l

the other option would be to use the kernel module bcm43xx.ko but this is slow and buggy

EDIT: dont forget to blacklist the kernel module if you use ndiswrapper

edit the file /etc/modprobe.d/blacklist
add a line
blacklist bcm43xx

---

