---
title: "Running out of network connections ?"
date: 2008-06-17
forum: Networking &amp; Wireless
---

### Post by cybergypsy on 2008-06-17
Hi Guys

Since installing Ubuntu 8.04 I have noticed a problem with the wired network , after running for a couple of days the PC seems to run out of network connections.

When it happened today I could access my web site via http but not its control panel page via https.

I know its not a router issue as other PC's on the LAN don't have the same problem and after restarting this PC the problem disappears.

This PC does run a multitude of applications that use a lot of connections :-
[LIST]
[*]rtorrent (500 connections max)
[*]amule (200 connections max)
[*]apache (?)
[*]firefox (?)
[/LIST]
I have noticed when I restart the PC that Network Manager has a problem closing and seems to be killed instead.

dmesg shows this for the network card :-
```

Realtek RTL8201 PHY transceiver found at address 1.
Using transceiver found at address 1 as default
eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 16,

```

Anyone else seeing similar issues ?

---

### Post by dmizer on 2008-06-17
does the problem persist if you disable NetworkManager?

---

### Post by cybergypsy on 2008-06-17
thanks dmizer , I have uninstalled network Manager and will see what happens.

---

### Post by cybergypsy on 2008-06-18
OK , I removed Network-Manager and rebooted. Got the network working again and it has run for 24 hours.

Now again this morning I am having the same problem accessing our webhosts control panel via HTTPS on Ubuntu , yet it loads fine on my Nokia N800 on the same LAN.

This problem didn't happen on Ubuntu 7.10 so my guess its something that has changed in the network stack since then.

Daily rebooting reminds me of my Windows days :(

Any suggestions for a fix ?

---

### Post by cybergypsy on 2008-06-18
I think I may have found the culprit.

Instead of restarting the PC I restarted the moblock service and the problem has disappeared , I think I may have found a bug! :)

---

### Post by dmizer on 2008-06-18
please post the results of:
```
lshw -C network
```
it may be a driver/module issue.  i also recall reading about and experiencing problems with sis cards.  several problems were solved by changing the MTU.

edit:
i see we seem to have been posting at the same time ;)  sounds like you have things nailed down.

---

### Post by cybergypsy on 2008-06-18
thanks again dmizer , i am emailing the moblock-deb dev now.

---

### Post by jre on 2008-06-18
eMail received ... unfortunately I have no idea, yet.
Is MoBlock still properly running after 24h? Try and report the result of "moblock-control test" and "moblock-control status".
Is there anything special in moblock.log or syslog??
What's the last entry in moblock-control.log?
Am I right that your webhosts control panel via HTTPS is NOT blocked by moblock?
Which version of Moblock are you using (current version is 0.9~rc2-11)?

If it's really a bug of MoBlock we have to contact the upstream author at moblock.berlios.de or perhaps the netfilter (iptables) guys.

Greets
jre

---

### Post by cybergypsy on 2008-06-18
thanks for getting back to me so promptly jre , its not a big problem now I know that restarting the moblock service corrects the problem.

1. Moblock is still running correctly after 24 hours , but I will test more when it happens again.
2. Nothing odd in syslog
3. In the moblock.log I can see it blocking inbound and outbound addresses as expected but no errors or problems.
4. In mobloc-control I can see the service restarting as intructed , no other warnings or problems.
5. My webhosting isn't blocked as it works fine again after a restart.
6. Searched though all the blocklists in /var/spool/moblock/ and my sites IP address isn't amongst them. I also run moblock on my proxy server and this has been unaffected and allows my n800 to access the site even when my desktop is blocked.
7. Version = 0.9~rc2-11~hardy

I will keep my eye on it for now and report back.
Perhaps if others are having similar problems we will find out more.

Thanks again.

---

### Post by jre on 2008-10-31
Does the problem still exist?
For now I mention it in BUGS.

---

### Post by cybergypsy on 2008-10-31
yep its still happening.

I recently changed pc and reinstalled ubuntu 8.04 from scratch , the exact same network problems after about 24 hours.

fixed it the same way by restarting the moblock daemon every hour.

---

