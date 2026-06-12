---
title: "Why I am getting so very frustrated with Linux"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by djenge on 2009-04-06
I've spent too many hours trying unsuccessfully to burn a Video DVD.  These are the avenues I've gone, and the problems I've run into.  It was always so easy on Windows with DVD Shrink.

K9Copy:
     Rips the disk just fine into Video_TS and Audio_TS folders, but will not create an .iso file or write with K3B like I tell it to.  The searching I found with this error just lead to more people with the same problem and no solutions that worked.

DVD Shrink through wine
     Never worked for me, just got errors

ManDVD
     I tried to add multiple .avi files to a project and make a menu to create a DVD (like it's supposed to do).  The first error I got was a sound issue in the menu, which I found a workaround for by creating a silent MP3 to insert as the menu background music.  After that there are 3 options to make a DVD:
    - Burn DVD:  Says Burn successful, but it didn't do anything.  In   the console, the error says it :-( unable to open64("/dev/dvd0",O_RDONLY): No such file or directory.  I tried changing the drive location to several things, with no luck.  (/dev/dvd0, /dev/dvd1, /dev/dvd, /dev/scd0, etc)
    - Burn with K3b:  Opens the project in K3b, but shows the project file size as 148Kb, and burns it that way with none of the videos making it in the DVD, just the menu and 148 Kb of the very first video file.  ManDVD correctly says the project size is a couple gigs
     - Create an ISO Image:  "Error encountered during ISO creation"  message.  Here's what the console says: 
genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
genisoimage: Can't open VMG info for '/home/djenge/Videos//DVD/'.
genisoimage: Unable to parse DVD-Video structures.
genisoimage: Could not find correct 'VIDEO_TS' directory.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

Brasero:  After creating a new Video DVD project with all of my files inserted, I click burn, which opens a new dialog where everything looks right, but the "burn" button is greyed out and can't be clicked.  Searching for this error also just left me with lots of others with the same problem and no solutions.  


Can anyone help me get at least one of these options to work.  There's two tasks I would like to be able to do.  1.  Backup a DVD (like DVDShrink) and 2.  Compile a DVD from several videos.  They have to work in a normal DVD player.  I would sure appreciate some advice here.

---

### Post by SuperSonic4 on 2009-04-06
1. k9copy works ok for me. did you make sure it says "ISO Image" under output device? If so then you should press the copy button at the top and it will make an ISO of the whole disc although it might only do a single layer. Selecting all will be necessary too of course.

2. DeVeDe works the best for me, it creates an ISO file to be burnt to disc although you can also test the ISOs in VLC

---

### Post by robert shearer on 2009-04-06
This guide for k9copy should get it working for you.

[http://www.dvd-guides.com/content/view/213/59/](http://www.dvd-guides.com/content/view/213/59/)

---

### Post by Mulenmar on 2009-04-06
Sounds like it's time to file some bug reports...

I think I use AcidRip, or somesuch named program, and it worked in ripping to .avi, but I never tried to write to another disc.

---

### Post by lhb1142 on 2009-04-06
:KS  Why not do what I do?

Just use k9copy to create your copy files in the folder of your choice. (I have k9copy install to the otherwise unused "dwhelper" folder so I know where the resultant files will be. k9copy creates a subfolder entitled 'dvd' which contains the AUDIO_TS and VIDEO_TS folders.)

Then insert a blank DVD into your drive.

You should then be able to open "CD/DVD Creator." (If you have it set to do so, as I do, "CD/DVD Creator" opens automatically upon my insertion of a blank DVD.)

Copy the AUDIO_TS and VIDEO_TS folders to "CD/DVD Creator" and then click on "Write to Disk."

You can adjust the burning speed (I always use the slowest one) and you can even name your DVD disk.

This is quite simple and works perfectly. (I do not like "Brasero" at all and I no longer even try it.)

By the way, using an Acer Extensa laptop, I have not had any problems at all using DVDShrink under Wine, though, with the latest version of k9copy, I do not need to use it. In my opinion k9copy is a complete and excellent program (it is easy and straightforward to configure) and the Ubuntu default "CD/DVD Creator" is likewise excellent and very easy to use.

By the way, I do NOT use "CD/DVD Creator" to burn CDs; rather, I use "k3b."

I hope you have success in this endeavor. ):P

---

### Post by lhb1142 on 2009-04-06
:KS  I should like to mention a small "bug" in the use of "CD/DVD Creator."

After burning is complete, you definitely want to delete the AUDIO_TS and VIDEO_TS folders within "CD/DVD Creator" and then close the program. (If the disk comes out perfectly and you have verified this by watching it, you can then safely delete the "dvd" folder in "dwhelper" or the folder you have chosen.)

You will see that your DVD has been ejected, but, on the Desktop, the icon for "Blank DVD" is still present.

You should remove the burned DVD and then you must physically close the EMPTY CD/DVD drawer, right-click on the "Blank DVD" icon, and then choose the "Eject" option. This will reopen the (empty) CD/DVD tray and the "Blank DVD" icon will then disappear.

It's a silly "bug" and I don't know why it has not been corrected but it is minor - more annoying than harmful. I'm used to it! ):P

---

### Post by sneeks on 2009-04-06
> **djenge said:**
> I've spent too many hours trying unsuccessfully to burn a Video DVD.  These are the avenues I've gone, and the problems I've run into.  It was always so easy on Windows with DVD Shrink.

K9Copy:
     Rips the disk just fine into Video_TS and Audio_TS folders, but will not create an .iso file or write with K3B like I tell it to.  The searching I found with this error just lead to more people with the same problem and no solutions that worked.

DVD Shrink through wine
     Never worked for me, just got errors

ManDVD
     I tried to add multiple .avi files to a project and make a menu to create a DVD (like it's supposed to do).  The first error I got was a sound issue in the menu, which I found a workaround for by creating a silent MP3 to insert as the menu background music.  After that there are 3 options to make a DVD:
    - Burn DVD:  Says Burn successful, but it didn't do anything.  In   the console, the error says it :-( unable to open64("/dev/dvd0",O_RDONLY): No such file or directory.  I tried changing the drive location to several things, with no luck.  (/dev/dvd0, /dev/dvd1, /dev/dvd, /dev/scd0, etc)
    - Burn with K3b:  Opens the project in K3b, but shows the project file size as 148Kb, and burns it that way with none of the videos making it in the DVD, just the menu and 148 Kb of the very first video file.  ManDVD correctly says the project size is a couple gigs
     - Create an ISO Image:  "Error encountered during ISO creation"  message.  Here's what the console says: 
genisoimage: No such file or directory. Failed to open VIDEO_TS.IFO
genisoimage: Can't open VMG info for '/home/djenge/Videos//DVD/'.
genisoimage: Unable to parse DVD-Video structures.
genisoimage: Could not find correct 'VIDEO_TS' directory.
genisoimage: Unable to make a DVD-Video image.
Possible reasons:
  - VIDEO_TS subdirectory was not found on specified location
  - VIDEO_TS has invalid contents

Brasero:  After creating a new Video DVD project with all of my files inserted, I click burn, which opens a new dialog where everything looks right, but the "burn" button is greyed out and can't be clicked.  Searching for this error also just left me with lots of others with the same problem and no solutions.  


Can anyone help me get at least one of these options to work.  There's two tasks I would like to be able to do.  1.  Backup a DVD (like DVDShrink) and 2.  Compile a DVD from several videos.  They have to work in a normal DVD player.  I would sure appreciate some advice here.

make sure the target is iso file in k9copy and all should be fine,just remember where you put it,videos is a good one,then just burn with k3b

---

### Post by albinootje on 2009-04-06
> **lhb1142 said:**
> :KS  I should like to mention a small "bug" in the use of "CD/DVD Creator."

You can find out whether this bug was already reported at [http://launchpad.net/](http://launchpad.net/) If not, please file a bug-report.

---

### Post by sandyd on 2009-04-06
+1 for devedee, that thing works like a charm

p.s. : theirs a thing called neroforlinux (search on google if you must) and it... well as its name says, runs nero on linux :)

---

### Post by anjilslaire on 2009-04-06
> **djenge said:**
> IDVD Shrink through wine
     Never worked for me, just got errors

I use DVDShrink nearly every day under Linux, you need to just set it correctly in Wine. My settings are as follows:

Windows Version: XP
Libraries: quartz.dll (native/builtin)

That should work. Be sure to insert the dvd and mount it (open the disc contents) **before** launching DVDShrink, or it wil likely not recognize the disc.

This has worked flawlessly for years for me. I just prefer it to K9copy, as I've used it for years prior to moving to Linux, and it still works on most discs.

I use acidrip as well for converting to xvid after ripping the disc.

---

### Post by servicetech on 2009-04-06
Ubuntu 9.04 has a K9copy assistant that has worked well for me, not sure if you can get it for older versions.

---

### Post by djenge on 2009-04-09
OK cool, thanks for all the replies.  I got both tasks I needed to work.  DeVeDe worked well for compiling a new DVD to make an .iso file.  That worked great.  And for some reason, k9copy suddenly started working when I changed a couple settings.  I changed the output size to 4400MB (from 4600) and checked "Quick Scan."  Everything else was the same, and now it works, so I'm happy.  
I burned the .iso's with Brasero, which worked fine.  K3b was being dumb.  It kept saying that the .iso file was too large for the empty DVD.  It's a standard 4.7G disc and the files were 3.9 and 4.4G.  Haven't figured that out yet.  
The DVD Shrink advice also worked for me.  I wasn't opening the disk beforehand nor did I have quartz.dll library added.

---

### Post by crjackson on 2009-04-09
> **djenge said:**
> OK cool, thanks for all the replies.  I got both tasks I needed to work.  DeVeDe worked well for compiling a new DVD to make an .iso file.  That worked great.  And for some reason, k9copy suddenly started working when I changed a couple settings.  I changed the output size to 4400MB (from 4600) and checked "Quick Scan."  Everything else was the same, and now it works, so I'm happy.  
I burned the .iso's with Brasero, which worked fine.  K3b was being dumb.  It kept saying that the .iso file was too large for the empty DVD.  It's a standard 4.7G disc and the files were 3.9 and 4.4G.  Haven't figured that out yet.  
The DVD Shrink advice also worked for me.  I wasn't opening the disk beforehand nor did I have quartz.dll library added.

Diferent programs calculate disc size differently. I suggest you drop your setting from 4400MB to 4300 and give it a go. MANY programs default to 4300 under Linux and Win.

---

### Post by GuiGuy on 2009-04-18
> **carlee said:**
> +1 for devedee, that thing works like a charm

p.s. : theirs a thing called neroforlinux (search on google if you must) and it... well as its name says, runs nero on linux :)

Do you mean Nero for Linux? I bought it. Got sick and tired of the flakiness of what was available on linux. It doesn't cost much and works a treat.

---

### Post by 3rdalbum on 2009-04-18
The version of K9Copy in Ubuntu 8.10 has a dumb bug in it when you want to create an ISO file: it fails if there are spaces in the filename. If you don't use spaces in the filename, you'll be fine; alternatively you can unpack the Jaunty .deb and manually drag the file from it into the appropriate directories - it works fine.

---

### Post by TAspr on 2011-06-04
> **lhb1142 said:**
> :KS  Why not do what I do?

Just use k9copy to create your copy files in the folder of your choice. (I have k9copy install to the otherwise unused "dwhelper" folder so I know where the resultant files will be. k9copy creates a subfolder entitled 'dvd' which contains the AUDIO_TS and VIDEO_TS folders.)

Then insert a blank DVD into your drive.

You should then be able to open "CD/DVD Creator." (If you have it set to do so, as I do, "CD/DVD Creator" opens automatically upon my insertion of a blank DVD.)

Copy the AUDIO_TS and VIDEO_TS folders to "CD/DVD Creator" and then click on "Write to Disk."

You can adjust the burning speed (I always use the slowest one) and you can even name your DVD disk.

This is quite simple and works perfectly. (I do not like "Brasero" at all and I no longer even try it.)

By the way, using an Acer Extensa laptop, I have not had any problems at all using DVDShrink under Wine, though, with the latest version of k9copy, I do not need to use it. In my opinion k9copy is a complete and excellent program (it is easy and straightforward to configure) and the Ubuntu default "CD/DVD Creator" is likewise excellent and very easy to use.

By the way, I do NOT use "CD/DVD Creator" to burn CDs; rather, I use "k3b."

I hope you have success in this endeavor. ):P


Why do I get these errors with my system no matter if I output the files to a DVD or a folder??

(See pcitures below)

---

### Post by lhb1142 on 2011-06-05
> **TAspr said:**
> Why do I get these errors with my system no matter if I output the files to a DVD or a folder??

(See pcitures below)

I don't know about the second thumbnail, but in the first one, it appears that you are trying to output to the same location as the input. You can't do that. You'll have to change the output to something else. (And if you are using an external CD drive, you'll have to change the input from SR0 to SR1.)

Hope this helps.

---

### Post by dmizer on 2011-06-05
> **TAspr said:**
> Why do I get these errors with my system no matter if I output the files to a DVD or a folder??

(See pcitures below)

Please start a new thread about this problem. This thread is over 2 years old and includes advice that is out of date. You'll be better off simply starting your own thread.

Thank you.

---

