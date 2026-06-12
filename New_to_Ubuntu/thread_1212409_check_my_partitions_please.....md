---
title: "check my partitions please...."
date: 2009-07-13
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-13
i did a re-install and think i might have blew it again... i was trying to install a 5gb swap a 20 gig / a 140 gig /home and the rest in empty space...

to me it looks like i blew it...

any comments ???

thanks...

sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc0fdc0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433       26747   195310237+  83  Linux
/dev/sda3           26748       27355     4883760   82  Linux swap / Solaris

---

### Post by 73ckn797 on 2009-07-13
Where did Windows go? It is not showing in the info you list. From your other post I thought you were going to install as a dual boot.

---

### Post by Crafty Kisses on 2009-07-13
What are the results of?
```
sudo fdisk -lu
```

---

### Post by bodhi.zazen on 2009-07-13
From what you posted it appears you have two partitions, one swap and the other /

Does not sound like what you wanted.

---

### Post by NOTAGEEK on 2009-07-13
> **Codename said:**
> What are the results of?
```
sudo fdisk -lu
```



Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdc0fdc0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39070079    19535008+  83  Linux
/dev/sda2        39070080   429690554   195310237+  83  Linux
/dev/sda3       429690555   439458074     4883760   82  Linux swap / Solaris

---

### Post by lindsay7 on 2009-07-13
Run Gparted and take a look at what it shows. Take a screen shot and post it if you want some help partitioning your drive.

---

### Post by NOTAGEEK on 2009-07-13
> **bodhi.zazen said:**
> From what you posted it appears you have two partitions, one swap and the other /

Does not sound like what you wanted.



i was trying to get approx 140 gig /home, approx 20 gig /, approx 5 gig swap, and the rest in free space... am i even close ???

i am not even a novice with pc's/9.04 yet but working on it...

thanks...

---

### Post by raymondh on 2009-07-13
> **lindsay7 said:**
> Run Gparted and take a look at what it shows. Take a screen shot and post it if you want some help partitioning your drive.

+1 .... this will help visualize

---

### Post by lindsay7 on 2009-07-13
Close but I can not tell for sure how much space you have,  run gparted and it will show you. Also you can look at Systme/Administration/system monitor, look at the file systems tab.

---

### Post by LewRockwell on 2009-07-13
It's so confusing when you continually start new threads dealing with the same equipment, the same software, and the same problems...

Why can't it all be in the same thread?

It's crazy that everyone reading and responding to your threads has to go to your profile and chase down all your previous threads and posts where important information and past advice has been established...

Thanks!

.

---

### Post by NOTAGEEK on 2009-07-13
> **raymondhenson said:**
> +1 .... this will help visualize

i would like to but i have looked for gparted and cant find it amywhere...

i have lots of trouble visualizing something i cant find...

guess i better come back when i get more know how huh ???

---

### Post by lindsay7 on 2009-07-13
Look under system/administration/partition editor. If it is not there get it from the add/remove programs under application on the menu bar.

---

### Post by LewRockwell on 2009-07-13
> **NOTAGEEK said:**
> i would like to but i have looked for gparted and cant find it amywhere...

i have lots of trouble visualizing something i cant find...

guess i better come back when i get more know how huh ???

The GUI way:

System > Administration > Partition Editor


The CLI way:```
gksudo gparted
```

.

---

### Post by NOTAGEEK on 2009-07-13
> **LewRockwell said:**
> It's so confusing when you continually start new threads dealing with the same equipment, the same software, and the same problems...

Why can't it all be in the same thread?

It's crazy that everyone reading and responding to your threads has to go to your profile and chase down all your previous threads and posts where important information and past advice has been established...

Thanks!

.


rather than confuse the issue i tagged the other solved like you suggest...

i could have been away from the forum if you helped me instead of post just to criticize... 

nevermind lew ok ???

---

### Post by LewRockwell on 2009-07-13
> **lindsay7 said:**
> Look under system/administration/partition editor. If it is not there get it from the add/remove programs under application on the menu bar.

yes, it is not normally included in the default administration menu(sorry)

so you can add it to the main menu by going to:

System > Preferences > Main Menu

then you'll select "Administration" under "menus" and then put a check mark on "Partition Editor" then select "close" (NOT revert!) so that it shows up in the GUI menu

.

---

### Post by LewRockwell on 2009-07-13
> **NOTAGEEK said:**
> rather than confuse the issue i tagged the other solved like you suggest...

i could have been away from the forum if you helped me instead of post just to criticize... 

nevermind lew ok ???

no, it's not ok to continually start new threads when your issues are all related

as I said before, it's important to keep all the history together and not fragment it all over the place

people in this thread are giving you the SAME commands they gave you in your previous EIGHTEEN threads

