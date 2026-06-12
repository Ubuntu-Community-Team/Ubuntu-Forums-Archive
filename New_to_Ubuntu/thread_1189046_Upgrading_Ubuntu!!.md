---
title: "Upgrading Ubuntu!!"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-06-16
Yup I have been using ubuntu from 8.04 to the present 9.04 and would continue to use it ,But the problem is that every time i upgrade ubuntu i loose all the apps installed in it ,firefox setting , addons themes compiz setting etc.I dont  use a separate home partition as i dont know how much i should allocate to "/" and "/home". So in this thread can you people tell me all the ways you upgrade ubuntu without loosing much data ,Tell me all the tricks and ways so that i could also follow it
The way in which i do is
I copy all the archive in /var/cache/apt/archives so that i need not download them again (i have a really slow internet connection)

---

### Post by ~sHyLoCk~ on 2009-06-16
1. Launch the Run prompt by hitting ALT+F2.

2. Type &#8220;update-manager -d&#8221; without quotes and in the window click Upgrade.

---

### Post by tarps87 on 2009-06-16
> **~sHyLoCk~ said:**
> 1. Launch the Run prompt by hitting ALT+F2.

2. Type &#8220;update-manager -d&#8221; without quotes and in the window click Upgrade.

This is probably the better way, although if it doesn't work.
(I will assume you are using ubuntu)
```
sudo gedit /etc/apt/sources.list
```
Now find and replace all instances of intrepid with jaunty, then save.
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by rajeev1204 on 2009-06-16
> **ravi_buz said:**
> Yup I have been using ubuntu from 8.04 to the present 9.04 and would continue to use it ,But the problem is that every time i upgrade ubuntu i loose all the apps installed in it ,firefox setting , addons themes compiz setting etc.I dont  use a separate home partition as i dont know how much i should allocate to "/" and "/home". So in this thread can you people tell me all the ways you upgrade ubuntu without loosing much data ,Tell me all the tricks and ways so that i could also follow it
The way in which i do is
I copy all the archive in /var/cache/apt/archives so that i need not download them again (i have a really slow internet connection)


If you are using intrepid right now,update manager will give you the option to upgrade directly to 9.04.It will be almost a 1 gb upgrade so expect quite a few hours depending on your connection.

If update manager doesnt show you the upgrade option, do a sudo update-manager -d in terminal which will give you the option to upgrade.

Another option is sudo apt-get dist-upgrade which does the same thing.

These methods help you preserve all your settings.

---

### Post by ajgreeny on 2009-06-16
To be honest, I think it is better to backup my /home folder and do a complete new clean install.. i have never yet upgraded ubuntu version, so can't compare, but it is so fast to install the system, and now that I know exactly what extras I want, it is only a matter of a few minutes to add them afterwards.

All youe configs that are stored in /home can be backed up easily provided you make sure you backup the hidden folders you want.  I only ever bother with .mozilla and .mozilla-thunderbird, .purple, .openoffice, and one or two others that I want to keep, but I don't bother with things like .gconf; I like to reset that after I have installed.  My compiz settings are kept in a backup of the profile, which I do everytime I make a change to my compiz settings, by using the export option in CCSM.

So, as you see, my recommendation?  Clean install every time.

---

### Post by tarps87 on 2009-06-16
> **~sHyLoCk~ said:**
> 1. Launch the Run prompt by hitting ALT+F2.

2. Type “update-manager -d” without quotes and in the window click Upgrade.

> **ajgreeny said:**
> To be honest, I think it is better to backup my /home folder and do a complete new clean install.. i have never yet upgraded ubuntu version, so can't compare, but it is so fast to install the system, and now that I know exactly what extras I want, it is only a matter of a few minutes to add them afterwards.

All youe configs that are stored in /home can be backed up easily provided you make sure you backup the hidden folders you want.  I only ever bother with .mozilla and .mozilla-thunderbird, .purple, .openoffice, and one or two others that I want to keep, but I don't bother with things like .gconf; I like to reset that after I have installed.  My compiz settings are kept in a backup of the profile, which I do everytime I make a change to my compiz settings, by using the export option in CCSM.

So, as you see, my recommendation?  Clean install every time.

I use to but upgrading seems more reliable now (compared to earlier versions not a clean install), plus I have a apt cache server setup so download cost is not much of an issue. Then again I also use arch which uses rolling release cycle.
If you are going to do a clean install each time I would suggest creating a separate /home partition. I find 20GB for / (root) to be plenty, but there are lots of threads about discussing the be size, a quick search should find you a suitable answer

---

### Post by Jazzy_Jeff on 2009-06-16
I personally back up what I want and then do a clean install. I find I have a lot less problems and headaches this way.

---

### Post by raymondh on 2009-06-16
Hello,

There are a lot of advantages of having a separate /home.... and if you plan to do a clean re-install, that will be a good opportunity to create your home partition as well.  

This is psychocats' guide which has been recommended many times in the forum.

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

I do have a separate /home and have found it valuable in retaining settings when upgrading from 8.10 to 9.04.  

However, I found a HOW-TO by bodhi.zazen (actually, a partitioning guide) where he recommended the use of /data.  After deliberating on it, I agree to his logic and now use /data.  Note that I use /data as I have various distros and various users with various inputs in my household :)

Here is his HOW-TO which you may find interesting.  His comment about /data is under OPTIONS

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

Good luck and happy Ubuntu-ing.

---

### Post by Therion on 2009-06-16
> **Jazzy_Jeff said:**
> I personally back up what I want and then do a clean install. I find I have a lot less problems and headaches this way.
+1

Doing a fresh install takes about 30-45 minutes.  Then I install [QuickStart](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11) and in less than an hour I'm good to go with a fully tweaked, customized system.  

A couple hours out of my day is a small price to pay for (usually) zero post-install headaches.

---

### Post by rajeev1204 on 2009-06-18
> **Therion said:**
> +1

Doing a fresh install takes about 30-45 minutes.  Then I install [QuickStart](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11) and in less than an hour I'm good to go with a fully tweaked, customized system.  

A couple hours out of my day is a small price to pay for (usually) zero post-install headaches.


You forget the time taken to download the iso.Many have a slow connection and can run into a lot of hours.

Also, the developers want to perfect the upgrade through update manager, so i would suggest recommending users this method.

Its the easiest way to upgrade and as many will say, its also relatively trouble free.

Of course, i prefer the manual install cos it just feels nice and neat.

---

