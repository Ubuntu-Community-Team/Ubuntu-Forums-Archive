---
title: "ipod touch woes in jaunty- won't mount; not recognized by amarok or gtkpod"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by confused_person on 2009-08-20
I have a now-jailbroken 1st generation ipod touch with 2.2.1 firmware. My original problem (documented at this thread: [http://ubuntuforums.org/showthread.php?t=1228436](http://ubuntuforums.org/showthread.php?t=1228436)) was that when I plugged it in, it would mount as a camera and I couldn't access any of my music. Someone kindly directed me to a website instructing me to jailbreak the ipod and use ssh to modfy an xml file on the ipod, which I achieved without a problem. 

Unfortunately, little has changed. Although the ipod has been modified, it still acts like it's a camera when I plug it in and isn't recognized by gtkpod or amarok. 

I did some digging around on the subject and downloaded ipod-convenience and set it up with the ipod's IP address. However, when I give the command ipod-touch-mount in terminal, I get the following message: cannot touch `/media/ipod/test': Permission denied
Unable to write to /media/ipod.  Please adjust permissions and try again.

I'm terribly confused and just want to be able to use gtkpod (or amarok) like itunes to sync my music without having to install another OS. I hear there's a way to wirelessly transfer music using pwnplayer, but if there's a way to sync normally I would rather do that; various sources contend it is possible to sync with my situation but I just can't figure out how. Any input is much appreciated. Noob-friendly language would be helpful; if you have terminal-based advice, please spell it out so I know exactly what I'm doing! Thanks!

---

### Post by Katalog on 2009-08-20
Instead of just issuing the command "ipod-touch-mount" have you tried "sudo ipod-touch-mount"? That might get you past the permissions problem since you would be issuing the command as su rather than a regular user.

---

### Post by confused_person on 2009-08-20
> **Katalog said:**
> Instead of just issuing the command "ipod-touch-mount" have you tried "sudo ipod-touch-mount"? That might get you past the permissions problem since you would be issuing the command as su rather than a regular user.

Ah, that seemed to do the trick. Thank you! :) (Incidentally I also had to join the "fuse" group to do that, but it wasn't hard to find out how to do that.) 

However, now I have a new problem. when I issue sudo ipod-touch-mount, I get this error:

iPod is not responding to pings at xxx.xxx.x.xxx
Please set the environment variable IGNOREPING if you want to ignore this.

What do I do now...:confused:

---

### Post by Katalog on 2009-08-20
> **confused_person said:**
> Ah, that seemed to do the trick. Thank you! :) (Incidentally I also had to join the "fuse" group to do that, but it wasn't hard to find out how to do that.) 

However, now I have a new problem. when I issue sudo ipod-touch-mount, I get this error:

iPod is not responding to pings at xxx.xxx.x.xxx
Please set the environment variable IGNOREPING if you want to ignore this.

What do I do now...:confused:

Glad you got that far anyway. I do not own a Touch (or any other non-Linux friendly devices, for that matter - own a Sansa Fuze myself) and I'm not really familiar with fuse, so beyond the advice I already gave you I'm afraid I'm not going to be able to be of much assistance. Sorry I can't be of more help. Hopefully someone who is an expert on this sort of thing will stumble on this thread and be able to give you some guidance.

Best of luck! :)

---

### Post by Spencer Caplan on 2009-08-20
I have an iPod touch with firmware 2.2.1 and I tried entering the command: 
"sudo ipod-touch-mount"
and it said "command  not found."

Why is it not found?

---

### Post by hyperdude111 on 2009-08-20
> **Spencer Caplan said:**
> I have an iPod touch with firmware 2.2.1 and I tried entering the command: 
"sudo ipod-touch-mount"
and it said "command  not found."

Why is it not found?

You need to jaillbrake.

---

### Post by confused_person on 2009-08-21
bump

---

