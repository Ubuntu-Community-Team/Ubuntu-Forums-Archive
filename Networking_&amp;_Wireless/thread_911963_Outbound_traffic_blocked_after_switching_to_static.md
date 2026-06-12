---
title: "Outbound traffic blocked after switching to static IP"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by jemptymethod on 2008-09-06
I was able to successfully change from using to DHCP to setting a static IP, and it "worked" in that, I could set my wireless router to let http traffic through to that IP on port 80, and I was able to access it via [http://wan_address](http://wan_address)

However, logged in across my local network via SSH, I was not able to use apt-get to install new packages, it hung when trying to connect to the repository, so then I also just tried to ping some external sites and no traffic was allowed through.

Have switched back to DHCP for the time being, and now I can apt-get packages to my heart's delight :)  But I'd like to switch back to my static IP and do likewise.

Any pointers would be appreciated.

---

### Post by jemptymethod on 2008-09-06
Anybody? Please!

This is on Ubuntu 7.10.  It is connected via RJ45 directly to the (wireless) router by the way.

One other clue?  Now that it's connected via DHCP, when I ssh to it, the connection is instantaneous.  When it had a different, static IP, there was a significant pause when first connecting via SSH, as though it were doing a reverse DNS lookup?

Thanks in advance

---

### Post by caljohnsmith on 2008-09-06
When you say you could access the computer with a static IP via [http://wan_address](http://wan_address), does that mean from outside your LAN (i.e. from the internet) I assume? And when the computer has a static IP and you ping outside websites, have you tried pinging their IP addresses to make sure its not a DNS problem? For instance, try pinging 64.233.187.99 which is one of google's addresses. If that doesn't work, can you ping your router's IP and access your router's settings via a web browser? Also, are there any other computers on your LAN you could use to confirm you still can access the internet while your one computer has a static IP (just as a sanity check)?

---

### Post by jemptymethod on 2008-09-06
> **caljohnsmith said:**
> When you say you could access the computer with a static IP via [http://wan_address](http://wan_address), does that mean from outside your LAN (i.e. from the internet) I assume?

Yes that's correct

> And when the computer has a static IP and you ping outside websites, have you tried pinging their IP addresses to make sure its not a DNS problem? For instance, try pinging 64.233.187.99 which is one of google's addresses. 

No I could not ping that, but could from a different computer on the LAN

> If that doesn't work, can you ping your router's IP and access your router's settings via a web browser? Also, are there any other computers on your LAN you could use to confirm you still can access the internet while your one computer has a static IP (just as a sanity check)?

Yes to all of the above.  Seems like a DNS problem?  At the bottom I've pasted the contents of my /etc/network/interface file, do I add some sort of DNS setting here?  Or to /etc/host?

When I do ipconfig from a Windows box wirelessly on the same network I see a setting:

Connection specific DNS suffix: hsd1.ga.comcast.net

Similarly, though with a slight difference, from the Ubuntu server's /etc/host:

127.0.0.1       localhost
127.0.1.1       jemptymethod.hsd1.ga.comcast.net.       jemptymethod

I'm wondering if that reference to the machine's name (jemptymethod) is the problem?  I think this might have gotten put in here when it had been connecting via DHCP?  As it indicates that name when using the router's web interface and showing the dhcp clients table.  I just removed that entry from the DHCP clients table on the router by the way, and restarted the network (/etc/init.d/networking restart) but still could not ping that Google IP you suggested.

I'm guessing I'm very close?  Maybe just delete the line for 127.0.1.1 in /etc/host, or at least the references to "jemptymethod" in that line.

Thanks in advance

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
  address 192.168.0.99
  netmask 255.255.255.0
  network 192.168.0.0
  broadcast 192.168.0.255
  gateway 192.168.0.254

---

### Post by caljohnsmith on 2008-09-06
If you can't ping the Google IP from that computer, then it's not a DNS issue at this point. You definitely need that 127.0.1.1 entry in your hosts file, but how does it compare to /etc/hostname? They should be exactly identical. In other words, I think your /etc/hosts should be:
```
127.0.0.1 localhost
127.0.1.1 jemptymethod.hsd1.ga.comcast.net
```
And /etc/hostname should be:
```
jemptymethod.hsd1.ga.comcast.net
```
Give that a try and see if that gets you any closer. Also, please post the output of:
```
route -n
traceroute 64.233.187.99
```
The second one will probably return an error of some sort, but let me know what it says.

---

### Post by jemptymethod on 2008-09-06
I had to switch back to the DHCP connection in order to apt-get traceroute.  So I did route -n while connected via DHCP and discovered the problem: I had the gateway wrong.

I really want to thank you.  Isn't there a way to "officially" thank you, and/or tag this thread as "solved"?

Thanks again

---

### Post by caljohnsmith on 2008-09-06
> **jemptymethod said:**
> I had to switch back to the DHCP connection in order to apt-get traceroute.  So I did route -n while connected via DHCP and discovered the problem: I had the gateway wrong.

I really want to thank you.  Isn't there a way to "officially" thank you, and/or tag this thread as "solved"?

Thanks again

That's great news it turned out to be something simple, and you're certainly welcome. Glad it's working again. :) And if you want to "officially" thank someone, you can press the little "medal" at the bottom-right corner of their posting. Also, just click the "thread tools" at the top of the thread, and then choose "mark as solved".

---

