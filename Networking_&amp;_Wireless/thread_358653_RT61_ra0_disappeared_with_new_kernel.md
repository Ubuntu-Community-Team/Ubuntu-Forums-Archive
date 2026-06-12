---
title: "RT61 ra0 disappeared with new kernel"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by sblanzio on 2007-02-11
Hi

this morning, after the last kernel upgrade from
2.6.17-10-386
to
2.6.17-11-386

my ra0 pci wireless card simply disappeared.

Both ifconfig and iwconfig answered no wireless card was found. However i could see that in lspci list.

Now, is there a simple way to recover that under this new kernel?

Is it too much to hope for a better recognizement of this kind of hardware..? I know drivers are out there, but each time we upgrade kernel we always get hard troubles...

to recover is just needed to load the previous kernel at boot.

hoping for a solution
thanks
Sblanzio

---

### Post by Guranic on 2007-02-11
I assume that you made your rt61 wlan card working with howto (address to post attached below). I updated new kernel to my laptop this morning and ra0 disappeared, so I just made this howto again except config-file parts, because they are already there... And, dadaa... Everything is flying just fine again! Hope you get your card back in business..

[http://ubuntuforums.org/showthread.php?t=296822&highlight=rt61+edgy](http://ubuntuforums.org/showthread.php?t=296822&highlight=rt61+edgy)

---

### Post by maxwellcom on 2007-02-11
I originally used the same HOWTO to set up my wireless card using the RT61 chipset.  After the latest kernel update, like sblanzio and guranic my ra0 had also disappeared.  After running a long CAT5 and connecting to the interent, I followed the [link to the HOWTO]("http://ubuntuforums.org/showthread.php?t=296822&highlight=rt61+edgy"), went through the steps, and recovered my wireless (w/WPA) connection.  

Hope it works for others.  For those of us trying to learn Linux- can someone explain how updating the kernel broke the wireless configuration?

---

### Post by Guranic on 2007-02-11
First of all, I'm a newbie with Linux, but I've been experimenting to learn (K)Ubuntu environment about a two months now. My guess is that compiled wireless driver is a kernel module and if you "update" your kernel to new version system leaves old kernel still there. Because of that you actually install new kernel instead of updating old one. And this leaves third party modules out from new kernel. If I got this right, I have a question. Why kernel developers won't add this working rt61 module to this kernel, it's solid stable?

---

### Post by shannondoko on 2007-02-13
I just fixed this seconds ago, it was quite simple actually, assuming it worked to begin with..

```
sudo cp /lib/modules/2.6.17-10-generic/kernel/drivers/net/rt61.ko /lib/modules/2.6.17-11-generic/kernel/drivers/net
sudo depmod
sudo modprobe rt61

```

then reboot

Should work as it did prior to the update. Also, something you might not know, if you hit TAB a lot, it will make navigating a lot easier for example /lib/mo(TAB)/(TAB)0(TAB)/

etc... would help you navigate a lot faster, it took me forever to learn that. Anyway.. I hope I didn't mis type anything, or I didn't leave anything out.. 

Hope this helps. and is relevant..

Also, I was thinking about it, and I'm going to try to explain this out of ignorance, but it sounds right to me..
The reason it stopped working is because it is a kernel module, it isn't built into the kernel, so when we updated to the new kernel we lost the module, all we had to do was copy the module from the old kernel to the new one, and load it back in.  
Does that make sense?

---

