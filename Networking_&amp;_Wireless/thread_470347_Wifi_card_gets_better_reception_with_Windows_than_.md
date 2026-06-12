---
title: "Wifi card gets better reception with Windows than Linux"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by Protagonistics on 2007-06-10
I used Wubi to install FF on my dell laptop and it works fantastically. I'm very new to linux and have only a basic understanding of the terminal and its commands. I don't have wifi in my house (my parents still use dial-up on a -gasp- originally windows 95 computer now upgraded to win98 ) but I can access my neighbour's signal which comes in well enough to stay connected 95% of the time when I'm running windows but can't connect because the signal is too weak, it seems, in the same spot in my house with Ubuntu. I took my lappy out the to porch when I wanted to do the internet thing on ubuntu but the signal is only coming in at about 8-20%. Why is this and how can I change it? I use my pcmia slot or whatever its acronym is on the side instead of the internal wifi card which I have, by the way, downloaded the firmware for and it is working when I'm closer to a router. 
My card is a D-link DWL-G630 which comes up as Atheros communications AR5005G on the wireless network monitor in the top right of the screen and when I terminal "lspci". So what's the deal? why is my connection weaker or harder to hold in Ubuntu Feisty Fawn compared to Windows XP?

Thanks.

---

### Post by spd106 on 2007-06-12
This is a difficult issue as the madwifi driver reports signal strength differently to most other wifi cards. There are some workarounds for this, but I haven't tested them to see if they work.

You might want to consider using ndiswrapper with the windows driver to see if you get better results. You will need to disable the madwifi driver first though. To do this modify the /etc/default/linux-restricted-modules-common file, then reboot. Make sure you have an alternate network connection first or at least install the ndiswrapper packages.

---

### Post by asho79 on 2008-07-12
I'm pretty new to Linux and don't really understand how drivers work. But I do know that I had poor reception with my wireless on ubuntu compared to vista and installing additional drivers fixed the problem. However, I didn't uninstall my broadcom driver though. The forum I posted on is [Here]("http://ubuntuforums.org/showthread.php?p=5363511#post5363511") Maybe this isn't your problem though. It might be specifically for my computer. Compaq C500. 

Whenever I have to use windows (at our backwards work) I cringe. Ubuntu is heaps better than any Windows I've seen. I love it!

I even managed to get my wife onto it and she now loves it too.

---

