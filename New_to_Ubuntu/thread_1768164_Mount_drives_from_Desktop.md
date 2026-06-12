---
title: "Mount drives from Desktop"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by thorstenmz on 2011-05-26
Hi all,

I'm using Ubuntu Natty with the Unity GUI. Is there a way to mount drives (Windows partition) from the desktop? I don't want to open Nautilus merely for that. There used to be a panel applet for that…

---

### Post by ajgreeny on 2011-05-26
It is disk mounter, but I am not sure if it's available for unity.

I use it a lot in my system which has 5 OSs in total, so I find it terrifically useful.  I am pretty sure it will be available for natty if you use the classic desktop, but I suspect it's not there for unity, just like many other things that seem to have gone and make life much more difficult.

---

### Post by ILoveYorkies on 2011-05-26
[SIZE=3]HELLO,[/SIZE] 
[SIZE=3]on my install of Ubuntu 11.04 I have to go to the panel on the left  (that pops out if the cursor touches it) scroll down to apps then disk  utility. Your drives should show up in the left panel click on the one/s  that you want, scroll down to the bottom of the page it should have a box  below the format box (careful not to check that). The box below format  should say mount dev check that box, do this for each drive you want to  show up on your desktop then exit out of disk utility. The drives should  show up on your Unity desktop it does work on mine. Of course, you go  back into disk utility and uncheck  the boxes which unmounts the  devices. Unless you want them to be on your desktop when you reboot  without going through disk utility each time. I unmount each time before  shutting down but that might not be needed.

Hope this helps. let me know if it works for you.[/SIZE]

---

### Post by coffeecat on 2011-05-26
> **thorstenmz said:**
> I don't want to open Nautilus merely for that.

Really? One click to open Nautilus from the launcher and one more click to mount an internal partition. I find that extremely elegant. Not at all making life more difficult as the previous poster suggests - imho.

---

### Post by quarkhirad on 2011-05-27
> **thorstenmz said:**
> Hi all,

I'm using Ubuntu Natty with the Unity GUI. Is there a way to mount drives (Windows partition) from the desktop? I don't want to open Nautilus merely for that. There used to be a panel applet for that…


Open terminal and type the following. Please paste the outputs of all the commands.

```

khirad@jeena:~$ cat /etc/fstab
khirad@jeena:~$ mount
khirad@jeena:~$ sudo fdisk -l

```

Please note in your terminal khirad will be your username and jeena will be your hostname.

---

### Post by grahammechanical on 2011-05-27
I can give you this link that I picked up from another thread the other day.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Regards.

---

### Post by Paqman on 2011-05-27
Why not add them to /etc/fstab? Then you don't have to click on anything to mount them, they'll be automatically mounted at boot.

---

