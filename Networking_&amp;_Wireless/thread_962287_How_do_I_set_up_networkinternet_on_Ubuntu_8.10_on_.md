---
title: "How do I set up network/internet on Ubuntu 8.10 on my school's network?"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by riahc3 on 2008-10-29
Hey

Im trying to connect to the network/internet of my school's network but I can't seem to get it to work. Under Vista, it works perfectly.

Some details (under Vista):

Obtain an IP address automatically
Default gateway: 195.235.113.3
Use the following DNS server addresses:
Preferred DNS server: 192.235.96.90
Alternate DNS server: 195.235.113.3

In "Advanced..."
DHCP Enabled
Default gateways:
195.235.113.3 metric automatic

---

### Post by ad_267 on 2008-10-29
How are you trying to set it up?

You can right click on the network icon in the panel and select edit connections, then edit your network and you can set those options under IPv4 Settings.

---

### Post by riahc3 on 2008-10-29
> **ad_267 said:**
> How are you trying to set it up?

You can right click on the network icon in the panel and select edit connections, then edit your network and you can set those options under IPv4 Settings.

I tried and

1: Im not sure If I did it correctly
2: There were some options that I believe are not there or Im not sure how to find it.


Is there any way I can write (or someone can help me write) a shellscript to automatically configure it when I run it in Ubuntu?

---

### Post by ad_267 on 2008-10-29
If you want to set up a script to do this I think [this guide]("http://ubuntuforums.org/showthread.php?t=571188") might help, although it does seem a bit complicated.

It should be possible to get this working with the gui tools though, one of the main focuses of 8.10 was in making connecting to wireless networks easier.

---

### Post by riahc3 on 2008-10-30
I couldnt get it to work with the GUI.

Ill post SS in Vista of what I want to do exactly...

---

### Post by riahc3 on 2008-10-30
[img]http://img363.imageshack.us/img363/6595/19767375gl0.jpg[/img]

[img]http://img363.imageshack.us/img363/7950/89055859en2.jpg[/img]

[img]http://img353.imageshack.us/img353/1169/79029945vr4.jpg[/img]

---

### Post by ad_267 on 2008-10-30
Does this work, or does it not let you leave the Address and Netmask blank?

I'm a bit confused now myself because it seems like if you set the method to DHCP you can't set the default gateway.

If that doesn't work you could try setting the default gateway manually as described in [http://ubuntuforums.org/showthread.php?t=677626](http://ubuntuforums.org/showthread.php?t=677626)

---

### Post by ad_267 on 2008-10-30
Edit: Duplicate post.

---

### Post by riahc3 on 2008-10-30
> **ad_267 said:**
> Does this work, or does it not let you leave the Address and Netmask blank?

I'm a bit confused now myself because it seems like if you set the method to DHCP you can't set the default gateway.

If that doesn't work you could try setting the default gateway manually as described in [http://ubuntuforums.org/showthread.php?t=677626](http://ubuntuforums.org/showthread.php?t=677626)

Yes you can set the default gateway using DHCP.

Thanks for your help (and Ill see that thread) but please leave this to someone that truely understands.

---

### Post by riahc3 on 2008-11-05
Haven't got this to work yet; Any more help?

---

### Post by karlatsaic on 2008-11-05
Looking at this, there is not enough information to really help. I presume this is a wireless connection? With 8.10, you really shouldn't have to do anything. Ensure that Multicast DNS Service discovery is checked under System/Administration/Services. If you upgraded from an earlier ubuntu, your /etc/network/interfaces file may have stuff which needs to be cleaned out. Make sure your /etc/network/interfaces only has 2 lines in it:
> auto lo
iface lo inet loopbackWhen I am at a public place, like a school, library, cafe, airport, ... the Network Manager figures everything out and creates a network profile on the fly, called something like "Auto networkName", where networkName is the SSID of the wireless network. So is this a wireless or a wired connection? The only reason I set up wireless profiles is to put in authentication information and to save it away. If you do create an editable connection, and you choose Manual as in the attachment (Automatic (DHCP) is recommended default), you need to put in a static IP address, netmask, and your gateway. I actually find ubuntu 8.10 easier than Windows as you ideally don't do anything - it just connects. Presuming this is a wireless connection you're trying to make, does the wireless network show up when you click on the Network Manager icon? Equivalently, you should see it with the output of 'iwlist scan' per [the guide]("http://ubuntuforums.org/showthread.php?t=571188") mentioned above. If you really want help, please describe the behavior of what you do and what happens when trying to connect. The output of 'lshw -C network' , 'iwconfig' (no arguments) as described in the guide link and the segment in your /var/log/syslog file while trying to connect would be useful for me or someone more knowledgeable to help you. You really should not need to write a shell script, although I do that under ubuntu 8.04 where the Network Manager isn't so capable. Should you really try to do things manually, you will probably need to stop the Network Manager processes (sudo /etc/init.d/NetworkManager stop) and try the manual commands. Note that at the bottom of the guide, under Static IP Addresses, it shows how to set the default gateway manually - which you really shouldn't need to do if Multicast DNS discovery is working.

---

### Post by riahc3 on 2008-11-10
> **karlatsaic said:**
> Looking at this, there is not enough information to really help. I presume this is a wireless connection?
Go ahead and ask what other information you need to know.

And no, this is not a wireless connection.

---

### Post by riahc3 on 2008-11-17
Bumping up.

---

