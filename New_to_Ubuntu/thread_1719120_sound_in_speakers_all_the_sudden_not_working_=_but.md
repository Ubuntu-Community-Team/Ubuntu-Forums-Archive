---
title: "sound in speakers all the sudden not working =/ but it in headphones"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by BrainMeltingInLinux on 2011-04-01
so all of the sudden my speakers are not working. I did just do an upstate so idk if that is what it is. my charging port was broken, dell replaced the fan, port, and motherborad but nothing else and messed with nothing else so it SHOULDN'T be what they did but who knows. I really am I beginner. I can use the termial but I don't know unix so I need direction as to what yo input! I did from another forum input something that spit out [http://www.alsa-project.org/db/?f=1dc248199bbad582d0181ed7fc3ae2dba3ccca92](http://www.alsa-project.org/db/?f=1dc248199bbad582d0181ed7fc3ae2dba3ccca92) sorry not sure if this helps or you can see it!. also i had to reset my pasword and it gave me a new user name??????? is there any way to change this? I loved my old one (why I picked it, but I chould change it (i was quantumParadox) I could do something else physics like but I don't like what it is now really.

thanks so much. oh and i am using the newest ubuntu and did all the updates that came my way. 10.10?

PLEASE HELP I WANT SOUND AGAIN! IT WAS SO GREAT WHEN IT WORKED!!!

THANKS LOVE YOU ALL!!
FORMALLY QUANTUMPARADOX! 

again i can and like to use the termiminal and want to learn it but I need direction. I can only really look at files and folders, mp3s and pictures! 
thanks! <3:o:o:o:o:KS:KS:KS

---

### Post by BrainMeltingInLinux on 2011-04-01
i posted this in another place because no one was responding here so it can be closed (not sure how or if i can do that)

---

### Post by wolfen69 on 2011-04-01
Have you checked your sound settings?

---

### Post by lidex on 2011-04-01
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=dell" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

