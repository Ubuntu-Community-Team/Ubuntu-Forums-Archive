---
title: "can not install lich king, how to &quot;unhide&quot;"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by Dontechjuan on 2008-12-28
i was trying to get World of Warcraft wrath of the lich king (wotlk) installed through wine. i had already installed the original WoW and the first expansion Burning Crusade and had been playing it for a couple of weeks. Now i have wotlk and every time i clicked the installer.exe or used the terminal /media/"lich king"/installer.exe both methods show this message "Installer data not found" I was told be someone on the forums that i need to get the tome files unhide so he said i have to mount the drive using the "unhide option". unfortuatly i have not been using ubuntu long and am almost completely terminal illiterate lol. so i have no idea how to do that. somwbody said to type this in

"sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/

Make sure you have unmounted the drive first with umount. then run this it should get ya going."

I tried entering it as its shown and i get this message "Mount: special device dev/cdrom does not exist" i checked the file and sure enough its not there, its in the media file with cdrom0 so i typed it in like this

"sudo mount -o ro,unhide,uid=1000,gid=1000 /media/cdrom /media/cdrom0/"

and it says this "mount: /media/cdrom0 is not a block device" I wonder if it matters that in the media folder with cdrom file and cdrom0 file is the file with the name "lich king" so i placed the name in the terminal command like

"sudo mount -o ro,unhide,uid=1000,gid=1000 /media/cdrom /media/"lich king"/"

I got this message "mount: mount point /media/lich king does not exist" yet i open the media file and there is a file named "lich king" so i have no idea what I'm doing wrong. So plz help me and remember that im terminal illiterate so plz lead me through step by step with "copy paste" terminal commands. thank you.

---

### Post by Dontechjuan on 2008-12-28
I got the tome files shown using the unhide option and the installer finally runs. I click install and it goes to the select language screen. ok select english and click ok and it goes to the End User agreement and it loads the window boarder and the agrre disagree buttons but the text is gone and it freezes up and I have to force quit it. Does anyone know how to fix this?

---

### Post by hyper_ch on 2008-12-29
I'd install it on windows and then just copy the whole thing over to linux

---

### Post by Dontechjuan on 2008-12-29
that might work except i don't have a second computer and my windows partition on this computer bit the dust a LONG time ago. i could never get windows to last longer than 3 or 4 months before a fatal system crash even though i would get the best virus scanners and firewalls.

---

### Post by hyper_ch on 2008-12-29
install it in vmware or virtualbox

---

### Post by shearn89 on 2008-12-29
to be slightly more helpful, have a look here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)
and see if the howto at the bottom of the page helps at all?

Also, apparently upgrading to wine 1.0.10 development version works too...

---

### Post by Dontechjuan on 2009-01-01
SUCCESS!! I finally figured it out. For those of you who are curious in how I got it working or anyone who has the same problem in the future I will go through the steps on how I got "Lich King" working.

1.Mounting the cd-rom drive with the "unhide" option. 

As stated above you must open the terminal and enter this line...
"sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom /media/cdrom0/"
However this did not work for me, because I do not have "/dev/cdrom". During one of the ubuntu updates it changed the folder name from cdrom to cdrom1 so i had to enter this line....
"sudo mount -o ro,unhide,uid=1000,gid=1000 /dev/cdrom1 /media/cdrom0/"
But it did not work either with or without the cd, i did get it working by opening the cd tray placing the cd in the tray entering the line on the terminal and when i did it pulled the tray in and it worked.

2.Copy the entire contents of the cd to a folder on your drive. 

I would suggest making a new folder on your desktop to copy the cd to. Do not copy it to the WoW folder.

3.Try running the "installer.exe" file.
If it works then great. If it freezes on the "End User Agreement" like it was doing on me then proceed to step 4.

4.Getting past the "End User Agreement"

As most of you know some games require you to go to the "configure wine" and add .dll files in the libraries tab. If you don't know where that is just click on "Applications" on the top left of your desktop on the toolbar, go down to "Wine", then "Configure Wine" and click on the "Libraries" tab. In this tab you can add .dll files and change their status to a couple of different options like, native, builtin, disable, ect. The problem that I was having was that a game I installed earlier required that I add the "mshtml.dll" and set it to "native". Having this .dll file added to the list was keeping the program from getting the data from online sources. I didn't know it when I was playing the original WoW and "The Burning Crusade" that when I started the game and the news page comes up that because of the mshtml.dll file it was not able to access the data for the news page. The same thing was happening to the "End User Agreement". So just write down on a piece of paper mshtml.dll(native), so that when you go to play the other game that requires it you'll be able to remember what to add to play the other game. And then remove the mshtml.dll from the list. Now open the "installer.exe" and it should work. If it does not then you may have another .dll file causing problems, so again start writing down all the .dll files you have added to your list and start removing them one by one and after each one try the installer. One should eventually work.

---

