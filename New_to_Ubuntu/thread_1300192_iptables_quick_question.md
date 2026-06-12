---
title: "iptables quick question"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by Rayve on 2009-10-24
Hey all,

I know there are threads out there already about iptables, I've scanned some of them and I found a really great "how to" by bodhi.zazen (yay, I'm loving the guides bodhi makes) but right now, I just need to make sure I get my netbook working fast, then I can get down to the serious reading. (Sorry, I hate making new threads when I know there are similar ones out there, but most I found are "solved" and a bit old, and don't describe my issue...)

I just got my Starling the other day, so it's running Ubuntu Netbook Remix 9.04.  Finally got the wifi working and connected to my home wireless network, but I can't load anything from the internet - email, firefox, Synaptic downloads, nothing.  I could do this when I first got the system, but my first shut-down after the newest update caused the issue where I had to get a wired connection and download updates / driver updates.  Connection is there, but Internet is not. (thread here: [http://ubuntuforums.org/showthread.php?t=1298997](http://ubuntuforums.org/showthread.php?t=1298997))

I'm thinking (no clue if I'm even close) maybe an iptables thing, since I have a solid connection but no actual Internet capability?

(this is really badly done code, as I'm looking at my netbook output and typing it in my desktop here)
```

INPUT (policy ACCEPT 13 packets, 1641 bytes)
ACCEPT   in        out    source        destination
(4 lines)  wlan0   any  anywhere   anywhere

FORWARD (policy ACCEPT 0 packets, 0 bytes)
ACCEPT   in    out       source            destination
(4 lines)  any   wlan0  anywhere        10.42.43.0/24   state RELATED, ESTABLISHED
              wlan0 any     10.42.43.0/24 anywhere
REJECT  any     wlan0   anywhere        anywhere        reject-with icmp-port-unreachable
REJECT  wlan0   any     ""                      ""                     ""

OUTPUT (policay ACCEPT 13 packets, 1641 bytes)
<no data under the headers>

```For comparison, here is my desktop's iptables:

```

Chain INPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination

```Since my desktop obviously works just fine, should I flush the iptables setting on my netbook?

Running to work now, but will check on this when I get home in the morning, and then do some heavy reading on iptables this week. :)  Thanks, all!

---

### Post by 101011010010 on 2009-10-24
Hello there,
You could just enable UFW (Uncomplicated Firewall) in the terminal and set it to deny. Then anything you initiate will be allowed back in.> sudo ufw enable > sudo ufw default deny You could then take your time to learn iptables.
I hope this helps.

---

### Post by Rayve on 2009-10-25
Thanks for the ufw info (scanned the man page, it does look uncomplicated!) but it didn't help the Internet issue.  I'm still getting a "Address not found" error whenever I try to load a website - google, ubuntu, anything.  Says it can't find the server.

---

### Post by Rayve on 2009-10-26
Anyone have any ideas?  I did the 

```
 sudo ufw default deny 
``` 

and still no luck...

---

### Post by 101011010010 on 2009-10-26
Hello there again,
I'm wondering if the ip table commands are still causing a problem. Try turning off the firewall > sudo ufw disableThen flush the rules> sudo iptables -FThen try to connect to a trusted site (before turning the firewall back on). If that doesn't work the site might be down so try a few others.
I hope this helps.

---

### Post by Rayve on 2009-10-26
Thank you for the reply.  :)  I tried those command (disabling ufw and flushing iptables) and then rebooted.  No luck.  Says "address not found"...

I have been doing some google searching and forum reading, and I think that my /etc/resolv.conf should have something in it for DNS, right?  (I know so little about this stuff still, so not sure.)  I see what my desktop has via

```
 cat /etc/resolv.conf
```and then copied that (there were 2 entries) into my netbook's /etc/resolv.conf and saved it (via sudo), but every time I reboot, the file is empty.  Could that be an issue?

Thanks again for your efforts!

EDIT: I talked with a friend of mine, and he said to do a ```
 netstat -nr 
``` and see what that gave - I had 2 destinations and 2 genmasks, but gateways were all 0.0.0.0.  He also mentioned that dhcp will overwrite my /etc/resolv.conf file every reboot.  I did find a way here [http://forums.debian.net/viewtopic.php?t=7239](http://forums.debian.net/viewtopic.php?t=7239) to disable that, but I did some more searching and also found this: [https://calomel.org/dhclient.html](https://calomel.org/dhclient.html)

I ran ```
 sudo dhclient wlan0 # where wlan0 is the name of my wireless given by iwconfig 
```

It gave some lines about DHCPDISCOVER, DHCPOFFER, DHCPREQUEST, and DHCPACK as it went through my router and back again, and voila, I can now see Google and UbuntuForums and other sites on my netbook.  

Firewalls are enabled again, rebooted, everything is still working nicely.  :)  I had to run dhclient wlan0 again to get internet up and going, may look for a way to get it to do so automatically, but we're in business.  Hope this helps some other folks!

---

### Post by 101011010010 on 2009-10-26
Hello again Rayve,
It seems that there are a few problems with different hardware and System 76. May be you should start a thread in that section of the forum, they seem very helpful and will know alot more about the problems that arise. If you mention the specific network card/s and modem/router names and info , they might be able to help you. I'm afraid that I can't think of any other ways of helping, sorry.
Good luck and I hope you get everything working quickly.

---

### Post by Rayve on 2009-10-26
I edited my post above - all is working now.  :)

Thank you!

---

### Post by 101011010010 on 2009-10-26
Hello again Rayve,
I just had a thought (almost fell off my chair).
Have you set your User settings, there's an option under Properties to allow connection to internet with a modem and to use modems (lower down the list). There's also an option to connect to wireless and ethernet networks.
System> Administration> Users and Groups. Click on "click to make changes", enter password. Click the Properties option and they're on the User privileges Tab.
Just a thought, I'm glad you got it working.

---

### Post by Rayve on 2009-10-26
I made sure to tick the "Available to all users" box on the settings of the wireless connection, right-clicking on the wireless icon and then "Edit Setting".  I should know that an icon menu is no substitute for a true settings change though, heh, my sound issue taught me that!

Thank you for the advice - I went to check it out, but the User Settings in Users and Groups is greyed out so I can't change anything.  I'm assuming I must do this as root?  I know gksudo nautilus but that gives me filesystem browsing, not settings changes, and I did enter a password... nevermind.  "Unlock" button ftw.  :P  Checked that off, thank you!

---

