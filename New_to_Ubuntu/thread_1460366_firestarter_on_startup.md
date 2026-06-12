---
title: "firestarter on startup?"
date: 2010-04-22
forum: New to Ubuntu
---

### Post by OneLine on 2010-04-22
Hi, I'm new to ubuntu and was wondering, I've installed firestarter and would like to have it run everytime I startup my computer, I've just reset my computer and firestarter didn't appear, I went to system > administration > firestarter.

Thank you.:KS

---

### Post by xaegis on 2010-04-22
Add it under: System>Preferences>Startup Applications

You can find out the startup command by right clicking on the Ubuntu logo and selecting Edit Menus then find the program and check its Preferences.

This is how I would do it. There may be a better way tho.
:)

---

### Post by OneLine on 2010-04-22
> **xaegis said:**
> Add it under: System>Preferences>Startup Applications

You can find out the startup command by right clicking on the Ubuntu logo and selecting Edit Menus then find the program and check its Preferences.

This is how I would do it. There may be a better way tho.
:)

Thanks for your reply, I just tried that, when I restarted it said there were not enough permissions to start firestarter :(

---

### Post by coffeecat on 2010-04-22
You don't need to run firestarter every time you boot up the computer. Firestarter is not the actual firewall - it is merely a GUI configuration tool to set up firewall rules. The real firewall is Iptables which is running all the time and its default configuration is quite adequate for most purposes.

Simply start Firestarter whenever you need to add/remove rules. But you probably don't need it anyway. Linux !=Windows. You are probably conditioned by Windows 3rd party firewalls which are an entirely different kettle of fish.

---

### Post by 2hot6ft2 on 2010-04-22
> **OneLine said:**
> Hi, I'm new to ubuntu and was wondering, I've installed firestarter and would like to have it run everytime I startup my computer, I've just reset my computer and firestarter didn't appear, I went to system > administration > firestarter.

Thank you.:KS
Firestarter is just a front end for configuring the iptables so it doesn't need to be in the notification area to be running.
Just click on Edit > Preferences
and check the box for minimize to tray on window close if you want to see it there.
Personally I would rather not see it since I know it's running.

---

### Post by OneLine on 2010-04-22
Thanks for the replies :).

I was looking at the Events in firestarter and there is loads of IPs trying different ports, one IP appears in red which tried SSH, are people trying to get into my computer?

---

### Post by 2hot6ft2 on 2010-04-22
> **OneLine said:**
> Thanks for the replies :).

I was looking at the Events in firestarter and there is loads of IPs trying different ports, one IP appears in red which tried SSH, are people trying to get into my computer?
You'll see a lot of that but unless you start installing SSH, samba and stuff you're ok the door is closed.
Most are from just normal web traffic.

---

### Post by 2hot6ft2 on 2010-04-22
You can test it here with the shields up port scanner
[https://www.grc.com/](https://www.grc.com/)

or any other port scanner you want. There are plenty out there

---

### Post by OneLine on 2010-04-22
> **2hot6ft2 said:**
> You'll see a lot of that but unless you start installing SSH, samba and stuff you're ok the door is closed.
Most are from just normal web traffic.

Thanks for your reply, I was thinking about setting up a second PC with Ubuntu Server on, would that be ok? would my computers remain secure? Thank you.

---

### Post by 2hot6ft2 on 2010-04-22
> **OneLine said:**
> Thanks for your reply, I was thinking about setting up a second PC with Ubuntu Server on, would that be ok? would my computers remain secure? Thank you.
Yes, unless you open ports then they are closed. There are many here running servers that can answer any specific questions you may have in the sub forums
Security Discussions
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)
and
Server Platforms
[http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339)

---

### Post by OneLine on 2010-04-22
Thank you very much.

---

### Post by 2hot6ft2 on 2010-04-22
> **OneLine said:**
> Thank you very much.
You're welcome and if you need any help just ask there are many very knowledgeable people here to help.

---

### Post by oldos2er on 2010-04-22
The OP might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by OneLine on 2010-04-27
I was looking on the log file, and over the past few days, it seems I'm getting 400 attacks on my computer a day, I'm worried.

---

