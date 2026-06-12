---
title: "[SOLVED] Studio has no wireless in low latency kernle"
date: 2007-08-17
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-08-17
I have installed Ubuntu Studio. It has added another kernel (something to do with low-latency) to the growing list. It has no wireless connectivity. I have learned why.

At another post titled:
 [B]
No wireless with low-latency kernel [/B] ([http://ubuntuforums.org/showthread.php?t=462403](http://ubuntuforums.org/showthread.php?t=462403)).   There is good help. I know I need to install the Restricted Driver for my wireless card (D-Link WDA 2320 Atheros chipset).

The instructions at the above thread say to:

"Yea, I had this too
If you click on the link to Restricted Drivers Manager it tells you it's missing the Linux-restricted modules
So...
hook up with a wired connection,
search Synaptic for linux restricted modules and find the one that matches the version of the low latency kernel."

I have no way to do that. Can this "restricted module" be downloaded and installed, with GDebi I hope?

Relevant output of lsmod is: Ath_Pci 97312 0 BUT is this the "module" for my low-latency kernel and wireless card?

Where do I go get the above module? Does it have to come over the 'net while I'm using the "other kernel"

---

### Post by Mark_in_Hollywood on 2007-08-18
Sometimes, as a rank newbie and computer amateur, I get *lucky*. It shouldn't be this way but because I've installed a package and it worked, I'm reporting the success and remarking this thread as solved in the following manner:

Googleing for the keyword that was returned in System/Administration/Restriced Drivers Manager, e.g. linux-restricted-modules-2.6.20-16-lowlatency I came across:

[http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-16-lowlatency](http://packages.ubuntu.com/feisty/misc/linux-restricted-modules-2.6.20-16-lowlatency)

please note that the file to download is at the very bottom of the page and as I have I386 I downloaded that. I was asked if I wanted Gdebi to install it, but chose to save it. 

I then rebooted into the Ubuntu Studio installed "lowlatency" kernel. (Normal restart) and allow Grub to select the kernel.

A moment later the desktop was up and first highlighting and then "right-clicking" brought up the Gdebi installer. I selected that. A few moments later GDebi told me another versions was available "online", but I clicked the "Install" radio button. A moment later that was done.

Checking System/Administration/Restriced Drivers Manager showed that my Atheros driver was installed but not in use. I rebooted and have my wireless back.

Meanwhile, the second time I went to find the page link URL above, I had trouble locating the exact same URL. Sometimes I just get lucky.

I cannot promise this will work for others but it did solve my problem. Meanwhile, sophisticated software such as Ubuntu Studio ought to inform the end user that such will need to take place. Putting the vulnerable newbie in such a position is frightening of doing much harm and little good.

Thank you all who read this post. I still adore the Ubuntu Community.

---

