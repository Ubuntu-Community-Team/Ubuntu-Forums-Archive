---
title: "Multiple Desktop Wallpapers in Lucid Lynx?"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by Valkyr333 on 2010-12-14
Hey everyone,

I'm pretty new to Ubuntu, and I'm trying to figure out if it's possible yet to put a different wallpaper on each of my Workspaces in my version of Ubuntu. As best as I can tell, that would be Ubuntu Lucid Lynx 10.10. I'm running Ubuntu Satanic Edition, and since its developers have made  so many aesthetically-appealing wallpapers, it's almost a sacrilege  (heh, heh) to have to use just one of them universally. 

All the other threads I've found on this topic were pretty out-dated, and I'm wondering if the Gnome/Compiz/etc. issues have been fixed or updated to solve this problem at the moment, or at least if anyone knows the latest news. 

Side note: I'd like to be sure about the version installed because I know it has a bearing on the right answer to the question. If I've forgotten specifically what version of Ubuntu I've installed, where in the system would I find those specifications?

Thanks for your time!

-Valkyr/Val

---

### Post by kroq-gar78 on 2010-12-14
Lucid lynx is 10.04 and Maverick Meerkat (the latest) is 10.10.

Now, I don't know the answer to your compiz question, but I do know how to find the version. Go to System (near top right of screen) -> About Ubuntu. In there (near top of text) should say the version. For me, this is "You are using Ubuntu 10.10
                - the Maverick Meerkat - released in October 2010 and supported until April 2012."

---

### Post by Valkyr333 on 2010-12-19
Thanks, I appreciate that. =)

And yeah, it turns out it's Lucid Lynx/10.04.

---

### Post by rich52x on 2010-12-19
I don't think you can do that in GNOME (take with a grain of salt) but I think that you can in KDE.
If you want to install that. take a look [here]("http://www.psychocats.net/ubuntu/kde"). 
If you decide to do this, once you're logged in, go to system settings -> Desktop -> Multiple Desktops. there is a checkbox to bind each desktop to a different activity. Then just go to each destop and change the wallpaper :)

Rich.

---

### Post by rburkartjo on 2010-12-21
val you can go to this link hit download and install one of the deb downloads. yes it will work in ubuntu 10.10. that is how i get a wallpaper on each desktop.

[http://linux.softpedia.com/get/Desktop-Environment/Tools/Wallpapoz-8113.shtml](http://linux.softpedia.com/get/Desktop-Environment/Tools/Wallpapoz-8113.shtml)

---

### Post by Valkyr333 on 2010-12-21
Thanks, guys. =)

@rich52x - Are there any potential disadvantages to using KDE instead of GNOME/GNU? Would you say that there's any big difference in user-friendliness?

@rburkartjo - Will that also work in Lucid Lynx/10.04? Is there any reason it would be dangerous to install/use in 10.04?

---

### Post by rburkartjo on 2010-12-21
val i used in 10.04 worked fine. note you have to have it running to change the desktops. let me know if you have any problems. you shouldnt but can help if you do.

---

### Post by Valkyr333 on 2010-12-22
I tried to download the .deb, "Ubuntu 8.04 DEB ALL"

When it changes to the page that tells me "your download is starting" nothing happens, and when I hit the link it gives to solve that, it says "Alert: 550 failed to change directory." For 7.04, I got a 404 Error:

"Not found. The requested URL /getdeb/wa/wallpapoz_0.4.1-1~getdeb1_all.deb was not found on this server."

The other one is a tar.bz2, and I'm a bit unfamiliar with that. Is there any way to get Wallpapoz through the Ubuntu Software Center?

Thanks for your help,

-Val

---

### Post by rburkartjo on 2010-12-25
val sorry the deb download site is no longer work. here is a link for a tar.bz2 download. it is working just checked it out

[http://www.filetransit.com/download.php?id=81060](http://www.filetransit.com/download.php?id=81060)

---

### Post by IndyGunFreak on 2010-12-25
> **kroq-gar78 said:**
> Lucid lynx is 10.04 and Maverick Meerkat (the latest) is 10.10.

Now, I don't know the answer to your compiz question, but I do know how to find the version. Go to System (near top right of screen) -> About Ubuntu. In there (near top of text) should say the version. For me, this is "You are using Ubuntu 10.10
                - the Maverick Meerkat - released in October 2010 and supported until April 2012."

That's not really a sure fire way to find out what you're using.  For instance, right now I'm DEFINITELY using 10.10... and when I go to About Ubuntu, it says I'm using the 11.04 Natty.  I've noticed this confusing a lot of 10.10 users.

To get the info you want.... 

Run lsb_release -a in a terminal

```
ken@ken-5315:~$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick
ken@ken-5315:~$ 


```

---

### Post by Valkyr333 on 2010-12-28
Hey again,

So I managed to browse around and find a Deb. for Wallpapoz. It works now, but I notice it seems a little slow changing the wallpapers as I switch workspaces. Like, I switch to a different workspace, the cube rolls over, the same picture is there, and then a second later it switches. It's a little confusing, and it feels like something I should be able to remedy with the right tweak.

Any ideas?

Thanks, everyone! =)

-Val

---

### Post by Valkyr333 on 2010-12-30
So I've got Wallpapoz working now. I found a .Deb online eventually, so the only other thing is that it seems to lag a bit in switching wallpapers between desktops/workstations. This seems like it either shouldn't be happening, or should be fixable with the right adjustment.

What do you guys think?

Ugh... Sorry for posting that twice. I thought I'd posted it before but the forum wasn't showing it. I only noticed after posting again. x.x

---

### Post by alohanate on 2011-01-09
Did you fix your problem with the cube rendering the wallpaper?  I wanted different wallpapers on my cube too, but I wouldn't want to if there is a delay.  Someone should be able to fix this, right?

---

