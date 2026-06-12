---
title: "Seagate 1TB hard drive ubuntu gutsy"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by superprash2003 on 2010-05-12
I have a seagate 1TB external USB hard drive which im trying to connect to an old ubuntu gutsy machine . I do agree that gutsy is a little too old and i should upgrade to a newer version , but there is so much on that machine that i really dont feel like upgrading it  , besides everything on that machine works perfectly except for this current issue.
  THe problem i am facing is that the seagate drive sometimes randomly disconnects and gets unmounted especially when transferring files . It usually doesn't disconnect when i leave it idle for a long time . But when i start transferring sometimes it disconnects but at times it completes the transfer successfully . 
  I have plugged this seagate into other computers as well which also includes a ubuntu 9.04 setup and it works perfectly on the 9.04 machine . i am able to transfer large amount of data without it disconnecting at all..
  Some extra info :  the seagate is running on ext3 hoping that it would be more ubuntu friendly than NTFS :) .. I also thought that this has something to do with the seagate drive spinning down , so i tried this but still no luck [http://www.cgkreality.com/?p=230](http://www.cgkreality.com/?p=230) ..
 Would really appreciate some help..thanks..

---

### Post by quadproc on 2010-05-12
> **superprash2003 said:**
> I have a seagate 1TB external USB hard drive which im trying to connect to an old ubuntu gutsy machine ....
Your Seagate drive probably includes SMART capability.  You might learn something by asking the drive how it has been doing.

If you have smartctl installed then this will give you a report:
```
sudo smartctl -a /dev/sdX
```where sdX is the device identifier of the disk of interest.

Some versions of Ubuntu have a crippled smartctl program.  This is a workaround because running the present version of smartctl on a flash drive can damage the flash drive so the temporary action was to make the program do nothing.  There is a simple one character fix in one file to re-enable it if you run into this problem.

quadproc

---

### Post by superprash2003 on 2010-05-12
thanks for the reply quadproc..
i get an error saying this device does not support SMART .. 
some extra info :  When i plug in the usb into the machine it appears in the sudo fdisk -l output. and as soon as the drive disconnects it isnt listed anymore in the fdisk output.. and i see a popup on my screen saying unsafe data removal - to avoid serious data loss use the EJECT button ..
  Basically its like removing a pen drive without using the safely remove hardware option even though im not trying to unmount the drive..
  Strangely none of this happens on 9.04 !!

---

### Post by quadproc on 2010-05-12
> **superprash2003 said:**
> thanks for the reply quadproc..
i get an error saying this device does not support SMART .. 
That is unfortunate.  Well, it was worth a try.> 
some extra info :  When i plug in the usb into the machine it appears in the sudo fdisk -l output. and as soon as the drive disconnects it isnt listed anymore in the fdisk output.. and i see a popup on my screen saying unsafe data removal - to avoid serious data loss use the EJECT button ..
  Basically its like removing a pen drive without using the safely remove hardware option even though im not trying to unmount the drive..
  Strangely none of this happens on 9.04 !!
That sure sounds like an OS bug.  I wonder if it is because of the size of the disk: 1 TB might be more than the OS can handle.  That thought suggests another possible approach: partition the disk into pieces less than about 200 GB and see you can use one of those partitions without a problem.  Naturally, there is some risk involved in this approach.

quadproc

---

### Post by kansasnoob on 2010-05-12
I don't know about the drive problem but are you aware that Gutsy has not even received security updates since April 2009! Thirteen months without security updates :P

---

