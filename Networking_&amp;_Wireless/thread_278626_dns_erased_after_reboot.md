---
title: "dns erased after reboot"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by zekopeko on 2006-10-16
my resolv.conf is getting erased every time i reboot my computer.
my network setup is:

usb adsl modem connected on a win xp sp2 machine. internet connection sharing is turned on. my network card has this settings:

Physical Address: 00-60-94-25-01-D9
IP Address: 192.168.0.1
Subnet Mask: 255.255.255.0
Default Gateway: 
DNS Server: 
WINS Server:

the above machine connects to my ubuntu machine over a switch.
ubuntu has this setting on eth0:

IP Address: 192.168.0.100
Subnet Mask: 255.255.255.0
Gateway: 192.168.0.1

i set the DNS to 192.168.0.1 but it gets reset every time i reboot the computer.
i tried some of the solutions for this problem:

editing my /etc/dhcp3/dhcpclient (something like that) by erasing DOMAIN-NAME-SERVERS in the request line.

chmod 444 /etc/resolve.conf <--- haven't tried this but i think it won't work.

i also found somebody saying to put a script in crontab so that it get executed every five minutes erasing the empty resolv.conf with a new one with nameserver.
 but this solution was because a guy/girl had a problem similar to mine plus it erased the resolve.conf every few hours. i don't have this problem since i leave my computer on when i go out and there is no problem.

is it possible to make a script so that it runs on startup? before everything else so that gaim can connect automaticly

---

### Post by Endwin on 2006-10-16
In **/etc/dhcp3/dhclient.conf** look for the line **#prepend domain-name-servers 127.0.0.1;** uncomment it and replace 127.0.0.1 with the IP addres you want.

---

### Post by zekopeko on 2006-10-16
still doesn't work. it gets reset on reboot. 
permissions where 644 before reboot and 777 after reboot. something is messing my resolv.conf.
any ideas?

---

### Post by handy on 2006-10-17
Apparently **/etc/resolv.conf** is a **temp**' file, your solution will be behind it.

I noticed that you have 192.168.0.1 for your xp, Ubuntu & gateway address?

---

### Post by zekopeko on 2006-10-17
sorry my bad. ubuntu is 192.168.0.100 , xp is 192.168.0.1 and is a gateway. 

and what do you mean about resolv.conf being a temp file?

---

### Post by Kateikyoushi on 2006-10-17
Resolv.conf gets overwritten if you are using dhcp client.
So you should look there for a solution.
/etc/dhcp3/dhclient.conf has a prepend domain-name-servers line, that should solve it.

edit: Ahh I see some already recommended it.

---

### Post by zekopeko on 2006-10-17
everything is ok now. used the prepend domain-nameservers.
last night it didn't work but now it works.
thnx

---

### Post by handy on 2006-10-17
> **zekopeko said:**
> everything is ok now. used the prepend domain-nameservers.
last night it didn't work but now it works.
thnx

It would have taken a restart of the network or a reboot to come into effect.

Glad it sorted now... :D

---

