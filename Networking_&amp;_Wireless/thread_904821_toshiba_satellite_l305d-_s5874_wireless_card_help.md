---
title: "toshiba satellite l305d- s5874 wireless card help"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by upsidedown010 on 2008-08-29
I just installed ubuntu on my toshiba satellite l305d- s5874 and the wireless card does not even show up. I have checked restricted drivers and the one for my card is on, but still no dice. can anyone shed some light for me, thanks!

---

### Post by mlrivera on 2008-09-30
I'm having the exact same problem mentioned above. In "Network" there is no option for wireless connection... 
I'm completely new at ubuntu, so any help explained as if i were a 3 year old would be much appreciated.

---

### Post by Keenan-Windel on 2008-10-23
I had this problem on my l305d-s5900. I think we've got the same wireless card, but I'm not sure, so you might want to research that. The madwifi driver probably needs to be installed: [http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780) I think the l305d is 64 bit, so that should work. I tried 32 bit instructions with no success even though I am running 32 bit Ubuntu on my 64 bit system. So do use the instructions in the link above.

When I followed those instructions, my card would detect essid's, but it couldn't connect to them on Intrepid Ibex. So I installed a program called WICD which can be found at [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) and that allows me to connect. WICD is a wireless utility, and it will replace and delete the gnome network manager.

Hope that helps.

Keenan

---

