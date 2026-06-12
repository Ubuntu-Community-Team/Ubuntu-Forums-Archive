---
title: "Deleting files from virus infected pen drive"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by mmasroorali on 2009-08-08
Dear all,
I know that one of the most effective ways to clean a virus infected pen drive is to insert it in a linux box and then delete those files. It has worked for me for a long time.

This morning a friend brought a pen drive which has a number new files (exe) and some folders. All of them are in read only condition. Now to begin with, I can not delete the files (read-only file system), chmod +w does not work (same message). 

I do not know what to do now. I am not a Windows user, but being the local Linux enthusiast, the Windows users like to get this help from me.

I know that I can copy the good files to a linux machine and then format the pen drive, but then it will appear to me that I am avoiding the challenge.

Any suggestion will be appreciated.

---

### Post by SunnyRabbiera on 2009-08-08
You could just reformat the entire drive, that will fix it ;)

---

### Post by ubudog on 2009-08-08
Do ls /media and see what the name of your pen drive is, and then do sudo cd /media/nameofyourpendrive,enter your password,and then do: rm virusinfectedfiles - virusinfectedfiles being the virus infected files of course, and it should work.  Hope that helps! :P

---

### Post by Clorow on 2009-08-08
The way most viruses spread through USB drives is through automatically running software upon insertion. To stop this, delete /media/nameofdisk/autorun.inf.

---

### Post by mike555 on 2009-08-08
Kinda late , but next time set your USB to read only by using a USB that has a micro switch just for that ...
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820183232&Tpk=ridata%20slider](http://www.newegg.com/Product/Product.aspx?Item=N82E16820183232&Tpk=ridata%20slider)

---

### Post by starcannon on 2009-08-08
I'd flatten it with gparted; if there are files that you must keep, then copy them off first, then flatten it with gparted.

---

### Post by superprash2003 on 2009-08-08
you could go to the terminal and type **sudo nautilus**  , then browse to the pen drive and you should be able to delete now..

---

### Post by ubudog on 2009-08-08
> **superprash2003 said:**
> you could go to the terminal and type **sudo nautilus**  , then browse to the pen drive and you should be able to delete now..

True, that would work. :P

---

### Post by firen on 2009-08-08
"gksu" and typing nautilus at the prompt works for me; Nice for 'terminal fearing' people.

---

### Post by jacklinux on 2009-08-08
> **superprash2003 said:**
> you could go to the terminal and type **sudo nautilus**  , then browse to the pen drive and you should be able to delete now..
Best option by far.

---

### Post by harry2006 on 2009-08-08
smart answer!

---

### Post by mmasroorali on 2009-08-09
It appears that none of my friends read my post before posting. I had already tried sudo rm -rvf <infected files> before posting. Most of the suggestions are in this line.

I even tried sudo nautilus and then removing the files (equivalent to the above rm), it did not work. It appears that the whole file system has been made read only.

Please suggest how to make a read only file system to writable.

---

### Post by cariboo on 2009-08-09
Set your mount point as world read/writeable:

```
sudo chmod -R 777 /media/device
```

substitute the mount point you have for /media/device, you should now be able to manage files on the usb device.

Remember once you are finished to set the permissions back to 755.

---

