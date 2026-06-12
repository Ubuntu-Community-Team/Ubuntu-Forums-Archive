---
title: "Netgear WG111v2 and Gutsy Gibbon"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by AdsoInk on 2007-11-09
Howdy,

This might be a fun one...

I'm working on a little development project and found that I needed to be mobile. I don't own a laptop, so I finangled one from my place of employment. It's a 1.6gz ThinkPad with 768mb RAM. It's not in the least bit optimal, but it's something and ensures that I can easily work side by side with my PM and graphics guy.

That said, the laptop had been stripped of it's wireless card and was delivered to me with a stripped to the bone install of XP. This project requires me to do a lot of work with RoR, so I figgered Linux would be my best bet for an OS. 

I have a Netgear WG111v2 Wireless USB 2.0 adapter that works fine on both Mac and Windows. I used it briefly with a previous install of Ubuntu with no issue. Given that Gutsy is a pretty recent distro, I haven't had any luck finding much of anything on-line away from Edgy and Fiesty instructions that haven't solved the issue.

All the conflicting USB ports have been blacklisted and I've also done everything possible with the ndiswrapper. The WIN98/ME drivers are installed, though I get an error message when I try to enable ndiswrapper telling me that the drivers aren't valid.

I did manage to get some activity out of it last night. Network Manager saw the available networks in my neighborhood, but the blue LED on the dongle didn't come on at all. After that one little nurst of success, nothing (and I have since tested the dongle on other machines).

I hope I've explained this well. I am relatively new to Ubuntu and haven't worked inside a terminal in ages.

HELP!!

Another question: would it behoove me to work with Xubuntu rather than the latest, full-blown OS?

Thanks,

TM

---

### Post by Lambert on 2007-11-10
This device looks to use the realtek rtl8180 chipset.

there are a couple recent posts with gutsy and this chipset.

Read these to see if they help you.

[http://ubuntuforums.org/showthread.php?t=584046&highlight=rtl8180](http://ubuntuforums.org/showthread.php?t=584046&highlight=rtl8180)

[http://ubuntuforums.org/showthread.php?t=585712&highlight=rtl8180](http://ubuntuforums.org/showthread.php?t=585712&highlight=rtl8180)

---

### Post by slayer^_^ on 2007-12-09
it appears your device is a fake v2 (mounting a v1 hardware).

i've posted my experience here, maybe it could be useful...

[http://ubuntuforums.org/showthread.php?t=632651](http://ubuntuforums.org/showthread.php?t=632651)

bye

---

