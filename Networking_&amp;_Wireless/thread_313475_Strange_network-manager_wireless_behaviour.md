---
title: "Strange network-manager wireless behaviour"
date: 2006-12-06
forum: Networking &amp; Wireless
---

### Post by coffeecat on 2006-12-06
I'm not really asking for a solution to this issue; I'm simply curious to know if other people have seen it, but if anyone does know of a fix....

I get this problem in network-manager connecting wirelessly to my router using WPA in both Dapper and Edgy (Gnome) - I've set my laptop up as a multiboot btw. Sometimes immediately after nm connects to my router, or sometimes a couple of minutes after satisfactory working, I find I can't connect to internet pages. I can ping my router and log on to its configuration interface. I can ping external numerical IP addresses OK, but if I ping a www address, I get 'unknown host'. It's clearly a name resolution issue but strangely my ISPs DNS server addresses are showing OK in the router status page.

At first I thought my router was playing up, so I would reboot it and have to reconnect nm and everything was OK. Or, I'd change to my other router. But then I got the same with my spare router and I noticed that my desktop, which has a wired connection, can browse the internet OK at the times when the laptop can't.

Realising that it was nm that was the problem, I now simply disconnect using the nm applet icon and then get it to reconnect after which everything is hunky-dory. But I seem to be having to do this every time I boot up now and I'm sure I didn't have this issue much or at all when I first installed Dapper.

Interestingly, I get a completely different problem with Fedora Core 6 on another partition. With FC6 NM will usually connect (and without the Ubuntu problem) if the battery is almost charged and the recharger is plugged in, but almost never if the battery is at about 50% and no charger. I didn't get this with FC5. :?

All very odd. I know nm is still really a pre-beta, but has anyone any comments? And what about its obsession with the keyring password? Is there any way of disabling that? It seemed to be disabled in Suse 10.1, but I abandoned SuSE after the zen update manager debacle and  now use Ubuntu as my primary distro. Ubuntu is much better anyway. :wink:

---

### Post by ngch on 2006-12-06
You can get network-manager to stop asking for the keyring password through this guide:
[http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring](http://ubuntuforums.org/showthread.php?t=192281&highlight=keyring)

---

### Post by coffeecat on 2006-12-07
Thanks for the link. I'll go through that carefully, because some posters are reporting that updates of a few months ago broke the fix.

---

