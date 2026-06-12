---
title: "8021x Wired Setup - Can't Write to /etc/ location...help!"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by mkukis on 2008-08-07
Using 8.04.1 LTS - Desktop:

I'm new to linux as you could've guessed but I'm trying to set up the 8021x authentication for the wired ethernet using this guide: [http://www.stevens.edu/itwiki/cgi-bin/wiki/index.php?title=Linux_802.1x](http://www.stevens.edu/itwiki/cgi-bin/wiki/index.php?title=Linux_802.1x)

the problem i'm having is that it won't let me add/create/save any files into the /etc/ directory...and i don't know what to do haha.

and then for the second step it says to "chmod +x it". does that mean to chmod +x 802wired.sh ? 

Thanks in advance for any help. sorry if they are noob questions but i searched around and couldn't find my answer. 

-matt

---

### Post by cdtech on 2008-08-07
First, welcome to the GNU/Linux world and the Ubuntu forum.

They did fail to mention that you need to be "root" to issue the commands at hand. All you need to do is add "sudo whatevercommand" and you'll be fine.

This is the same as having Administrator privileges but within Linux. Yes that does mean to chmod +x 802wired.sh so you would type on a command line (using a terminal) "sudo chmod +x ./802wired.sh (the ./ means current directory). To run the program you would type on the command line "sudo ./802wired.sh".

Hope this helps, and good luck.........

---

### Post by mkukis on 2008-08-07
thanks for the help!

i'm still having a problem adding the wpa_supplicant.wired.conf to the /etc/ directory. it gives me an "Error moving file: Permission denied". 

is there a way to override these permissions via the terminal and sudo commands? is there a way to create a .conf file via the terminal?

thanks again,

matt

- i attached a screenshot of my error

---

### Post by mkukis on 2008-08-07
I found out how to login as Root via some searching and i was able to add the wpa_supplicant.wired.conf to the /etc/ directory while in root. I think i have everything working now.


thanks for your help! 


-matt

---

