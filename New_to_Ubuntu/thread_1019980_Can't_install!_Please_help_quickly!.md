---
title: "Can't install! Please help quickly!"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by karatepig on 2008-12-23
I was following this guide, [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1) , and everything has gone smoothly so far. But, when I try to install linux, the part where I am suppose to select "guided-choose the largest continuous free space", looks completely different than in the guide! I have tried to attach an image of what I am seeing, but the site keeps giving me an error. However, I trust that someone among you knows what the step I am talking about looks like. Ow ya, this is the latest version of unbuntu (8.10).

---

### Post by SuperSonic4 on 2008-12-23
> **karatepig said:**
> I was following [**this guide**]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1"), and everything has gone smoothly so far. But, when I try to install linux, the part where I am suppose to select "guided-choose the largest continuous free space", looks completely different than in the guide! I have tried to attach an image of what I am seeing, but the site keeps giving me an error. However, I trust that someone among you knows what the step I am talking about looks like. Ow ya, this is the latest version of unbuntu (8.10).

Fixed a bad link. I'm not sure what the problem is, can you host it on imageshack and link us using the [img] tags.

edit: that guide is for 8.04 so it would almost certainly look different, shouldn't act differently though

---

### Post by 73ckn797 on 2008-12-23
> **karatepig said:**
> I was following this guide, [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1) , and everything has gone smoothly so far. But, when I try to install linux, the part where I am suppose to select "guided-choose the largest continuous free space", looks completely different than in the guide! I have tried to attach an image of what I am seeing, but the site keeps giving me an error. However, I trust that someone among you knows what the step I am talking about looks like. Ow ya, this is the latest version of unbuntu (8.10).

Did you look in the forums for instructions?

---

### Post by LANT on 2008-12-23
Can't really see the guide you are trying to use. If ubuntu will be the only OS on your box I recomment your just follow up the guided partitioning. If you have an other os partition I recommend you use the manual one. As you can easily resize the other partition and create a new one for you ubuntu.

Tell us more things thought, you told very little to help you...

---

### Post by karatepig on 2008-12-23
Image shack?

---

### Post by karatepig on 2008-12-23
> **LANT said:**
> Can't really see the guide you are trying to use. If ubuntu will be the only OS on your box I recomment your just follow up the guided partitioning. If you have an other os partition I recommend you use the manual one. As you can easily resize the other partition and create a new one for you ubuntu.

Tell us more things thought, you told very little to help you...

Thats the trouble, it doesn't have any option for manual, guided, etc. Just a white box, and some un-clickable buttons.

---

### Post by WelshChris on 2008-12-23
karatepig - take care!  Post more information, as other replies have asked for, in particular tell us if linux is to be the only OS on your box!

---

### Post by karatepig on 2008-12-23
I am trying to dual-boot with vista, in case I decide that I don't like linux. I am trying to get you the image, the site's uploader won't work, and I am not sure what you mean by "imageshack":confused:
The link I gave is working for me...

Edit: I googled image shack. I tried to use it, but it says "bad file type".
I'll try taking another screenshot...

---

### Post by SuperSonic4 on 2008-12-23
[http://imageshack.us/](http://imageshack.us/)

you upload the photos and then past the image code it gives (hotlinks for forums 1): I put the ubuntu logo as an example xD

[[IMG]http://img227.imageshack.us/img227/5932/jmakubuntulogofg1.png[/IMG]](http://imageshack.us)
[[IMG]http://img227.imageshack.us/img227/jmakubuntulogofg1.png/1/w310.png[/IMG]](http://g.imageshack.us/img227/jmakubuntulogofg1.png/1/)

---

### Post by karatepig on 2008-12-23
[[IMG]http://img522.imageshack.us/img522/2766/screenshotinstalloa6.th.png[/IMG]](http://img522.imageshack.us/my.php?image=screenshotinstalloa6.png)

Here you go.
Say,that's a pretty nifty service. And for free too!

---

### Post by karatepig on 2008-12-23
And this is what the guide shows (I think it is only part of it)

---

### Post by balaknair on 2008-12-23
If you're unsure about Linux, why not just try a Wubi install which lets you install Ubuntu without partitioning the hard drive. Ubuntu performance will be a little slower and Suspend/Resume/Hibernate might not work in Ubuntu with a Wubi install, but should you find Ubuntu not to your taste, it becomes much simpler to remove Ubuntu(just uninstall it from the Add/remove applications menu in Vista).

---

### Post by karatepig on 2008-12-23
I have to get off the computer soon. Does anyone know what I need to do?
Balaknai: I am hoping a new os will solve an issue I am having with my pc.

---

### Post by SuperSonic4 on 2008-12-23
You're using a VM? Can't you just make another VM from within windows?

---

### Post by karatepig on 2008-12-23
> **SuperSonic4 said:**
> You're using a VM? Can't you just make another VM from within windows?

A vm? I am not even in windows right now. I booted from the cd, so I could scout around the OS before spending the time to install it. I actually like it, but I can't use it if I can't install it.

---

### Post by SuperSonic4 on 2008-12-23
Virtual machine, it's running on OS inside another OS yet with little or no interaction

---

### Post by karatepig on 2008-12-23
No, I am not on a vm, I am completely outside of windows right now.

---

### Post by startherepodcast on 2008-12-23
OK if it does not show you any hard drives you could partition, then something is wrong. As previously said, I would suggest you try an install inside Windows first. 

I do not know exactly how this works but I can tell you that you get a boot menu just like with the real install. Disk performance will be slightly slower, but it's not like Ubuntu is running "on top of" Windows. You are not going to notice anything about your Windows install. And the best thing is you can easily remove it if something does not work or put it on a real partition if you like it a lot.

---

### Post by ranch hand on 2008-12-23
I would creat your partitions under Vista and then try to install again.  Vista will be happier if the partitions are its creation anyway.

If you continue to have a problem installing from the CD, boot in as you have to the desk top from the CD and click on the install button on the desk top.

---

