---
title: "precompiled slmodemd; wvdial; error: NO CARRIER but not always"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by towsonu2003 on 2005-10-14
Hi,
I read some of the slmodem threads here but it seems everyone is using the slmodem they compiled using the ubuntu packages. My situation is a bit different so I wanted to post a new thread.

To connect, I am using a precompiled slmodemd I received from discuss@linmodems. Basicaly, to connect all you do is to download the zipped slmodemd and do
sudo ./slmodemd --alsa -c USA modem:1
then
sudo wvdial

In a previous thread to laptop support (with no reply), I mentioned that this particular modem works only in ubuntu, which is weird.

My current problem is: 
Statistically speaking, in every 5 dialup attempt, 3 exits with "NO CARRIER". (In other distros, all 5 exited with "NO CARRIER".) 

I was wondering whether anyone had any idea why this could be the case. 

PS. I have been trying to solve this NO CARRIER for a couple of months now with other distros with no success. So I'm hopeful that ubuntu will be my answer...

PS2. Let me now if you need any output. As for tail -f /var/log/messages, pppd won't start at all (i.e. no messages) if I get the NO CARRIER error.

---

### Post by Duo on 2005-10-15
I used to get a similar error.  I appeneded *Carrier Check = No* to the end of my wvdial.conf, and it worked fine. I don't know i you have tried this or not, but it worked for me. ;)

---

### Post by towsonu2003 on 2005-10-15
Yes, I have that in wvdial.conf. I also have Stupid Mode = Yes, if it's relevant...
But NO CARRIER still appears 3 in 5 trials. Thanks for the idea though :)

---

