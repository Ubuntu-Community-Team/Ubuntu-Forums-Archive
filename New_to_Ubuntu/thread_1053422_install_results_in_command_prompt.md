---
title: "install results in command prompt"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by mrsynergy on 2009-01-28
I am tryint to remain loyal to Ubuntu but my first try kind of failed. Here's what i did. Desktop installed ubuntu-8.10-desktop-i386(2).iso on a compaq deskpro PIII with 256 ram. All other devices are std compaq devices. Everything booted up as normal, I got the std install screen, but when if finished it just got.
ubuntu@ubuntu:$_ 
So I have no idea where the log file is so I can give you more info on why it failed. I typed ls and it said Desktop. I then typed uname -a and idsplayed 2.6.27-7 generic.

I was at least expecting to see verion 8.10

So what do I do now. 



No idea what to do from here?:(

---

### Post by avtolle on 2009-01-28
You are indeed in 8.10. Given your RAM, I'm surprised it installed from the Live (Desktop) CD, as the minimum RAM is 384 mb, according to the official site. The command prompt makes me believe you are still on the installation CD. Did you remove the CD and restart your system once installation finished?

---

### Post by utnubuuser on 2009-01-28
try > sudo startx

---

### Post by Gulyan on 2009-01-28
> **mrsynergy said:**
> 2.6.27-7 generic.
I was at least expecting to see verion 8.10

1). the 2.6.27-7 is the kernel version, not the ubuntu one :)
2). try to run one these commands to start the graphical interface:
```

sudo /etc/init.d/gdm start
sudo xinit

```

I hope this solves your problem.

---

### Post by mrsynergy on 2009-01-29
> **avtolle said:**
> You are indeed in 8.10. Given your RAM, I'm surprised it installed from the Live (Desktop) CD, as the minimum RAM is 384 mb, according to the official site. The command prompt makes me believe you are still on the installation CD. Did you remove the CD and restart your system once installation finished?

Well that serves me right for not reading properly. When I remove the CD and rebooted, it when straight back to XP so I was on the try before you install. I am retrying again (as we spk). How if there is insufficent memory then sure, Ubuntu should just dispaly a message "insufficent memory". I have a done a belarc report. I 

Answer this question. All I want is to get the log file with all the boot up errors. They just disapppear of the screen to fast.

---

### Post by mrsynergy on 2009-01-29
> **utnubuuser said:**
> try

Fatal: Module mach64 not found
(EE) drm Open failed
(EE) MACH64(0): DRIScreenInit Failed
could not init font path element /usr/share/fonts/x11/misc, removing list

Fatal server error
could not open defaukt font "fixed"
giving up
xinit: connection refused (errno111): unable to connect to X server
xinit: No such process (errno 3): Server error.
ubuntu@ubuntu: $_ 

That is a screen dump of what I can see. 
How the heck do you type the tilda sign?
:(

---

### Post by mrsynergy on 2009-01-29
> **Gulyan said:**
> 1). the 2.6.27-7 is the kernel version, not the ubuntu one :)
2). try to run one these commands to start the graphical interface:
```

sudo /etc/init.d/gdm start
sudo xinit

```

I hope this solves your problem.


fatal server error could not open default font 'fixed'giving up
connectio refused errno (1111) : unable to connect to server
No such process (errno3): Server error

It looks like this pc is toast. What ya think?

---

### Post by mrsynergy on 2009-01-29
> **avtolle said:**
> You are indeed in 8.10. Given your RAM, I'm surprised it installed from the Live (Desktop) CD, as the minimum RAM is 384 mb, according to the official site. The command prompt makes me believe you are still on the installation CD. Did you remove the CD and restart your system once installation finished?
BTW (By the way) I removed the CD and when I rebooted it still cmae back with XP so I guess notning installed over XP. Damm Microsoft, but I will prevail with the help from the community.

---

### Post by egalvan on 2009-01-29
> **mrsynergy said:**
> fatal server error could not open default font 'fixed'giving up
connectio refused errno (1111) : unable to connect to server
No such process (errno3): Server error

It looks like this pc is toast. What ya think?

Probably not enough RAM. 

Try running the memtest option on the LiveCD.
It's one of the last options, towared the bottom of the initial LiveCD boot screen.

Also,
Try downloading Puppy Linux LiveCD.

It will run fine on 256M. 

This will test your machine to see if it is working.

---

