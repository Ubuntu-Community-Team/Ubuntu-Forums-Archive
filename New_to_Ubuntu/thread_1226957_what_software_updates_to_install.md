---
title: "what software updates to install"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by gshockxc on 2009-07-30
Almost every day, I get Software Updates from the KDE notifier in the panel.  When I click on the icon to install them, it lists what is available.  But there's never a description so I can figure out if I need it or not.  

Also, I have 4 updates that continue to show up, that are blocked and I don't know why.  But when I hover on the icon in the panel, it tells me that there are 8 updates.  

[IMG]http://i33.photobucket.com/albums/d89/kristanxc/UpdateNotifier.png[/IMG]

Can someone explain?

Thanks.

---

### Post by cozmicharlie on 2009-07-30
You bring up a good point about the notification not giving you any information.  I am not sure what version of Ubuntu you are using (looks like kubuntu) but in 9.04 the update manager has a "description of update" on the bottom you can hit an get more info.  If you open synaptic and in the menu go to settings>repository>updates you should see a list of "Ubuntu updates".  This controls what updates you want on your system.  The native installation by default has the security updates and recommended updates checked.  These are generally safe to install (but sometimes an update does cause a problem) and you should install the security updates.  If you want newer (i.e. bleeding edge) updates then you can check Pre-released updates (these are updates that are released but are not official yet) and unsupported-updates (often referred to as backports).  Any update also appears in synaptic - go to "custom filters">upgradeable and it will list any updates and it usually has a short explanation.  As per the particular updates you note - these are kernel updates (remember linux is not an operating system it is a kernel) so these are updates to the linux kernel and it is usually a good idea to install them.  They usually contain many bug fixes and security fixes.  When Ubuntu installs a new kernel it does not uninstall the old one so if you have problems you can always go back to the old kernel in grub when you boot.  Once you have used the new kernel and all is good you may want to uninstall the old one (especially if you are short on hard drive space).   You can do that in Synaptic.

I hope this helps 

Enjoy!

---

