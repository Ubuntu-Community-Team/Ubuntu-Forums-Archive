---
title: "Graphics problems."
date: 2009-05-13
forum: New to Ubuntu
---

### Post by Canucker25 on 2009-05-13
I'm now into my first 24 hours of having Linux and I'm really trying to like it but it's not making it easy on me. After trying all day yesterday to get my graphics card to work on Jaunty without any luck I downgraded to Hardy. I installed the graphics drivers about 2 hours ago and I thought everything was going great. 

Recently however I tried to view some screen savers just to make sure it was working and all of a sudden a my screen turns black and it logs me out of Ubuntu. 

Anyone have any idea what's going on?

---

### Post by TeoBigusGeekus on 2009-05-13
Don't play with screensavers in Ubuntu, they have always been buggy, at least for me. Just keep the default one.
Otherwise, Hardy Heron is an excellent distro and if you have managed to get everything working (graphics, wifi, printing, etc)
then it will stay like this for a long time...

---

### Post by Canucker25 on 2009-05-13
A new problem just arose. Updates has just finished downloading everything for the first time and after I restarted my computer and logged in all I get is a white screen. Could that have something to do with my graphics?

---

### Post by TeoBigusGeekus on 2009-05-13
Hmmm...
Restart, choose recovery mode from grub and let ubuntu reconfigure your graphics' settings.

---

### Post by Canucker25 on 2009-05-13
> **TeoBigusGeekus said:**
> Hmmm...
Restart, choose recovery mode from grub and let ubuntu reconfigure your graphics' settings.
Will do. Be back with an update in a few.

---

### Post by Canucker25 on 2009-05-13
Okay I don't what it did but it is now in low graphics mode. I  no longer get the white screen but it says my driver is "not in use" and I cannot change the resolution above 800x600. Should I enable it?

---

### Post by TeoBigusGeekus on 2009-05-13
Yeah... do that.

---

### Post by Don1500 on 2009-05-13
yes

---

### Post by Canucker25 on 2009-05-13
> **TeoBigusGeekus said:**
> Yeah... do that.

Should it be downloading something? I thought I already installed the driver. Will this conflict with Catalyst?

---

### Post by TeoBigusGeekus on 2009-05-13
Maybe it wasn't installed correctly, who knows?
Let it finish and post update.

---

### Post by Canucker25 on 2009-05-13
> **TeoBigusGeekus said:**
> Maybe it wasn't installed correctly, who knows?
Let it finish and post update.

Okay it installed and it asked me to replace some files so I allowed it and now I'm restarting. Hopefully I'll be right back with an update.

---

### Post by Canucker25 on 2009-05-13
Alright it restarted successfully but when I tried to run ```
sudo glxgears
``` only a black box popped up with nothing in it and terminal gave me the error:

"owen@owen-desktop:~$ sudo glxgears
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 42823 requests (42822 known processed) with 8 events remaining.
owen@owen-desktop:~$ "

How do I tell if my card is working or not?

---

### Post by TeoBigusGeekus on 2009-05-13
Can you enable advanced desktop effects?

---

### Post by Canucker25 on 2009-05-13
> **TeoBigusGeekus said:**
> Can you enable advanced desktop effects?

I think so. When I clicked it it didn't give me an error but I have no idea if the effects are working or not.

---

### Post by TeoBigusGeekus on 2009-05-13
When you move a window, does it shake like brazilian booty?

---

### Post by Canucker25 on 2009-05-13
> **TeoBigusGeekus said:**
> When you move a window, does it shake like brazilian booty?

Yes it does. seems a little choppy though but that could be my mouse.

---

### Post by TeoBigusGeekus on 2009-05-13
You're done then. Congratulations!

---

### Post by Canucker25 on 2009-05-13
> **TeoBigusGeekus said:**
> You're done then. Congratulations!

Are you sure it's working? How come I can't use glxgears?

---

### Post by TeoBigusGeekus on 2009-05-13
Try removing and reinstalling it
```
sudo apt-get purge glxgears
```
and then
```
sudo apt-get install glxgears
```

---

### Post by Canucker25 on 2009-05-13
> **TeoBigusGeekus said:**
> Try removing and reinstalling it
```
sudo apt-get purge glxgears
```and then
```
sudo apt-get install glxgears
```

