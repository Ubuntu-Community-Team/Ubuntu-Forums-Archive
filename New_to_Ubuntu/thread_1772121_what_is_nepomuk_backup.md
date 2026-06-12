---
title: "what is nepomuk backup?"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by soylentcola on 2011-05-31
So I noticed a few weeks ago this strange "nepomuk backup" application installed under my system tools, and I have no clue what it does!

Can anyone out there enlighten me as to what this is (I ran it and nothing happened) and what purpose it serves?

---

### Post by KL_72_TR on 2011-05-31
These can give you an answer: [http://en.wikipedia.org/wiki/NEPOMUK_%28framework%29](http://en.wikipedia.org/wiki/NEPOMUK_%28framework%29) and [http://nepomuk.kde.org/](http://nepomuk.kde.org/)

---

### Post by tropdoug on 2011-12-04
I too have wondered about this app. I looked at the two links and ummmm yeah. Still don't know what it does or why. 

Any chance of a plain english non technical explanation?

---

### Post by beew on 2011-12-04
> **tropdoug said:**
> I too have wondered about this app. I looked at the two links and ummmm yeah. Still don't know what it does or why. 

Any chance of a plain english non technical explanation?

If you haven't installed it yourself chances are it was installed as a dependency for some other kde applications that you have installed. It is a kde back up tool. If you are not using Kubuntu it doesn't have any use on its own, but other kde apps may depend on some shared libraries so you may not be able to remove it.

To see why it was installed you can do an experiment by trying to remove it from synaptic, it will show you a list of apps that will be removed as well, once you see the list you can just hit cancel so that nothing will be removed.

---

### Post by bluexrider on 2011-12-04
it usually gets installed with kde-base as in when you install K3b or some other KDE app

---

### Post by lolpenguin on 2011-12-04
It includes runtime libraries and is a backup utilities, both used by computers of the K Desktop Environment. It gets installed as a dependency of many KDE components. If you do not use Kubuntu, or have no KDE components installed, it is safe to remove it.

---

### Post by bluexrider on 2011-12-04
> **lolpenguin said:**
> It includes runtime libraries and is a backup utilities, both used by computers of the K Desktop Environment. It gets installed as a dependency of many KDE components. If you do not use Kubuntu, or have no KDE components installed, it is safe to remove it.

If it was installed with another app like K3b, removing it will break the application. Ive tried.

---

### Post by tropdoug on 2011-12-07
OK - so it was installed by default, thats cool. However is it a backup tool that I can use to back up my /home directory to an external drive or is it for internal system backups that happen behind the scenes?

---

### Post by lolpenguin on 2011-12-07
> **bluexrider said:**
> If it was installed with another app like K3b, removing it will break the application. Ive tried.

It is only installed if you use KDE applications or a Kubuntu system. In my case, it was installed as a dependency of a KDE component, and it was unused, and I uninstalled it.

> OK - so it was installed by default, thats cool. However is it a backup tool that I can use to back up my /home directory to an external drive or is it for internal system backups that happen behind the scenes?
If you use Kubuntu, yes, but if you use other DE's then you should use the backup tool instead that came with it (unless you don't like it). If it isn't needed by any packages, and you aren't going to use it, run
```
sudo apt-get autoremove
```
to get rid of any unused packages.

---

### Post by ExileAmongYou on 2011-12-07
> **tropdoug said:**
> OK - so it was installed by default, thats cool. However is it a backup tool that I can use to back up my /home directory to an external drive or is it for internal system backups that happen behind the scenes?

If you're running KDE, Nepomuk can do those kind of back-ups for you. If you're running with Unity/Gnome (the default desktop environment for Ubuntu), then it might not work properly, because the services it uses to keep track of changes to files probably aren't running. On Ubuntu 11.10, there's a backup application installed by default, search for Backup in the dash or look for the Backup entry in system settings.

---

### Post by mastablasta on 2011-12-07
nepomuk is also the thing giving the problems in current KDE. let's hope they iron it out for next release. but it has to be there. don't you just love shared libraries?!?!

---

### Post by tropdoug on 2011-12-07
OK so this is weird, using the backup tool does not give any menu to configure the tool to backup certain folders or files. Going onto the Nepomuk site reveals the final build was in 2010 and it is not being continued. Also the PSEW file you need to actually run the application is only for 32 bit -- not much use to me on 64 bit.

So why is what appears to be a odd and reasonably useless app included in the latest release with menu items for doing what? 

I have been having quite a few crashes since install a week ago, could it be the fault of Nepomuk?

---

### Post by mastablasta on 2011-12-07
you checked this one: [http://nepomuk.kde.org/aggregator](http://nepomuk.kde.org/aggregator)
 
it's been released in November. as i understand it is also used for file search/connection (hence the crashes in connection with other applciations).
 
> Nepomuk allows applications to use information from all over the desktop, the web, other devices, and combine it into one coherent interface.

 
The bug i read is that if you disable it you keep getting notification that it is disabled. and apparently that is not a bug. :)
 
yeah crashes could be due to nepomuk.

---

### Post by tkoco on 2012-03-02
Though this thread is a bit old, I had the same question as the original person - what the heck is nepomuk? I read the replies. 
My 2 cents worth of reply - the machine sharing/processing of data sounds like what MS Windows does. If nepomuk becomes the standard desktop service, I suppose that the machine requirements for running nepomuk will be astronomical like Windows, and that we will have to have virus/malware detection/prevention software running.  :(
Again, just an opinion.

---

