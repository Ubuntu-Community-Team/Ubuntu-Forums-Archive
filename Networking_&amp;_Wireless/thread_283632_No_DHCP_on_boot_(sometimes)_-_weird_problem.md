---
title: "No DHCP on boot (sometimes) - weird problem"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by TheYetiMan on 2006-10-24
Hello there!

I've recently moved almost totally to Ubuntu 6.06 from WinXP and I must say it's sweet! I've got XGL and Beryl all in the mix it's great! I'd just like to say thanks to the community on Ubuntuforums - i have used this forum a lot to help me figure stuff out.

Anyway that's not why I am here....

I've got a weird problem in that when Ubuntu boots up, everything appears to be perfectly fine, except sometimes (not every time, but most) I get into Gnome and I find I have no IP address!

A quick 'sudo dhclient' solves this 100% of the time and I am back up and running - but what I don't get is why this is happening!? Why is Ubuntu unable to get my IP address by DHCP at boot time? It works fine from a shell afterwards. (i.e. there's nothing wrong with my network setup - 7 other PCs connected to it work without a hitch using DHCP). Just seems to be a client-side problem.

I don't really know where to look / what to look for to troubleshoot my problem. I took a look in dmesg for any strange output regarding eth0 or dhcp but cannot find anything - can anyone provide any suggestions as to what might be happening?

Thanks,

Yeti

---

### Post by wieman01 on 2006-10-25
Wireless or Ethernet? What card are you using?

---

### Post by TheYetiMan on 2006-10-25
> **wieman01 said:**
> Wireless or Ethernet? What card are you using?

Sorry I probably should have said.....

It's just an on-board 10/100 ethernet connection on my DFI LanParty UT NF4 Ultra-D motherboard.

So, no WPA or anything  getting in the way. Just bog standard ethernet my man.

---

### Post by wieman01 on 2006-10-25
I know it sounds silly but have your tried another cord? If you have to restart your network after startup & the system has not complained during boot that it is unable to receive a DHCP offer, there is a pretty good chance there is something wrong with the cable. A thought...

---

### Post by Delphinus on 2006-11-03
I'm having exactly the same problem, all i have to do as well is ifdown and ifup my eth0.

i'm 99.9% sure its not a cable  issue as winxp works fine everytime and its only since installing dapper. Would be very keen to see a solution to this.

I also have a NF4 motherboard.

---

### Post by bmillsap on 2006-11-03
If you look in syslog, what kind of dhclient messages do you see from the time it's booting up and fails to get an address?  That might give an indication of what dhclient thinks went wrong.

---

### Post by TheYetiMan on 2006-11-09
Hi again guys, sorry to hear another person seems to be having the same problem :(

Unfortunately (for you, Delphinus) I didn't really find a software solution.... mine just worked itself out - works 100% now. I think (and I am pretty certain) that it was a router problem. Basically I had 2 devices on my network, one which was a dedicated router running monowall, the other a d-link router/switch/access point which had a dhcp server on it but was disabled (i.e. the monowall was doing all the dhcp. I was just using the dlink as a wireless AP).... Except now I have got rid of the piece of s**t d-link and got a dedicated wireless AP (with dhcp turned off ;)) and everything seems to be hunky dory.

I think windows works because it just relentlessly tries to get an ip address whereas dhclient does not (I'm not sure, just a theory).

Sorry if I cannot help any more, Delphinus.

Thanks to anyone who tried to help,

Yeti

---

### Post by Delphinus on 2006-11-09
bmillsap - How does one look in my syslog please?

TheYetiMan - Yeah I am cabled into a Pfsense box, (built off monowall)

I've managed to get myself some bad superblock issues at the moment so i might just do a clean 6.10 install see if that resolves things...

---

### Post by bmillsap on 2006-11-09
The system log should be /var/log/syslog.  You can open it with whatever text editor you use.  Messages about trying to get a DHCP address should be headed with "dhclient:" and say things like DHCPREQUEST and DHCPACK etc.  See what kind of messages there are around the time you're not getting an address.

---

### Post by Delphinus on 2006-11-13
ummm

```
jack@delph:~$ cat /var/log/syslog
Nov 13 18:49:51 delph syslogd 1.4.1#17ubuntu7: restart.
Nov 13 18:49:51 delph anacron[4725]: Job `cron.daily' terminated
jack@delph:~$

```

I assume i have to crank up the syslogging detail?

---

