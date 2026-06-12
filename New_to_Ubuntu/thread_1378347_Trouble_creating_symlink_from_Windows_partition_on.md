---
title: "Trouble creating symlink from Windows partition on my Dual boot system."
date: 2010-01-11
forum: New to Ubuntu
---

### Post by scrypt on 2010-01-11
Hello All.

Im trying to get World of Warcraft up and running on Ubuntu 9.10 Karmic.
I know it is possible.
I am Using Wine and PlayOnLinux to configure and play World of Warcraft on Ubuntu.

I am using A partitioned HDD with dual Boot Windows7 and Ubuntu. with Windows7 on my Primary OS but use GRUB as my bootloader.

I must admit though I am still newish to Ubuntu and I am having difficulty following this step from the bellow paragraph :

Can somebody help me to understand where I should be looking and what app I should be using to find the folder/Directories?

I am unsure how to create the correct symlink to my World of Warcraft folder on my windows partition.
WoW is instaled in the default folders etc on my Windows partition too.

Can somebody help me to understand this please?

I am using this site as my main source of info :

[http://gameshogun.ws/libregame/how-to-play-world-of-warcraft-on-ubuntu-linux-smoothly](http://gameshogun.ws/libregame/how-to-play-world-of-warcraft-on-ubuntu-linux-smoothly)

 Just follow the steps below:

    * Download this POL file: wow-dualboot2.pol (right-click and save as)
    * Run POL by going to Applications -> Other -> PlayOnLinux
    * Go to Tools -> Run a non-official script
    * Select wow-dualboot2.pol and just follow the instructions

Now that everything has been setup, it is time to create a symlink:

    * Go to ~/.PlayOnLinux/wineprefix/WorldOfWarcraft/drive_c/Program Files
    * If there is an existing World of Warcraft folder, rename it to anything you want
    * Go to your WinXP WoW folder
    * Right click on your World of Warcraft folder and select ‘Make Link’
    * Cut the newly created symlink and paste it here: ~/.PlayOnLinux/wineprefix/WorldOfWarcraft/drive_c/Program Files
    * Rename the symlink to World of Warcraft

I am following it to the letter but I am stuck at this point :

I cannoy find this and I do not know how to find the following folder or where to look.:

Where and how do I find the following folders in Ubuntu? :

  * Go to ~/.PlayOnLinux/wineprefix/WorldOfWarcraft/drive_c/Program Files

---

### Post by J V on 2010-01-11
Definitly absolute beginners :)

Files or folders with a dot at the beginning of a ~ at the end are hidden, press ctrl H to unhide them....

~ is your home

---

### Post by scrypt on 2010-01-11
Thanks for the reply.

Okay thank-you for telling me about the hidden folders.

I  am still unsure how to correctly execute the following instruction.

Now that everything has been setup, it is time to create a symlink:

* Go to ~/.PlayOnLinux/wineprefix/WorldOfWarcraft/drive_c/Program Files
* If there is an existing World of Warcraft folder, rename it to anything you want
* Go to your WinXP WoW folder
* Right click on your World of Warcraft folder and select ‘Make Link’
* Cut the newly created symlink and paste it here: ~/.PlayOnLinux/wineprefix/WorldOfWarcraft/drive_c/Program Files
* Rename the symlink to World of Warcraft

Can Somebody help me to understand what to do?

Can somebody who has experience of these commands please show me step by step how to do the above?

I have read various help articles but I am still unsure

---

### Post by scrypt on 2010-01-12
Bump

---

### Post by gordong11 on 2010-05-11
Hey I was having the same problem, but I figured out an easy alternate solution, if you are still having trouble. let me know if this helps. I have Vista 64bit and lucid 32bit on dual boot.

For me I did:

1. Places--> Computer
2. open Windows File System Drive
3. Locate the WoW folder (mine is Users/public/games/World of Warcraft)
4. click "WoW.exe


That is it, the game plays perfect with wine installed. you can also right click on the desktop, then create launcher, and browse the path to WoW.exe.

hope this helped

---

