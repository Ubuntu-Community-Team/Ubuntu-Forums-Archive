---
title: "Wireless problem with Live CD?"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by kobudo on 2009-05-05
Hi all,

I am just getting started with Ubuntu 9.0.4. I am running the live CD with the boot assist installed.

I have been having a hard time connecting to my wireless network -- I'm using an old Dlink Airplus DWL-G520 PCI card with a Dlink DI 624 router. I am using 128 bit encryption.

Every time thus far (except for once, see below) I enter my WEP key, the network manager applet has one green light and a blue circle that swirls around for a while before asking again for the WEP key.

The one time I actually establish a connection, I open Firefox and the default homepage comes up. I'm thrilled. This temporary hope is quickly dashed as I try to browse over to Google. I could bring the home page up, and nothing else. 

I log out to go back through my internet settings in Windows and double-check everything. When I restart in Ubuntu, I try getting the connection set up again to no avail.

Is this something I'm doing wrong, or is this a common problem that is found when playing with the Live CD -- especially with the minimum 256 Mb of RAM? 

I'm considering just doing a full install and seeing if that fixes everything, but it's a hassle to remove and reinstall an OS twice just to see if it fixes a problem.

Thanks for any advice I can get!

---

### Post by bruno9779 on 2009-05-05
I have had similar issues in the past:

Once with my laptop, wifi wouldn't work in LIVE CD but did straight out of the box once i installed (I think it was Gutsy)

One other time with my wife's laptop, wifi wouldn't work even after full install. I had to look up for help in the forums, and found some useful tip for ndswrapper, and all worked fine.

I do not know your wifi card, so you should look up more info before expecting things to go just as they did for me.

I hope this helps at least a little

---

### Post by bruno9779 on 2009-05-05
Actually, i have found this:

[http://www.phoronix.com/forums/showthread.php?t=2241](http://www.phoronix.com/forums/showthread.php?t=2241)

It appears that your card works under most linux distros with a little tweaking.

---

### Post by kobudo on 2009-05-05
> **bruno9779 said:**
> Actually, i have found this:

[http://www.phoronix.com/forums/showthread.php?t=2241](http://www.phoronix.com/forums/showthread.php?t=2241)

It appears that your card works under most linux distros with a little tweaking.

Thanks bruno. According to the [ubuntu help page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI") for supported wireless cards, mine "should" work out of the box. I'm guessing that it might be a good idea to have the newest madwifi driver handy, just in case... I saw that it didn't work out of the box with Hoary. Better to have it & not need it and all that.

It's probably worth mentioning that my computer really didn't like booting from the CD without the boot helper installed.

---

