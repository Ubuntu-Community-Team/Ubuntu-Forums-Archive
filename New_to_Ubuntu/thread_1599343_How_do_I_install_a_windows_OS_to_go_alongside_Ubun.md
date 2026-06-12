---
title: "How do I install a windows OS to go alongside Ubuntu?"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by kroni_hunter on 2010-10-17
First things first, I'm a complete newbie and Ubuntu illiterate.  I tried reading all the guides about this issue and I just can't follow them the terminology confuses me.  My problem is that I have no clue how to dual boot.  I don't know how to get the Windows7 CD to start up.  Is there anyone that can give me easy to understand instructions on how to go about this?

---

### Post by Hippytaff on 2010-10-17
What do you want to do...do you have windows installed and want to dual boot with ubuntu?

this is the bit that confuses me

> 
 I don't know how to get the Windows7 CD to start up


---

### Post by kroni_hunter on 2010-10-17
Sorry, I'll clarify.
I have installed Ubuntu 10.04 on a custom computer.  I have a windows 7 disc that has not been installed yet and I want to create a separate partition to have Windows as a second Operations System

---

### Post by Hippytaff on 2010-10-17
ah...to be honest it's easier the other way around, in my experience. Linux (and therefore ubuntu) are used to and cater for people who want linux as their second os, but windows doesn't generally cater or this. maybe back everything up, install windoze, then from a live cd install ubuntu as the secondary os.

You can always try using gparted in ubuntu to reduce the partition size of ubuntu, then install windows on the remaining partition, but to be honest I'm not really sure that'll work or if it is even a possibility :-)

---

### Post by kroni_hunter on 2010-10-17
Yeah I was thinking I might have to wind up doing that.  Would you be able to explain to me how to uninstall Ubuntu?

---

### Post by WaveMyBlackFlag on 2010-10-17
Back everything up (i.e. your important stuff), restart computer with Windows CD in drive, you may need to hit a certain key to boot from cd. if so it should be displayed on screen during boot. When the windows install program starts it should have an option to format the drive and install automatically.

be sure your back up is on a separate medium (cd/dvd/etc.) than the hard drive as formatting will usually erase all data on drive

Once windows is installed and booted, restart computer with ubuntu cd in drive, ubuntu install software will have instructions and guides to help you through the process of installing boot loader, resizing the windows partition, making a linux partition and finally installing ubuntu.  once done, reboot and you should be taken straight to the bootloader where you can select windows or linux to boot into.  

hope this helps, let me know if i need to clear anything up

---

### Post by Hippytaff on 2010-10-17
> **WaveMyBlackFlag said:**
> Back everything up (i.e. your important stuff), restart computer with Windows CD in drive, you may need to hit a certain key to boot from cd. if so it should be displayed on screen during boot. When the windows install program starts it should have an option to format the drive and install automatically.

be sure your back up is on a separate medium (cd/dvd/etc.) than the hard drive as formatting will usually erase all data on drive

Then, once that is done, insert the ubuntu cd, let it do it's thing then choose install - if you've got a printer print and follow this or if you have a spare pc follow it from that
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

---

### Post by kroni_hunter on 2010-10-17
I've got my media all on an external drive.  
When I startup with the cd loaded nothing happens.  There's a message that says Press DEL for Setup, Press 4 for ACC, and Press TAB for POST BIOS but thats it.  Is it one of those?

---

### Post by WaveMyBlackFlag on 2010-10-17
press DEL, go into setup and look for "first boot device" or something similar and change to "cd(or dvd)-rom", save changes exit and reboot with cd in drive

---

### Post by WaveMyBlackFlag on 2010-10-17
> **Hippytaff said:**
> Then, once that is done, insert the ubuntu cd, let it do it's thing then choose install - if you've got a printer print and follow this or if you have a spare pc follow it from that
[http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot)

whoops, hit post by accident, was yelling at alex smith... lol

---

### Post by Hippytaff on 2010-10-17
> **kroni_hunter said:**
> I've got my media all on an external drive.  
When I startup with the cd loaded nothing happens.  There's a message that says Press DEL for Setup, Press 4 for ACC, and Press TAB for POST BIOS but thats it.  Is it one of those?
  not sure, but I'd try DEL first :-)

---

### Post by Hippytaff on 2010-10-17
> **WaveMyBlackFlag said:**
> whoops, hit post by accident, was yelling at alex smith... lol

Are you apologising for helping me help someone out? :-)

This forum is far too polite :-D I like it

---

### Post by WaveMyBlackFlag on 2010-10-17
> **Hippytaff said:**
> Are you apologising for helping me help someone out? :-)

This forum is far too polite :-D I like it


haha, no I was busy telling Singletary to take Alex Smith out of the game and hit post by accident without finishing my thought, left the post incomplete but its fixed now. However, if I am stepping on your toes I'll chime out

---

### Post by Hippytaff on 2010-10-17
> **WaveMyBlackFlag said:**
> haha, no I was busy telling Singletary to take Alex Smith out of the game and hit post by accident without finishing my thought, left the post incomplete but its fixed now. However, if I am stepping on your toes I'll chime out

lol good God no...please feel free to step on these toes...the toes are for stepping on...plus I need your knowledge because mine is incomplete

---

### Post by baraka607 on 2010-10-17
> **WaveMyBlackFlag said:**
> whoops, hit post by accident, was yelling at alex smith... lol

I guess i got nothing else to add, just remember to mark it SOLVED if you  are satisfied with their help. Thanks and all the best:guitar:

---

### Post by Hippytaff on 2010-10-17
> **baraka607 said:**
> I guess i got nothing else to add, just  remember to mark it SOLVED if you  are satisfied with their help. Thanks  and all the best:guitar:

our help mr baraka...and also post back if you get troubles....and if you don't let us know how it went

---

### Post by baraka607 on 2010-10-17
> **kroni_hunter said:**
> I've got my media all on an external drive.  
When I startup with the cd loaded nothing happens.  There's a message that says Press DEL for Setup, Press 4 for ACC, and Press TAB for POST BIOS but thats it.  Is it one of those?

just hit DEL and choose to boot from cd first and the second should be your hard drive then the rest follows.:guitar:

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Windows aren't so friendly so they tend to write on everything else when installed. However when you install Windows you have some options on how to install Ubuntu. So if you are completely new to Ubuntu and you just want an experimenting period with it you can install it with wubi. It installs Ubuntu like a Windows program on a virtual drive and if you want to delete it later you can do it via Control Panel. Or you can install VBox or VMware and install Ubuntu there as a virtual machine. Then when you are sure you like Ubuntu you can always install it either dual booting with Windows or by itself. I'm suggesting this because there's Windows in the way so the installation/uninstallation process can turn hard.

---