Still just a black box and the same error:

"owen@owen-desktop:~$ sudo glxgears
[sudo] password for owen: 
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 156395 requests (156394 known processed) with 10 events remaining.
owen@owen-desktop:~$"


It's also choppy when I minimize a window so I'm sure it's not my mouse.

---

### Post by TeoBigusGeekus on 2009-05-13
I would just wait for updates.
I'm sure I saw some other threads about problems with the recent updates, so you can't be the only one.
Have patience ):P

---

### Post by CatKiller on 2009-05-13
> **Canucker25 said:**
> How do I tell if my card is working or not?

glxinfo | grep direct

If it says yes, then you're using direct rendering.

btw, you don't need to run glxgears as root.

---

### Post by Canucker25 on 2009-05-13
> **TeoBigusGeekus said:**
> I would just wait for updates.
I'm sure I saw some other threads about problems with the recent updates, so you can't be the only one.
Have patience ):P

Alright :| thanks for the suggestions. I have another problem to worry about now anyway lol. I think this is payback for stealing Windows all those years.

---

### Post by Canucker25 on 2009-05-13
> **CatKiller said:**
> glxinfo | grep direct

If it says yes, then you're using direct rendering.

btw, you don't need to run glxgears as root.

I typed that in and nothing happened.

---

### Post by TeoBigusGeekus on 2009-05-13
> **Canucker25 said:**
> Alright :| thanks for the suggestions. I have another problem to worry about now anyway lol. I think this is payback for stealing Windows for all those years.

Hush hush... I've been stealing window$ for 13 years now and nothing ever happened to me. Don't worry, everything will be fixed eventually - that's the way to learn in linux.

---

### Post by Canucker25 on 2009-05-13
Should I try reinstalling catalyst or will that put me back in the same position as last time?

---

### Post by CatKiller on 2009-05-13
> **Canucker25 said:**
> I typed that in and nothing happened.

In a Terminal window?

You could try just glxinfo and scroll up to the line about direct rendering.

---

### Post by Canucker25 on 2009-05-13
> **CatKiller said:**
> In a Terminal window?

You could try just glxinfo and scroll up to the line about direct rendering.

"owen@owen-desktop:~$ glxinfo
name of display: :0.0"

That's all I got. 

Could the problem be that I still have Jaunty on my second hard drive? Maybe the installs are conflicting with each other? (sorry if that sounds stupid but I know absolutely nothing about linux.)

---

### Post by CatKiller on 2009-05-13
> **Canucker25 said:**
> "owen@owen-desktop:~$ glxinfo
name of display: :0.0"

That's all I got.

Weird. I think it's safe to say that your graphics driver isn't working properly then.

I get that line and then, after a short pause, a whole bunch of other stuff as the driver reports the glx capabilities of my card.

---

### Post by Canucker25 on 2009-05-13
> **CatKiller said:**
> Weird. I think it's safe to say that your graphics driver isn't working properly then.

I get that line and then, after a short pause, a whole bunch of other stuff as the driver reports the glx capabilities of my card.

So what do you suggest I do? I've already tried reinstalling twice.

---

### Post by CatKiller on 2009-05-13
> **Canucker25 said:**
> So what do you suggest I do? I've already tried reinstalling twice.

I don't know. I don't have any experience of Ati graphics.

If I understand correctly, you're on Hardy and it was working, and a recent update has made it not work. Is that right?

You could try using Synaptic to keep the xorg-driver-fglrx package at the previous version (Package -> Force Version).

---

### Post by Canucker25 on 2009-05-13
I guess I'll try installing one more time and if that doesn't work I'm going to look for a different distro. Ubuntu just isn't agreeing with me I've now tried 2 different versions and both of those didn't work. I don't want to downgrade too much and be light years behind everyone else.

---

### Post by Canucker25 on 2009-05-13
Alright I guess it's goodbye everyone. I'm off to look for another distro that has better driver support. I thank you all for your suggestions and attempts to help.

 Apart from the forums my overall experience with Ubuntu has been horrible. I hate to say it but I would not recommend this distro to anyone. 

Good luck and thanks again ):P):P):P

---

