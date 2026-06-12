---
title: "I cant connect to unsecured wireless hotspots in 8.04 on my eee"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by squidfish2 on 2008-06-07
I've recently installed ubuntu 8.04 on my eee 701. i then used ricey's eee script to get most of the drivers working. wireless didnt work, but i compiled the madwifi stuff myself and now the wireless driver works fine. im able to connect to my home wireless which is secured with WPA. however, i've noticed that when i try to connect to hotspots that dont use encryption, i am unable to connect.
the kind of networks that im talking about, are the kind you find at hotels that let you connect without a wep key, but when you try to load a page, redirect to a login page (where your login details are provided by the hotel, or whoever).
the network manager that comes with ubuntu doesnt allow me to leave the security field blank - it forces me to choose either wep or wpa security, even if i KNOW the network doesnt use any. regardless of which one i choose (leaving the field for the actual key itself blank), i am unable to connect. if i set it to roaming mode, it also is unable to any wireless network (regardless of security).
does anyone have any solution to this, or at least know why it isnt working?
also, i googled around and chatted on #ubuntu, and the only possible thing i've found is to try Wicd instead of the network manager that comes with ubuntu. i've installed it now, but i'll have to wait until 2moz before i can test it at a hotspot. regardless of whether or not this works - i would still like help to get the default ubuntu network manager working fully. i find it ridiculous that it seems the default ubuntu network manager is unable to connect to unsecured networks.
surely this is not the case? surely its just something i've missed...

---

### Post by kevinatkins on 2008-07-01
I'm seeing exactly the same behaviour, and I'm sure it used to work. Worse still, if I repeat attempts to connect, the whole machine freezes dead and I have to do a hard reset.. Does anyone know what's going on?!

---

### Post by hannah187 on 2008-07-02
same here.. I have got my REALTEK wifi sorted through NDISWRAPPER however cannot connect to unsecured wireless hotspots. Any remedy..anyone

---

### Post by detroit/zero on 2008-07-02
I've had the same problem in Feisty and Gutsy. I haven't run into it with Hardy, yet, though. I'm sure I will eventually, if other people are, too.

---

### Post by HELLO_science on 2008-07-06
could it be some hotspots are scared of linux?

isn't their some system information that the hotspot asks for that the hotspot can(or could) deny access?

i have this problem.  some 'spots work great but others dont.

---

### Post by Boompoet on 2008-11-12
I've had the same problem at a super 8 hotel and I recently had the same issue at a Comfort Inn, but wired worked and the wireless worked in the lobby. The Super 8 had plenty of signal, but never could connect. It's bizzar. I'm running duel boot with XP on the other side and the networking is hosed in it (surprise surprise) so I couldn't get on at all even to look up the problem.

---

### Post by Monkenstein on 2008-12-08
I've had the same problem. In my case the hotspot router was giving out a /32 host address with DHCP so the default gateway was on a different subnet. I changed the subnet mask with

```
sudo ifconfig ath0 netmask 255.255.255.0
```

and added a default route pointing at the hotspot router with

```
sudo route add default gw 172.28.64.1
```

and the connection worked fine.

Maybe Windows just doesn't care if you're on a different network to your gateway?

Hope this helps.

---

### Post by 00chilli00 on 2009-01-06
hey im just putting this out there
but 
maby they are filterd networks?
because it will show unsuicure even if it is filterd, just cheak that there not filterd
hope i helped

---

### Post by robbiewalter on 2009-01-27
Monkenstein's solution worked for me.

Changing the netmask worked the first time, but adding the route took a few tries.

At first, when running

     sudo route add default gw 172.20.100.1

I received the message

     SIOCADDRT: No such process

But after 3 or so tries (or about 2 minutes), it completed successfully and now I am on the internet.

Thanks for the help!

BTW: I'm running Eeebuntu 8.10 on a 701 4G.

---

