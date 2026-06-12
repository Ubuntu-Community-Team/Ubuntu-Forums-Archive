---
title: "I fail...."
date: 2009-01-16
forum: New to Ubuntu
---

### Post by Sheeplauncher on 2009-01-16
So a month or so back I was away with my laptop and someone figured out my pw so I changed it and now I have not used this CPU for awhile because I have my desktop but now for the life of me can't remember what I changed it too or if I changed my user name. Are their any work arounds. I know of registry editor stuff for windows and i assume if exists in soMe form for ubuntu. I'm still kind of new so any help would be appreciated. Thanks 
-sheep

---

### Post by wannadumpwindows on 2009-01-16
Probably not the answer you're looking for, but . . . .

If someone figured out your password, and you were worried enough to need to change it, it might not be a bad idea to reinstall anyways. 

You never know what kind of software could have been installed while this person had access.

If it were myself, I would absolutely reinstall, maybe even wipe the disk in between just in case.

You can always use a LiveCD to back up any important data beforehand, and you should be all set.

There's no way to know for sure . . . .

---

### Post by iaculallad on 2009-01-16
Try reading Psychocat's [How to reset your password in Ubuntu]("http://www.psychocats.net/ubuntu/resetpassword").
On the registry issue, Ubuntu's got one: the **gconf-editor**.

---

### Post by Sheeplauncher on 2009-01-16
> **wannadumpwindows said:**
> Probably not the answer you're looking for, but . . . .

If someone figured out your password, and you were worried enough to need to change it, it might not be a bad idea to reinstall anyways. 

You never know what kind of software could have been installed while this person had access.

If it were myself, I would absolutely reinstall, maybe even wipe the disk in between just in case.

You can always use a LiveCD to back up any important data beforehand, and you should be all set.

There's no way to know for sure . . . .

No someone I did work with just guessed if and then I changed it but will check that link in the morning since it's 2 am and typing with and iPhone is annoying

---

### Post by newbee70 on 2009-01-16
> **Sheeplauncher said:**
> So a month or so back I was away with my laptop and someone figured out my pw so I changed it and now I have not used this CPU for awhile because I have my desktop but now for the life of me can't remember what I changed it too or if I changed my user name. Are their any work arounds. I know of registry editor stuff for windows and i assume if exists in soMe form for ubuntu. I'm still kind of new so any help would be appreciated. Thanks 
-sheep

I concur with wannadumpwindows.

Once your system has been compromised you can never be sure, it is a dirty system, and possibly a risk for you and your information.

---

### Post by hyper_ch on 2009-01-16
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Sheeplauncher on 2009-01-16
Ok i apologize but i used the link for pw changing and i go into recovery mode, and enter the (drop to root shell prompt) and it prompts me for a root pw what should i put?

---

### Post by albinootje on 2009-01-16
> **Sheeplauncher said:**
> Ok i apologize but i used the link for pw changing and i go into recovery mode, and enter the (drop to root shell prompt) and it prompts me for a root pw what should i put?

In that case boot from the Ubuntu installation cdrom first, start a terminal, and post here the output of :

```

sudo fdisk -l

```

And imho if someone guessed your password, and *also* has set a root password on your system, then it's time for a complete reinstall!
Make proper backups of your data first, and be careful with what has possibly been changed from that data too.

---

### Post by Sheeplauncher on 2009-01-16
i believe i changed the root pw i just dont remember it. Also once i have booted from CD how do i get a terminal

---

### Post by Sheeplauncher on 2009-01-16
?

---

### Post by eilios on 2009-01-16
Double posting with a question mark is not really a good way to bump a thread. :P
Once you have booted from a CD go into Konsole and type what the people above you have said. I think.

---

### Post by albinootje on 2009-01-16
> **Sheeplauncher said:**
> i believe i changed the root pw i just dont remember it. 

Okay. I still recommend thinking about a reinstall after someone else has been changing your user password without asking.
> 
Also once i have booted from CD how do i get a terminal

-> Applications -> Accessories -> Terminal.

Or : hit alt and F2 at the same time, wait till the run-command windows pops up.
Type in : gnome-terminal

For Kubuntu it would be : konsole
For Xubuntu it is simply : terminal or xterminal I think

---

### Post by Sheeplauncher on 2009-01-16
i booted from the Cd it came with and i have install options etc and nothing to go into console. oh so start without installing and get in that way ok.

---

### Post by albinootje on 2009-01-16
> **Sheeplauncher said:**
> i booted from the Cd it came with and i have install options etc and nothing to go into console

With the Ubuntu 8.04.x and 8.10 installation cdroms you can choose "try without installing".

With 7.10 Gutsy I think you will just get a desktop with the install icon in the end.

---

### Post by Sheeplauncher on 2009-01-16
scrtach that did it wrong 1 sec

---

### Post by Sheeplauncher on 2009-01-16
```

Disk /dev/sba 160.0 GB 160041885696 bytes
255 heads, 63 sectors/track, 19456 cylinders
Units = cyclinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70000000

Device boot      Start      End      Blocks    Id    System
/dev/sda1            1        12       96358+    de    Dell utility
/dev/sda2            13        404      3148740   b     W95 FAT32
/dev/sda3 *          405        19016   149500890  83   Linux
/dev/sda4           19017       19457    3542332+    5     Extended
/dev/sda5          19017         19457      3522301   82     linux swap / solaris


```

---

### Post by albinootje on 2009-01-16
> **Sheeplauncher said:**
> ```

/dev/sda3 *          405        19016   149500890  83   Linux

```

OK, then try the following :
```

sudo mount /dev/sda3 /mnt
sudo chroot /mnt

```
And then :
```

passwd root

```

---

### Post by Sheeplauncher on 2009-01-16
Hrmmm said i changed pw successfully so i restarted and i guess i dont know my username as well.

So then i tried to use root and the pw i changd it 2 and it said the system administrator is not allowed to login from this screen

---

### Post by albinootje on 2009-01-16
> **Sheeplauncher said:**
> Hrmmm said i changed pw successfully so i restarted and i guess i dont know my username as well.

So then i tried to use root and the pw i changd it 2 and it said the system administrator is not allowed to login from this screen

Root (administrator) is by default not allowed to log in via the Display Manager.

But now you have successfully changed the password for root, it's time to follow the instructions from the earlier mentioned, in order to change the password for your normal user :

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Sheeplauncher on 2009-01-16
ah right... lol good call

---

### Post by Sheeplauncher on 2009-01-16
Thanks a lot. Success i have logged in.

---

### Post by albinootje on 2009-01-16
> **Sheeplauncher said:**
> Thanks a lot. Success i have logged in.

Great. Glad it is solved now.

---

