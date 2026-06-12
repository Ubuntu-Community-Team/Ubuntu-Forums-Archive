---
title: "Upgrade to Lucid failed Ubuntu won't boot."
date: 2010-06-10
forum: New to Ubuntu
---

### Post by Blodskaal on 2010-06-10
Hello everybody,

I'm running Ubuntu 9.10 for approximately 2 months now (currently on kernel linux 2.6.31-22), and I found it to be a very pleasant OS. However, I recently tried to update to Lucid Lynx.

On the first day, my distribution update refused to update to LL because of a "malformed release file".

On the second day, I managed to 'fix' the problem by deactivationg all repositories except for Karmic main.
Now my distribution update refused to update because my '/var' partition was full. NOTE: It was simply smaller than what was required to upgrade to Lucid. So even when it was empty it was considered 'full'.

On the third day, I tried several times unsuccessfully to fix this problem by creating live boot USB's (that ultimately would return a syslinux error upon attempting to boot) and symbolic linking certain libraries from my '/var' partition to my '/home' partition which did have enough space.

On the fourth day, I managed to fix the problem by recovering the CD which I used to install Ubuntu. I ran gparted from the live-boot and managed to shring '/home' and grow '/var'. I booted my installed Ubuntu again and ran the distribution update. It proceeded to estimate a remaining time of 18 hours, and then it began...
[label A]An error dialog appeared "package <x> could not be installed because <y>" note that <x> was the package name and <y> was (as far as I could see) a different reason for every <x> (including "it is already installed correctly"). Note that the distribution update would halt until I clicked 'close' (the only option). As soon as I did that, the update continued. Within half a second,  [if !tired: goto A].
Seeing as this would continue for 18 hours, requiring me to click close buttons every second, I did xkill.

Now my Ubuntu won't boot, the error message says that it failed to mount a filesystem.

Please help me get Ubuntu to boot, I'm sick (literally but that started before this), tired and I have to use windows.

Hopefully,

Blodskaal

---

### Post by garvinrick4 on 2010-06-10
You can try this in a Live CD it is just a shot in the dark. Do not know your set-up and or why it was acting up. I do know if it stopped in the middle of a upgrade it needs to continue. I would say if this does not work. Do a clean install into your partition for /.
It sounds like you made a/ a /home a /var  ect.ect. ect. 

Boot off or a Live CD.
This is given my / partition is sda5 and I have a label of lucid. Change to what ever yours are. Or you can give a Label in Disk Utility or gparted if you do not have labels.

```
sudo mkdir /media/lucid
``````
sudo mount /dev/sda5 /media/lucid
``````
sudo cp /etc/resolv.conf /media/lucid/etc/resolv.conf
``````
sudo chroot /media/lucid
``````
apt-get update && apt-get upgrade
``````
Ctrl/D
sudo umount /media/lucid
```Now if you made a seperate partition for /boot say in sda1: Make directory and mount also at start. Hope this continues updates and upgrades.
If not it is all I got. Tough situation.

---

### Post by Blodskaal on 2010-06-11
I managed to install Lucid from a CD I burned in Windows. It'll take a few days to get all of the software I originally had installed back again (mostly because I didn't have a list of what I had installed an can only recall it slowly) but I'll manage.
@garvinrick4: Thanks for your time, and the good advice.

---

### Post by garvinrick4 on 2010-06-11
> **Blodskaal said:**
> I managed to install Lucid from a CD I burned in Windows. It'll take a few days to get all of the software I originally had installed back again (mostly because I didn't have a list of what I had installed an can only recall it slowly) but I'll manage.
@garvinrick4: Thanks for your time, and the good advice.
Hey partner just for a quick bit of advice if you desire it. But it is always nice to start
off a new install with.

1. Go to Software Sources and check the box marked partners. Then start this way.

```
sudo apt-get install ubuntu-restricted-extras && sudo apt-get install gparted && sudo apt-get update && sudo apt-get upgrade
```While that is going you can set up your panels and right click in far up hand left corner of upper panel and choose edit menus and then edit what you want to keep or not use. If you are new to Firefox you can go to Bookmarks and Organize bookmarks and upper panel to import or backup bookmarks and take a backup every week or so and you will always have a file to import and have all your bookmarks returned in case you do a fresh install. It will be only files ending in .json  Nice to have around though.

That should give a good start in less than 20 minutes or so to set-up of desktop and up to date OS. Just a suggestion.

---

### Post by pdlethbridge on 2010-06-11
In system/administration/ synaptic open file. It has a couple of things you can use, at least in the future. Read markings and save markings. 
When you have your OS loaded and your software and updates loaded, select save markings. This will end up in your home folder. When you reinstall your OS, go to the read markings and click apply. This will load all your updates plus all the software you added. You may have to add a program or 2 and make an adjustment, but this will save you a bunch of time on your next install. It's a great tool.

---

### Post by garvinrick4 on 2010-06-12
> **pdlethbridge said:**
> In system/administration/ synaptic open file. It has a couple of things you can use, at least in the future. Read markings and save markings. 
When you have your OS loaded and your software and updates loaded, select save markings. This will end up in your home folder. When you reinstall your OS, go to the read markings and click apply. This will load all your updates plus all the software you added. You may have to add a program or 2 and make an adjustment, but this will save you a bunch of time on your next install. It's a great tool.
I will have to try that again sometime, tried it a few times and did not work. Will make a save markings in Maverick and give a try next clean install. Really would be nice if worked. Here is another way. If you just run the first code it gives you a alphabetic list
of your installed packages in there true linux package names. Good for having around when you forget what a package is called for terminal use. Have not tried second command to reinstall because I forgot where I put this note on last clean install.


  	 	 	 	 	 	  The second way of doing this doesn't create a large package, but rather a small list of apps that can be used to direct your computer to what to reinstall. This requires no installation of anything to actually run the command, but does require an internet connection. Now, this creates a list of everything, even standard system stuff, so don't get freaked out if theres stuff you've never seen on it before. Any overlap with standard stuff works itself out, it won't reinstall or duplicate things. The really nice thing about this method is that you can manually add or subtract stuff from the list.

To do this, run this command:
 
[LIST]
[*][FONT=inherit]sudo dpkg --get-selections > 	installedsoftware[/FONT]  	
[/LIST]
 [FONT=inherit]Then, all you have to do is copy that folder over to the home f[/FONT]older of the next computer and/or after the clean install, and then run:
 
[LIST]
[*]sudo dpkg --set-selections < installedsoftware  	
[/LIST]
 Remember, this second method requires an internet connection.

---

