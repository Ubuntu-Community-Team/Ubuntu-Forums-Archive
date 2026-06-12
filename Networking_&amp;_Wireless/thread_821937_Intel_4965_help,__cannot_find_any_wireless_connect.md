---
title: "Intel 4965 help,  cannot find any wireless connections"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by fatjedi on 2008-06-07
I need help fixing my wireless after upgrading from XP to Hardy. The card works (because i used it in windows) but after upgrading i cannot find any connections that i know for certain are available and there. I am using an Intel 4965. The iwconfig and iwlist are posted below. If any other info is needed don't hesitate to ask.

iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


iwlist wlan0 scan:
> wlan0     Interface doesn't support scanning : Network is down

---

### Post by Unix_Slayer on 2008-06-07
> **fatjedi said:**
> I need help fixing my wireless after upgrading from XP to Hardy. The card works (because i used it in windows) but after upgrading i cannot find any connections that i know for certain are available and there. I am using an Intel 4965. The iwconfig and iwlist are posted below. If any other info is needed don't hesitate to ask.

iwconfig:


iwlist wlan0 scan:


What are you using? Ndiswrapper? or not.

---

### Post by fatjedi on 2008-06-07
No i believe i am still using the ilw4965, and have not installed the ndiswrapper.

---

### Post by Unix_Slayer on 2008-06-07
> **fatjedi said:**
> No i believe i am still using the ilw4965, and have not installed the ndiswrapper.

If you have a Winxp 32 bit driver, ndiswrapper should work. Do you know the make of your adapter?

---

### Post by fatjedi on 2008-06-07
no idea, do you know how to check?

---

### Post by Unix_Slayer on 2008-06-07
> **fatjedi said:**
> no idea, do you know how to check?

Intel® Wireless WiFi Link 4965AGN. Do you know if it's just b/g or is it b/g/n. 

try this in a terminal window:

```
lsusb
```

Paste back what you get.

For drivers, you can do a search on Intel.
This is a google search for your adpater. ==>[http://www.google.com/search?q=Intel+4965&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a]("http://www.google.com/search?q=Intel+4965&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")

---

### Post by gfg on 2008-06-07
I have the same card, and it worked right out of the box. Have you tried looking around in network config? It seems like Ubuntu sees your card, but it's not enabled somehow.

---

### Post by Bubba64 on 2008-06-07
> **gfg said:**
> I have the same card, and it worked right out of the box. Have you tried looking around in network config? It seems like Ubuntu sees your card, but it's not enabled somehow.

Yes sometimes it takes a try at roam in wired and wireless to get things working, you know recognized

---

### Post by Unix_Slayer on 2008-06-07
Also.... if it does see your adapter..... if you have the cat5 plugged in, it will not work. Linux grabs the first available adapter with internet connection.

---

### Post by fatjedi on 2008-06-08
its b/g/n

lsusb:
```
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 04f2:b018 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 147e:2016  
Bus 002 Device 002: ID 0a5c:2101 Broadcom Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

nothing else is a problem

---

### Post by stchman on 2008-06-08
The 4965 works OOB in Hardy.  I found that wicd is a better manager than network-manager.

---

### Post by fatjedi on 2008-06-08
i am using wicd as well and it cannot find networks to connect to

---

### Post by Unix_Slayer on 2008-06-08
> **fatjedi said:**
> i am using wicd as well and it cannot find networks to connect to


I didn't like wicd. Try another one. Try kwifimanager. I had the same problem, until I switched over to using knetworkmanager. Now it works fantastic. I hot coded my wired card in second. Now I use my wireless card for the internet, and my wired for the intranet.

---

### Post by stchman on 2008-06-09
> **Unix_Slayer said:**
> I didn't like wicd. Try another one. Try kwifimanager. I had the same problem, until I switched over to using knetworkmanager. Now it works fantastic. I hot coded my wired card in second. Now I use my wireless card for the internet, and my wired for the intranet.

Wicd is awesome.

---

### Post by Unix_Slayer on 2008-06-09
> **stchman said:**
> Wicd is awesome.

When it works. I just tried to install it again, and it no worky.

---

### Post by fatjedi on 2008-06-09
neither work

---

### Post by Unix_Slayer on 2008-06-09
> **fatjedi said:**
> neither work


Forget the wicd. They a different wlan manager. I seem to be able to use wifimanager or wireless assistant.

---

### Post by Creap on 2008-08-02
> **Unix_Slayer said:**
> I didn't like wicd. Try another one. Try kwifimanager. I had the same problem, until I switched over to using knetworkmanager. Now it works fantastic. I hot coded my wired card in second. Now I use my wireless card for the internet, and my wired for the intranet.
I tried kwifimanager. Pressing Scan for Networks, I simply get "no networks were found". And besides my own, there are several other networks in my near vicinity...

---

