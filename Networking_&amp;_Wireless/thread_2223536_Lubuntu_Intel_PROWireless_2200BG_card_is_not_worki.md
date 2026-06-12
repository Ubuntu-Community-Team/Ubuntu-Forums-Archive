---
title: "Lubuntu Intel PRO/Wireless 2200BG card is not working"
date: 2014-05-11
forum: Networking &amp; Wireless
---

### Post by grman401 on 2014-05-11
Im new to ubuntu and i am on a gateway MA2 laptop and my wireless card is a [COLOR=#000000][FONT=Proxima-Nova]Intel PRO/Wireless 2200BG and i have no clue how to get this working if someone could help that would be great thanks![/FONT][/COLOR]

---

### Post by grman401 on 2014-05-11
yes i just installed lubuntu 14.04 on my gateway ma2 and i cannot connect wirelessly at all..my wireless card is not working..How can i do this offline to install the right things needed?

---

### Post by praseodym on 2014-05-11
Hi,

please show
```

lsmod
ifconfig -a
iwconfig
rfkill list
cat /etc/resolv.conf
```

---

### Post by kc1di on 2014-05-11
Hi and welcome to Ubuntu,
[here is a thread]("http://ubuntuforums.org/showthread.php?t=2079211") that may be of help in getting it going.

---

### Post by mörgæs on 2014-05-11
Please stop multiposting. Threads merged.

---

### Post by grman401 on 2014-05-11
the thread did not help at all..i followed the directions and nothing!

---

### Post by beaucoder2 on 2014-05-12
Hi grman401,

A few things to check:  

Does your computer have a wireless LED showing Off and On. Some systems are orange at off showing they are activated and then turn blue when a signal is detected. If NO lights show the wireless CANNOT function. Usually a function key will show something that looks like an antenna. Check your user manual. Look it up online if you can't find it.

Can you find anywhere else via google for a fix to your wireless LAN device? Such as stackoverflow or ubuntu geek or superuser, etc? 

Do you have any wireless adapters handy or you can borrow? I have 4 adapters precisely because upgrades are slow to accommodate most of the adapters used. My old Netgear N150 has saved the day a few times. I also test with a KeeBox, Tenda and another newer Netgear. You can get a Tenda for about $10.00 on sale. Amazon has tons of low-cost adapters available. Check for Linux compatibility first. Think you want the ZoomSig X3111899893?  Google on "Linux ZoomSig X3111899893" if it has problems they will show up. No news is good news here. Unless, of course, the Wireless card has just come out. I avoid the latest and greatest. Don't like being a guinea pig.

At Intel or maybe a related site if Intel didn't make the Wireless card, you might find some Linux/Ubuntu support listings. I once found source code for an early Tenda and deciphered the tortured instructions, compiled the code and it worked. 

Remember, too, that you can make changes to your kernel modules. It just takes time finding the instructions. 

As always, keep a log or journal that you edit along the way: what you did and the result. Mine say "Action" and "Result" in a 2-column Writer doc. MAKE BACKUPS!!! Nothing worse than trying to remember what the config entries looked like before I started twiddling with them.  Even better: Get Clonezilla and make an image backup to whatever drive or drives you have available. That way you can restore the whole partition or drive to exactly where it was before you started. Clonezilla is a jewel.

HTH and keep at it. Eventually the solution materializes. 

Ken

---

### Post by mörgæs on 2014-05-12
> **grman401 said:**
> the thread did not help at all..i followed the directions and nothing!

No you didn't. You have still not posted the output requested in post #3.

---

### Post by kc1di on 2014-05-12
Try this if you have not already done so.
```
rfkill unblock all
```
list the outputs of the commands in post # 3 also so we can see what's going on.

---

