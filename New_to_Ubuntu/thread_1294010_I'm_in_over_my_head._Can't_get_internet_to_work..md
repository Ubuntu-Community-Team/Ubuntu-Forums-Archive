---
title: "I'm in over my head. Can't get internet to work."
date: 2009-10-17
forum: New to Ubuntu
---

### Post by alekhidell on 2009-10-17
I recently downloaded ubuntu 9.04 jaunty on my dell studio 1737 laptop, but haven't been able to connect to the internet. I started by trying to find NetworkManager in the system notification area and for some reason i cannot find it. My immediate thought was that it had to be my driver. I looked in hardware drivers and found Broadcom STA wireless driver connecte. I guess my first questions are, does the wireless half mini-card, DW1397, 4312BG, also act as my wired connection? and if so, do I have to configure it as wireless even though I am using a
direct connection. After I found that the driver seemed to have been found, I contacted my ip and obtained my physical address which is different than the one that is showing on the network, also the ip address showed an address with ie6. Wierd, since I did a clean install. With that being said would it be in my best interest to format the drive and start from scratch. I know this is probably mind numbing for those with a higher IQ than mine, but I want this to work.
SCREW GATES

---

### Post by 73ckn797 on 2009-10-18
For wireless drivers, sometimes going to System/Administration/Synaptic Package Manager and installing "ndisgtk" will work. From there install the Windows XP driver for the card. The Windows driver will be found either on the disk for the computer or from the manufacturer. See if that will work. A wired connection will be different probably.

---

### Post by aesis05401 on 2009-10-18
Hello, 

You almost lost me with the 'screw gates' thing.  I'm not here to screw anyone.  Just help other users when I can.  Secondly, the wording in your post is not quite specific enough to provide help.  Do you have both wired and wireless adapters in your machine?  

Can you open a terminal, input the following two commands and provide us with the output:
```

lspci

```

```

ifconfig -a

```

Thanks.

---

### Post by anewguy on 2009-10-18
> **alekhidell said:**
> I recently downloaded ubuntu 9.04 jaunty on my dell studio 1737 laptop, but haven't been able to connect to the internet. 

Do you mean you just can't connect via wireless, or does hard-wire not work either?

>  I looked in hardware drivers and found Broadcom STA wireless driver connecte. I guess my first questions are, does the wireless half mini-card, DW1397, 4312BG, also act as my wired connection? and if so, do I have to configure it as wireless even though I am using a
direct connection.

I checked the dell support link for wireless drivers for you model and can't find a driver list as being for a DW1397 or 4312BG (see  [[COLOR="RoyalBlue"]this[/COLOR]]("http://support.dell.com/support/downloads/driverslist.aspx?os=WLH&catid=20&dateid=-1&impid=-1&osl=EN&typeid=-1&formatid=-1&servicetag=&SystemID=STUDIO1737&hidos=WLH&hidlang=en&TabIndex=&scanSupported=False&scanConsent=False") link).

As mentioned by a previous poster, please log in to a terminal window (applications/accessories/terminal) and type:

lspci <press enter>

Also:

lsusb <press enter> (some laptop adapters actually go through an internal USB link)

Copy and paste the output of the those back here for us and we'll have more to go on.

Thanks!
Dave :)

---

### Post by cmwarre on 2009-10-18
Just from another beginner I would suggest just downloading sun virtualbox and just virtualizing Ubuntu until you get the hang of the operating system.  I know nothing about drivers or any of that so sorry if this isn't much help...

---

### Post by Peter09 on 2009-10-18
Note that if your are using a NAT router, which you most probably are, then the IP address of your local machine will NOT be the same as the IP address given to you by your ISP. If you are seeing an IP address on your local machine then you are likly connected to your router. 

Have you tried

```
ping <ip address of your router>
```

in a terminal. Your ip address of your router will be something like - 192.168.0.1

---

