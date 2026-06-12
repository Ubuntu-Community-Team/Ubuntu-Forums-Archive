---
title: "Wireless Manual Configuration"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by AntiHeroJoe on 2008-03-13
I'm having issues with my wireless configuration. I'm in an area where there are quite a few wireless networks, and some are open. If for whatever reason my network cuts out, Ubuntu auto-connects to an open network. To try and curb this, I shut off roaming for my wireless and manually entered the wireless info and checked the wireless checkbox in the network manager. But now it doesn't connect at all, and the icon just sits there saying "Manual Configuration". No connection bars, nothing. If I right click the icon, there is no longer an Enable Wireless item/checkbox, as with roaming this would exist! HALP!

(CHALLENGE MODE: How can this be fixed without terminal or editing text files? GUI only!)

---

### Post by handydan918 on 2008-03-13
> **AntiHeroJoe said:**
> I'm having issues with my wireless configuration. I'm in an area where there are quite a few wireless networks, and some are open. If for whatever reason my network cuts out, Ubuntu auto-connects to an open network. To try and curb this, I shut off roaming for my wireless and manually entered the wireless info and checked the wireless checkbox in the network manager. But now it doesn't connect at all, and the icon just sits there saying "Manual Configuration". No connection bars, nothing. If I right click the icon, there is no longer an Enable Wireless item/checkbox, as with roaming this would exist! HALP!

(CHALLENGE MODE: How can this be fixed without terminal or editing text files? GUI only!)

I have a four-letter word for you. 

WICD

---

### Post by igotit on 2008-03-13
hello and may be you can help me, i can not get my ubuntu to notice my wi fi  how do i get drivers to it its resticted and will not let me enable it

---

### Post by AntiHeroJoe on 2008-03-13
> **handydan918 said:**
> I have a four-letter word for you. 

WICD

WICD for some reason couldn't connect to the network I wanted, so I tried reverting back to network-manager...and forgot network-manager-gnome along the way. Without the internet it was really quite difficult to get this package. I ended up having to use someone else's WinXP machine to research what to do and manually download/install the package via thumb drive. How humiliating to have to use winXP :roll:

---

### Post by ourblu on 2008-05-27
> **AntiHeroJoe said:**
> I'm having issues with my wireless configuration. I'm in an area where there are quite a few wireless networks, and some are open. If for whatever reason my network cuts out, Ubuntu auto-connects to an open network. To try and curb this, I shut off roaming for my wireless and manually entered the wireless info and checked the wireless checkbox in the network manager. But now it doesn't connect at all, and the icon just sits there saying "Manual Configuration". No connection bars, nothing. If I right click the icon, there is no longer an Enable Wireless item/checkbox, as with roaming this would exist! HALP!

(CHALLENGE MODE: How can this be fixed without terminal or editing text files? GUI only!)

Hey Joe, I had the same problem (as a matter of fact, I've had a hell of a time the past two days getting wireless to work the way I want it to work on my new server). Anyhow, I ran into the same situation you did. My wireless worked fine in roaming mode, but when I tried to perform a manual configuration I was unable to connect. But after I restarted networking everything worked fine (honestly I was not aware of this command as I'm still a newb to Linux):

sudo /etc/init.d/networking restart

After performing that command, your network interfaces should be restarted. Now enter this following command to see your connection stats:

iwconfig

Assuming your network device is wlan0, you should see the "Link Quality" (the bars), as well as some other connection stats. Now try connecting to a website. Hope this works for you.

---

