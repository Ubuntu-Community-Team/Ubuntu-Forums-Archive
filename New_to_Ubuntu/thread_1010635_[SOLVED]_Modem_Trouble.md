---
title: "[SOLVED] Modem Trouble"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by jalehtor on 2008-12-14
This is my third very, very stupid question for the day, but the first two questions received wonderful answers, so here goes.

Thanks to help from this forum, I've got Ubuntu 8.10 installed on a stripped (well, not so stripped now) Compaq. I have cable connection through Charter. My modem is Ambit u10co18.The problem is that the modem is not allowing me to connect to the internet. According to the intro, I'm going to need to download further files to get this to work. Does anyone know where I can get hold of these files? Also, I'm having a hard time finding info about this modem. Any ideas on where I can go to learn more about all this?

---

### Post by slammed87d21 on 2008-12-14
Is it a cable modem?

---

### Post by jalehtor on 2008-12-14
Yes it is. It is a modem for Charter cable.

---

### Post by HotShotDJ on 2008-12-14
> **jalehtor said:**
> Yes it is. It is a modem for Charter cable.
How do you have it (the cable modem) connected to your computer?  If you are using an ethernet cable, it should work without any further configuration.  Since your having trouble, I suspect you have it connected via a USB cable.  If at all possible, switch to ethernet and you should have no trouble.

---

### Post by jalehtor on 2008-12-14
repeat post sorry

---

### Post by jalehtor on 2008-12-14
> **HotShotDJ said:**
> How do you have it (the cable modem) connected to your computer?  If you are using an ethernet cable, it should work without any further configuration.  Since your having trouble, I suspect you have it connected via a USB cable.  If at all possible, switch to ethernet and you should have no trouble.

No, it's not a USB cable. It's still not connecting, however. I wonder if there's a problem with the installation, since I'm already having some problem with freezing. I've tried out the games, and the computer invariably freezes and must be restarted after any preinstalled game. It also froze when I put it through a hardware component test.

---

### Post by HotShotDJ on 2008-12-14
> **jalehtor said:**
> I wonder if there's a problem with the installation, since I'm already having some problem with freezing. I've tried out the games, and the computer invariably freezes and must be restarted after any preinstalled game. It also froze when I put it through a hardware component test.I doubt that these two things are related, but NEITHER should be happening.  Are you by any chance dual booting with Windows?  If so, can you get to the internet when you boot to Windows?

A couple other things to try... shut down you computer, then unplug the modem's electrical cord.  After at least 1 minute, plug the modem back in.  After the modem cycles back on, boot up your computer into Ubuntu.  Do you have a connection now?

If that doesn't work... try booting up using the installation CD that you used to install Ubuntu.  Do you get a connection to the internet when you are running the LiveCD?  If so, a reinstallation may be indicated.

---

### Post by Martje_001 on 2008-12-14
To find more info about your hardware, go to a terminal (Applications --> Accessories --> Terminal) and type:
```
sudo lshw
```
It will then ask you for a password. This is the password of your user account, you don't see what you type! After that copy and paste it here between [ CODE ] - tags. Good luck!

---

### Post by jalehtor on 2008-12-14
> **Martje_001 said:**
> To find more info about your hardware, go to a terminal (Applications --> Accessories --> Terminal) and type:
```
sudo lshw
```
It will then ask you for a password. This is the password of your user account, you don't see what you type! After that copy and paste it here between [ CODE ] - tags. Good luck!

I did as you said, and I do indeed use ethernet interface.

---

### Post by Martje_001 on 2008-12-14
OK, can you post it here? And could you post the output of
```
ifconfig
```
?

---

### Post by jalehtor on 2008-12-14
> **HotShotDJ said:**
> I doubt that these two things are related, but NEITHER should be happening.  Are you by any chance dual booting with Windows?  If so, can you get to the internet when you boot to Windows?

A couple other things to try... shut down you computer, then unplug the modem's electrical cord.  After at least 1 minute, plug the modem back in.  After the modem cycles back on, boot up your computer into Ubuntu.  Do you have a connection now?

If that doesn't work... try booting up using the installation CD that you used to install Ubuntu.  Do you get a connection to the internet when you are running the LiveCD?  If so, a reinstallation may be indicated.

I shut down the computer, unplugged the modem, waited and reinstalled, and it worked!

Thank you.

Now I have to figure out what truly stupid question I will be able to come up with next. 

THANK YOU! I love these forums.

---

### Post by HotShotDJ on 2008-12-14
> **jalehtor said:**
> THANK YOU! I love these forums.I'm pleased that we were able to get you fixed up. :)

---

### Post by jalehtor on 2008-12-14
> **HotShotDJ said:**
> I'm pleased that we were able to get you fixed up. :)

I'm pleased, too. Now I need to figure out how to put a "solved" mark next to my threads. 

Btw, Ubuntu works nearly four times as fast as my poor mother's Vista laptop. I don't quite understand how anyone in his right mind would have okd releasing that most unfortunate system to the public. Ubuntu is (so far) working faster than my old xp as well. So I'm pretty damned happy right now, but it's nearly 4 am where I am, and this could all be a hallucination....:confused:

Thank you.

---

### Post by HotShotDJ on 2008-12-14
> **jalehtor said:**
> I'm pleased, too. Now I need to figure out how to put a "solved" mark next to my threads.Just use the "Thread Tools" menu near the top of the thread.  Also, don't forget to click the "Thanks" button in the reply(s) that were helpful to you (the red & yellow button in the bottom-right of the helpful message -- near the "quote" button)

Oh, BTW... I've been using Linux as my primary operating system for nearly 8 years now, and I assure you, you are not hallucinating. :)

---

