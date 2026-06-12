---
title: "Help: Broadcom 4306 in Ubuntu 7.10"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by NHansen on 2007-12-20
Ok, so I have a Dell Inspiron 5160 with a Broadcom 4306 rev03 wireless card.
I did a fresh install of Ubuntu, then tried to use fwcutter. It worked great, except for the fact that it wouldn't connect to any networks. I could see them, but it always got stuck at "Acquiring IP..." using wifi-radar.

Then I tried a bunch of the ndiswrapper tutorials, but none of them finished because most of the ones I saw required you to have an internet connection.

Fearing that I just jumbled everything up, I am about to install Ubuntu 7.10 again and try fresh.

So, for someone that has NO internet in linux (but has internet access on a windows computer with USB drives) - how in tarnation can I get this to work properly?

I got real excited when the fwcutter (almost) worked. Is there something else I should have done?

I know many people have this problem, but I can't even try a lot of the tutorials because of my lack of internet in linux.

Please help.
Thanks.

---

### Post by jan quark on 2007-12-20
my solution for this problem was to switch completely to static ip addresses. its not very elegant but i can post this now. for me the fwcutter thing worked fine, but when i update the cutter software via the update manager internet connection broke down. I am still looking like you for a solution for this issue.

---

### Post by NHansen on 2007-12-20
what do you mean by using a static ip?
I pretty much don't know what I'm doing here, which makes this all worse.
I mean I wasn't even positive as to what settings I should have put in wifi radar for my WEP Connection, but I tried all sorts of combos...

---

### Post by NHansen on 2007-12-20
ok weird, i was going to reinstall ubuntu, but I tried modprobe -r ndiswrapper then modprobe bcm43xx - just for kicks. and it worked...
the connection is real crappy right now tho... but hopefully it wont crap out like everyone else says happens

---

### Post by josephmc on 2007-12-22
i've been having the same problem. i can't connect to a wireless network with encryption. it won't obtain an ip address via dhcp. if i turn wep off on my home network it works just fine. i even tried switching to WICD.

if i setup the wireless from the command line it works flawlessly
> 
iwconfig eth1 essid wirelessnetwork enc blahblahblah
sudo dhcpclient(probably not real command...i'm in windows right now) -t 10 eth1

i'm sure it would work if i set it up through /etc/network or whatever it is too but that is really impractical. 

this has been really frustrating. i have built in wireless and i'm having to wire up. any help would be MUCH appreciated!

---

### Post by David Valentine on 2007-12-24
NHansen:  have you tried using the restricted driver manager?  It works like a charm for my Broadcom 4306.

josephmc:  try putting quote marks (" ") around your WEP key.

---

