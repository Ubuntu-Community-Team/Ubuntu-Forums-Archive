---
title: "lost wired internet connection 10.10"
date: 2011-02-08
forum: New to Ubuntu
---

### Post by jumpingjaxs on 2011-02-08
hi there,

have a desktop with ubuntu 10.10 (recently upgraded from 8.04 with help of a local volunteer tech and his live cd).
my computer is connected straight to a modem. 

the day after the upgrade things seemed fine. i used the internet for a few hours, installed VLC and imported my bookmarks. 
but then while browsing online, internet suddenly disconnected. ethernet cable etc were all in place. rebooted. internet was connected again. used for little while longer, shut down.

next day booted computer, no internet. cables all in place. tried repowering modem and rebooting computer. tried ping thing, immediately failed. phoned my isp (shaw cable) -they said my modem is online but i have no ip address. they offered no further help because unfamiliar with ubuntu, but suggested to upgrade drivers.

i believe my ethernet (card?) is RTL 8139/8139C/8139C+, but i cannot find how or where to upgrade the driver for this, incl the realtek site.

have been searching forums and google for couple days now with no luck. had ubuntu for awhile but im extremely new to troubleshooting .. any step by steps and patience would be greatly appreciated.
ive used the terminal a little bit.

thx so much

---

### Post by Aetherith on 2011-02-08
Ok for starters let's try disconnecting all power and network cables  from the machine and letting it sit for a moment.  It seems that  something that has come out recently gets Realtek NICs stuck and  refusing to access the internet.  This happened with my laptop (also  10.10 w/ Realtek NIC) and this idea "unstuck" it.  It's a long shot but  worth a go anyway.

Next, do you have another machine you know works that you can test the  PC->Modem->Internet link?  It's still possible the problem is on  Shaw's end so we need to rule that out first.  So if you can get another  machine connected to the internet without issue then we can probably  discount your ISP as the problem.

After that I'd say hook up your Ubuntu machine and set it to ping Google  continuously and wait until it drops (assuming you can get it to  connect at all).  When it drops stop ping and post up the results of  "ifconfig -a" so we can see what your machine is doing IP wise.  Also  have you ever set it to a static IP (you pick the settings instead of  getting them through the modem from Shaw)?

---

### Post by jumpingjaxs on 2011-02-11
Aetherith,

thanks for your reply. i hadnt been able to re-access the forum til now cause the laptop i borrowed to connect also went offline. which reminded me my desktop was connected first through a router, and TheN to the modem. (sigh, what a dunce i am)
so i am back online, as ive linked the ethernet cable directly now. 

i guess i can mark this solved and move on to diagnose my wireless router issue.

btw, i had been trying to set up a static ip, reading some guides/ tutorials, but i cant quite figure it out. do you know how to do it on 10.10?

---

### Post by Aetherith on 2011-02-11
To set up a static IP you go to Preferences -> Network Connections then pick the connection you want a static IP for and click edit.  That'll pop up a new window for the connection you're editing and you'll want to select the IPv4 Settings tab at the top of the window.  Then in the Method dropdown select Manual and hit Add next to the Address text box.  Fill in the IP, Netmask, and Gateway you want along with a DNS server or two (either use the ones Shaw provides or I believe Google DNS is 4.4.4.4 and 4.4.4.8 ).  Hit Apply and close out of the dialogs and that *should* set you up the way you want.

One warning however, don't try setting up a static IP when connected directly to your modem because odds are Shaw hands out modem IPs through DHCP and unless your modem turns your public Shaw IP into a private IP, there is a chance when your IP changes it will conflict with someone else's machine and you will lose network connection again.  Good luck!

---

### Post by jumpingjaxs on 2011-02-11
oohk,

but how do i know what numbers to "Fill in the IP, Netmask, and Gateway you want"?

---

### Post by Aetherith on 2011-02-11
Well that depends on whether or not you're sitting behind a router.  If your setup looks like this:

(Internet) -> Modem -> Router -> PC

then you probably will need an IP of 192.168.0.x a Netmask of 255.255.255.0 and a Gateway of 192.168.0.1.  Best bet however is to connect up to your router and have it set everything up through DHCP just to make sure you've got the right address range because some routers use 192.168.1.x or 192.168.2.x as their address ranges.  Once you know the right address range (Terminal and "ifconfig -a"; look for the address for eth0 most likely) then everything else is effectively the same.  However if your setup is:

(Internet) -> Modem -> PC

you may have to keep DHCP on because you're probably getting a public IP from Shaw.  As in it's not a 192.168.x.x private address.  Although if you've got a 192.168.x.x address while connected up to your Modem you don't need to worry and can set up static IPs as much as you like.  Just be sure to never assign two machines with the same IP or you'll have issues.

---

### Post by jumpingjaxs on 2011-02-12
thx much for your help Aetherith, once i solve my router probs il try the static ip setup.

take care !

---

