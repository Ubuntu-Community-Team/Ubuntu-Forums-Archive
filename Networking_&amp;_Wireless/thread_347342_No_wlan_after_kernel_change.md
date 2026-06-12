---
title: "No wlan after kernel change"
date: 2007-01-27
forum: Networking &amp; Wireless
---

### Post by Ehnvis on 2007-01-27
Probably in the wrong forum part but I hope a mod will move it in that case.

I installed Ubunty 6.10 on my HP NC4010 a few days ago and after a few trial and errors I got my wlan working with the network manager gnome (WPA encrypted). But this morning I decided to try and get the undervolting going (as I did use a similar thing under Gentoo) so I followed the Undervolting guide in the wiki.

But after the reboot to the new kernel I lost my wlan, iwconfig tells me that I dont have any wlan card. Had a look and it seems like the ath_pci modules are not compiled during the build of the new kernel.

Modprobe ath_pci while booted the new kernel says no module found, works fine when I boot the old kernel again.

Any suggestions on how to get my wlan working again without too much hassle? I do want to stick with ubuntu as it seems to be a nice setup for a laptop that I only use for surfing the web, music and movies.

---

### Post by Ehnvis on 2007-01-29
Ah well, seems like no one knows how to help me here regarding this matter.

Did some tests and it seems like the linux-restricted-modules doesn't like custom kernels so I had to fallback on the old non custom kernel which pisses me off. Atleast it works but I think that the way ubuntu handles custom kernels is way out off track. Why isn't it possible to install the restricted modules on a custom kernel? I couldn't find a way for it anyway.

About to give up and go back to Gentoo where I had full control.

---

### Post by Korsaire71100 on 2007-02-16
Heloo,

Just look here, it's surely gonna be helpfull :
[http://ubuntuforums.org/showthread.php?t=358004](http://ubuntuforums.org/showthread.php?t=358004)

bye

---

### Post by Ehnvis on 2007-02-27
Hmm, gives me a few new pointers to try out. Thanks.

---

### Post by Ehnvis on 2007-03-03
Tried the stuff from the post but no luck. So I guess I either have to give up trying or move away from ubuntu and go back to Gentoo where it's alot easier to work with custom kernels.

---

