---
title: "host name resolution stopped working after last update"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by jaimeab on 2007-06-05
Hi,

everything was working fine (more than that!) on my Feisty Fawn (latest version) until yesterday I installed the latest update. Since then, I can't resolv any host name, even if:

- I can ping everywhere (by IP address), even my DNS servers
- if I start nslookup, the dns servers are correctly configured, but just cannot reach them (!) - probably it's asking its name
- another computer in the same network is working perfectly (no linux :-( )
- everything about the network is statically configured
- netstat -r and ifconfig -a both look ok to me
- /etc/resolv.conf is as sane as it's been

Most amazing is, if I execute dhclient (my router has dhcp enabled even if I don't use it), everything works again but only for a while (!).

Last thing: I've discovered I've running some avahi-daemon that seems to do a lot of nice but probably unnecesary things with my name resolution.

I'm most worried as, believe it or not, this machine is very important for my work. Yes, I should not get the very last version of everything, but I cannot help.:p

Another way to help: is there a method to roll-back the last update?

Thanks in advance,

jaime

---

### Post by psychoelf on 2007-06-05
Same problem here.  No problems with hardwire ethernet in Windows.

If I boot up kernel 2.6.20-16 or 12, I have to restart my wired connection and it works for awhile.   Not sure exactly how long.

Any help is appreciated.

---

### Post by antillas21 on 2007-06-05
I have also been getting problems with my wireless card connecting to my modem-router since I applied the last update this weekend.
Before that, my wireless card was working flawlessly with open and WEP network. But since I applied the update, every time I log into my laptop, I must remove and reconnect  the card and manually configure my connection to the internet for around two or three times until I get a successful connection.

Does anyone know if this is related to the the updates applied or how could it be resolved?

---

### Post by Sloddy Shipper on 2007-06-07
I'm having this problem too. ie. wireless is connected to the access point no problem, i can ping the router, the dns server and any ip address but names are not getting resolved.  I know zero about dns. Where should i be looking to find out what is going on? Any advice much appreciated.

 Do you suspect the kernel updates to have caused this? Everything worked fine for me after the kernel updates. Is it possible this was caused by the recent firefox updates? This only started for me today, the first time i have rebooted since the firefox updates.

---

### Post by Sloddy Shipper on 2007-06-07
blast! ok jaimeab, i think we are having exactly the same problem. My wireless card is also statically configured, but when i run dhclient i get a new ip from the router and dns works again. I don't understand why this should be, can anyone explain?

---

### Post by jaimeab on 2007-06-07
Nice to know I'm not alone :-)
I don't remember exactly what updates I did install but, yes, it worked fine until I rebooted the machine.

It'd be amazing if firefox had something to do with that, as the problem far exceeds firefox!

As for now, I have a useless linux machine, and some pressure to go back to "other operating systems". I'll resist but really need a solution.

Regards,

jaime

---

### Post by jaimeab on 2007-06-08
Hi again,

I'm most despaired. I've worked a wired connection for the machine, disabled the wifi one, and it worked... but only for a couple of hours!

I'm absolutely lost at this point, and totaly unable to work with this machine.

Regards,

jaime

---

### Post by antillas21 on 2007-06-08
Well one of the attempts I have to do in order for my wireless card to connect successfully to the router and the internet is to provide an static IP address and then switch to a DHCP assigned IP address... and only then it works... at leat as long as I keep the session alive, there is no random dropping.
And as mentioned in an earlier post, it was after Firefox restarted from its update (2.0.4) that this issue began. At first I thought it was after the last ubuntu update (the one including kernel update), but then I realized that all worked just fine after that, because the Firefox update came later (aprox. 20 mins) and in the spirit of having all my system up-to-date, I restarted Firefox.

Is it really Firefox the culprit....? or the linux kernel? I'm growing tired of having to disconnect my wireless card and assign an static IP address, then a DHCP assigned one... and really, I can't afford to have my computer on all day.

---

### Post by Sloddy Shipper on 2007-06-11
Hmm, i have a work around which may help you with this. Every so often the /etc/resolv.conf file is getting overwritten with an ipaddress of vmwares network interface, (eh? no idea what's going on here). So i edit the file to read

nameserver MYROUTER

replace MYROUTER with your normal DNS server that works, mine is via my access point.
then

sudo chmod -w /etc/resolv.conf

to prevent getting changed back by whatever funny business is going here. Someone can probably tell me why this is a bad idea but i don't recall asking anything to change my DNS settings in the first place and this seems to work for now and i can use static ip again. Hope this helps make your machine usable again and can anyone give me a clue as to what's happening here?

---

### Post by jaimeab on 2007-06-11
Hi,

thanks for the idea. I just came up with a different workaround.

My resolv.conf file was not being overwritten (well, actually it was, but the nameservers remained the correct ones).

Just trying things I enabled the DNS capability of my router and put its address as the first resolv.conf nameserver... and, suprise! it now works!

Why? I don't know. I've always been able to "ping" my nameservers, so...

It's a workaround, but at least I can work on ubuntu again.

Cheers,

jaime

---

