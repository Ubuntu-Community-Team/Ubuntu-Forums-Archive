---
title: "Strange Internet Problem (Positive Trivial Checks)"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by mohitchawla on 2008-05-27
I had been using Gutsy for three months, when I decided to try some new distributions, when I removed Gutsy completely and got the new stuff working. But then again, I decided to install Gutsy again, with an additional Puppy Linux. Now , the thing is Internet won't work on Gutsy(wired or wireless) , while it works fine on Puppy.
The strange part is :

1. Earlier, with only Ubuntu (and a useless FreeDOS) installed, Internet(wired AND wireless) worked fine. But now, with Puppy and Ubuntu both installed ( no FreeDOS), Internet works fine on Puppy, but not on Ubuntu. So I tried to access Internet from the LiveCD interface, still no luck except a half loaded Ubuntu.com website and getting stuck at ```
Connecting to xxx.xxx.com ...
``` on eventually trying out Ubuntu.com again alongwith other sites.

2. I performed all the trivial tests and the results were :
->correct device recognition, correct driver recognition, correct interface information, correct dhcp address assignment, correct DNS, positive ping results with 0% packet loss. 

Now, I've started to believe there's some problem with Mozilla, but that seems somewhat improbable. I am really confused right now, and any help will be really appreciated. Thanks !

Edit : I  have also tried the ipv6 fix by disabling it, but still , no use.

---

### Post by SpaceTeddy on 2008-05-28
mhm - what can you ping, exactly ? only local machines, or stuff on the internet aswell ? also, can you access the paket repositories, or is that blocked too ?

if it is not blocked, i'd suggest you try something like w3m or wget to test of this is a firefox or a general computer problem...

Also, i did not see the check for the proper default gateway in your list :) did you check that aswell ?

hope it helps (somewhat) :)

---

### Post by Iowan on 2008-05-28
Did you power-down between OS's?  There's a thread around here (somewhere) that mentions the NIC not getting properly reset between OS changes (it was XP and Ubuntu) unless machine was fully restarted.

---

