---
title: "Beginner questions on optimization, add/remove, etc..."
date: 2009-05-09
forum: New to Ubuntu
---

### Post by darrel_h on 2009-05-09
Hello all.  I recently installed the Ubuntu Netbook Remix on my MSI Wind U100 and am having a few issues.  Now, I am an absolute novice when it comes to Linux, so please bear with me and if you can, any suggestions should be made in the most layman terms (thank you).  

First let me say that I was very suprised that once loaded, Ubuntu seemed to work 100%.  No issues with wireless internet, all my hot keys worked, everything seems fine.  Now, in saying that, when I go to System -Administration - Hardware Drivers, nothing is shown.  Anybody know why this is?  Like I said, I know they're there, everything is working (sound, monitor settings, video...).

Also, there's a lot of programs I have absolutely no intentions on using, like Evolution and blue tooth (the MSI I bought does not have it anyways) but, when I attempt to remove the programs they tell me I can't.  So, I went into the Synaptics Package Manager and tried it from there.  When I attempt to deinstall all of the Bluez stuff and Evolution, then, I believe because of dependancies, it ends up deleting my Gnome interface or some other stuff.  I'm not 100% sure what's happening but i know i've had to reinstall the ubuntu a couple of times because, being this much of a novice, i didn't know how to get what i needed using the terminal.  So, basically (sorry for being so long winded), how do I remove programs that i don't want without removing certain dependancies?

And lastly, i'm a windows user and before i switched to ubuntu, i was going through xp like a madman stoping all the startup applications and deleting stuff from the registry, just trying to remove all the crap that wasn't needed and improve performance.  Does anyone have any tips like that for UNR?  I already know about System - Preferances - Startup Applications, but there's a few things in there i'm not sure if i can stop or not, like all the Daemon stuff, like the GNOME Settings and Keyring Daemons, the AT SPI Registry Wrapper, Indicator Applet (what is that for anyways?), Seahorse Daemon (???). 

Well, any help with any of this stuff would be greatly appreciated.  Like i said, i'm a novice, so be gentle,  I've been doing as much research as i can and trying to learn things on my own, but i haven't been able to find a whole lot on the Netbook Remix verxion.  Well, not what i'm looking for anyways.  Basically, any suggestions to improve performance and streamline things would be great.  Thanks in advance for all your help.

---