([http://ubuntuforums.org/search.php?searchid=61706522](http://ubuntuforums.org/search.php?searchid=61706522))

NINETEEN THREADS...

.

---

### Post by NOTAGEEK on 2009-07-13
> **LewRockwell said:**
> yes, it is not normally included in the default administration menu(sorry)

so you can add it to the main menu by going to:

System > Preferences > Main Menu

then you'll select "Administration" under "menus" and then put a check mark on "Partition Editor" then select "close" (NOT revert!) so that it shows up in the GUI menu

.


everything works up to "partition editor" as it is not on that list...

thanks...

---

### Post by LewRockwell on 2009-07-13
> **NOTAGEEK said:**
> everything works up to "partition editor" as it is not on that list...

thanks...

```
sudo apt-get gparted
```

---

### Post by lindsay7 on 2009-07-13
see these


[ATTACH]121009[/ATTACH]

[ATTACH]121010[/ATTACH]

---

### Post by NOTAGEEK on 2009-07-13
> **LewRockwell said:**
> ```
sudo apt-get gparted
```


E: Invalid operation gparted




> **lindsay7 said:**
> see these


[ATTACH]121009[/ATTACH]

[ATTACH]121010[/ATTACH]


i have very poor eyesight --- it looks kike in your screenshot that it starts with kre or kde... ctrl + does not help as i am see ing blurrrr...  i have been looking for gparted and partition editor...

i am likely missing something again

---

### Post by bodhi.zazen on 2009-07-13
you forgot the *install*

```
sudo apt-get install gparted
```

IMO partitions are best managed from a live CD, and gparted is on the live CD. It is not installed by default.

---

### Post by LewRockwell on 2009-07-13
> **bodhi.zazen said:**
> you forgot the *install*

```
sudo apt-get install gparted
```

IMO partitions are best managed from a live CD, and gparted is on the live CD. It is not installed by default.

yep, forgot

tx

.

---

### Post by NOTAGEEK on 2009-07-13
> **bodhi.zazen said:**
> you forgot the *install*

```
sudo apt-get install gparted
```IMO partitions are best managed from a live CD, and gparted is on the live CD. It is not installed by default.

thanks very much i now have gparted installed... i dont know how to do a screenshot but what i saw looked ok to me... could i be right ??? i dont know but it looked ok...

thanks...

---

### Post by LewRockwell on 2009-07-13
> **NOTAGEEK said:**
> thanks very much i now have gparted installed... i dont know how to do a screenshot but what i saw looked ok to me... could i be right ??? i dont know but it looked ok...

thanks...

Applications > Accessories > "Take Screenshot"

and you can experiment with it from there

.

---

### Post by NOTAGEEK on 2009-07-13
> **LewRockwell said:**
> Applications > Accessories > "Take Screenshot"

and you can experiment with it from there

.
thanks i got that part figured out and am trying to figure out how to post it here... i have been messing around with the paper clip to attach but dont have it figured out how yet...

---

### Post by bodhi.zazen on 2009-07-13
Post it somewhere else (photobucket) and link back.

[noparse][[img]http://thumb_nail[/img]](http://large_picture)[/noparse]

---

### Post by LewRockwell on 2009-07-13
here's a screenshot that shows my partition editor and also I wanted to note that I have placed icons on the top menu bar...from left to right it's "terminal" "screenshot" "calculator" "text editor" "thunderbird" "firefox"

(arrow is pointing to "screenshot")

now you're looking at that via a 42 inch screen but the original screen display is on an 8.9 inch netbook screen...

.

---

### Post by NOTAGEEK on 2009-07-13
> **NOTAGEEK said:**
> thanks i got that part figured out and am trying to figure out how to post it here... i have been messing around with the paper clip to attach but dont have it figured out how yet...



When you take a screenshot, the Save Screenshot dialog 
  opens. To save the screenshot as an image file, enter the filename for the 
  screenshot, choose a location from the drop-down list and click the Save button. You can also use the Copy to Clipboard button to copy the image to the clipboard or transfer it to another application by drag-and-drop.
  

**when i take a screenshot the save screenshot box does not open...**

---

### Post by LewRockwell on 2009-07-13
> **NOTAGEEK said:**
> thanks i got that part figured out and am trying to figure out how to post it here... i have been messing around with the paper clip to attach but dont have it figured out how yet...

when you quote and/or reply you can scroll down on that particular screen and you will see "Additional Options" in red and under that as you scroll down you will see "Attach Files" and under that will be bold text saying "Manage Attachments" and those words are actually a link to an upload page so you can browse to your photo/file/etc. and upload it as an attachment to go with your post

you'll figure it out!

.

---

### Post by NOTAGEEK on 2009-07-13
> **LewRockwell said:**
> here's a screenshot that shows my partition editor and also I wanted to note that I have placed icons on the top menu bar...from left to right it's "terminal" "screenshot" "calculator" "text editor" "thunderbird" "firefox"

(arrow is pointing to "screenshot")

now you're looking at that via a 42 inch screen but the original screen display is on an 8.9 inch netbook screen...

.


and when i click it to view it it comes up real clear... mine is nowhere as involved...

---

### Post by LewRockwell on 2009-07-13
> **NOTAGEEK said:**
> When you take a screenshot, the Save Screenshot dialog 
  opens. To save the screenshot as an image file, enter the filename for the 
  screenshot, choose a location from the drop-down list and click the Save button. You can also use the Copy to Clipboard button to copy the image to the clipboard or transfer it to another application by drag-and-drop.
  

**when i take a screenshot the save screenshot box does not open...**

are you sure it's not hiding behind anything?

you might have to reduce all your other windows and just play around with that function til you figure it out

.

---

### Post by Bartender on 2009-07-13
Someone mentioned gparted LiveCD earlier.
I can't stress enough that this is what you need to do.  Trying to partition with the built-in GParted will NOT work as well as running GParted from a LiveCD.
Assuming you have a standard i-386-based PC, you want to download the latest stable version
[http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)
See gparted-live-0.4.5-3.iso?  That's the one you want.  You can download and burn this on any Windows PC with a broadband connection.  As long as you understand how to burn an .iso, that is.
Once you've burned it correctly, boot from the CD.  That might mean you have to go into your BIOS and tell it to boot from the optical drive.  You'll know whether you have to or not - drop the CD in the optical drive and restart the PC.  If it doesn't start up GParted then you 'll have to change the BIOS Boot Options.
GParted LiveCD is the way to go to set up your partitions first, then install Ubuntu manually.
There's only one drawback to using the GP LiveCD inyour case - it's more difficult to take a screenshot from the CD than it is from GParted inside Ubuntu.

---

### Post by NOTAGEEK on 2009-07-13
> **lewrockwell said:**
> when you quote and/or reply you can scroll down on that particular screen and you will see "additional options" in red and under that as you scroll down you will see "attach files" and under that will be bold text saying "manage attachments" and those words are actually a link to an upload page so you can browse to your photo/file/etc. And upload it as an attachment to go with your post

you'll figure it out!

.

> **notageek said:**
> when you take a screenshot, the save screenshot dialog 
  opens. To save the screenshot as an image file, enter the filename for the 
  screenshot, choose a location from the drop-down list and click the save button. You can also use the copy to clipboard button to copy the image to the clipboard or transfer it to another application by drag-and-drop.
  

**when i take a screenshot the save screenshot box does not open...**



[attach]121014[/attach]

---

### Post by LewRockwell on 2009-07-13
> **Bartender said:**
> Someone mentioned gparted LiveCD earlier.
I can't stress enough that this is what you need to do.  Trying to partition with the built-in GParted will NOT work as well as running GParted from a LiveCD.
Assuming you have a standard i-386-based PC, you want to download the latest stable version
[http://sourceforge.net/projects/gparted/files/](http://sourceforge.net/projects/gparted/files/)
See gparted-live-0.4.5-3.iso?  That's the one you want.  You can download and burn this on any Windows PC with a broadband connection.  As long as you understand how to burn an .iso, that is.
Once you've burned it correctly, boot from the CD.  That might mean you have to go into your BIOS and tell it to boot from the optical drive.  You'll know whether you have to or not - drop the CD in the optical drive and restart the PC.  If it doesn't start up GParted then you 'll have to change the BIOS Boot Options.
GParted LiveCD is the way to go to set up your partitions first, then install Ubuntu manually.
There's only one drawback to using the GP LiveCD inyour case - it's more difficult to take a screenshot from the CD than it is from GParted inside Ubuntu.

of course they can just LiveCD gparted with their UBUNTU disk...that they obviously already have...lol.

and gparted is included in Puppy Linux and Parted Magic to name just a few...

.

---

### Post by LewRockwell on 2009-07-13
> **NOTAGEEK said:**
> [attach]121014[/attach]

there you go!

it looks like it did what you told it to do...

.

---

### Post by NOTAGEEK on 2009-07-13
> **LewRockwell said:**
> there you go!

it looks like it did what you told it to do...

.


i am almost as impressed as you seem to be...

now can i get the ok to tag this thread solved as i need to start thread #20  ???

just kidding...

thanks...:guitar:

---

### Post by raymondh on 2009-07-13
> **NOTAGEEK said:**
> i am almost as impressed as you seem to be...

now can i get the ok to tag this thread solved as i need to start thread #20  ???

just kidding...

thanks...:guitar:

To put a solved tag ... go to your first post > edit > advanced > type SOLVED in front of your thread title > save.

Congratulations and Happy Ubuntu-ing =D>

---

