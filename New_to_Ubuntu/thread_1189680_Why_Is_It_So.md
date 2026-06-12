---
title: "Why Is It So"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by Mad_Max_1412 on 2009-06-17
Hi Guys,

Recently I went to change my monitor resolution via the nvidia control panel and when I went to save changes to the xorg.conf file, I found out it couldn't save changes as I hadn't started the control panel as root.

I had to search the forums to find out that I had to use the command "gksudo nvidia-settings"

I gather most people like myself who are just starting out with Ubuntu don't log into the system as Root each time we boot up (and I've been told we should never do this). Therefore, any program from the System menu is going to start up under the user permissions rather than root.  The reason for going into these menu items would be to change the settings, and I know that by default, this (starting apps as non-root user) stops people from messing up the system.  

Wouldn't a simple solution be the option of right-clicking a menu option (eg System --> Preferences --> Display) and asking it to start as Root?  I know that the first part of the terminal window command is gksudo, but I didn't know what the rest was (nvidia-settings) without having to research on the net.

Just a suggestion for future releases :-)

---

### Post by Steelmourne on 2009-06-17
That is true but you do get used to these options. Windows has idiosyncrasies too. The last thing Ubuntu needs is to become a Windows clone.

---

### Post by mgranet on 2009-06-17
You can just edit the launcher. Add gksudo before the nvidia-settings command. That way, each time you launch it, it will run as root.

---

### Post by super kim on 2009-06-17
why are we never supposed to log in as the root user? i am currently logged in as the root, i had to to change my grub menu list. i know theres an easier way but can never remember it, but what is wrong with being logged in as the root???

---

### Post by bcbotha on 2009-06-17
it's a safey thing that ubuntu have done. if you are new to ubuntu can are playing around and delete or edit or move something by mistake then those changes oare then set for the whole system. the command sudo gives a normal logged in user root permissions. it is always advisable to loggin as a normal user.

---

### Post by mcduck on 2009-06-17
> **super kim said:**
> why are we never supposed to log in as the root user? i am currently logged in as the root, i had to to change my grub menu list. i know theres an easier way but can never remember it, but what is wrong with being logged in as the root???

Logging in as root means that all the programs you run have full permissions on your system. Thus, a small bug or security hole in any program could break the whole system, or compromise security of every user.

When running as normal user, even one in admin group, the worst that this kind of issues can cause is breaking that user's setup, while leaving the system itself and all other users safe.

The basic idea behind security in Linux/Unix systems is to always use the minimum permissions required to complete the task at hand. This is what has made Linux/Unix systems more stable and secure than Windows is, and logging in as root and running all your programs with root permissions pretty much ruins it all.

---

### Post by Mornedhel on 2009-06-17
Also, not having a root account enabled means that brute force hackers have to do twice the work : not only do they have to guess your password, they also have to guess your username.

---

### Post by super kim on 2009-06-17
oh, i always thought the only virus ever made for a linux os was just proof of concept.
i knew about the sudo cammand but how could i open the grub menu list to edit using the sudo command? sorry this tread has mutated somewhat. please come and see my real problem:
[http://ubuntuforums.org/showthread.php?t=1189732](http://ubuntuforums.org/showthread.php?t=1189732)
its so much more fun on that thead lol

and ok i promise never to log in as the root again, infact i'll even disable the option from the login thingy (check the technical jargon!)

---

### Post by mcduck on 2009-06-17
> **super kim said:**
> oh, i always thought the only virus ever made for a linux os was just proof of concept.
i knew about the sudo cammand but how could i open the grub menu list to edit using the sudo command? sorry this tread has mutated somewhat. please come and see my real problem:
[http://ubuntuforums.org/showthread.php?t=1189732](http://ubuntuforums.org/showthread.php?t=1189732)
its so much more fun on that thead lol

and ok i promise never to log in as the root again, infact i'll even disable the option from the login thingy (check the technical jargon!)

The thing is, if people would commonly use Linux as root all the time there would be Linux viruses around as the strict separation between users and root is the biggest reason why making a Linux virus is s hard.

Also, viruses and trojans are not the only threat in the Internet.

Anyway, to edit the menu.lst you can either run "sudo nano /boot/grub/menu.lst" (to edit it with command-line editor Nano) or "gksudo gedit /boot/grub/menu.lst" (to edit with eGdit, the default text edit in Gnome).

One more useful tip is opening the file manager as root with "gksudo nautilus". This way you can access all the files as root just like as if you were logged in as root. (Still, only that file manager window and everything opened from it runs as root, while rest of your desktop continues running with user privileges so it's lot better way than logging into the desktop itself as root). Just remember to be careful and close the window as soon as you don't need it any more to avoid accidentally deleting wrong files or something. I actually always set the root Nautilus to use red background to serve as a small warning and to make the difference between Nautilus running as root and other Nautilus windows more clear.

---

### Post by super kim on 2009-06-17
ok well that explains it all, did you get a chance to view my other thread?
[http://ubuntuforums.org/showthread.php?t=1189732](http://ubuntuforums.org/showthread.php?t=1189732)
i've been trying for about er 6 hours now and still no joy :(

---

### Post by Paqman on 2009-06-17
> **Mad_Max_1412 said:**
> 
Just a suggestion for future releases :-)

I've always thought that's stupid, too. However, since this tool is from Nvidia, you might want to direct your suggestion to them. Ubuntu don't actually control the nvidia-settings utility.

---

### Post by tom56 on 2009-06-17
> **Mad_Max_1412 said:**
> Therefore, any program from the System menu is going to start up under the user permissions rather than root.  The reason for going into these menu items would be to change the settings, and I know that by default, this (starting apps as non-root user) stops people from messing up the system.  

Wouldn't a simple solution be the option of right-clicking a menu option (eg System --> Preferences --> Display) and asking it to start as Root?  I know that the first part of the terminal window command is gksudo, but I didn't know what the rest was (nvidia-settings) without having to research on the net.

Just a suggestion for future releases :-)

Anything in System->Administration should ask for your password when it wants to be root. Unfortunately, nvidia control panel is the exception since it is closed-source so the problem can only be fixed by nvidia developers.

---

