---
title: "[SOLVED] Intel/PRO 2915ABG wireless card not working"
date: 2007-10-04
forum: Networking &amp; Wireless
---

### Post by dysonsphere23 on 2007-10-04
I have tried to install the drivers for my Intel/PRO 2915ABG wireless.

I have a Dell Inspiron 9300.  Ubuntu 7.04 (Studio, lowlatency kernel).  It was working fine until I had to return it to Dell for an unrelated problem.  They returned the laptop with a new system board, and since then there is no wireless card detected (iwconfig).

In the Device Manager (System>Preferences>hardware information) it is listed as PRO/Wireless 2915ABG Network Connection (i don't know if that was the same as the previous system board).  I have tried installing the drivers from Synaptic and also manually following [Spif's Tutorial]("http://ubuntuforums.org/showthread.php?t=13576"), to no avail.  

iwconfig reads a depressing: 

 lo        no wireless extensions.

eth2      no wireless extensions.

crap now i can't even configure my connections with the network manager, that is new since I tried the manual install, guess I deleted/overwrote some essential stuff.

hope someone can help, i am not in the mood for full system rebuild.

Thanks in advance.

---

### Post by dysonsphere23 on 2007-10-10
Well, it was fixed with a simple call to Dell support.

Power off machine, unplug, and remove battery.

Physically remove wireless card, clean the connections (blow like the old NES), reattach card.

Power up machine.  Presto, wireless!

Thanks for the great forum.

---

### Post by Lambert on 2007-10-10
Got to love a solution like that. 

Glad to see it was something that simple and it's working for you.

---

