---
title: "Please help me recover photos?"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by svejkovat on 2011-06-24
Screenshot below.

Burned images with brasero onto dvd.   Stupidly I trashed the photos while the camera was plugged in before I checked the dvd.   I needed a photo so I installed the dvd but it was corrupted and unrecongnized.   Can't imagine what went wrong with the burn,  brasero said it was successful and ejected the media.   Any hints on how to force open the images on the dvd?

I plugged the camera back  into the usb and attempted to restore the trash.   I got both the camera window and the trash window to display all files.  When I tried to restore files in the trash window it said it was unable and suddenly reduced the photos to two.  Can't even restore those.   The files (though seemingly empty/gone) still appear in the camera memory,  

Can I do anything from this point?

---

### Post by goldshirt9 on 2011-06-24
if you access to a windows system , i have and achieved success with a free program called CONVAR
[http://www.pcinspector.de/SmartRecovery/info.htm?language=1](http://www.pcinspector.de/SmartRecovery/info.htm?language=1)

I dont know a program for Linux though.
any decent small chemist that prints photos should be able to recover the pictures

---

### Post by nomko on 2011-06-24
Did you overwrite the memory/memory disc of the camera? If not, then you can get most of the photo's back. Use a prgram called photorec: [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
Read this wiki. Remember this: If you overwritten the memeory disc of your camera, then some photo's can't be recovered.

---

### Post by svejkovat on 2011-06-24
Thank you.  I'll try the recovery software mentioned. 

I already tried  "CD Recovery Toolbox" which was recommended, but it does not even recognize the dvd in the drive.  What the heck did Brasero do to this disc?

Brasero has an option for "last project" that, frustratingly, is empty.  Did I have to manually save it with some option? 

I've never had a disc (that was not physically damaged) that simply did not register at all in a drive.

---

### Post by svejkovat on 2011-06-24
I had saved all of the photos in "shotwell" but now they only show up there under "missing files".   The thumbnail images  are all still there but I don't seem able to retrieve the photos.

Any suggestions with this option?

---

### Post by jerrrys on 2011-06-24
back to start...

first off you are looking at two different files.  the trash folder you clicked on is you system trash.  files/trash from your camera will not appear there when you delete pics from your camera.  camera trash files should be a hidden file in your camera.  **.trash**

looks like 400 pics in your camera.

and on a side note:  set your screenshot delay to one second to take a better pic.

---

### Post by svejkovat on 2011-06-24
Thanks.  I'll set the delay.   I tried photorec as suggested but it it's a command line program and I'm a wimp at that. 
I then plugged the camera into my windows laptop and downloaded some recovery "freeware" (listed as freeware, not shareware) from Tucows, installed it,  waited 10 minutes for it to recover files, clicked restore, only to be advised to purchase the program.  
Finally I found a program called Recuva which was truly freeware and did a very nice quick job of recovering what was in the camera.  
Is there a data recovery application I can install/enable in Ubuntu that has "gui for idiots" 

Oops...  I just reread the thread and entirely missed the CONVAR suggestion. Sorry goldshirt9. That might have saved me some grief. 

Below is a screenshot of Shotwell. (didn't set the delay again...dammit)    From an absolute beginners' perspective, shotwell is not terribly intuitive.  I 'uploaded' photos to shotwell earlier.  Apparantly I was only uploading thumbnail link images to the memory card on my camera, which worked as long as the cameral was plugged in.  It took so long to upload those images that I assumed the whole file was getting transferred.  When the images were trashcanned on the camera, shotwell still had thumbnail images but they led nowhere. Or at least this is what I gather from reading a couple of threads on the topic here.   Is this pretty much correct?

---

### Post by jerrrys on 2011-06-24
in nautilus go to view>show hidden files and then go to

1055CAM>.trash

got anything?

---

### Post by svejkovat on 2011-06-24
Please describe how to navigate that better?

I went to home > help as suggested in a search for "where is nautilus in ubuntu" but still could not find my bearings.

Nevermind..... nautilus just mean "home" basically... right?   Ok, I've located the 'hidden files' tab.  Bear with me a sec.


Later....
I went to "home" "view" "show hidden files" but did not see any folder labeled 1055CAM>.trash

I must be going to the wrong place?

---

### Post by jerrrys on 2011-06-24
[ATTACH]195895[/ATTACH]

then just click on your camera

[ATTACH]195896[/ATTACH]

and you should see a folder labeled **.trash**

---

### Post by toor58 on 2011-06-24
As already suggested : [http://blog.mypapit.net/2007/10/how-to-recover-photo-files-from-sd-card-mmc-with-photorec.html]("http://blog.mypapit.net/2007/10/how-to-recover-photo-files-from-sd-card-mmc-with-photorec.html")

I have recovered photos from an over written sd card in the past, but understand it may not find all of them.

---

