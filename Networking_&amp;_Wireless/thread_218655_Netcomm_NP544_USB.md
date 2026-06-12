---
title: "Netcomm NP544 USB"
date: 2006-07-18
forum: Networking &amp; Wireless
---

### Post by McHenry on 2006-07-18
I have a USB wireless adapter that I would like to get running under ubuntu. 

I have searched google etc without any success.

The details of the card are as follows:
[http://www.netcomm.com.au/Spec_Sheets/NP544%20Spec%20Sheet-lowres.pdf](http://www.netcomm.com.au/Spec_Sheets/NP544%20Spec%20Sheet-lowres.pdf)

[http://www.netcomm.com.au/Support/downloads.php?Category=WIRELESS&Products=NP544](http://www.netcomm.com.au/Support/downloads.php?Category=WIRELESS&Products=NP544)

Any help would be greatly appreciated.

Thanks in advance...

---

### Post by McHenry on 2006-07-19
OK, it's working now...

I downloaded the driver from:
[http://www.atlantis-land.com/firmware/3463_A02-UP-W54%5BV10-20%5D.ZIP](http://www.atlantis-land.com/firmware/3463_A02-UP-W54%5BV10-20%5D.ZIP)

Then simply followed the instructions at:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Compile_and_install](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Compile_and_install)

And all works, well sort of anyway... it appears I need to rerun through the process after every reboot :(

I think the problem is the following command "ndiswrapper -m" which I issued before it was 100%. Now when I get it working and I want to save the settings if I try it again I get the following error:

modprobe config already contains alias directive

Does this sound like the reason I'm losing my settings after each reboot ?

---

