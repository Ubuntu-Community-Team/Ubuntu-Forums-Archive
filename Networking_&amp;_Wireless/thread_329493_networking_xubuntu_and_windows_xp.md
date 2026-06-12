---
title: "networking xubuntu and windows xp"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by TheOtherLinuxFreak on 2007-01-01
ok i want 2 network windows xp and xubuntu Edgy. i want to hook them up directly to each other. the windows has 2 network cards and the xubuntu is pluged directly into it. i want to share the internet connection.  
How do i set it up? i heard that to connect two pcs together u have to make a crossover cable. Do u have to make one in order for it to work? thats no big deal if u have to i was just wondering. i have experemented connecting 2 windows pc together but not linux.


thanks in advance

---

### Post by TheOtherLinuxFreak on 2007-01-01
does any of the 17 people that looked at this have any advice??

---

### Post by TheOtherLinuxFreak on 2007-01-02
anyone:confused: :confused:

---

### Post by wireddad on 2007-01-02
I am not an expert and have not attempted this but have you tried assigning a static IP to the linux machine and tell it to use the windows machine IP as the gateway?  The setup should be very close in either windows or linux.

---

### Post by sphetr2 on 2007-01-02
.

---

### Post by scrooge_74 on 2007-01-02
i have done that but the other way around.  The second card was in the Linbox, which then had dhclient to get an ip, then i would give static ip to the Winbox.  And i ran a firewall on the linbox plus use it as printer server and file server for the Winbox.

I used a old 10 mps hub I had because eventually I hooked other computers to that network.

---

### Post by Tazix on 2007-01-02
Yes, you need a crossover cable if you are directly connecting 2 machines to their ethernet ports (regardless of the OS).

A normal patch cable is for a hub or switch.

-Taz

---

### Post by scrooge_74 on 2007-01-02
Exactly I had a couple of extra patch cables around and the old hub

---

### Post by TheOtherLinuxFreak on 2007-01-02
i have no idea how to do this and i need to make a crossover cable. i will need pretty much step by step intructions. do i have to download anything? i didnt find anything that had to do with networking on my linux box. download samba? thats what i haerd was ubuntu's networking program

thanks for all the replys!!

---

### Post by scrooge_74 on 2007-01-02
You need samba if you want your Winbox to see files or use a printer in your Linbox, about making a crossover cable I have no idea.

---

### Post by TheOtherLinuxFreak on 2007-01-02
i think i have samba all set up. all i need is to make a crossover cable. or should i try with out one?

---

### Post by Tazix on 2007-01-03
> **TheOtherLinuxFreak said:**
> i think i have samba all set up. all i need is to make a crossover cable. **or should i try with out one?**

If you don't have a hub or a switch, it will not work without a crossover cable. You won't get link lights on the ethernet cards. It has nothing to do with the Operating Systems.

Connecting 2 machines directly with a cable (ethernet card to ethernet card) = crossover patch cable.

Connecting 2 or more machines to a hub or switch = normal patch cables.

-Taz

---

### Post by bobpur on 2007-01-03
The crossover cable is no big issue. You can buy one at about any place that sells computer parts. Some can even make one for you.
I never cared much for experimenting on a lot of expensive computer parts, especially if they're mine:)

---

### Post by TheOtherLinuxFreak on 2007-01-04
ok, today i will try to get one

---

### Post by TheOtherLinuxFreak on 2007-01-05
i got a crossover cable and i followed stormbringer's how to on networking and now it works. but how do i configure internet connection sharing?

---

### Post by TheOtherLinuxFreak on 2007-01-10
anyone??????

---

