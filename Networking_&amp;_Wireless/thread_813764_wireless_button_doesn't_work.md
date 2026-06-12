---
title: "wireless button doesn't work"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by ming136 on 2008-05-31
Hi,

I'm new to ubuntu, but I think my main problem is that I am unable to turn on my wireless to scan for networks. The wireless button on my keyboard does not work in ubuntu.

Can anyone help me?

Im using ubuntu hardy on a acer travelmate notebook.

Thanks!

---

### Post by lisati on 2008-05-31
1) This isn't Windows, so you might have to do some tinkering in Ubuntu that you wouldn't have to do in Windows, and vice versa.
2) Have a look at the Syetem->Preferences->Keyboard menu - you might be able to set the "Wireless" button to do what you want (but I'm not sure of what exactly to type in)
3) Use the mouse to click on the networking icon on the top of the screen - this can help you set up some aspects of networking, including wireless

---

### Post by ming136 on 2008-05-31
Hey,

Thanks for that. I tried looking at the keyboard menu before already and couldnt find anything related to a wireless button.

I also changed my network manager to wicd manager as someone had recommended me before, but there I was also not able to find any option to turn on my wireless.

is there no terminal command i can enter to activate my wireless?

thanks.

---

### Post by Kevbert on 2008-05-31
This post may help: [http://ubuntuforums.org/showthread.php?t=541953]("http://ubuntuforums.org/showthread.php?t=541953")
Unfortunately the best thread I can't find and I deleted my subscription to it yesterday!!!
I have a travelmate 803Lci with both XP and Gutsy on it.  I find that if I run XP, leaving wireless on, when I next boot into Gutsy the wireless switch works fine, but if I turn it off in XP, when I next run Gutsy the wireless switch no longer works.

---

### Post by chili555 on 2008-05-31
You might check here: [http://ubuntuforums.org/showthread.php?t=224350&highlight=acer-acpi&page=10](http://ubuntuforums.org/showthread.php?t=224350&highlight=acer-acpi&page=10) and start at post #96. In summarry, to activate wireless, you will need to:```
sudo su
echo 1 > /proc/acpi/acer/wireless
```Let us know.

---

