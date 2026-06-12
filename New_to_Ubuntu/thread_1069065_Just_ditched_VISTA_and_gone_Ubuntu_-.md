---
title: "Just ditched VISTA and gone Ubuntu -"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by cjslim on 2009-02-13
Well, i made the jump - somewhat involuntarily in a way - I tried installing Ubuntu to dual boot with VISTA, it installed fine, great, boot into windows, still works, cool....right....Ubuntu show me your wares!! So i boot into Ubuntu...splash comes up good..loading ...sweet...Splash disappears, monitor fickeres - NO SIGNAL? - keyboard lights flashin every seconds on - off - on - off..so i figure give it time...hardware config i'll let it go....nothin' happens, again and again i try.
i figure corrupt install...
reinstalled same problem.

Ok back to Vista, check out how to re-format and just start over, follow the instructions, blows my MBR, didnt overwrite grub :S.... ok now i'm pissed, now i have no operating system at all...


Had to load vista from CD reformat the entire drive & partitions and load into windows..

I figure, F*** it all  my data backed up so i made the jump, threw ubuntu into the drive - reboot - reformat my entire drive and partition again with Ubuntu...

Reboot, add the 'noapic nolapic' on boot...voila!! the drums are here!!

I logged in checked it out and loving it!! Recommending to everyone to make the switch...

Pisser is, if i had added noapic nolapic when i first installed to dual boot it probably would have worked ....but i prefer to think it wouldnt have ;)

So, anyway installed wine, i love FM 09, installed via wine, Didnt work, tried unintalling, didnt work, got annoyed and re-installed the entire o/s again....ah the joys of learning..

Still, Would like some advice and ideas on the best system maintainance tools and comp. management tools etc as well as any other kick *** apps that can further light the fire in my heart for linux...

Thanks;
:)

---

### Post by lazyart on 2009-02-13
Nice thread on apps can be found here: [http://ubuntuforums.org/showthread.php?t=993694&highlight=favorite+apps](http://ubuntuforums.org/showthread.php?t=993694&highlight=favorite+apps)

Personally I love apwal.  I tie my middle mouse button to it and add most used apps.  Middle click and you get icons for the apps you configured.  Click one an it launches.  Great for stuff like gedit, terminal, firefox, home folder.  Include a shortcut to let you reconfigure apwal as well and it's really, really nice.

---

### Post by jdeslip on 2009-02-13
Don't reinstall the whole OS just caReply use a wine app wouldn't uninstall.  Everything you install with wine goes into the ~/.wine directory (the . makes it hidden).  Under the .wine directory is your "drive_c" which is like the fake "windows" drive.  So, just delete the .wine directory and everything you installed in wine is gone!  Next time you run wine it will recreate a brand new drive_c for you to mess around in again!

---

### Post by listerdl on 2009-02-13
Well done.

Bin Vista.

Ubuntu is the answer!

---

### Post by trukin on 2009-02-13
You sir, just made my day.

---

### Post by cjslim on 2009-02-14
> **jdeslip said:**
> Don't reinstall the whole OS just caReply use a wine app wouldn't uninstall.  Everything you install with wine goes into the ~/.wine directory (the . makes it hidden).  Under the .wine directory is your "drive_c" which is like the fake "windows" drive.  So, just delete the .wine directory and everything you installed in wine is gone!  Next time you run wine it will recreate a brand new drive_c for you to mess around in again!

Thanks!! 
This has to be one of the best tips so far..
I'll retry til me little heart is content :)

---

### Post by Sealbhach on 2009-02-14
Looks like you were destined to become an Ubuntu user.:)

Some good info on apps here:

[http://linuxappfinder.com/alternatives](http://linuxappfinder.com/alternatives)

You'll probably find most of them in the repos already. Better to install them from there.


Also, you can find some nice themes here:

[http://www.techiesouls.com/2008/11/27/collection-of-50-best-looking-linux-gnomeubuntu-themes-to-download/](http://www.techiesouls.com/2008/11/27/collection-of-50-best-looking-linux-gnomeubuntu-themes-to-download/)

.

---

### Post by rburkartjo on 2009-02-15
cj yea i ditched vista about 2 years ago. have fun with ubuntu and if you ever need help this form is a great place to ask/cheesemaker

---

### Post by Paqman on 2009-02-15
> **cjslim said:**
> 
Still, Would like some advice and ideas on the best system maintainance tools and comp. management tools etc

My favourites:

[LIST]
[*]startupmanager : Does splash screens, grub cleanups, default kernels, etc.
[*]gtkorphan: Fast utility for removing orphaned packages.
[*]compizconfig-settings-manager: Gives you total control over your Compiz setup.
[*]grsync: Create and update backups easily.
[*]sbackup: Sets up automated backups.
[*]preload: Not a tool, but will speed how quickly apps launch.
[/LIST]

---

### Post by stalkingwolf on 2009-02-15
you can also find several useful things by right clicking on the 
top panel, then click Add to Panel.  a couple that I use are force quit
and the cpu monitor.

another thing you can do if there are apps in the menu you want faster access to 
is to right click on the app in the menu then select add to panel
or add to desktop.  which ever you want.  or both.

---

