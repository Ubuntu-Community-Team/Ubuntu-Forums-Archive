---
title: "&quot;There are 58 updates available.&quot;  Seriously?"
date: 2009-03-13
forum: New to Ubuntu
---

### Post by DigiTan on 2009-03-13
Okay, after weeks of grappling with hardware issues I finally installed yesterday.  Now the problem is it says there are 58 possible updates.
[LIST]
[*]dash - POSIX-compliant shell
[*]firefox-gnome-support
[*]libcurl3 - Multi-protocol file transfer library (OpenSSL)
[*]sudo - Provide limited super user privileges to specific users
[*]vim-common - Common files
[*]acpid - Utilities for using ACPI power management
[/LIST]
...just to name a few.  I have no idea which ones are applicable.  How do you tell what's needed and what isn't?  Or do you just cross your fingers and install every last one?

---

### Post by Locutus_of_Borg on 2009-03-13
install all of them only if you want to update everything in your system

if you want to use older versions of something, dont include that update

---

### Post by scphan on 2009-03-13
if you have an idea on what you don't want to update then you can deselect it otherwise i think it's better to just let it update everything else

if you just got done with hardware issues that have to do something with the updates than you can knock those out if you have everything perfect with the hardware and don't want to risk it messing up your system than at your pace experiment with the updates if you want to, just a suggestion, for me i'd just install all of them since i'm just a rookie at ubuntu and don't know every single detail of every single app i have on my computer and especially because there's a chance the updates would actually improve some of the apps

---

### Post by tgalati4 on 2009-03-13
Ceiling Cat says SRYSLY.

Update all and be happy.

---

### Post by mcla0203 on 2009-03-13
at least there's not an annoying "configurating updates, please wait... 0%" screen before you relogin to ubuntu for 20 minutes... cough Vista... haha

---

### Post by Stenrad on 2009-03-13
> **mcla0203 said:**
> at least there's not an annoying "configurating updates, please wait... 0%" screen before you relogin to ubuntu for 20 minutes... Cough vista... Haha

+1!

---

### Post by humphreybc on 2009-03-13
Choice! Updates are golden. Install all of them and enjoy your newfound functionality and lesser bugs.

---

### Post by SwimDude0614 on 2009-03-13
i'm a rookie thats been using various version of ubuntu (Xubuntu, Kubuntu, etc) since 7.04 was first released, and i've always installed every update without hesitation. never had any problems! (because of the updates anyway :P )

---

### Post by Therion on 2009-03-13
> **DigiTan said:**
> Or do you just cross your fingers and install every last one?
Yeah, seriously.

No finger crossing required in my experience.  Just install them all.

---

### Post by DigiTan on 2009-03-13
Okay, I'll try it.  If I don't make it back, tell them I want a Viking's funeral and I had nothing to do with the skeleton in the cellar.

---

### Post by ugm6hr on 2009-03-13
> **DigiTan said:**
> Okay, after weeks of grappling with hardware issues I finally installed yesterday.  Now the problem is it says there are 58 possible updates.

I'm surprised there aren't more.

Both 8.10 and 8.04.2 are already months old.

The updates are for everything (inc all office. media and system applications), not just the OS base alone.

---

### Post by 73ckn797 on 2009-03-13
> **Therion said:**
> Yeah, seriously.

No finger crossing required in my experience.  Just install them all.


+1

The only finger crossing occurs when you try to type fast and are not an efficient typist!

---

### Post by hyper_ch on 2009-03-14
go into software sources and in the update tab just enable security updates. Those are a must, the others are optional - although I would also tick the normal updates ones.

---

### Post by Georgia boy on 2009-03-14
I also let everything update. So far no problems from doing that. Then again, I haven't been on Ubuntu for ages to know exactly what is important and what's not. So when in doubt I let it all ride.

Tom

---

### Post by markbuntu on 2009-03-14
The only time you may run into problems with updates is if you install something from outside the repositories, like video drivers from ati or nvidia, or if you customized some configuration file. In most cases this will only happen withspecific application or kernel updates and you can just reinstall or reconfigure to restore operations to normal.

---

### Post by Pappy1911 on 2009-03-15
I find that the updates are starting to eat up my HD space. I only have 4.9Gb left...

---

### Post by abn91c on 2009-03-15
> **Pappy1911 said:**
> I find that the updates are starting to eat up my HD space. I only have 4.9Gb left...
do```
sudo apt-get autoremove
``` to get rid ofjunk Ubuntu no longer needs, also remove programs you may never use like bluetooth, tape back up, kopete, torrent, instant messaging etc...

---

### Post by ugm6hr on 2009-03-15
This will remove all the downloaded files (but leave the updates intact):
```
sudo apt-get clean
```

Remember the downside is that if you re-install, you will have to re-download after an apt-get clean.

---

### Post by Pappy1911 on 2009-03-15
Thanks guys....I'll give it a go...

---

