---
title: "wireless is POS"
date: 2008-02-06
forum: Networking &amp; Wireless
---

### Post by cakemaster on 2008-02-06
I have been having an immense amount of trouble with my wireless connection.  The hardware is not defective, I have used it properly in windows but made the switch to ubuntu and it has been less than stable.  I have gotten it to work by following many many tutorials' and forums' instructions but it has never responded exactly the way it was "supposed to."  It has worked, and has, two times, stopped working after having been working.  I do not know what it is doing exactly because it has done things I have not told it to do and occasionally will not do what I tell it to do.  One time (the first time) when it stopped letting me have access to the box from any outside source (I usually will ssh into this machine because of a limited amount of desk space for monitors) I simply turned it off and back on and it reset itself to work and associated itself with my router and so forth.  the second time (this time) I had no such luck and in fact will only get back to the point it was at when I turned it off and on again.  In my router, which I can access from this machine, it gives no local ip and no name but it has a mac address registered.  I have reserved a local ip for the currently nonworking box, and when there were dashes in these fields previously using the reserved ip had worked.  it does not now.  according to iwconfig it has associated with the AP and has the correct mac and the essid it right, as well as the channel.  I have no way of checking net access besides downloading packages because I am running the server edition (yeah, I know wireless is no good for servers, but its for personal use only and if my wireless is down my need for the server is down as well).  If I have a way other than that I do not know it besides pinging someone elses server and as I understand it servers are usually not appreciative of being pinged.  The connection in question has, at one point, worked fully.  the router's attached devices list gave me the correct name and dhc ip of the box, but usually those fields were filled with dashes.  when I try to dhclient it sends on the fallback of 255.255.255.255 or the ip I give (I have tried the router ip and the router subnet mask) and any attempt returns no dhcoffers and then sleeps.  I had to use ndiswrapper for the card to work, but this is probably not the problem since the device appears to work correctly as far as drivers are concerned.  The router is using wpa, and I am running wpa supplicant.  any help?  need more info?  etc...  I appreciate any help.

---

### Post by Hightide on 2008-02-07
Hi cakemaster

I appreciate your frustration but could you provide more information on your setup i.e AP, wireless card/usb  so we can help?

:)

---

### Post by cakemaster on 2008-02-07
The AP is a netgear wgt624 and the wireless card is a zonet pci zew1602a.  For ndiswrapper I took the drivers for winxp from the disk that came with it.  I first tried to use the downloaded drivers but they did not work.  It is a marvell chipset.  I don't believe I mentioned that the AP is using wpa and I used wpa_supplicant.  When it has worked, to any degree, the outputs of commands have not been what they should, and the first time it worked it was a surprise to me and I only found out by chance it had connected.  I was skeptical but accepted it and did not want to mess if it was working after two days frustration.  Any other more detailed information can be gotten, however I will probably need to be told how to get it since I am fairly new to Linux.

---

### Post by cakemaster on 2008-02-08
I am currently reinstalling the OS because I think in my zeal to get things up and running as fast as possible I screwed up my stuff in some way that I was unaware of, seeing as I am still trying to learn how to effectively use this os.  If it works, I will post again, otherwise I will still need help, so if anyone has any suggestions of what to do this time around, let me know.  I figured I had screwed something up when, anytime I went to look at my current configurations with iwconfig the commandline would halt (as in the prompt would move up a line and nothing would be displayed, no new commands had effect and ctrl-c did not break the command, even after a restart this was the case).

---

### Post by kevdog on 2008-02-08
Off topic

I love the title of this thread -- Im sure the mods do not!

---

### Post by Junglizer on 2008-02-08
You should try to use more paragraph breaks.

---

