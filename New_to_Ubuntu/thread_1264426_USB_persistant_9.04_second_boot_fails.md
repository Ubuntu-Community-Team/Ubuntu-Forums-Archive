---
title: "USB persistant 9.04 second boot fails"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by GCDB on 2009-09-12
Hello,
I have followed this guide [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/) to install 9.04 on a 8gb usb stick with the 4gb casper file for persistant, which boots the live 9.04 first time ok.
When shutting down i get errors which happen fast so i can not read them. Then on reboot,the usb stick is not recognised and the internal drive is just booted up,which is xpe. The usb stick then shows up as a cd drive in xpe which when i click on says insert disk. If i remove the usb stick in xpe, then re-insert it, it shows up as bootable again and then i can access the files from xpe. If i reboot after this, it boots up again from the usb ok?
I have created a file on the desktop in 9.04 and this shows up so persistant changes seem to be working. 
Is there a quick fix so that the usb stick will be re-booted every time?
By the way i am using a thin client hp t5720 with xpe on.
I have also waited the full 60 seconds which one post recommends on shutdown so that time is allowed to save to the usb stick.
Thanks
Gav

---

### Post by LewRockwell on 2009-09-12
maybe you should try waiting longer than 60 seconds?

.

---

### Post by GCDB on 2009-09-12
Well thanks Lew....
for the bump anyway.
Seriously, any help on this would be greatly appreciated.
Ta
Gav

---

### Post by LewRockwell on 2009-09-12
> **GCDB said:**
> Well thanks Lew....
for the bump anyway.
Seriously, any help on this would be greatly appreciated.
Ta
Gav

seriously...

what happened when you waited longer than 60 seconds?

what was the longest time period of this experimentation?

.

---

### Post by GCDB on 2009-09-12
Hi,
the system shuts down with the same errors and wont re-boot from the usb stick again,
caught a bit of the error,
'end request I/O error' but screen full of them for a second.
So really the system still shuts down but it is when i re-boot, it wont re-boot from the usb stick and i think it is to do with the I/O errors ?
Does that make sense?
ta gav

---

### Post by GeorgeVita on 2009-09-12
Hi **GCDB**, reading your 1st post I started some tests resulting to the following notes, hoping will give you some ideas and help you find a solution.

- at 9.04 the USB startup disk creator CANNOT  make the persistent file. Your link suggests/provide a preformated 'casper-rw' file.

- using the 9.10 version of USB startup disk creator (9.10 is still in development) you can make a persistent file up to 4GB (tested and failed with a 6GB, succeeded with 4GB). Final LiveUSB +persistend are OK as updates done/stored, rebooted, connected and 'now posting'.

- you can use any live .iso for the creation of USB startup disk (9.04, 8.10 or even a [daily-live]("http://cdimage.ubuntu.com/daily-live/") to test 9.10)

- note that creation of the persistent file takes some time (for my 4GB was 20 minutes).

Although I am not sure if your 'real problem' was the preformated 'casper-rw' file or other h/w reason, I am listing my actions to make the working persistent LiveUSB stick:

- Backup previous data from the 'target USB stick'
- Get an 9.10 .iso, make a LiveCD, boot 9.10, attach 'target USB stick', wait for the icon to appear.
- right click 'target USB stick' icon and select 'Format'
- follow instructions and format it to 'Fat' (default), place an informative 'name'
- after finishing, close any 'file manager' appeared
- from System > Administration > USB startup disk creator
- point to the 'target .iso file'
- point to the 'target USB stick'
- adjust persistent file UP TO 4GB
- start procedure and wait ... (larger file = more time)
- finally press 'quit'
- REMOVE 'target USB stick', shut down and TRY it!

Above tested on EeePC 1000H with an 8GB Transcend JetFlash V30, with 9.04 and 9.10 .iso files.

Regards,
George

---

### Post by GCDB on 2009-09-13
Thanks George,
I will try it but i have to get a usb cd drive first or another usb stick large enough(i have only one). The way i did it i avoided making a live cd.
Thanks for your response.
Gav

---

### Post by Bike_13 on 2010-01-12
Hi, I am about to image a t5735 (see here: [http://ubuntuforums.org/showthread.php?t=1379697](http://ubuntuforums.org/showthread.php?t=1379697)) and from this, I interpret that I:

1. create live USB stick with my preferred OS
2. boot client with that
3. stick a second FAT formatted USB stick into other USB slot and wait until it apperas on the desktop
4. install to the FAT usb stick (reformatting to ext3/4)
5. turn off machine once installed, remove live USB stick
5. restart using USB as boot

Anything I've missed?

Is it really that simple?

---

