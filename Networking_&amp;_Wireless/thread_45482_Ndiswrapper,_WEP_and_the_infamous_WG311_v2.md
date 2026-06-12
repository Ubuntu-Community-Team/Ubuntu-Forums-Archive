---
title: "Ndiswrapper, WEP and the infamous WG311 v2"
date: 2005-06-30
forum: Networking &amp; Wireless
---

### Post by Dodge on 2005-06-30
Hi guys,

Having a bit of a nightmare with this PCI card and Hoary 5.04.  I can set it up using the ACX drivers with no probs, and apparently WEP doesn't work which is a known issue.  ANyway - the card works good with the ACX drivers and without WEP.

Anyway, I need WEP so on searching the forums and I get the following methods to get it working:

1.  Get and install ndiswrapper_utils
2.  Get current drivers for my card (Netgear WG311 v2)
3.  Remove the ACX driver from /lib/modules/etc. etc. and run depmod -a
4.  sudo ndiswrapper -i wg311v2.inf
5.  sudo ndiswrapper -l and make sure drivers are loaded and hardware present.  (It is)
6.  sudo ndiswrapper -m (no errors)
7.  sudo modprobe ndiswrapper (no errors)

I can then see the card in the Network control panel in the GUI and attempt to configure it.  I enter my ESSID, my WEP key and activate the card.  After 30 seconds it says it's activated.

If I then go to a console and IFCONFIG, the card doesn't have an IP address (It has something in the IPv6 address setting though).  Anyway, it doesn't work and I'm scratching my head.

After a reboot, the card is no longer listed in the GUI network setting until I modprobe ndiswrapper again - it still doesn't work.

If someone could post a detailed description from virgin install to WG311 v2 working with WEP and ndiswrapper I'd be a very grateful newbie.

Cheers!

Dodge

---

### Post by rince77 on 2005-06-30
Hello!

Well, the new drivers from [http://acx100.sourceforge,net](http://acx100.sourceforge,net) seem to have cracked the whole WEP thing...
But sadly im well known to linux but not to ubuntu and i'm not able to install the "new" drivers due to the directory structure (kernel not in /usr/src/linux and so on).
I would be glad if someone could post a howto...

[the acx100 ftp-directory](http://rhlx01.fht-esslingen.de/~andi/acx100/) to download the drivers. since version acx100-0.2.0pre8_plus_fixes_55 the readme says WEP is now working with acx111 cards, as we both (sadly;) have.

so far... :)

---

### Post by Dodge on 2005-06-30
Hi rince77,

I'm a total newbie at this, Ubuntu being my first foray into linux.  I'm as much in the dark as you are mate, I wouldn't know where to start installing the newer drivers.

Cheers!

Dodge

---

### Post by rince77 on 2005-06-30
Well, i would know where to start, actually it's quite simple you just have to run 
[PHP]make inject KSRC="whereever the kernel source is"[/PHP] in a root-console within the directory of the acx100 driver package.
but... i'm not quite sure if the source i always entered is the right one...
i entered /lib/modules/2.6.10-5-387/kernel/drivers ... could someone confirm or correct this? i mean, it has to point the the right kernel source.

Edit: Uh, you first have to install some stuff which requires internet-connection since it's the easiest way to do it through apt-get...
[This is the How-To](https://wiki.ubuntu.com/KernelByHandHowto) ... i think it would be possible to install all the stuff by hand but i'm not really into doing all that stuff in console!
hmm... i'm trying some things and then i'll report:)

---

### Post by carlos_ on 2005-06-30
I nstalled the source code using synaptic.  I simply searched for the kernel version and I saw one entry with the name similar to <VERSION>-headers.  It installed with no errors and I was then able to compile a different version of ndiswrapper v1.1.  For some reason the ndiswrapper version that I installed using synaptic wouldn't recognize that my card supported WPA... but that's another story.

---

### Post by rince77 on 2005-06-30
@carlos:

well, the point is that i actually have no internet-connection under ubuntu... so i must download all the packages under winXP, and install all of them by hand :roll:

---

### Post by rince77 on 2005-06-30
Oh man, ist's bloody complicated to get all the needed packages. does anyone have a reliable mirror where i can download all the packages mentioned in the how-to i linked above?

---

### Post by carlos_ on 2005-06-30
Oh, I missed that bit about not having any internet connection... that sounds like a difficult problem.

However, now that I think about it, the kernel source might be on the install cd in which case synaptic might still work... worth a try.

---

### Post by rince77 on 2005-06-30
:???: 
i didn't find it on the install cd... well, i gotta search again:)

---

### Post by carlos_ on 2005-06-30
You shouldn't look on the cd, synaptic should prompt you for the cd if the package is on the cd.  
Pull up synaptic and click on "search" at the top.  Type in the kernel version and hit go.  It should show you some packages that matched your search string... hopefully one will look like "<KERNEL_VERSION>-headers".  Select it for install and hopefully synaptic will prompt you for the Hoary cd and install it from there.  If it gives you an error message saying it couldn't connect to the repository, then you might be out of luck.

---

### Post by Dodge on 2005-07-01
Ok, I may be being a bit ignorant here, but if I connect using the ACX driver that doesn't support WEP and do an update, am I likely to download a later ACX driver that supports WEP?

Dodge

---

### Post by Dodge on 2005-07-01
Update:  It's a WEP problem, not ndiswrapper.  Switch off WEP and the adapter works fine using ndiswrapper.

I've had a little search on the forums, and i've tried using the GUI to enter my wep key as "XXXXXXXXXX", "XXXX-XXXX-XX" to no avail.  I've also tried putting in "restricted XXXXXXXXXX" and "restricted XXXX-XXXX-XX" in the GUI with no joy.

Still trying....

Dodge

---

### Post by Dodge on 2005-07-01
Success!  Writing this email from Ubuntu!

Don't use the drivers off the CD.  I downloaded the latest non-beta XP drivers from Netgear and they work.  You have to remove the ACX driver though.

Cheers for everybody's help!

Dodge

---

### Post by rince77 on 2005-07-01
Congratulations!

But you are using ndiswrapper though right?

:)

---

### Post by cat on 2005-07-01
Could you post a link to that new driver?

---

### Post by Dodge on 2005-07-05
Hi Cat,

THe driver I used was this:  [http://kbserver.netgear.com/support_details.asp?dnldID=770](http://kbserver.netgear.com/support_details.asp?dnldID=770)

rince77 - yes, using ndiswrapper.  I needed a working solution rather that the 'best' solution, but I will take a closer look at the newer ACX driver at some point.

Dodge

---

### Post by cat on 2005-07-06
Thanks, I finally managed to work it out  :)

---

