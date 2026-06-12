---
title: "Thrilled, but puzzled"
date: 2007-06-13
forum: Networking &amp; Wireless
---

### Post by leegwebb on 2007-06-13
After 2 months, I am finally soo close to having exactly what I wanted re Wifi with a Broadcom 4306 card.  I'm not interested in rehashing all the steps I went through except to point out, as others also have, that there are about 17 different threads with sets of instructions on this forum and it was extremely frustrating (this doesn't begin to describe it) to have tried many of them to no avail before finally finding a method of installing fwcutter and 43xx that worked.  

One strange thing happened.  I should say that I am running Xubuntu Dapper on a Thinkpad i1200 with 64MB RAM.  The only way I had to get this computer online without buying something new is via the PCMCIA card I already owned, because I have no dialup and it has no ethernet.  

I was finally able to achieve this by borrowing an Orinoco card from a friend.  This card was immediately recognized and operational at bootup with no configuring, etc.  I entered my ssid and network key once and from then on always had a connection.  Using this connection, I was able to download what I needed to get my own bcm 4306 card working.

However, though the card activated upon startup, I no longer enjoyed automatic connection to the network.  I had to go into network-admin and deactivate the interface, then reactivate it every time I started up.  It remembered my settings, but still, this was an extra step I prefer not to have to do.

I tried Wifi Radar, which always immediately (after trying for no more than a second) replied "could not get ip address."

So I read a few more posts, which suggested using Network Manager.  I installed Network Manager using Synaptic, and now, it works just as I wanted it to.  When I start up I am connected.  My only problem is that I can't find Network Manager in any application menu, and there is no applet running on my desktop, which some of the posts described, where I should be able to see the strength of the signal, etc.  I can't even confirm that I am connected to my own ssid and not some unsecured network in my neigborhood, because there is no list of available networks, etc.

I also have a better computer that I run Ubuntu Feisty on, and, while it does connect automatically when I startup, I can always click the network icon in the corner to see the strength of my signal and other networks, etc.

Sorry for such a long post on such a small problem (especially given what I had to go through to reach this point) but if anyone could tell me how to make Network Manager visible, my wifi setup would be perfect.

And (and I know I am repeating what other posts have said) PLEASE SOMEBODY build some support for bcm cards into future Ubuntu releases.  It took me about 100 hours to sift through all the posts that claimed to be the definitive solution to the bcm problem until I finally find the method that worked.  MEPIS 6.5 autodetected this card and it worked with no configuration other than manually entering the ssid and network key.  Why shouldn't it be so easy in Ubuntu?  The only reason I stuck with Xubuntu for this computer was that MEPIS doesn't have a version light enough to run well in 64MB RAM.

Thanks for what is othewise a great OS that has given a new life to this old clunker!  It now vastly outperforms my third laptop which is much newer, ostensibly faster and better-RAM-endowed but is still. alas. burdened with XP and all its bloat.

---

### Post by dmizer on 2007-06-13
you should be able to right click on one of the panels in the notification area (near the system time) and select "add to panel" network manager should be in that list.  if not, you can add it using the "application launcher" button.

it's definitely a pain trying to sift through all the various howtos.  when doing so, it's important to pay attention to the post date, and most recent edit to the howto.  obviously the more recent the better, though you can glean good information from older howtos on some occasions.

---

### Post by leegwebb on 2007-06-13
Network manager is not in the list of available items to "add to panel" nor can I find it to add to an application launcher menu.  There is a utility called Xfce Appfinder that lets you search for apps.  Network Manager is not found.   I know I installed it with Synaptic, and I know that my network connection was not working before I installed it and now it is, but it appears to be completely invisible.

---

