---
title: "Issues Starting WIFI"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by Zinnin on 2007-01-25
My basic issue is that the way my wifi card is setup sucks...
I am running a Compaq Persario V5000 with a built in wifi card

I know that the wifi card works in Linux, since I have gotten it working in
Sabayon Linux with zero configuration required

The problem is that my laptop has a built in power button for the wifi and 
that for what ever reason, unless the light is on for it
I can't use the wifi card

Problem is Linux doesn't see it as a button and assumes the card is off \ not there

In Sabayon I had to force a connection under Network Manager, but in Ubuntu thats
not working...

So I am wondering if anyone has another approach for this

Ubuntu 6.10 running on a

Compaq Persario v5000
2ghz AMD sempron
512 memory - 128 shared to the
ATI radeon  xpress 200m

---

### Post by featherking on 2007-01-25
is there a setting in your bios to keep the wireless on all the time? if there is turn that on then try networkmanager in ubuntu

---

### Post by Zinnin on 2007-01-25
nope, only thing there is to turn it off all the time

---

### Post by featherking on 2007-01-25
what kind of wifi card is it

---

### Post by Zinnin on 2007-01-26
I got it working last night using ndiswrapper, its a broadcom something but I don't remember off the top of my head, thank you for your time though

---

