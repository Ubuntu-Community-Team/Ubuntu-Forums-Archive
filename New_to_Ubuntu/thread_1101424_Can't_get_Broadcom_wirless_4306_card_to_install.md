---
title: "Can't get Broadcom wirless 4306 card to install"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by smitty65 on 2009-03-20
I have been trying to install my wireless to work with no luck. Ubuntu 8.10 complete install-  I am running a dell inspiron 1100 - with a broadcom eternet 4401 chipset and a broadcom 4306 wireless card. The wired networing has never been a problem but each try at installing my wireless has failed. I have am a newbie but have run thru many different threads on possible fixes.  I will post the results of my computers network but I need help- please. When I open the network controller it only has ever showed a wired connection - no wireless. when i run the lshw -C NETWORK it only shows the ethernet network - when I had a fresh install it showed an ethernet and another Disabled network. I am concerned that if I go any further on my own I will do more damage than good-that said I really like the Ubuntu 8.10 OS and the software packages.. NEED HELP-PLEASE

---

### Post by porchrat on 2009-03-20
We need to know exactly what you have and haven't tried so far, for example:

did you try installing any other drivers (sometimes the ones that come with Ubuntu are a little outdated so sometimes installing the newer driver can solve the problem - worked for my broadcom card)?

have you tried using ndiswrapper? - it will allow you to use the Windows drivers (would've come on a CD with your machine) to run it in Ubuntu.

---

### Post by avtolle on 2009-03-20
If you are using ndiswrapper, as I understand it you will need to obtain the XP driver (not the Vista driver).

I don't know if you have seen this, but [http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers](http://wireless.kernel.org/en/users/Download#DownloadlatestLinuxwirelessdrivers) is a site that provides Linux drivers for various wireless chipsets, including broadcom. This might be an alternative you would want to pursue.

---

