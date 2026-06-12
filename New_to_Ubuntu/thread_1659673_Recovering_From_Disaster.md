---
title: "Recovering From Disaster"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by ray_silva on 2011-01-04
I installed ubuntu in VirtualBox on my Windows 7 machine. I finally got everything to work and also installed three programs after great difficulty and a lot of questions and research. Everything seemed to be working great. I also downloaded an ISO for another install I wanted to do. Then, I did an upgrade check and continued to install all the updates. However, towards the end, I got a message that my disk space was low. I thought of transferring the ISO to an external USB drivie and started to figure out how to have it recognized to I could do so. But, before I could do it, the updates completed and told me I had to reboot. When I did so, an error came up saying gnome did not load properly and that I should contact my system administrator. When I would try to enter my password at the login dialog, ubuntu shut down. I searched around for some help and found that I could open the terminal screen. People suggested different things to try, but at every attempt my password entry attempt returned that it was incorrect. I tried using sudo, but nothing worked. I am trying to avoid having to do a complete reinstall and save what I have done. I found that I had set the initial VBox too small. I'm at the point that I have created a new larger box and I'd like to "clone" everything I did from the old Vbox install. Am I out of luck here, or is there something I can do? :confused:

---

### Post by anystupidname1 on 2011-01-04
EDIT: Slightly cleaner way to do this [http://undercovertechguy.wordpress.com/2010/10/21/growing-a-virtualbox-vdi-is-easy/](http://undercovertechguy.wordpress.com/2010/10/21/growing-a-virtualbox-vdi-is-easy/)

1) Detach OLD.vdi
1a) VBoxManage createhd NEW.vdi
2) VBoxManage clonehd --existing OLD.vdi NEW.vdi
2a) Attach NEW.vdi to VM
3) Boot VM from liveCD with gparted in it and expand partition on NEW.vdi

See [http://www.my-guides.net/en/content/view/122/26/]("http://forums.virtualbox.org/viewtopic.php?f=6&t=17512")

VDI expand functionality will be available in Vbox 4.X

---

### Post by ray_silva on 2011-01-04
"VDI expand functionality will be available in Vbox 4.X"
 
I installed 4.0 and I don't see this functionality. Also, I tried to follow your instructions by following your first link. Please see the reply I posted there. I'm not clear about what appears to be the most critical step.

---

### Post by anystupidname1 on 2011-01-04
I don't see what reply you wanted me to see. Where exactly?

Regarding expand in v4, [http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi]("http://www.virtualbox.org/ticket/28")

---

### Post by ray_silva on 2011-01-04
"EDIT: Slightly cleaner way to do this [[COLOR=#444444]http://undercovertechguy.wordpress.c...x-vdi-is-easy/[/COLOR]]("http://undercovertechguy.wordpress.com/2010/10/21/growing-a-virtualbox-vdi-is-easy/")"

---

### Post by anystupidname1 on 2011-01-05
Don't see ANY comments there...

---

### Post by ray_silva on 2011-01-05
Weird - OK, in your instructions I got to this step:
 
**"Release** and **Remove** your old harddrive from VBox’ grasp using the Virtual Media Manager; You have to do this otherwise the next step will fail. All you need to do is to release it, then remove it and [COLOR=#ff0000]**REMEMBER**[/COLOR] to “Keep” the hard disk image when you do that!"
 
I replied with the following comment:
 
This is not clear to me. What do you mean by release and remove? I upgraded to VBox 4.0; then, I created another vid, but have not installed anything in it yet. I added the new vdi to the same controller where the old one that isn’t working is on. I can see where I can attach or remove vids from the controller, but I don’t see anything that says ‘release’ or ‘remove.’ In either case, I don’t see anything that says I can ‘keep’ the hard disk image. This all seems crucial from your instructions, but the statement is vague enough to make me very unsure about exactly what you are saying to do.
 
Sorry about the merry-go-round effect.

---

### Post by tgm4883 on 2011-01-05
> **ray_silva said:**
> Weird - OK, in your instructions I got to this step:
 
**"Release** and **Remove** your old harddrive from VBox’ grasp using the Virtual Media Manager; You have to do this otherwise the next step will fail. All you need to do is to release it, then remove it and [COLOR=#ff0000]**REMEMBER**[/COLOR] to “Keep” the hard disk image when you do that!"
 
I replied with the following comment:
 
This is not clear to me. What do you mean by release and remove? I upgraded to VBox 4.0; then, I created another vid, but have not installed anything in it yet. I added the new vdi to the same controller where the old one that isn’t working is on. I can see where I can attach or remove vids from the controller, but I don’t see anything that says ‘release’ or ‘remove.’ In either case, I don’t see anything that says I can ‘keep’ the hard disk image. This all seems crucial from your instructions, but the statement is vague enough to make me very unsure about exactly what you are saying to do.
 
Sorry about the merry-go-round effect.

The key is where he says "using the **Virtual Media Manager**"

---

### Post by ray_silva on 2011-01-05
That is exactly what I am using - it is the Virtual Media Manager in VirtualBox 4.0, called "Oracle VM Virtual Box Manager." Within that, I select "Storage." and that's where you can add or delete a vdi to a storage controller. I don't see anything that allows you to save or "keep" the disk image.

---

### Post by ray_silva on 2011-01-05
OK, in my desperation, I went ahead and removed both the vdis I had created (the original that became too small and the new one that I planned to use to clone the old one to). Removal does not delete them, so I see that I could add either or both back to the storage controller. Now, what do I do?

---

### Post by ray_silva on 2011-01-05
Do you know if it is OK to make the new vdi dynamic? The instructions say to make it static, but if you find out that dynamic works to let him know.

---

### Post by ray_silva on 2011-01-05
The next step in the instruction is this:
 
"**Clone** your old (and smaller) VDI into the new (and larger) one like so using the VBox command line tool: VBoxManage clonehd --existing OLD.vdi NEW.vdi"
 
The problem I have with this step is that I don't see anything in VirtualBox that allows me to use a command line tool...AND, doesn't that presume that you are able to boot up ubuntu? This is exactly what I am unable to do since the failure.

---

### Post by anystupidname1 on 2011-01-05
I'm still not clear why you can't simply expand the original disk with the new functionality in 4.X. --resize
[http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi](http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi)

 I don't know if you can do it in the GUI since I run everything  headless. Also, I've never used 4 (was actually under the impression it  was still beta :-\" when I first answered you until I checked). I guess I should upgrade. Oracle is making me a bit uneasy lately though...

Regarding you're latest question about cloning:
From the VM HOST, run
```
**[B]VBoxManage clonehd --existing OLD.vdi NEW.vdi**[/B]
```

---

### Post by ray_silva on 2011-01-05
Thanks. I was finally able to figure out and follow the clonehd procedure and it seemed to work alright; however, the problem on starting the vdi persists. I get the login dialog and an error message saying that "there was an install problem: the configuration defaults for the GNOME power manager were not installed correctly." I cannot log in at the dialog, but I can log in from a terminal window. I need to figure out how I can extend the partition (or if it was done automatically when I cloned the small vdi on which I had run out of disk space). I never got any error other than I was running low on space. This happened while I was doing an update. When it finished, I was instructed to reboot. That's when it did not work again. I'm trying to save all the installations and settings that I had already done up to that point. So, now I am working with a new larger vdi, but I still can't log into it via the GUI. Please help?

---

