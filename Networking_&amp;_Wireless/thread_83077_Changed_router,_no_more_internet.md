---
title: "Changed router, no more internet"
date: 2005-10-27
forum: Networking &amp; Wireless
---

### Post by Tulip on 2005-10-27
Hello,

Im very new to Ubuntu and to Linux - Ive just installed my first attempt on a new machine which was wonderfully easy. Everything autodetected, and I was able to browse the internet and the shared docs on my networked xp machines using DHCP.

However I replaced my D-link DSL-504G ADSL router with a Netgear DG632 and now things are not so rosy. I can still access the network shared folders with the Ubuntu machine (although a little slower it seems) but it can no longer access the internet. Ive tried using a static IP address with no luck (can still access the network though). The D-Link used to allocate ips in the range of 10.1.1.*, but the Netgear uses 192.168.0.* The XP machines have coped with the change without problems. Ive done some google searching but with no luck so far.

Ive had a quick look in Applications>System Tools>Network Tools but without any real understanding of what Im seeing. The initial displayed device is Loopback Interface (lo), and Ethernet Interface (eth0) is selectable from the dropdown menu. On selecting it it displays protocol IPv4 and IPv6 in the IP information. Next to IPv4 is the correct static IP address info, IPv6 has a machine address or something - fe80:: etc. Not sure if this is relevant. 

The first time I checked out this setting, I opened firefox and successfully connected - I hadnt changed anything so it was probably a coincidence, but about 5 minutes later it stopped working again. I would really appreciate some  guidance as to what to try next, simply worded or stepped if possible - Im pretty stoopid :)

Cheers,
Rob

---

### Post by ThirdWorld on 2005-10-27
rob I duno If this will help but something similar happend to me, and i tried everything but nothing seemed to work. Actually the only thing that worked was to unplug my modem and my router for 1 minute and plug it back. everything works fine so far.

---

### Post by Tulip on 2005-10-27
No joy unfortunately. Ive tried restarting the machine, rebooting the modem and Ive played musical ports with the network cables but with no result. Thanks for the post though, any other thoughts?

---

### Post by jakev383 on 2005-10-27
Try to ping the router first: 192.168.0.1 and see if that goes through.  Then try pinging an external IP address (66.94.234.13 is one of Yahoo's) to see if this worked.  If everything has worked so far, the problem will be with DNS.  If not, try the 'route' command from a shell, and post the results.

---

### Post by Tulip on 2005-10-27
I can successfully ping the router and outside IP addresses. Just to tease me, it briefly allowed me to connect to the internet again while I was doing this, only to deny me again after another 5 minutes. 

So the problem is with DNS...  With a little bit of googling I got to

[http://ubuntuforums.org/showthread.php?t=3699&highlight=iPv6](http://ubuntuforums.org/showthread.php?t=3699&highlight=iPv6)

and used about:config in Firefox. Scrolled down to network.dns.disableIPv6 and set it as true. Viola, I can connect again - just hope its not another little tease. I'll post again if it decides to act up.

Thanks for the DNS tip Jake.

Cheers,
Rob

---

### Post by jakev383 on 2005-10-28
No problem. I didn't even think of the IP6 issue - all of the routers I use (which are Linux boxes) I've already made IP6 compliant. They also server as my DNS servers for the LANs.
Glad to see you got everything working again!

---

### Post by Tulip on 2005-11-02
Oh dear, a little premature. Internet browsing is still fine, but some other internet apps are also not working correctly with this new modem. 

GAIM can no longer connect me to my MSN account. With the previous modem it worked well on this computer. Ive set up a ubuntu machine at home (problem machine is at work) and using the old modem I was able to connect to my MSN account successfully this morning, so its not Microsoft playing funny games (this time). 

On this home machine I was also able to install Automatix and successfully add its features. On the problem machine I get time outs all over the place - error messages such as 

hkp server wwwkeys.eu.pgp.net 
keyserver timed out

and

err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy
could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out

Any ideas what I should try next?
Cheers,
Rob

---

### Post by mips on 2005-11-03
Tulip,

Dont stress, easy to sort out.

First I would suggest you get the latest firmware for your Netgear router, my DG834G works fine without any IPv6 hacks. [http://kbserver.netgear.com/products/DG632.asp](http://kbserver.netgear.com/products/DG632.asp)  v3.4 is available as well as a new beta v3.6.0.

If you still have hassles then you have to globally disable IPv6. Look at **Option 1** on my post here: [http://ubuntuforums.org/showthread.php?t=78337](http://ubuntuforums.org/showthread.php?t=78337)

---

### Post by teaker1s on 2005-11-03
dns resolution caused me problems I manually configured mine as ubuntu didn't like auto discover mode

---

### Post by Tulip on 2005-11-03
I upgraded the firmware of the DG362 modem to version 3.40, I was scared off trying the beta 3.6 by the big red warnings and I dont have ADSL2. It didn't fix the problem unfortunately.

Your Option 1 looked very promising:-

Open a terminal and enter:
sudo gedit /etc/modprobe.d/aliases
Look for the line that reads:
alias net-pf-10 ipv6
Change it to:
alias net-pf-10 off #ipv6
Save and reboot your PC.

Unfortunately it didnt work either - still cant connect through GAIM or Synaptic.

I will give manual configuration of DNS resolution a go next, although Im not sure how to do this - is this done on the ubuntu machine or in the modem? 

Thanks very much for your input guys, I appreciate the time you've taken to help me out.
Cheers,
Rob

---

### Post by mips on 2005-11-04
It is done in the PC (you can also add it to the router if you want).

System->Administration->Nertworking->DNS->Add

---

### Post by Tulip on 2005-11-04
Success! Manually adding my provider's DNS server and removing the router address did the trick. Grrr Netgear. I can now connect to my MSN account via GAIM, and Automatix is now doing its thing without all the timeouts. Well done guys and thankyou very much.

---

### Post by stream303 on 2006-01-17
To prevent you from having to do this manually each time you reboot or get a new dhcp lease, you may want to edit your **/etc/dhcp3/dhclient.conf** file and add this line before the request line with your known isp dns addresses:
[B]
supersede domain-name-servers 123.45.689.90, 234.56.789.01;[/B]

just separate with commas and place a semicolon at the end.

Now the dns addresses in your /etc/resolv.conf file won't get overwritten by dhclient.

---

