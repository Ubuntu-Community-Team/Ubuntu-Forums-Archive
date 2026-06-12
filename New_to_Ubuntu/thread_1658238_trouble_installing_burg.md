---
title: "trouble installing burg"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by nash black on 2011-01-02
Hi

I tried to install burg a few days ago and had a couple of issues. I am running a Windows XP and Ubuntu dual-boot with windows on one hard disk and Ubuntu, Grub, and a shared partition on the second one.

While installing burg, I was prompted to install it on 'sda' or 'sdb' and I accidentally selected 'sda' I believe that I should have installed it on 'sdb'. The computer still boots into both OSs just fine, but there are now a few little glitches during the process (longer blank screen, etc) that I would prefer to get rid of and, of course, the burg screen does not appear.

The first thing that I would like to do is undo what I did there^

Secondly, I would like to install burg-manager. I have not been successful doing so, following these instructions:

[http://ubuntuguide.net/decorate-grub-2-boot-loader-with-burg-manager-gui-for-burg](http://ubuntuguide.net/decorate-grub-2-boot-loader-with-burg-manager-gui-for-burg)

On step three I get an error message about a directory not existing and enabling user sharing...



EDIT: I just found burg manager in the Ubuntu software center and installed it... I must have missed it before... I tried to use it to uninstall and reinstall burg, but it still bahaves the same way. It boots fine, but the burg screen does not appear, just the old grub screen

---

### Post by cariboo on 2011-01-02
You may be better off enabling the [burg ppa]("https://launchpad.net/~bean123ch/+archive/burg"), then using the Software Center or Synaptic Package Manager to install burg.

---

### Post by nash black on 2011-01-02
Yeah, I actually just noticed it there. It is actually the burg-manager that shows up.

I used that to uninstall burg, then reinstalled it. Still didn't work.

Next I used synaptic pkg mgr to completely remove all burg related items.

The weird thing about this is that in both cases, the 'burg' file and all of its contents remained in the 'boot' folder.

And after all of that, I installed burg-manager through Ubuntu Software Center, used that to install and configure burg and am still getting the same result: 1 second longer startup and no burg :mad:

---

