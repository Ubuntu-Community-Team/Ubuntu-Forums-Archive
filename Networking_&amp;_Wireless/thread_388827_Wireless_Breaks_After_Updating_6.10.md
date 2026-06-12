---
title: "Wireless Breaks After Updating 6.10"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by Spira Studios on 2007-03-20
I'll preface this post by stating that I am by no means a Linux expert. I've played around with a few distros, but I still have a tremendous amount to learn.

On to the problem...

I recently revived an older Athlon machine with the intentions of using it as a media server/LAMP Test Environment/Lesson In Linux.

I had a Live CD I burned of Ubuntu 6.10 that I downloaded several (6 maybe?) months ago. I used the disc to install Ubuntu desktop. The machine has both an ethernet card, as well as a Linksys WMP11 802.11b wireless card. Upon the initial installation, everything seemed to be working properly. I was able to fill in my router's SSID and connected to the internet with no problems.

My next step was to open up a terminal with the intentions of getting my install up to date, since I had used a CD that was several months old. I followed instructions for enabling the multiverse and universe repositories, and then I did a "sudo apt-get update" and then "sudo apt-get upgrade". My confidence was feeling a boost now as I watched the lines of text scroll by indicating that I had successfully initiated the update process.

The update finishes, and I restart the machine. I  log in, and much to my surprise I find that my wireless card is no longer working. I check the "Network" section under "Administration", and see that my wireless card is still listed, however it now says it is a "Wired Connection (wlan0)".

At this point, my lack of experience leaves me with no idea of what to do next. I assume this could be some sort of driver issue, but it seems to me that a simple upgrade should not break an otherwise functioning piece of hardware.

Any advice or solutions that anyone can provide would be greatly appreciated. I'm not at the machine now, but I can provide more details later tonight if necessary.

Thank you in advance.


Matthew Kivett | SpiraStudios.com

---

### Post by spd106 on 2007-03-21
Try following this thread [http://www.ubuntuforums.org/showthread.php?t=377545](http://www.ubuntuforums.org/showthread.php?t=377545)

---

