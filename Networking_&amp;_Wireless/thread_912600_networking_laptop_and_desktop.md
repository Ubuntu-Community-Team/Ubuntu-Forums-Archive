---
title: "networking laptop and desktop"
date: 2008-09-06
forum: Networking &amp; Wireless
---

### Post by n8makar on 2008-09-06
i will try to make this short. i have a desktop running windows xp hardwired into a dlink router and a laptop running ubuntu gutsy on wireless.

what i want to be able to do is access _everything_ on the desktop from my ubuntu laptop. i have samba installed and have made numerous attempts to create shared folders using different how to's, but windows wont recognize anything. also the ubuntu laptop can only ping itself and recieves no reponse from the desktop.

is there another better tutorial or am i just missing something?

---

### Post by n8makar on 2008-09-07
bump for great justice

---

### Post by n8makar on 2008-09-07
?

---

### Post by superprash2003 on 2008-09-07
firstly ensure that your xp machine is getting an ip address by typing ipconfig in the command prompt..then try pinging your ubuntu machine.. ensure that no firewall is blocking anything?

---

### Post by sanemanmad on 2008-09-07
> **n8makar said:**
> i will try to make this short. i have a desktop running windows xp hardwired into a dlink router and a laptop running ubuntu gutsy on wireless.

what i want to be able to do is access _everything_ on the desktop from my ubuntu laptop. i have samba installed and have made numerous attempts to create shared folders using different how to's, but windows wont recognize anything. also the ubuntu laptop can only ping itself and recieves no reponse from the desktop.

is there another better tutorial or am i just missing something?

Hi n8makar~ 

I have a few suggestions...

1. check your 'WORKGROUP' settings.
     *i.e* is Windows and Ubuntu on same workgroup?
2. Have you disabled any firewalls on Windows.
3. Does your Dlink have any settings that enable/disable netbios?
4. What does *ifconfig ath0* show? - Ubuntu
5. What does *ipconfig /all* show? - Windows

---

### Post by sanemanmad on 2008-09-07
> what i want to be able to do is access _everything_ on the desktop from my ubuntu laptop. i have samba installed and have made numerous attempts to create shared folders using different how to's, but windows wont recognize anything. also the ubuntu laptop can only ping itself and recieves no reponse from the desktop.

is there another better tutorial or am i just missing something?

Are you interested in something like VNC?... 

[http://realvnc.com/support/documentation.html](http://realvnc.com/support/documentation.html)

or 


Windows RDP or similiar

[http://ubuntuforums.org/showthread.php?t=763112&highlight=Windows+RDP](http://ubuntuforums.org/showthread.php?t=763112&highlight=Windows+RDP)

---

