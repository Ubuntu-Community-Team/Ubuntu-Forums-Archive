---
title: "Internet not working a short while after booting"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by ddh33 on 2007-01-28
This problem has been bothering me. Around 15-30 minutes after I start up my system, the net starts to become unusable. If I'm downloading stuff I can see speeds dropping steadily until it hits zero. FIrefox will be super slow or time out. But my network connection is still fine (lots of packets being received, ISP's two DNS servers the same as usual in "Networking." So I don't  think they are being lost as described in many posts. 

And I'm still connected on Gaim. I can use "host" in terminal to get IPs of websites...I can't use Synaptic. If I'm downloading software the speeds will drop to zero.

What I have done thus far:

1. Disabled ipv6 system-wide.
2. Firefox tweaks. I followed a detailed post on this forum.
3. Added the two DNS servers I mentioned to /etc/dhcp3/dhclient.conf. I believe they are my ISP's by default because they have always been shown in "Networking-DNS". This might be an unneeded move..I don't know if I should add the public DNSs that some have suggested. There are also quite a few of these DNSs. 

See my signature for system info. It's really annoying to have to reboot once in a while just to use the net. Thanks in advance. :)

Edit: Somehow I don't see my own signature under this post even though it's enabled..maybe because I actually added that after I wrote this. I'm using an Inspiron 6000/Comcast direct connection/DHCP.

---

### Post by Cobikegeek on 2007-01-28
As a test you might see if you have the same problem when you boot from the live cd.  If everything works with the live cd, look at how ubuntu set up your network connection in "system->networking" and replicate that in your installed setup.

---

### Post by ddh33 on 2007-01-29
Anyone else? I also noticed that replugging in the cable helps over half the time. Once, after I entered my password and got into "Networking," then quit without making any changes, the internet started working again..it's so weird.

If you need more info I can post it.

---

