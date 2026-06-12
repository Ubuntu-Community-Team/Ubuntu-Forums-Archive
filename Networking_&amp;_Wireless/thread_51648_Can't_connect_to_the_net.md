---
title: "Can't connect to the net"
date: 2005-07-24
forum: Networking &amp; Wireless
---

### Post by runebinder on 2005-07-24
Hiya, I decided after the advice of my housemate to change my pc to a dual boot system, and installed ubuntu 5.04 amd64 version on a new partition, got it working ok but can't seem to be able to connect to my router and get online, my ethernet connection has been made active and it was able to download four packages for xmms but now no net connection. Help anybody?

---

### Post by DJ_Max on 2005-07-24
Well, it sounds like you have an connection, unless you downloaded the xmms packages from the CD-ROM??

do this in a terminal
```
ping -c4 google.com
```

BTW, how are you connecting? DHCP?

---

### Post by runebinder on 2005-07-25
Hi just tried to install another package in ubuntu without the dvd rom in and would'nt do anything, so yeah looks like xmms was installed from the dvd. 

Typed in what you said to the terminal, and got a response  
"4 packets transmitted, 4 recieved, 0%packet loss, time 3002ms" was part of what came up so take it that it is making a connection, but when I tried to use mozzila again it still would not connect to any sites. 

The router is set up through DHCP

---

### Post by DJ_Max on 2005-07-25
I was thinking it's an IPv6 issue, but check these threads out.
[http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)
[http://ubuntuforums.org/showthread.php?t=50842](http://ubuntuforums.org/showthread.php?t=50842)

---

### Post by Rhawi Dantas on 2005-07-25
I had a problem almost as the same as you :)
I just deactivated the network card in System->Administration->Ethernet Connection
I have some e-mails with Ubuntu messages that I can send you if you want

---

### Post by runebinder on 2005-07-25
Hi have tried deactivating the ethernet card anr reactivating it but no joy. Yeah wouldn't mind having a look at those emails if it's ok

---

### Post by Rhawi Dantas on 2005-07-25
ok...
Tell me your e-mail address and then I'll send you :)

Cheers :P

---

### Post by runebinder on 2005-07-25
K, it's [email]runebinder@btinternet.com[/email] cheers. Is strange can access some pages now but it still keeps timing out on most of em including this site

---

### Post by Rhawi Dantas on 2005-07-25
Yeah... that's a problem very unusual...
Could you tell me your configuration ? Maybe it's something in common with our machines that behave strangely with the system...

I have a 3Com HomeConnect, through a ADSL-512 kbps DHCP and a Network Card VIA Rhine-III VT6105 with a Soyo Dragon... But I bought this network card, because I thought that could be something related to the network card thats onboard...

Anyway, I've just send you the e-mail :)
If you have any problems, please mail me :)

Cheers

---

### Post by runebinder on 2005-07-25
Cheers for the email, shall see if there's anything in there of help. Got a btyahoo 2mb adsl broadband connection, using a D-link dsl-504t ADSL router, my ethernet card is an onboard Realtek RTL8169/8110 Family Gigabit Ethernet NIC

---

