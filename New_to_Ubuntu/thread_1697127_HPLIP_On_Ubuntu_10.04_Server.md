---
title: "HPLIP On Ubuntu 10.04 Server"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by gdeeble on 2011-02-28
Good Afternoon, and thank you for looking. I'm still relatively new to Linux in general but I've jumped ship from CentOS, as a lot of friends said that this would be easier for me to use. I've seen a lot of great features of the Ubuntu Server and want to thank everyone who's put this together along with a lot of the posts that people who've answered questions for other people that I've used. The main reason for starting to use the Ubuntu is the recommendation which I should have done from the start, but the other side is, I've got an HP Photosmart All-in-one C5580 printer, which I've searched for info on, but can not get to work right. I've asked my friends who've recommended this, and I've installed the proper programs(Cups and HP Lip) and seem to still be having issues. The problem I'm experiencing, is that when I install the printer, no PPD is found for my printer, despite the fact that HP LIP says it's supported. I know when I hooked the printer up in CentOS it was found as a C8100 without HP LIP and I couldn't figure out exactly how to use the HP LIP properly with it.  With this it's detected as a C5500 and didn't have the driver, so I've searched for a guide to get it to work right, but have been unsuccessful, the only things I've found are about the bug of it printing in 600dpi vs 1200dpi which included a PPD file but when I use that, it seems that the printer only prints on the bottom right corner of the page. If anyone has some tutorials for this printer or has personal experience with setting up this printer and could provide me either the tutorial(which I'm not lazy, I'll attempt read it and see if I can't fix it from the tutorial first, then ask for more assistance) or some direction and assistance with getting this up, I would be greatly appreciative. Thanks for all your time. -Gary

---

### Post by gdeeble on 2011-02-28
Might also be important to say that it's going to be networked, and I'm also running Zentyal(Ebox) on the computer for management as well.

---

### Post by gdeeble on 2011-03-01
I just tried downloading the tarball file and exacting the PPD files to see if that helps and for some reason, it's just spitting it down on the bottom right with all the PPD files found in the tarball. No one with any suggestions?

---

### Post by Sef on 2011-03-01
Copy and paste this command from the terminal to see if it is already installed, and if not, then it will install it:

```
Sudo apt-get update && sudo apt-get install hplip
```

---

### Post by gdeeble on 2011-03-01
Appreciate it. Seems that it did an update for the packages but sadly it's still not printing to the appropriate way. :( It's printing the test print on 4 sheets of paper. I know it's something on the linux box as I just connected it to my windows machine and printed the test page out there and it's only 1 sheet on there. :-\. It seems to have updated libhpmud0, hplip-data, hplip(3.10.2) though I had 3.11.1, and hpijs.

---

### Post by gdeeble on 2011-03-01
I retract my last statement, I guess it's a bug with 3.11.1 because the 3.10.2 driver just worked. Thank you so much.

---

