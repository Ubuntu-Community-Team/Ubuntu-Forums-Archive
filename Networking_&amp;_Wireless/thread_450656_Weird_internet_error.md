---
title: "Weird internet error"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by Repsa_Jih on 2007-05-21
I am currently encoutering a really weird internet error. I am on a DELL Inspiron 6400, Fiesty Fawn. I can currently connect to the internet, however: there seems to be some error sending packages :S

I can ping to all sites. But actually browsing sites only works for a few. The sites which loaded were: google.com, gamefaqs.com Well, there might be other sites that work too.

On all other sites, errors are encountered. Firefox says "Waiting for ubuntuforums.org..." indefinitely. wget doesn't work too. Please help me, I really want to get away from Microsoft ASAP :P

---

### Post by lloyd_b on 2007-05-21
Some websites work, while other don't, could possibly be a result of an "MTU" issue.  "MTU" (Max Transmission Unit) specifies the maximum size of a packet.  While the internet is *supposed* to "fragment and reassemble" packets that are too large for a given segment, there seems to be a number of ISP's that simply drop packets that exceed a certain size.

(The following assumes your primary network interface is "eth0" (which it may or may not be).  If you're using a different primary interface, simply substitute that for "eth0" in the instructions.) 

In a terminal window:
```
sudo ifconfig eth0 mtu 1400
```
Then test to see if those websites are working.  If not, repeat with 1300, 1200, etc, until you reach 500.  If things haven't started working by 500, then I'm guessing wrong as to your problem.

Lloyd B.

---

### Post by coolclassic on 2007-05-21
I had the same problem it was fixed by editing the following file /etc/sysctl.conf the following line needs to be entered into this file:

net.ipv4.tcp_window_scaling=0

save file

and in a shell 

sudo sysctl -p

to reload file

have a look here for further info

---

