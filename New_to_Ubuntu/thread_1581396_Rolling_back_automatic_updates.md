---
title: "Rolling back automatic updates?"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by BumberBot3K on 2010-09-24
(Running Kubuntu 10.04 64-bit)

I'm new to package management in linux/Kubuntu. I was hearing good things about KDE 4.5.1 and so I started following the directions on this site:

[http://www.kubuntu.org/news/packages-available-kde-platform-plasma-and-applications-451](http://www.kubuntu.org/news/packages-available-kde-platform-plasma-and-applications-451)

and added the backports "ppa" as a source. However, I then changed my mind and took no further action. I left that ppa in my repository sources list. I didn't realize at the time that it would try and do updates anyways, and so now I think I have some bizarre mix of new and old features. My notifications now take up a quarter of the screen and are filled with mostly blank space. Some of my widgets (specifically System Monitor) are broken, and the System Settings has lost the Advanced Tab in exchange for the "Lost and Found" section. I've also apparently lost Oxygen theming in my styles settings. However there are no monochrome tray icons like I thought was part of 4.5.1.

Bottom line is that I don't know what version of what I'm running, and would like to rollback any updates that occurred by adding that backports ppa, and stick with "stock" 10.04 until 10.10 is released. Any ideas?

TIA
BB3K

---

### Post by clhsharky on 2010-09-24
BumberBot3K

Did you do a backup of 10.04.1 that you can go back to?

You may all so be able to do a
```
ppa-purge (name of ppa)
``` 
but I'm not familiar with KDE backport, and if it has a ppa-purge installed with that package.

I had Kubuntu 10.10 on a test drive that broke this week, so KDE is out for me.

I'm sure someone can give you more help than me.


Sharky

---

### Post by jtarin on 2010-09-24
How many times did you do an update before this fatal one?
Here's a listing of packaged....chack them against your installed versions.

---

### Post by BumberBot3K on 2010-09-24
> **clhsharky said:**
> BumberBot3K

Did you do a backup of 10.04.1 that you can go back to?

You may all so be able to do a
```
ppa-purge (name of ppa)
``` 
but I'm not familiar with KDE backport, and if it has a ppa-purge installed with that package.

I had Kubuntu 10.10 on a test drive that broke this week, so KDE is out for me.

I'm sure someone can give you more help than me.


Sharky

Thanks for the response. I did not do a backup... it's a fairly fresh install, and I was still considering my partition layout and dual-boot options when this happened.

ppa-purge responds with "command not found" so it must not be part of the KDE package.

---

### Post by BumberBot3K on 2010-09-25
So I found some people with the same problem and followed some questionable advice that included the command

```
sudo apt-get remove kde*
```

Yeah, I know. Pretty stupid. But it worked out OK because it gave me the impetus to finally set up my dual-boot. Win 7 and Kubuntu playing nice... it's a wonderful thing! :)

---

### Post by beew on 2010-09-25
ppa-purge has to be installed from Synaptic. I think it is in fact in one of the back port PPAs you may wany to purge, if that is the case it is no good.

Instead of doing sudo apt-get remove everything a more elegant approach would be to install Ubuntu Tweak and use its ppa purge function. You just check the ppa you want to purge and it will downgrade all the packages you have installed from that ppa safely to the next lower version in one of the repositories on your sources list with all the dependencies taken care of. It will then remove these packages from the said ppa so they won't get upgraded through this particular PPA again, but they will still get upgraded from the other sources where their current versions come from. You can then decide whether to remove the ppa in your sources list by deleting it.

That's right, you can install Ubuntu Tweak from a PPA. :)
[URL="https://launchpad.net/~tualatrix/+archive/ppa"]
https://launchpad.net/~tualatrix/+archive/ppa[/URL]

---

### Post by BumberBot3K on 2010-09-25
> **beew said:**
> ppa-purge has to be installed from Synaptic. I think it is in fact in one of the back port PPAs you may wany to purge, if that is the case it is no good.

Instead of doing sudo apt-get remove everything a more elegant approach would be to install Ubuntu Tweak and use its ppa purge function. You just check the ppa you want to purge and it will downgrade all the packages you have installed from that ppa safely to the next lower version in one of the repositories on your sources list with all the dependencies taken care of. It will then remove these packages from the said ppa so they won't get upgraded through this particular PPA again, but they will still get upgraded from the other sources where their current versions come from. You can then decide whether to remove the ppa in your sources list by deleting it.

That's right, you can install Ubuntu Tweak from a PPA. :)
[URL="https://launchpad.net/~tualatrix/+archive/ppa"]
https://launchpad.net/~tualatrix/+archive/ppa[/URL]

That's awesome advice and I will save it for the next time I mess something up!

---

