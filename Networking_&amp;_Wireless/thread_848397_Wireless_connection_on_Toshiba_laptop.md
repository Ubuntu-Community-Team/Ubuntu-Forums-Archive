---
title: "Wireless connection on Toshiba laptop"
date: 2008-07-03
forum: Networking &amp; Wireless
---

### Post by johannalb on 2008-07-03
Hi I've just installed Ubuntu 8 on my Toshiba Equiem L40 - 10U (that's what it says on the label). I think my wireless is Atheros AR5007EG, and it's WPA-Personal. I've tried following instructions on other posts and using ndiswrapper/madwifi but nothing seems to work. I'm a complete beginner at all this so please help :)

Thanks

Johanna

---

### Post by johannalb on 2008-07-04
Just bumping this up

---

### Post by Zack McCool on 2008-07-04
The new Atheros isn't supported in Linux yet.  The new madwifi will address it, but unless you want to install beta from tarballs, I would skip it.

That presents you with a new problem...   The drivers that came with your laptop are probably for Vista.  Ndiswrapper needs the XP driver.  You don't have it...   ;)

So, you need to find the right drivers.  I have the drivers for the 5006,and have attached it.  I believe it is the same for your card, so give it a shot.  Install ndisgtk from the repositories, extract the attached tar.gz file to a directory of your choosing, then run the "Windows Wireless Drivers" app from your Administration menu, add the driver, and you should be good to go.

---

### Post by johannalb on 2008-07-04
EDIT:

Ok I found a different version of the net5211.inf which seems to have installed properly (the one you offered didn't seem to work for some reason ..) it says the hardware is present but I don't know what to do now, it still doesn't seem to be picking up the network ...

Thanks
Johanna

---

### Post by johannalb on 2008-07-06
Just bumping

---

### Post by Zack McCool on 2008-07-07
What do you mean by "doesn't seem to be picking up the network"?

When you click on the Network Manager icon on your task bar, does it come up with a list of wireless networks, or does it show none?  

Is your router set up to broadcast the SSID?

---

### Post by kevdog on 2008-07-07
That particular chipset: AR5007EG is supported in Hardy without the use of ndiswrapper.  Do a search on the forums for this number since there have been a lot of articles written about it.  I remember a flurry of things posted about 3 months ago.

---

### Post by BLTicklemonster on 2008-07-07
You might have some luck with this

[http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)

maybe.

---

### Post by Zack McCool on 2008-07-10
> **kevdog said:**
> That particular chipset: AR5007EG is supported in Hardy without the use of ndiswrapper.  Do a search on the forums for this number since there have been a lot of articles written about it.  I remember a flurry of things posted about 3 months ago.

It is not supported by Hardy (as-is anyhow).  There are a number of how-to's on the forums, and I am sure that they are all great, but for a newbie, they will be much harder to follow than installing the wrapped win driver.

They require the removal of the restricted driver that Hardy loads, removal of the restricted driver manager (along with any nvidia or ATI video drivers that may be installed through it), then the installation of the (still beta) madwifi drivers.

[http://ubuntuforums.org/showthread.php?t=795984&highlight=AR5006](http://ubuntuforums.org/showthread.php?t=795984&highlight=AR5006)

These directions will work if you choose to do that rather than wrapped, but I sure wouldn't want to reccomend them to someone that is just starting out with Ubuntu (or Linux in General).

I may, though, consider installing them on my laptop to try them out.  The stupid ATI driver never really worked the way I want it to anyhow (won't work right with my LCD TV), so it will force me to upgrade that, and perhaps fix other issues...   ;)

---

