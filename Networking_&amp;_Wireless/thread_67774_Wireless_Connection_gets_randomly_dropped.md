---
title: "Wireless Connection gets randomly dropped"
date: 2005-09-21
forum: Networking &amp; Wireless
---

### Post by Lem on 2005-09-21
I've been happily running Hoary for a few weeks now, but find that my wireless connection occasionally goes down and won't restart (I've tried restarting manually too).
If I reboot, everything is fine. I've locked my resolv.conf file with chattr +i to stop it being changed (my first problem - quickly fixed)
What's really odd is this doesn't happen on a fixed timescale - sometimes it's fine for a few days, sometimes just a few hours.

I'm running Hoary 5.04 on an Via Epia M10000 with a netgear WG311v2 WLAN PCI card.

Any ideas?

---

### Post by Lem on 2005-09-22
I've had a search on the forum and I've yet to figure out what's causing this..

---

### Post by rschouten on 2005-09-22
I am having a similar, if not the same, issue. I just bought a brand new Thinkpad and wireless router and can't seem to keep my wireless connection up for very long. It seems random at this point too (although my connection lasts for hours, but never days). I too must restart in order to get back on the network.

I am running a Thinkpad R51 with Centrino chip set.

Just out of curiousity, what type of wireless router are you using?

P.S. Sorry to get your hopes up with a possible answer. If you make some progress please post it.

---

### Post by Lem on 2005-09-22
I'm using a DLINK G604T router.

Problem seems like it might be where the dhcp renews my ip.. but not sure.

---

### Post by Lem on 2005-09-23
Well i've tried running GTK Wi-fi and setting my IP to static on the router, but it's still going down.  :? 

Mildly irritating, rather than a no-go situation, but when everything else works perfectly, it's a bit of a shame.

Should I not use DCHP? - can't think of anything else. Always worked ok in Windows.

---

### Post by mit on 2005-09-24
Hi,

I had/ am having the same issues with my Centrino based laptop. As I am a newbie to *nix it is probably something I have/haven't done.  [-X 
What I don't get is that during the text based set-up it detects both 10/100 and the Centrino wireless 2200G and asks which one to use to update Ubuntu.
It asks for the WEP key but says it is incorrect even though it isn't.  :-? 
Then, when using it with via the 10/100 wire it sometimes drops so i think it must be a driver issue. 
Anyone else having trouble with both wired and wireless set-up's on their Centrino?

Mit

---

### Post by xristos on 2005-09-24
If you are using your interfaces to bring up a ppp interface then in /etc/ppp/options comment out the lines with lcp-.............

---

### Post by mit on 2005-09-24
Thanks for your reply. Do i type this at the bash prompt?

---

### Post by xristos on 2005-09-24
In a terminal type ```
sudo gedit /etc/ppp/options
``` 

and put # in front of lines that start with the word lcp-request or something like that

---

### Post by Lem on 2005-09-26
Seems to working (so far)... thanks xristos.. you're a star!

---

