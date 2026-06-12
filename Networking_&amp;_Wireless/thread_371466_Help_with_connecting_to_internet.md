---
title: "Help with connecting to internet"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by Shroud on 2007-02-26
Help please!

I just installed the latest version of Ubuntu (From the front page, i think its Draper)

I cant seem to connect to the internet, however, I can ping all other IPs on the home network, I can ping websites, but I cannot connect to them.

When I do a traceroute everything comes back with no reply except ip hop #1 (my own IP)

my router is configured to give IPs via DHCP.. i've also tried manually configuring the IP.. same result!!

Anyone have any ideas? :(

---

### Post by tgalati4 on 2007-02-27
Perhaps you have a router that has a firewall enabled that will not allow http port 80 packets to go through.  That's the only thing that I can think of that would allow you to ping remote sites but not be able to connect to them.

You have have to reboot your router/modem with your Ubuntu machine on to reset the DHCP settings.

---

### Post by Shroud on 2007-02-27
I tried configuring my router to allow these ports to go through to my ubuntu machine Ip address but STILL no connection :(

I have discovered that I can go to a website if I use a numeric ip address and enter it into the web browser, but the text doesnt work :\ very strange..

help!??? :(

---

### Post by Floppyjoe on 2007-02-27
Close Port 80 unless you have a web server there. Port 80 is only needed if you are serving web pages. Your problem is a DNS Issue.

[http://www.opendns.com/start/unix.php](http://www.opendns.com/start/unix.php)
This Url May be of Help to you.

---

### Post by tgalati4 on 2007-02-27
Good call.  I have a few servers running so I didn't think of that.

Also, your /etc/resolv.conf file should contain your router's address if it doesn't already:

nameserver 192.168.0.1

(Your 192.XXX address may be different.)  If that doesn't work, then try reflashing the firmware of your router.  They sometimes get weird.

Good luck.

---

