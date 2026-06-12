---
title: "Cant get started"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by muzzaq on 2009-05-23
Hi I downloaded and burnt a CD , I checked it and it seems OK, have cd in when start, have gone to Phoenix BIOS Setup utility and put cd-rom/dvd  drive at top of list. But windows just keeps starting up, i get no menu or such?? 
It is a laptop Toshiba Satalite P30 80g hard drive split , so its c drive 40 d drive 40 , 1g processor , runs windows XP . 
Can anyone help please ?? :confused:

---

### Post by LinuxFox on 2009-05-23
How did you burn the CD?  Did you burn the Ubuntu ISO to CD or did you use an ISO burning program?  Just burning the ISO onto the CD probably won't do anything since it's seen as a file.

---

### Post by zeex on 2009-05-23
> **muzzaq said:**
> Hi I downloaded and burnt a CD , I checked it and it seems OK, have cd in when start, have gone to Phoenix BIOS Setup utility and put cd-rom/dvd  drive at top of list. But windows just keeps starting up, i get no menu or such?? 
It is a laptop Toshiba Satalite P30 80g hard drive split , so its c drive 40 d drive 40 , 1g processor , runs windows XP . 
Can anyone help please ?? :confused:

Hi, 

Seems like something wrong with the CD. Did you burn the iso as image or data. These are two very different option. Seems like you made the CD as data CD. It won't boot as data CD. Try burning iso as image. If you are using Nero on windows, it has an option "Burn image" select that -> select ISO -> Burn

Good luck :)

---

### Post by muzzaq on 2009-05-23
Thanks will try your advice

---

### Post by muzzaq on 2009-05-23
it says it is an iso image file , the device or program is Record Now which is only basic, it does not seem to have a Burn as image

---

### Post by crew51m on 2009-05-23
Did you use an iso burnng program? You cant just copy an iso from a regular burning program such as real or windows media. An iso program copies the proper files to load and make a bootable disc.

---

### Post by muzzaq on 2009-05-23
> **crew51m said:**
> Did you use an iso burnng program? You cant just copy an iso from a regular burning program such as real or windows media. An iso program copies the proper files to load and make a bootable disc.

Im sorry but I dont know if the program is iso burning or not, i think not as in its menu it says audio cds, data disc and exact copy, ?  Is there a free program that I can get to do this ?

---

### Post by zhhansen on 2009-05-23
I have the best results with infra-recorder ([http://infrarecorder.org/](http://infrarecorder.org/))

From [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)


[LIST=1]
[*]Download and install [Infra Recorder]("http://infrarecorder.sourceforge.net/"), a free and open source image burning program. 
[*]Insert a blank CD in the drive and select **Do nothing** or **Cancel** if an autorun dialog pops up. 
[*]Open Infra Recorder and click the 'Write Image' button in the main screen. 
[LIST]
[*]Alternatively you can select the 'Actions' menu, then 'Burn image'. 
[/LIST]
[*]Select the Ubuntu CD image file you want to use, then click 'Open'. 
[*]In the dialog, click 'OK'.
[/LIST]
That should work, the problem was probably that what you used to burn the iso didn't write the image, just placed the file on the CD.

Good Luck,
zhhansen

---

### Post by muzzaq on 2009-05-23
Thank you for your help ... I will go down that track tomorrow as its late in oz now
  Have a good day

---

### Post by LinuxFox on 2009-05-23
> **muzzaq said:**
> Im sorry but I dont know if the program is iso burning or not, i think not as in its menu it says audio cds, data disc and exact copy, ?  Is there a free program that I can get to do this ?A data disc just means it was burned as a file, similar to burning a downloaded file or a document to a CD.

ISO burning burns the image as a disc.  Usually after burning it the CD will load up like a real software disc, instead of a CD with one file.  When I got Ubuntu, I used [ISO Recorder]("http://isorecorder.alexfeinman.com/isorecorder.htm").

To know if it's successful, try loading Ubuntu's CD in Windows.  If an autorun screen comes up, you should be good to go (this is for the Wubi installer). Just restart and try it out as a Live CD to make sure it's working ok.  From the menu, you could even check for defects.

---

### Post by muzzaq on 2009-05-23
Thank you  LinuxFox I will try all this tomorrow, just gettin a wee tired

---

### Post by sgosnell on 2009-05-23
I like [ImgBurn](http://www.imgburn.com). It's free, and it does a good job of burning .iso images to CD.

---

### Post by muzzaq on 2009-05-24
Hi Ubuntu community a big thanks for your help it was a burning of CD issue,I downloaded Infra Recorder, reburnt CD,  I am now up and running and am blown away by this program...... goodbye windows

Again Thanks to all

---

