---
title: "Strange Internet problem"
date: 2005-06-20
forum: Networking &amp; Wireless
---

### Post by caaz on 2005-06-20
hi,
I have very strange internet connection problems. I can reach the internet with ping and wget, but with firefox and synaptic I get timeout errors. 

I use a DHCP Connection and under windows everything works fine. I have set the nameserver properly and my other computer, also ubuntu hoary, works just fine with this settings. I use a HAMA DR-20 router.

I have already tried to lock the resolv.conf with chattr but without effect.
Hopefully you can help me...

caaz

---

### Post by intangible on 2005-06-20
Have you tried changing your nameservers to different ones yet?

Ubuntu has IPV6 enabled and some nameservers go nuts with that... it's broken on thier side, but that doesn't help you any I'm sure.

Try the OpenNIC servers, this thread will help I think: [http://www.ubuntuforums.org/showthread.php?postid=209197](http://www.ubuntuforums.org/showthread.php?postid=209197)

Maybe this setup would help:
**sudo gedit /etc/resolv.conf**
```

nameserver 63.226.12.96
nameserver 64.151.103.120
nameserver 216.87.84.209
nameserver 68.15.165.12

```

Good Luck

---

### Post by antwerx on 2005-06-20
Hello - 

What is the topography of your Internet connection. ex. Cable or DSL with D-Link DSL/Cable router connected directly toyour pc/laptop, or Ubuntu server running NAT as a router for internet sharing.

Wired or Wireless?

Can you ping by IP address only or by DNS name, i.e. yahoo.com.

Sorry for the questions, but may help troubleshoot this.

 :)

---

### Post by caaz on 2005-06-21
I have tried to use other nameserver but it doesn't work. I also disabled IPv6.

I can ping by IP address and by DNS name. My connection is wired and it goes from my PC to the router and the router goes to the dsl modem.

Hopefully that will help you...

---

### Post by sgenchev on 2005-06-21
Could it be that you have configured proxy for Firefox and synaptics and it points to a non- working proxy?

---

### Post by intangible on 2005-06-21
Have you tried booting a live CD in that computer and seeing if it browses the net ok?

---

### Post by caaz on 2005-06-21
Unfortunately I dont use any proxys and with the live CD I get the same errors.

---

### Post by intangible on 2005-06-21
Do you know what network chip you have?  If not, what motherboard, or what model computer (if it's a pre-built)?

Now it's starting to seem like a hardware problem considering you have another Ubuntu computer that can access the net without a problem, and this one acts the same with a Live CD.  Maybe it's something specific to the network device.

---

### Post by caaz on 2005-06-21
My network chip is a **Marvell Yukon Gigabit Ethernet 10/100/1000Base-T Adapter, Copper RJ-45**. 
The problems original started when i changed my router from an SMC (who is out of order now, with the SMC i reached the internet with ubuntu without problems) to a **HAMA DR-20**. 
But the other PC works without problems with the new router...

---

### Post by intangible on 2005-06-21
Just to help eliminate more crazy ideas, have you turned off the other PC, restarted this one by itself and tried it out as the only one on the router?

---

### Post by Cas on 2005-06-21
i have the same problem, i can do ping to a ip or a name but , using the firefox or ssh por example i cant reach the destination by the name, only by the ip number... i am connected to a wireless adsl router using wireless, but i tried with cable and got the same problem.... for example: 

i want to connect to mywebpage.org with ssh (firefox), but if i use the name (mywebpage.org) simply does nothing.. solution , i do "ping mywebpage.org" and solve it to 211.111.111.111 and then i use this ip , "ssh 211.111.111.111" (works) !!

the problem is not relation with the wireless card (ipw2200bg) , network card or router because in slackware 10 with the same equipment (toshiba m30 laptop) it works perfectly...

anyone  to help??

Sorry my bad english , im from portugal... 

thanks for reading , Paulo Pereira (Cas).

---

### Post by caaz on 2005-06-22
[QUOTE=intangible]Just to help eliminate more crazy ideas, have you turned off the other PC, restarted this one by itself and tried it out as the only one on the router?[/QUOTE]
Doesnt change anything. Maybe it is the easyest way to buy a new router....  :-|
Hope that one of you guys will have the rescuing idea...

---

### Post by intangible on 2005-06-22
I still find it strange that one Ubuntu computer works fine, yet this one doesn't.

Can you dig up another network card to try out in the offending machine?  Disable the onboard one in the BIOS and then just try the other one, see if it still acts up.

---

### Post by Cas on 2005-06-23
i have solve my problem... apparently the ubuntu distro can't solve the 192.168.1.1 nameserver in resolv.conf  ](*,)  ](*,) ??!!?? (router have dynamic dns, slackware recognize it well) ... so i made a search about the dns servers that my isp use ( 194.65.3.20 and 194.65.3.21 for sapo isp in portugal) and i used this ips in resolv.conf ... but another strange thing is , if you reboot the ubuntu os, the resolv.conf file is changed to original .. solution : "sudo chattr +i /etc/resolv.conf" to block the write access to file..  since then , everything works  \\:D/ , wireless card and ethernet card with only the resolv.conf changes ... 

*from man chattr* 
"       A file with the `i' attribute cannot be modified: it  can-
       not  be deleted or renamed, no link can be created to this
       file and no data can be written  to  the  file.  Only  the
       superuser can set or clear this attribute.
"

i hope this help... once again , sorry my english... :)

---

### Post by skippuff54 on 2005-07-03
> apparently the ubuntu distro can't solve the 192.168.1.1 nameserver in resolv.conf   

why is that, and how'd you find out?  i'm having similar problems with a wireless netgear pci card, and wired card and a bridge.  the wireless is bridged to the wired, that's hooked to a wireless router and the router is plugged in to local timewarner cable.

---

