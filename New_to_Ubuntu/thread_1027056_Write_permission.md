---
title: "Write permission"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by gacostac on 2008-12-31
Hi

I installed kubuntu 8.10 on a Dell studio540 today and cant get the computer to make a single sound.

I found a forum thread that explains how to solve my problem but cant add the line "options snd-hda-intel probe_mask=1" to the alsa-base file because i have no "write permission",

[http://ubuntuforums.org/showthread.php?t=969611]("http://ubuntuforums.org/showthread.php?t=969611")

How do I change my account so that i have complete control over this files to be able to modify them as required?

Thanks a lot

---

### Post by Michael.Godawski on 2008-12-31
hi,

with what application do you edit the file?

perhaps a simple 
```
kdesu
```
in front of the command will give you the necessary super user rights.

---

### Post by Paqman on 2008-12-31
> **gacostac said:**
> 
How do I change my account so that i have complete control over this files to be able to modify them as required?


You already do, you just need to tell the system to open them with full rights (aka root permissions)

Prefix your command with kdesu as described. So to edit a file you might use:
```

kdesu kate *path/to/file*

```

The system will ask for your password to authenticate that you aren't a threat and you'll be in.

---

### Post by gacostac on 2008-12-31
I found it using Dolphin file manager, and when i cliked it was opened by a program named 'Kate" V3.1.3

I don't understand were to type "kdesu". when i input this "edit /etc/modprobe.d/alsa-base" on the terminal, i get: 


gacostac@gacostac-desktop:~$ edit /etc/modprobe.d/alsa-base
Warning: unknown mime-type for "/etc/modprobe.d/alsa-base" -- using "application/octet-stream"
Error: no write permission for file "/etc/modprobe.d/alsa-base"

---

### Post by Paqman on 2008-12-31
Open a terminal and enter:
```

kdesu kate /etc/modprobe.d/alsa-base

```

You can hit tab to autocomplete file and folder names in the terminal, btw.

---

### Post by gacostac on 2008-12-31
This i what i get:

gacostac@gacostac-desktop:~$ kdesu kate /etc/modprobe.d/alsa-base
bash: kdesu: command not found
 

By the way, thanks for answering so fast :)

---

### Post by SuperSonic4 on 2008-12-31
KDE4 doesn't like kdesu much, I use kdesudo but I think you need to install it ```
sudo apt-get install kdesudo
```

Or you can use nano which is a terminal editor ```
sudo nano <file>
```

---

### Post by gacostac on 2008-12-31
I get this:

gacostac@gacostac-desktop:~$ sudo apt-get install kdesudo
Reading package lists... Done
Building dependency tree
Reading state information... Done
kdesudo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And then again:

gacostac@gacostac-desktop:~$ kdesu kate /etc/modprobe.d/alsa-base
bash: kdesu: command not found

I dont understand the other option:

Or you can use nano which is a terminal editor
Code:
---------
sudo nano <file>

---

### Post by Michael.Godawski on 2008-12-31
Try :

```
sudo nano /etc/modprobe.d/alsa-base
```

---

### Post by gacostac on 2008-12-31
Sorry

I read the last thread to fast, I used kdesudo and i was able to edit the file in Kate and saved it.

Know how do I proceed with the next part in the instruction:

Reboot or reload the module with
Code:

sudo modprobe -r snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=1

---

### Post by gacostac on 2008-12-31
I get this:

gacostac@gacostac-desktop:~$ sudo modprobe -r snd-hda-intel
FATAL: Module snd_hda_intel is in use.

---

### Post by Paqman on 2008-12-31
Try feeding it the second of those commands. If that doesn't work, just reboot.

---

### Post by gacostac on 2008-12-31
Guy, THANKS A LOT!!! I rebooted the computer and i can play music now!

This is why i love linux, this community forum is worth more than anything proprietary software can offer. 

Im very impressed at how fast you guys answer me! It was like a live chat with 3 experts.

I hope to keep on learning about linux, but now i know that with this forums help i will be able to get through anything, thanks :)

---