### Post by spiderbatdad on 2009-05-09
I'll try to answer one of those questions. Ubuntu actually uses modules instead of hardware drivers...at lest that is my understanding. What gets listed in the Hardware Drivers applet you viewed, is offered proprietary drivers, if the kernel detects they are needed for your system. To see what modules are loaded and in use on your system, open your terminal...Applications>>Accessories>>Terminal and enter ```
lsmod
```as in list modules. Hope this helps, and I am not too far off.

---

### Post by Didius Falco on 2009-05-09
> **darrel_h said:**
> Hello all.  I recently installed the Ubuntu Netbook Remix on my MSI Wind U100 and am having a few issues.  Now, I am an absolute novice when it comes to Linux, so please bear with me and if you can, any suggestions should be made in the most layman terms (thank you).  

First let me say that I was very suprised that once loaded, Ubuntu seemed to work 100%.  No issues with wireless internet, all my hot keys worked, everything seems fine.  Now, in saying that, when I go to System -Administration - Hardware Drivers, nothing is shown.  Anybody know why this is?  Like I said, I know they're there, everything is working (sound, monitor settings, video...).

Also, there's a lot of programs I have absolutely no intentions on using, like Evolution and blue tooth (the MSI I bought does not have it anyways) but, when I attempt to remove the programs they tell me I can't.  So, I went into the Synaptics Package Manager and tried it from there.  When I attempt to deinstall all of the Bluez stuff and Evolution, then, I believe because of dependancies, it ends up deleting my Gnome interface or some other stuff.  I'm not 100% sure what's happening but i know i've had to reinstall the ubuntu a couple of times because, being this much of a novice, i didn't know how to get what i needed using the terminal.  So, basically (sorry for being so long winded), how do I remove programs that i don't want without removing certain dependancies?

And lastly, i'm a windows user and before i switched to ubuntu, i was going through xp like a madman stopping all the startup applications and deleting stuff from the registry, just trying to remove all the crap that wasn't needed and improve performance.  Does anyone have any tips like that for UNR?  I already know about System - Preferences - Startup Applications, but there's a few things in there i'm not sure if i can stop or not, like all the Daemon stuff, like the GNOME Settings and Keyring Daemons, the AT SPI Registry Wrapper, Indicator Applet (what is that for anyways?), Seahorse Daemon (???). 

Well, any help with any of this stuff would be greatly appreciated.  Like i said, i'm a novice, so be gentle,  I've been doing as much research as i can and trying to learn things on my own, but i haven't been able to find a whole lot on the Netbook Remix version.  Well, not what i'm looking for anyways.  Basically, any suggestions to improve performance and streamline things would be great.  Thanks in advance for all your help.

Welcome!!

Most of the drivers you need are built right into the kernel. If nothing is showing up in the Harware Drivers, it's because there isn't any hardware on your computer that needs and/or qualifies for those drivers. The "qualifies" part is mostly to do with video card drivers. The drivers that show up there are Proprietary drivers produced by, for example ATI or nVidia.

As to removing packages, there is a core set of packages that are all tied together into the Gnome Desktop, and they share dependencies, as you've found out the hard way. This is one of the few things I don't like, but I can understand the reasoning behind it.

After all, your first comment was on how great it was that everything just worked. If they didn't tie all that stuff together, then a lot of folks would be left in a crippled state to start with. Imagine having a Bluetooth keyboard, installing Ubuntu and finding that it won't work, and you've no way of getting it to work because all your input devices, and maybe your net connection, depend on Bluetooth.

As to uninstalling, the key, I've found, is to use Synaptic Package Manager and look closely at what it will take with it if uninstalled. You can always ask here in the forum about things you are considering removing, too.

I've found, for the vast majority of things, that the "out of sight, out of mind" approach works best. Right-click on your menu and choose Edit. You can then check/uncheck boxes that will determine if applications appear in your menus. You can also rearrange them to suit your own preferences from there. I've found that the packages I don't use, but are tied into the core package, really don't take up that much space, and removing them from the menu just lets me forget they are even there.

The indicator applet is the little black window that opens up in the top right corner of your screen that gives you information, then fades away.

The Seahorse Daemon manages encryption  keys.

You can always ask specific questions, and it helps to do a couple of things; Make the thread title a good synopsis of what you need info about/assistance with, etc., and limit it to one thing when possible. The second thing is to give as much relevant information as you can in your first post, which will help others to help you without a tennis match of questions and answers.

I'm going to wrap up now, as it's taken me so long to type this that all your questions have probably already been answered by more pithy, nimbler-fingered forum members. <G>

Regards,

Didius

---

### Post by darrel_h on 2009-05-11
Thank you both for your replies.  I understand a little better what's going on now.  I have successfully removed the applications I will not be using from the Applications menu, I guess I'll just have to live with them in the packages.  From now on I will try to post straight forward questions in individual posts.  Again, thanks :-)

---

### Post by Paddy Landau on 2009-05-11
[Linux isn't Windows]("http://linux.oneandoneis2.org/LNW.htm").

And that means that you can forget about all that stuff about removing registry entries, running Ccleaner (or equivalents), worrying about startup programs, and so on. Linux is nicely efficient about it all. The core of Ubuntu with all its default applications is much smaller than the core of Windows, in terms of both disk space and RAM.

For example, you don't need to empty your temporary folder (/tmp), because Linux does that for you every time you boot.

If you want to clean up, here are a four things that you can do on a regular basis. But they are optional, unless you have a small hard drive.

[LIST]
[*]Remove installation files no longer needed, and modules that no longer have dependencies.
```
sudo apt-get clean
sudo apt-get autoremove
```
[*]Empty the var backups.
```
sudo rm /var/backups/*
```
[*]Remove backups from OpenOffice.
```
rm ~/.openoffice.org/3/user/backup
```
[*]Empty your Trash (right-click the trash can in your panel and select *Empty the Deleted Items folder*).
[/LIST]
The last item (empty the Trash) is the only item that I would strongly recommend, because, depending on what you delete, it could take a huge amount of space. The other items really are optional.

---

### Post by darrel_h on 2009-05-11
> **Paddy Landau said:**
> [Linux isn't Windows]("http://linux.oneandoneis2.org/LNW.htm").

And that means that you can forget about all that stuff about removing registry entries, running Ccleaner (or equivalents), worrying about startup programs, and so on. Linux is nicely efficient about it all. The core of Ubuntu with all its default applications is much smaller than the core of Windows, in terms of both disk space and RAM.

For example, you don't need to empty your temporary folder (/tmp), because Linux does that for you every time you boot.

If you want to clean up, here are a four things that you can do on a regular basis. But they are optional, unless you have a small hard drive.

[LIST]
[*]Remove installation files no longer needed, and modules that no longer have dependencies.
```
sudo apt-get clean
sudo apt-get autoremove
```
[*]Empty the var backups.
```
sudo rm /var/backups/*
```
[*]Remove backups from OpenOffice.
```
rm ~/.openoffice.org/3/user/backup
```
[*]Empty your Trash (right-click the trash can in your panel and select *Empty the Deleted Items folder*).
[/LIST]
The last item (empty the Trash) is the only item that I would strongly recommend, because, depending on what you delete, it could take a huge amount of space. The other items really are optional.


I did all these things and it didn't seem to do too much.  most of them just ran and one of them said no files to remove.  the openoffice one didn't do anything though, it told me the .openoffice.org/3/user/backup was a directory.  thanks for you help though.

---

### Post by Paddy Landau on 2009-05-11
> **darrel_h said:**
> the .openoffice.org/3/user/backup was a directory
Sorry, my mistake. It should have read
```
rm ~/.openoffice.org/3/user/backup/*
```> **darrel_h said:**
> I did all these things and it didn't seem to do too much.
Yes, that's right. It won't do much. Linux doesn't need all this cleaning up stuff that Windows needs.

As I say, the only real thing is that if you delete lots of stuff or large files, then empty your Trash regularly or after deleting particularly large files.

---

