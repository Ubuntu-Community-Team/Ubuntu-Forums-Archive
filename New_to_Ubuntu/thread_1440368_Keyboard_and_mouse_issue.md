---
title: "|Keyboard and mouse issue"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by sheffield on 2010-03-27
Hi All
I need to get mu ubuntu up and running again as it has my wedding photos and 5 years+ of backed up photography work on them can anyone help?

A few days ago I started my linux box, which happily started to update then for some reason it crashed out (NVIDIA drivers I think).

I restarted, but the mouse and keyboard are not working at all
I have tried both USB/PS2 but niether are detected at all.  All I get is the login screen, and nothing else now obviously I cant type because no keyboard is working, so I dont know what state things are in.

But I can get to the terminal through the recovery console via grub

John

---

### Post by nothingspecial on 2010-03-27
Can you ssh into it from another box if you have one?

---

### Post by sheffield on 2010-03-27
I dont have another box apart from the one I use as a production machine

---

### Post by nothingspecial on 2010-03-27
If no keyboard or mouse will work then you are going to have to fix this via shh or a live cd.

---

### Post by sheffield on 2010-03-27
ok and thanks for that, but how I dont wanna lose any info I already have on the HD if possible

---

### Post by nothingspecial on 2010-03-27
Download a Ubuntu (or any other) linux live cd on your production machine and try to boot your broken machine with that.

Then copy your stuff to some sort of external media - you should really have backups anyway.

---

### Post by sheffield on 2010-03-28
HI
have managed to drop to terminal through grub and think it maybe the nvidia drivers?

---

### Post by sheffield on 2010-03-28
Have managed to get a login screen but still no keyboard or mouse everything just dead, wonder if something is starting or not starting?

how do i remove nvidia drivers from the terminal?

---

### Post by sandyd on 2010-03-28
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

---

### Post by sheffield on 2010-03-28
> **carlee said:**
> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

hi Carlee
tried still nothing

---

### Post by nothingspecial on 2010-03-28
Not a bad move.

If I were you though, I would try and backup my stuff with ssh or a live cd before trying to fix the computer.

Once you have it backed up, you have it backed up and if the computer explodes and turns into a mars bar you still have your stuff.

If you see what I mean.......

.......Your stuff is the priority, not the computer.... You can get another computer, you can`t get your photos back.

---

### Post by sheffield on 2010-03-28
hi and thanks
but sorry to sound really stupid but how do i use the live cd, do i mount it as per normal? or install onto the remainig partition?

many thanks to all

---

### Post by sheffield on 2010-04-05
Scrapped Ubuntu, managed to salvage what I could.  Dont think I shall use it again

---

### Post by nothingspecial on 2010-04-05
> **sheffield said:**
> Scrapped Ubuntu, managed to salvage what I could.  Dont think I shall use it again

After that experience, I don`t blame you.

As a victim of massive data loss myself, it doesn`t matter what operating system you use. I have 2 backups of most stuff. 3 of my music. And about 5 of my wifes college stuff.

[SIZE="4"][COLOR="Red"]_***BACKUP***_[/COLOR][/SIZE]

---

### Post by sheffield on 2010-04-06
thanks for your help and support, no longer using ubuntu

---

### Post by sheffield on 2010-04-06
But for those interested, heres how I managed to recover the files from the HD

used IF2ext for windows, mounted it as a drive, assigned a drive letter and copied from home dir to new drive

---

### Post by nothingspecial on 2010-04-06
I missed a post, the one on how to use the live cd.

Boot it, click on the computers file system and copy it.

Simples.

However, I don`t blame you after that experience, and, if I ever get a windows box, do you mind if I pm you?

---

### Post by sheffield on 2010-04-07
Nah I dont mind at all

currently rebuilding ubuntu, will it give a second chance

---

### Post by nothingspecial on 2010-04-07
Well, in that case, PM me any time you like. :)

---