### Post by Foster Grant on 2009-07-30
The blocked updates thing is a bug in KPackageKit; as near as I can tell, it has issues with updates that add new dependencies. At least, it's a bug in *Kubuntu's* version of KPackageKit as documented [_[color=#0000ff]in this thread over at Kubuntu Forums[/color]_](http://kubuntuforums.net/forums/index.php?topic=3104586.0). Really very annoying. ](*,)

Easy fix: Open konsole and enter the following two lines at the prompt:

```
USER@SYSTEM:~$ sudo aptitude update

{{provide password upon request, bunch of system messages scroll by, yada yada yada}}

USER@SYSTEM:~$ sudo aptitude safe-upgrade
```

Follow prompts as presented.

Unlike the posters at Kubuntu Forums, I cannot get Synaptic or Adept to install updates that KPackageKit lists as "blocked."

---

### Post by gshockxc on 2009-07-30
> **Foster Grant said:**
> The blocked updates thing is a bug in KPackageKit; as near as I can tell, it has issues with updates that add new dependencies. At least, it's a bug in *Kubuntu's* version of KPackageKit as documented [_[color=#0000ff]in this thread over at Kubuntu Forums[/color]_](http://kubuntuforums.net/forums/index.php?topic=3104586.0). Really very annoying. ](*,)

Easy fix: Open konsole and enter the following two lines at the prompt:

```
USER@SYSTEM:~$ sudo aptitude update

{{provide password upon request, bunch of system messages scroll by, yada yada yada}}

USER@SYSTEM:~$ sudo aptitude safe-upgrade
```

Follow prompts as presented.

Unlike the posters at Kubuntu Forums, I cannot get Synaptic or Adept to install updates that KPackageKit lists as "blocked."



Wow, that helped a lot.

```
4 packages upgraded, 4 newly installed, 37 to remove and 0 not upgraded.
```

Seems like I should do this on a regular basis.  I'm going to put a sticky on my desktop so I don't forget the commands.  Thanks again.

---

### Post by gshockxc on 2009-07-30
> **cozmicharlie said:**
>  (remember linux is not an operating system it is a kernel) 

Is this like saying, "Linux is an engine, not a car?"  I think I get your meaning.  Linux is the kernel, but Ubuntu is the operating system, right?

I'll probably need a little help figuring out how to remove the old kernel once the new on is installed, but I'll wait until I get a new set up updates to ask that question.

Thanks for your reply.  It was a BIG help.  I'll go to Synaptic from now on and use the custom filters to find the descriptions before installing updates.

---

### Post by abn91c on 2009-07-30
> **gshockxc said:**
> Wow, that helped a lot.

```
4 packages upgraded, 4 newly installed, 37 to remove and 0 not upgraded.
```

Seems like I should do this on a regular basis.  I'm going to put a sticky on my desktop so I don't forget the commands.  Thanks again.
you can just use [COLOR="Red"]**adept manager **[/COLOR]instead of KpackagetKit to install the blocked updates. Depending on your kubuntu setup you may need to install it first.

---

### Post by mgranet on 2009-07-30
Adept is no longer in development, and is considered obsolete. I installed the blocked updates with Synaptic with no problems.

---

### Post by gshockxc on 2009-07-30
> **mgranet said:**
> Adept is no longer in development, and is considered obsolete. I installed the blocked updates with Synaptic with no problems.

I didn't even know that I could do that.  Will try it next time.

---

### Post by shockdiode on 2009-08-18
Yay, more broken stuff in Kubuntu, what are the odds? A default package manager that can't handle managing packages? Great...

---

### Post by gshockxc on 2009-08-18
> **shockdiode said:**
> Yay, more broken stuff in Kubuntu, what are the odds? A default package manager that can't handle managing packages? Great...

It's not all bad.  At least you don't have the "Blue-screen of Death."  And there are all kinds of nice people willing to help for FREE!:biggrin:

~//  Glass is half full, or half empty?  \\~

(Nevermind the glass!  Where the heck are my cheeseburger and fries?  - :lolflag:)

---

### Post by shockdiode on 2009-08-18
> **gshockxc said:**
> It's not all bad.  At least you don't have the "Blue-screen of Death."  And there are all kinds of nice people willing to help for FREE!:biggrin:

~//  Glass is half full, or half empty?  \\~

(Nevermind the glass!  Where the heck are my cheeseburger and fries?  - :lolflag:)

Yes, but I've been a linux user and admin for around 10 years. I switched over to *buntu from straight Debian a few years back because it was quicker to get set up to my liking on a desktop/laptop and based on Debian (apt is really the best package manager I've found) and for quite some time was very happy. However, especially with the Kubuntu variant, the last couple of releases have released seriously not-ready or broken packages. 

You are correct that the community is very friendly and helpful. 

Just venting a bit, but I am likely on my way to another distro. Anyway, take care all.

---

### Post by MickS on 2009-08-18
I have 50 odd blocked updates I just ignore them and install the ones I can, presume they are blocked for a good reason they know more about it than I do.


Mick

---

### Post by gshockxc on 2009-08-18
> **shockdiode said:**
> Yes, but I've been a linux user and admin for around 10 years. I switched over to *buntu from straight Debian a few years back because it was quicker to get set up to my liking on a desktop/laptop and based on Debian (apt is really the best package manager I've found) and for quite some time was very happy. However, especially with the Kubuntu variant, the last couple of releases have released seriously not-ready or broken packages. 

You make a good point.  And it's probably the result of some decisions made to get more distros out there as a result of the popularity, rather than de-bug and test more thoroughly.  I'm not saying it's right or wrong, but with more people turning to Linux, there's probably a lot more demand for 'general' users, which leaves experts like you kind of out in the cold.  

Don't get me wrong, I wish I had your expertise to even appreciate the differences.  Such as it is, I hope you find a better distro.

---

### Post by shockdiode on 2009-08-18
> **gshockxc said:**
> You make a good point.  And it's probably the result of some decisions made to get more distros out there as a result of the popularity, rather than de-bug and test more thoroughly.  I'm not saying it's right or wrong, but with more people turning to Linux, there's probably a lot more demand for 'general' users, which leaves experts like you kind of out in the cold.  

Don't get me wrong, I wish I had your expertise to even appreciate the differences.  Such as it is, I hope you find a better distro.

Actually my concern here is quite the opposite: That this sort of thing turns off new and general users. It's just been frustrating for me that things don't "just work" lately as much as they used to in *buntu. I think that that would be a real turnoff to a lot of new users and I've gotten very used to not having to mess with things in Kubuntu and having it "just work" myself. Which is really nice. 

This particular instance is not a huge deal but rather confusing to many people, I think. Also, just at the moment, it holds up a kernel update which addresses a very serious security issue, so it's a bit annoying to know that many many people are sitting there with unpatched machines.

Anyway, I'm done with my rant. I just have some concerns and will now slowly back away from the thread :). Take care!

---

### Post by facefur on 2012-03-16
This is helpful, but what I find is that there are two "classes" of updates, Important and Recommended. I assume the Important ones should be done, but there are over 200 in th recommended category, and even the descriptions tend to be less than clear. I  think Ican skip things associated with Bluetooth, because I don't use it, but shuld I be skipping things associated with Gnome if I'm using the Unity desktop that came with 11.10?  What other similar updates should I skip or include?

---

