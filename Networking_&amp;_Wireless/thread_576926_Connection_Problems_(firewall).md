---
title: "Connection Problems (firewall?)"
date: 2007-10-15
forum: Networking &amp; Wireless
---

### Post by aliencam on 2007-10-15
SUMMARY of post, because people always see my posts are long then just go away: 

I can't make good connections in bit torrent or p2p clients and i tried using firestarter to fix it.  I also can't connect to ssh or VNC. It is not a router issue. 




Full Problem Description: 


I am having problems connecting to bit torrent and p2p networks.  I know that everyone will say "well just buy your music then" but that's not even the issue  here.  I am downloading linux distros and things like openoffice.  

When I use bit torrent clients, I only get a few connections, usually under 10 combined for peers and hosts, no matter how popular the torrent is.  In addition to this, I get downloads usually under 5 kbps.  

This is NOT a router problem.  I am in a school dorm room (ASU)  and it works for everyone else.  To test it out I downloaded the same torrent on my computer and my romate's comptuer while we were both on wireless, he has Mac OSX, and was able to connect to more than 100 peers and hosts, while I only got a few.  The OSX computer also was not labeled as "firewalled,"  (yellow dot in bit tornado) while my computer always seems to be firewalled, usually upload speed is only 1 or 2 kbps.  I then later used the wired connection available, on my computer, and my girlfriend's Windows Vista laptop, on a different torrent, and I had the same issue, while the Windows computer was able to work perfectly.  

When I try to use soulseek (a p2p network) (actually the program is nicotine-plus) i  connect for about 15 seconds, then am disconnected and reconnected infinitely, never making a connection longer than one second. 

Also I have tried the "Sheilds Up!" online network vulnerability scanner, and it shows that my computer is "invisible" and each port scanned is reported as "stealth" instead of closed or open. (while windows machines I have tried this on on the network do not show up  like this) 

I am unable to connect to my computer via SSH, VNC, and the ubuntu remote desktop application. I have followed all instructions and guides that I can find. 




What I Have Tried to do:


This issue happened to me over 3 different reformats and reinstallations of Ubuntu feisty, and one upgrade to gutsy.  I did not make a firewall as far as I can tell. 

I have installed the firestarter app through synaptic and tried configuring my firewall.  First I tried making a reasonable firewall, opening the ports that bit torrent uses in general, then opening the ports that my specific bit torrent client uses, also opening the ports that nicotine (soulseek) uses.  none of this worked.  

After making the reasonable firewall allowances, I used firestarter to open every single port, i made a rule allowing ports 1-99999 for all hosts. this still didn't work, and I still got the "stealth" rating when I used the Sheilds Up! scanner.  




Maybe the issue?: 

When I shut off my computer, I see the messages that would show in startup if it were not for the GUI, and I see "Starting Firestarter firewall:    [FAILED]"   among all of the others that did not fail.  maybe this is the issue?  but I still shouldn't have to use firestarter to open ports that I never closed in the first place.  I have heard something about iptables, but as far as I understand it is just the command-line version of firestarter (er, firestarter is the GUI version of iptables). however, firestarter should be doing the same thing that iptables does from what I understand.  

I do not have a firestarter ap running right now, I only ran it to configure the firewall, and I had the problems while it was running, so the only difference now is that i am having the same problems without running the program. 


I do not have problems using firefox, thunderbird,  update, AIM or other instant messaging programs. 


I am using Ubuntu 7.10 Gutsy Gibbon upgrade (i used update manager to get this from being in feisty)

---

### Post by ruibernardo on 2007-10-15
If you see a message saying "Starting Firestarter firewall:    [FAILED]", then you should run the Firestarter Wizard again and select the right network interface. I'm guessing that you didn't run it or maybe you didn't end its configuration or maybe you didn't configured with the right options like DHCP and/or others, depending on your network configuration.

Open Firestarter in the System, Administration, Firestarter menu, then inside Firestarter run the Wizard (on the Firewall menu, first option).

---

### Post by aliencam on 2007-10-15
I retried that, enabling DCHP, and making sure the device was ETH0 not eth1 or eth1, this worked to fix the p2p, but not the bit torrent...  so it's a partial solution, but p2p isn't important to me...

---

### Post by ruibernardo on 2007-10-15
Make sure you torrent client is using the default torrent ports and open the inbound ports in Firestarter (I think bitorrent ports are already on the list of services you can open). For a complete Firestarter tutorial, check [this very good tutorial]("http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html") about it.

As you are working with wireless, and it might not be always available ("come-and-go" network interfaces), take a look at this thread too: [How-To: Firestarter on startup (better & safer way)]("http://ubuntuforums.org/showthread.php?t=542756"). It should help you if Firestarter is failing to start because the network interface is not ready.

---

### Post by darkpark on 2007-11-23
I hope nobody minds if I butt in for a second :)  I have a similar problem.
How/where do I check to see if port 999 is open in Ubuntu?  I already have that port forwarded to my machine on my router.   Three different bit torrent clients fail to listen on that port (gnome bit torrent, deluge, and opera's built-in bit torrent).

ps: I'm not using firestarter or any other firewall s/w.  I have a fairly clean installation of gutsy gibbon.

---

### Post by zetetic on 2007-11-27
> **aliencam said:**
> After making the reasonable firewall allowances, I used firestarter to open every single port, i made a rule allowing ports 1-99999 for all hosts. 

99999 ports???
There are only 65535 ports (1-65535).
Why are you saying that there are 99999 ports?

Are you trying to say that Firestarter allowed you to open 99999 ports??

I don't use Firestarter any more, but, if this is true, than Firestarter is indeed a crap application; uninstall it.

regards
zetetic

---

### Post by aliencam on 2007-11-27
hmm... yeah. it did allow me to open 999999 ports. it won't let me do 7 digits of 9s but it will let me do 6...

---

### Post by zetetic on 2007-11-30
Well, my advice is: avoid Firestarter.

If you have a couple hours to spend, learn iptables and create your own firewall script.

---

