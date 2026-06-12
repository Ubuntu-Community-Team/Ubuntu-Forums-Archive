---
title: "[SOLVED] configuring Linksys WRT54g v.8.2 wireles router under Ubuntu"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by fullmetalgerbil on 2008-09-16
Awrite, I'm running Ubuntu 8.04 and I have a Linksys WRT54g v.8.2 router. I had previously configured the router under Windows xp (by Configure I mean I downloaded an auto configure program from Linksys, I never actually logged into the router and tweaked things), and then wiped xp and loaded Ubuntu. Everything has worked fine up until last night when there was a cable outage and suddenly no internets. Which was no big deal, I figured the cable would start working again and that would be that.
Well, this morning the cable was on but no internet. So I called the cable company and they checked my modem and everything appeared to be alright-only I couldn't connect to the internet. So I decided to unplug the router and just run straight from the modem. Ere I'm able to write this right now since I was able to connect when I ran straight from the modem to my computer.
So I know its a router problem. I don't think the router totally croaked on me because the lights are still on and it was even getting a signal from the modem. So I just figure that somehow the configuration got screwed up by the outage last night and I need to reset it and reconfigure it. Believe me, I wouldn't even be bringing this here but I called Linksys support and they have basically no idea how to work with Linux. 
And please don't just tell me to type 192.168.1.1 into the address bar and log in to the router and configure it. Thats the whole thing, I have no idea what to do once I'm logged into the router, and no idea whether I have as static IP, if I need to make one, and how.
Thanks ahead of time, my wife and the Linksys tech support dude told me I should just install Windows again to configure the router and then wipe it and reinstall Ubuntu once the router is set. I'm trying to avoid having to take such a blunt insturment approach though.

---

### Post by figmentx on 2008-09-16
Call linksys back and get a different tech, that one pulled what I call an "okie doke"... Linux has nothing to do with router configuration. (Now configuring your linux box to access a WEP enabled network is a different matter).  I assume you are able to logon to the router and get the initial status page right?  If they are asking you to run the cd setup wizard, tell them you lost the disk, but can access the router via browser. Then they can guide you through the menus.

I'm not at home right now, but the linksys website has pretty good setup documentation on their site, follow that, or if still no luck, I'll make another post when I'm home later tonight and can access my linksys menus.

---

### Post by fullmetalgerbil on 2008-09-16
Ok, thanks, I'll see if I can log in to my router start page first and then see what I can find on the Linksys site.

---

### Post by figmentx on 2008-09-16
Ah, ok I thought you were able to logon, you probably already know, but just incase, don't forget that after you reset the router to default, the logon info is:

Username: (leave blank)
Password: admin

Also, who's your ISP? Chances are your assigned an IP by your provider via DHCP, rather than a static ip. (I can tell you for sure, that Comcast and Verizon FIOS are assigned dynamically (DHCP))

---

### Post by fullmetalgerbil on 2008-09-16
It doesn't work. I mean I can't even log into the router. I reset it and it makes no difference. The lights are all on, but nothing happens when I try to connect. I think the router is just fried.

---

### Post by fullmetalgerbil on 2008-09-16
I think I'm just going to take the blunt insturment approach and load Windows until I can get the router configured then go back to Ubuntu. Then I'll have to do it all over again in two and a half weeks when we move and get a new ISP. Pain in the butt but its all I think I can do since I cant even log in to the router.
I'll be really ticked off if I go through all of this and it turns out the router is just broke. Nuh.

---

### Post by figmentx on 2008-09-16
If it's not too late,

Make sure you're holding the reset button on the router long enough, 30 seconds should do it.  When you try to logon, did the logon box just keep popping back at you, or did it give you an error page, if so what?

Then follow the steps outlined on [linksys' site]("http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=3686&lid=7775537401B02")

Make sure to observe all of the "for instructions, click here" type links, they have pictures to show you exactly what should be done.

Good Luck!

---

### Post by fullmetalgerbil on 2008-09-16
Actually, right now I'm back to square one. I tried loading Windows only to be flummoxed by a missing ethernet controller driver. I couldn't even connect to download the driver. So, I'm back to Ubu again and I'm going to have to just configure the router from here. That is, if I can ever log in to said router.
I have all the linksys configuration info now, and I'll try holding in the reset button for a full 30 seconds...however, I get the feeling that its not going to be as simple as that and I won't be able to log in. The last time I tried the login box didn't even appear at all, my browser wouldn't even connect to 192.169.1.1.

---

### Post by figmentx on 2008-09-16
> **fullmetalgerbil said:**
> my browser wouldn't even connect to 192.169.1.1.

Probably a typo, but make sure it's 192.168.1.1 (or [http://192.168.1.1](http://192.168.1.1))

Also refer to the [resetting the router documentation]("http://linksys.custhelp.com/cgi-bin/linksys.cfg/php/enduser/std_adp.php?p_faqid=4008")

Notice Step 3:
If the normal reset does not work, unplug then plug back the router's power adapter while pressing  the Reset button.

---

### Post by fullmetalgerbil on 2008-09-16
Teh eagle has landed! Success! Thanks a bunch figmentx. It turned out I had to log in to the router via 192.168.2.1, but after that it was cake. Now I just have to configure my security settings and all will be well. But that should be fairly simple since I won't be using WEP.
Y'know, its funny, alot of people gripe about Linux because they think the driver support is lacking. I just went from using an Ubuntu installation that worked seamlessly basically "out of the box" with a minor amount of work, to using a Windowsxp installation that that didn't have onboard drivers for my Ethernet controller, audio and a number of other devices. Then I load Ubuntu again and everything as far as my devices just works right away with zero effort needed (of course I have to put some effort into twealing everything "just so" but thats the joy of it)

---

