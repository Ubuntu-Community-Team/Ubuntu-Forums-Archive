---
title: "realtek ethernet card issue"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by erikyuu on 2007-08-03
I have a realtek gigabit ethernet (RTL 8168/8111) card in an Asus A8Js laptop that suddenly stopped working in Ubuntu yesterday. It's fine in XP (ironically enough). From what I've been able to find in the forums, this card is beginning to be a pain in the butt. I tried the bug fix (unload/reload the driver module) and no luck.

I'm still a newbie with linux, so I'll try to be more specific. The card is acting as if its deactivated, even though gnome's network tools says it shouldn't be. When I looked at the system logs, I saw this:

Aug  3 20:46:10 Pig NetworkManager: <information>^IWaking up from sleep. 
Aug  3 20:46:10 Pig NetworkManager: <information>^IDeactivating device eth0. 
Aug  3 20:46:10 Pig NetworkManager: <information>^Ieth0: Device is fully-supported using driver 'r8169'. 
Aug  3 20:46:10 Pig NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Aug  3 20:46:10 Pig NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Aug  3 20:46:10 Pig NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Aug  3 20:46:10 Pig NetworkManager: <information>^IDeactivating device eth0. 


eth0 is the ethernet device. It cycles like this continuously, starting around yesterday when the stupid card started to not work. 

If you need anything else from me, please let me know (and if its something from the command line, please also give the command).

Thank you :)

---

### Post by Silent Warrior on 2007-08-03
Spooky, I got the exact same problem, and it started at about the same time as well! (Though, I'm using a 8139C.) I don't know if it matters, but there was a driver "update" at Windows Update I thought I'd try. If that's the cause of it, I'm gonna have to wound someone's inner child... Dead annoying, that.
Well, as I'm on the internet, it stands to reason I'm writing from XP, so I can't access my system log at the moment. I'll remedy that the next time I use Ubuntu.

Same cable, same connection modem-side, same router as other computers, and still it doesn't work from the same computer... I don't have any constructive suggestion, sorry.

---

### Post by erikyuu on 2007-08-03
I think I found a fix (meaning that I'm going to go test it after this post). It seems it pays to keep rechecking the forums to see what old thread pops up :)

My solution is here: [http://ubuntuforums.org/showthread.php?t=467757&page=2](http://ubuntuforums.org/showthread.php?t=467757&page=2) 
under Ruis Pais's post. If this is the solution, (insert your favorite adjective here) XP was messing around with the card.

Anyways, thanks! I know I found the solution on my own, but still, the community is why I use ubuntu.

---

### Post by Silent Warrior on 2007-08-04
If this works, I think I like that Rui Pais.

To the test!

---

### Post by spandon on 2007-08-04
Hi,
I had the same problem with a machine with a Realtek 8139 ethernet card, which was multi booting with XP,Vista,Ubuntu 7.04.
The problem has nothing to do with Ubuntu, it is a Windows problem.
If you check the windows updates recently - I found that I had installed a Windows Realtek update.
I rolled back the driver on windows - and all systems could connect to the net using the ethernet card.
Don´t know where thenew  driver originated from, but sent a bug report to realtek

---

### Post by Erol on 2007-08-04
rolling back windows driver fixes this issue. this is realy strange, but I can confirm that my NIC works again. thank you for the post

---

