---
title: "Can't find network printers"
date: 2020-10-16
forum: Networking &amp; Wireless
---

### Post by The Dragon Master on 2020-10-16
Hi

I have worked in the same office and on the same laptop for three years.  Roughly 6-8 weeks ago I lost the ability to use or find network printers. I was using Ubuntu 18.04 LTS. Today I upgraded to 20.04 LTS, but the problem persists.  I connect to the network via a cable and continue to use the internet via that cable. 

When I try to "Add" a printer, a window opens where you can search for a printer on a network. I have both the correct printer name and it's IP address, but the window always reports "No printer was found at that address"

What might be going on?

Best regards
David

---

### Post by TheFu on 2020-10-16
I don't know anything specific about printing with 18.04 or 20.04.  I do know that CUPS runs on port 631/tcp and handles IPP communications.

Can you ping the IP?  Is port 631/tcp "listening"?
Do you have mDNS running or some other zeroconf implementation like **Avahi**?

---

### Post by The Dragon Master on 2020-10-16
Many thanks TheFu for your reply 

No, I cannot ping the printer

midoriya@Midoriya:~$ ping 172.17.0.85
PING 172.17.0.85 (172.17.0.85) 56(84) bytes of data.
From 172.17.0.1 icmp_seq=1 Destination Host Unreachable
From 172.17.0.1 icmp_seq=2 Destination Host Unreachable
From 172.17.0.1 icmp_seq=3 Destination Host Unreachable


mDNS is not running, but avahi is 

midoriya@Midoriya:~$ ps -aux|grep mdns
midoriya   10371  0.0  0.0  19592   760 pts/0    S+   15:55   0:00 grep --color=auto mdns

midoriya@Midoriya:~$ ps -aux|grep avahi 
avahi        935  0.0  0.0   9548  4992 ?        Ss   12:58   0:06 avahi-daemon: running [Midoriya.local]
avahi       1011  0.0  0.0   8552   356 ?        S    12:58   0:00 avahi-daemon: chroot helper
midoriya   10373  0.0  0.0  19724   760 pts/0    S+   15:55   0:00 grep --color=auto avahi

---

### Post by The Dragon Master on 2020-10-16
midoriya@Midoriya:~$ sudo netstat -tunlp|grep 631
tcp        0      0 0.0.0.0:631             0.0.0.0:*            LISTEN      940/cupsd           
tcp6      0      0 :::631                     :::*                    LISTEN      940/cupsd           
udp       0      0 0.0.0.0:631             0.0.0.0:*                             1059/cups-browsed

---

### Post by TheFu on 2020-10-16
If you can't ping it, then it isn't there and you'll never print at it.  That's a network issue, not a printing issue.

BTW, hostnames should be lowercase to avoid issues. In theory, it shouldn't matter, but how knows about all the code, written by random people around the world?  As an admin, I want to avoid problems whenever possible. This isn't specific to printing, at least not to my knowledge. I don't know if the printing subsystem cares or not.

---

### Post by The Dragon Master on 2020-10-16
Thank you

Well the printer is there - physically - I walk past it every day and my colleagues on windows all use it with no problem. 

So how should I go about investigating this network issue?

---

### Post by SeijiSensei on 2020-10-16
Does the printer have a static IP address? If it uses DHCP (bad idea), the address might have changed.

Try installing nmap from the repositories and running a ping scan of the network like this:
```
nmap -sP 172.17.0.0/24
```
It will return a list of all the active machines on your network. (You need to be root to do some nmap scans, but not this one.) Check the IP address for the printer.

---

### Post by TheFu on 2020-10-16
> **The Dragon Master said:**
> Thank you

Well the printer is there - physically - I walk past it every day and my colleagues on windows all use it with no problem. 

So how should I go about investigating this network issue?

Most network printers have a button to print a test page which contains all the specifics for that printer --- like the IP address, model number, whether it supports postscript or not, how much RAM is holes, etc.  I'd push that button and take the page back to my desk.

---

### Post by makitso on 2020-10-16
> [COLOR=#000000]I lost the ability to use or find network printers.


Foolish question to ask but is this a wifi connected printer?  If so, I would re-authenticate the printer to the network and then try again.[/COLOR]

---

