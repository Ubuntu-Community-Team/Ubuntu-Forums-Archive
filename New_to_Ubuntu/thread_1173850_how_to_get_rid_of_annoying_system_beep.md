---
title: "how to get rid of annoying system beep?"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by zzzonked on 2009-05-30
How do I get rid of that annoying system beep, and just get the screen to flash every time there's an error? I can't seem to find where to disable it. Ubuntu 9.04.

---

### Post by whoop on 2009-05-30
System-->preferences-->Power management-->general-->Extra--> Use sounde to.....

---

### Post by kpkeerthi on 2009-05-30
1. Edit this file:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

2. Add these lines:
```

blacklist pcspkr 
blacklist snd_pcsp 

```

3. Save and exit. **Reboot**.

---

### Post by zhhansen on 2009-05-30
Alternatively, this way works best for me.

```
sudo rmmod pcspkr
```

If you ever want the system beep back, use this command.

```
sudo modprobe pcspkr
```

---

### Post by fwaokda on 2009-07-12
If you have Jaunty(9.04) just go to System>Prefs>Sound and go to the sounds tab. Uncheck the "Play Alert Sound" and your good to go! ;)

---

### Post by khelben1979 on 2009-07-12
When I was using Debian on my Powerbook I just adjusted the bar inside KMix which affected beep so it was all down.

I see now that this isn't as easy on my PC. I have been able to disable it when I configured up and installed my own Linux kernel (sucessfully) a few years ago. Seeing what has been written in this thread, I see that it doesn't seem like a valid reason to compile your own kernel.. :)

---

### Post by JohnnySage50307 on 2009-07-13
> **zhhansen said:**
> Alternatively, this way works best for me.
 
```
sudo rmmod pcspkr
```
 
If you ever want the system beep back, use this command.
 
```
sudo modprobe pcspkr
```
 
I would avoid doing this...Supose your system crashes hard and you are attempting to repair it...that beep can be your friend when nothing else works.  Honestly, I would just go through System->Administration and just turn it off from there.  This will preserve it for both other users and should you need it for emergency purposes.

I'm actually speaking from experience...that beep is what told me if the OS kernel was even functioning or not on a friend's computer!!

---

### Post by sanemanmad on 2009-07-13
I agree. Don't remove the modules for the pcspkr, disabling through ```
System > Preferences > Sound > System Beep > untick system beep.
```

---

### Post by rivalarrival on 2009-08-01
[http://www.carcosa.net/jason/software/beep/](http://www.carcosa.net/jason/software/beep/)

Using the kernel module in the link, a script can listen on /dev/beep, and play a sound file every time the system beep would normally sound. 

Routed through the sound card, the system beep is MUCH less annoying, and quite useful.

---

### Post by Geocron on 2009-09-10
go to system>preferences>sound then on 2 tab (sounds) unclick "play alert sound"
that got rid of the beeping for me

---

