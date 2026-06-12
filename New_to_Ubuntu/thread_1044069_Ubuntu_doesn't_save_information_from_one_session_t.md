---
title: "Ubuntu doesn't save information from one session to the next"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by wisefaiz on 2009-01-19
Hello!

I'm running ubuntu, in windows, on a toshiba m40x. It's been installed for about a week now and ive been alternating between windows and ubuntu to see how it performs - I love it!

Here's a question: 
Why does my ubuntu not save the changes I make, updates I download and things I put on the desktop when I turn the computer off or switch back to windows? Also, when ubuntu starts it always trys to do a proper install (currently I've installed on wubi). I have to cancell the installer before the workspace loads up. 

If you need more information, tell me where to get it and ill post it!

Many thanks,

wisefaiz

---

### Post by Bölvaður on 2009-01-19
Do you have the live cd in the cd rom when you boot your computer into ububtu?

---

### Post by wisefaiz on 2009-01-19
Nope, I've installed using wubi and click on the 'ubuntu' option in the boot menu with nothing in my cd drive.

---

### Post by samhub1982 on 2009-01-19
I had my computer up to simply dual boot vista and unbuntu... same thing happened to me. It wouldn't save any settings... to include my graphics card setting. I couldn't get sound to work either. I eventually gave up and deleted that partition. I am holding on to the CD while I do more research into how I can get it up and running completely where it saves all my settings, plays sound, and will run ventrilo and world of warcraft. If anyone has any insight and can help me get to that the help would be GREATLY appreciated. I HATE Vista.

---

### Post by wisefaiz on 2009-01-19
Hahaha! You're holding out for World of Warcraft and I'm not gonna switch till I know Birth of the Federation will work! Lord help me, I need that game. Let me know if you find anything samhub1982 and i'll do the same for you.

---

### Post by Bölvaður on 2009-01-19
I have no idea what is wrong. On a normal (not wubi) install everything you do is saved to the harddisk.
Try do some simple tests like make an empty file or have a picture or something in a folder. Like /home/username/myfile.txt
and see if it remains there after a reboot, if not there is something very... waiiitt... I think I know what is happening.

May it be because you havent installed ubuntu 100%. Could it be that Wubi installs the iso onto a second partition where the iso is run from the hdd. It could be similar to running live cd where the os is running on RAM, and writes all the changes to RAM. Which in turn makes all your changes and installations evaporate on restart.
Try not to stop the installation process....

---

