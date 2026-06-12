---
title: "LAN problem"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by maja_88 on 2008-06-06
I have a problem accessing internet via ADSL connection. When I plug in the cable the network icon is activated, everything seems OK, IP adress, DNS, everything is set, but when I try to access any URL it just waits forever. I really don't know what could be the problem. Please help.

---

### Post by superprash2003 on 2008-06-06
could you post your ifconfig output.. also type ping google.com in your terminal and post output here

---

### Post by maja_88 on 2008-06-06
maja@maja-laptop:~$ifconfig
eth0      Link encap:Ethernet HWaddr 00:16:D4:FC:95:B0
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fefc:95b0/63 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1  
          RX packets:14 errors: 0 dropped:0 overruns:0 frame:0
          TX packets:42 errors: 0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3090 (3.0 KB) TX bytes:5774 (5.6 KB)
          Interrupt:18 Base address: 0xe000

lo:       Link encap:Local loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors: 0 dropped:0 overruns:0 frame:0
          TX packets:0 errors: 0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b) TX bytes:0 (0.0 b)


The following is just a part of the ping google.com output. The process seemed never ending (PS: I am sorry if I ask dumb questions, but I am a complete novice in ubuntu)

PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from google.com (72.14.207.99): icmp_seq=1 ttl=240 time=141ms
64 bytes from google.com (72.14.207.99): icmp_seq=2 ttl=240 time=138ms
64 bytes from google.com (72.14.207.99): icmp_seq=3 ttl=240 time=139ms
64 bytes from google.com (72.14.207.99): icmp_seq=4 ttl=240 time=138ms

---

### Post by xaco1234 on 2008-06-06
you connect thrue a router right?
do you have the same problem under windows?
is your router connected to the internett?

---

### Post by superprash2003 on 2008-06-06
this could be a DNS problem mate.. try using opendns servers [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html) .. i guess if you type [http://72.14.207.99](http://72.14.207.99) in your browser, google would open

---

### Post by uidb4056 on 2008-06-06
Have you checked that Firefox has not started with 'Work Offline', check in Firefox under menu File if 'work offline' has a mark, if has click on it to keep unchecked and try to open an URL.

---

### Post by brucewhanya on 2008-06-06
i have had wireless problems for 2 wks and cant get help

---

### Post by xaco1234 on 2008-06-06
you've gotten help, use ndiswrapper. if you got more issues with your problem bump your own thread. and ask for an url or other. this tread is to help maja with here network problem.

---

### Post by maja_88 on 2008-06-06
Guys, thank you all very very much, you are very helpful.
So, let's get back to the business :) Firefox is not the problem, it is not set to work offline, and I managed to open google by typing [http://72.14.207.99](http://72.14.207.99)  as you have said, but then what? I still can not access any other URL :(

---

### Post by superprash2003 on 2008-06-06
did you switch to opendns servers as i said?

---

### Post by maja_88 on 2008-06-07
I am trying to.. :( I followed the instructions on the web but whenever I enter the addresses for the openDNS in the DNS tab of the network config section, when I close it and then open it again, the old DNS address is restored. I also did the following:

$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ sudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
$ sudo ifdown eth0 && sudo ifup eth0

but the last command gives:
 ifdown:interface eth0 not configured
 Ignoring unknown interface eth0=eth0.

---

### Post by superprash2003 on 2008-06-07
are you using static ip or DHCP?

---

### Post by maja_88 on 2008-06-07
I tried both options. But nothing..

---

### Post by maja_88 on 2008-06-07
So, this is how far I am: when the address is set to dhcp, no matter of the DNS address in the DNS tab I can access [www.google.com](www.google.com), but only that URL and not any other. When I set the DNS server to 208.67.222.222 and 208.67.220.220 in the DNS tab, and I leave , then it again it is automatically set to the default DNS. I don't know how to make it not change.

$ sudo ifdown eth0 && sudo ifup eth0 

still does not work.

---

### Post by superprash2003 on 2008-06-07
that mostly means DHCP.. modify the dhclient.conf file like i said earlier and reboot your pc(better) instead of doing the ifdown, ifup.. then go to the DNS tab under system->admin->network and you should see opendns servers there..

---

### Post by maja_88 on 2008-06-08
I did all what you said. But there is something strange going on. Namely, I saved the configuration with the openDNS addresses as a separate location in network-admin. And whenever I apply it, and exit network-admin, then after only 10 seconds it is restored to the default location as before. Also, for a while I managed to access yahoo, but that was only once, then I couldn't do that any more with neither of the DNS addresses. I configured dhclient file, but it doesn't help. Just to be on the safe side, could you please tell me exactly the line I should include in there, in case I do something wrong? I am so sorry for this problem, it really took so long....

---

### Post by superprash2003 on 2008-06-08
prepend domain-name-servers 208.67.222.222,208.67.220.220;

if you still have problems.please post your dhclient.conf file

---

### Post by petrojn on 2008-06-08
I am having the same problem [Wireless DNS stopped working]("http://ubuntuforums.org/showthread.php?t=821276") and superprash2003 gave me the same advice and it didn't help either - although the opendns stuff was cool to learn about.

I am sitting next to my wireless router with a ethernet cable connected.  When I use the networkermanager to swap from the wired connection to the wireless interface - DNS stops working.  When I switch back it starts working again!?

This is truly mysterious behaviour ;)

I've looked back through the log of updates but nothing jumps out at me.  I have a similar issue with a beta or alpha dhcpclient update but nothing there has changed recently.

---

### Post by petrojn on 2008-06-08
Now I see that your DNS is working from your pings

I'll go back to my own thread now and try not to confuse your issue ;)

---

### Post by maja_88 on 2008-06-08
Here I attached the file. There is a step forward: I manage to access both google, yahoo, yahoo mail, and my e-mail account as long as I keep the DNS tab options opened and set to the openDNS adresses.However those were the only pages I could access. And as soon as I leave network-admin, as I said previously I can access nothing. The DNS address is switched back immediately.

---

### Post by superprash2003 on 2008-06-08
hey , i just saw your dhclient.txt file.. your last line is 

#prepend domain-name-servers 208.67.222.222,208.67.220.220;

dude..remove the # .. the # is used as a comment.. so if you start a line with # then it wont be used..so change that line to 

prepend domain-name-servers 208.67.222.222,208.67.220.220;

---

### Post by maja_88 on 2008-06-09
:lolflag: THANKS MAN. FINALLY...Really, thank you million times. I feel illuminated now after learning all this openDNS stuff. :)

---

