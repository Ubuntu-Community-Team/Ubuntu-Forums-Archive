---
title: "create iso image on hard drive from live cd"
date: 2010-08-26
forum: New to Ubuntu
---

### Post by salima on 2010-08-26
i made a cd from the iso image, then lost the image. It is really gone.

The cd or drive has a problem and i get a message it will not mount, 
which i know is an issue and i have tried various fixes but it wont work.
 It is a good cd, I had a friend look at it. What does happen when I put
 it in the drive after the error message is displayed is that there is an
 icon on the desktop as though it is mounted-when i click on properties i
 have this information:
  file system type: isofs
 DRIVE
drive-Moser Baer DH20A4P
connection SCSI
Media-CD-RW/DVD +/- RW drive 

VOLUME
Label Ubuntu 10.04
Size 699.8 MB
Media CD-R
File System iso 9660 (joliet Extension)

Mount Point: /media/cdrom0
File System: iso9660
Mount Options: ro nosuid nodev utf8

i found the following instructions for creating iso image from cd:
QUOTE 1. Insert the CD or DVD that you want to make an ISO image of.
2. Open a terminal window.
3. Execute the following command:
cat /dev/scd0 > /home/shamanstears/test.iso
where /dev/scd0 is the device name for your drive (to find this, go to the Main Menu, click on System, mouseover Administration and select System Monitor. Click the File Systems tab. The device name will be listed in the Device column). Also make sure to change the path and iso filename to the desired path and filename.

The disc will begin to spin and the ISO image will start being constructed. Once it has completed, you have an ISO image of your CD. To verify that the image was properly created, mount the ISO file and check the contents.
 QUOTE
 


 however i dont understand the instructions.  
 System Monitor gives me /dev/sdal (only one device listed, should there be a cdrom?)
 i am not sure what i should type but here is something i tried:
 **when i type the command:**
 cat/dev/sdal>/home/ubuntu-10.04-desktop-i386*.iso
 **this is what happens:**
 salima@salima-desktop:~$ sudo bash 
 [sudo] password for salima:  
 root@salima-desktop:~# cat/dev/sdal>/home/ubuntu-10.04-desktop-i386*.iso 
 bash: cat/dev/sdal: No such file or directory 
 root@salima-desktop:~#  
 

 or should i use a different command if i dont know the iso filename on the cd?

---

### Post by uRock on 2010-08-26
Have you tried using Brasero? If all ese fails use [Unetbootin]("http://unetbootin.sourceforge.net/") to install without burning the ISO to disk. Check out the link to [Unetbootin]("http://unetbootin.sourceforge.net/"). It is in the repository, so installing it is very easy.

---

### Post by jtarin on 2010-08-26
Use the command ```
eject -n
``` to determine your CD drive.

---

### Post by salima on 2010-08-27
thanks for replying-i was playing around and i may have discovered something
let me restate my problem in another way-
i have an ubuntu 10.04 live cd and i want to take the iso image and put it on my hard drive...

when i right clicked on the cd rom icon, i noticed there is an option to copy to disk, so i chose it. the copy was written and then the program (not brasero, i dont know what was doing it)asked me to insert a blank cd or dvd. there was no other option at that point, so i cancelled. i dont want a cd, i have a cd-i want the image so i can create a usb boot install (part two of the issue)

so i looked around and found the tmp place and got the iso file onto the desktop. i dont know if this is the answer to my problem or not, how it could be this easy...but i cant open the file-double left click tells me '                                  [COLOR=RoyalBlue]could not display-there is no application installed for this file type[/COLOR]


right click on properties tells me:
                                  name-image.iso.61MZHV
 type-unknown (application/octet-stream)
 size-699.8 MB
 location-/home/salima/Desktop
 volume-unknown



so do you think i actually have an iso file that can be made into a usb boot install for 10.04?

**edit:**
just noticed in the instructions i copied on the OP this statement:
 [COLOR=RoyalBlue]To verify that the image was properly created, mount the ISO file and check the contents.[/COLOR]
how do i do that?

---

### Post by jtarin on 2010-08-27
Try right-click and use Archive Manager and see if you can see it. I use Rar to do this normally in windows and Linux but the other might work.Another way to assure yourself would be to do an md5 checksum on the file and compare it to the md5 onsite where you got it.

---

### Post by vivek40 on 2010-08-27
hi...
1. insert the cd/dvd whose image you want to make
2. type this in terminal 
cat /dev/sr0 > /home/vivek/test.iso

(Please note /dev/sr0 may be different for your system.. just go to system monitor>filesystem and look for your cd /dvd drive and use that instead)

Give it some time and your iso image will be made
have fun!
Vivek

---

### Post by vivek40 on 2010-08-27
And yes to check the contents of your iso file.. just mount the iso image, and access it.. !

---

### Post by jtarin on 2010-08-27
> **salima said:**
> 
**edit:**
just noticed in the instructions i copied on the OP this statement:
 [COLOR=RoyalBlue]To verify that the image was properly created, mount the ISO file and check the contents.[/COLOR]
how do i do that?[Loop device ]("http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html")

---

### Post by salima on 2010-08-27
> **jtarin said:**
> [Loop device ]("http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html")

this is great stuff, i saved it to my tutorials folder...
but i am afraid i am getting discouraged now, i am in way over my head.

i right clicked on the image.iso icon and clicked on archive and perhaps an archive image has been made somewhere..but i dont know what to do next.

also i am afraid i am getting discouraged now, i am in way over my head.

all i want to do is a clean install of 10.04 over my 8.10, and then i can learn how to do stuff as i go along. but i have been unable to resolve the 'dbus mount' issue with the cd i created and i have been unable to retrieve a usable iso image to try making a usb install, and now my only resort is to go back and download the file again (four nights with my connection) and then create a usb stick and see if that will work.


oh, wait! there is a little box on my desk called image.iso and when i clicked on it the archive manager opened up and now it is shown in a box...but when i try to open it nothing happens. it shows name, size, type unknown, and date

---

### Post by salima on 2010-08-27
> **vivek40 said:**
> hi...
1. insert the cd/dvd whose image you want to make
2. type this in terminal 
cat /dev/sr0 > /home/vivek/test.iso

(Please note /dev/sr0 may be different for your system.. just go to system monitor>filesystem and look for your cd /dvd drive and use that instead)

Give it some time and your iso image will be made
have fun!
Vivek


i was having fun for about a week but now i am getting a little tired...before this it took me a week to get my modem working, that was the most fun of all-but now all i want to do is get the upgrade over with so i can start using things...

anyway here is what i typed and what happened:
salima@salima-desktop:~$ cat/dev/scd0>/home/vivek/test.iso
bash: /home/vivek/test.iso: No such file or directory
salima@salima-desktop:~$ 

is it an issue not to use the space bar when typing commands? should there be a space before and after the > ? (i also tried your command replacing my name with yours, but got the same result...)

---

### Post by salima on 2010-08-27
here is another interesting thing...
i tried the function 'create a usb startup disk' and though i have the cdrom icon on my desk it is not in the window for creating the disk. when i go to 'other' to try and get the iso image i saved to the desktop it is not listed among the files i can choose...

i guess it's back to the downloads page...

---

### Post by jtarin on 2010-08-27
[There's a way to mount it on a virtual drive.]("http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/") This one can be found in Synaptic.

---

### Post by salima on 2010-08-27
i was playing around some more and actually got the real iso image off the cd and onto the hard drive, and i think i created a usb thing...it said i did, and to restart with the usb in the machine.

when i did that, the monitor screen was black (its green light was on) and there was no light on the pen drive...then i didnt know what to do, took out the pen drive (after waiting for some time) and nothing changed, tried ctr/alt/del and nothing happened, so i cut the power.

when i restarted everything was ok but now i dont want to try the pen drive any more until i find out what went wrong.

i wonder why if i am able to get the image off the cd it wont boot and let me install? 
any ideas?

gee, thanks for hanging in there with me this far!

---

### Post by vivek40 on 2010-08-28
Hii.. well I just read your post ... Mam did you really say you typed this:-

[HTML]
anyway here is what i typed and what happened:
 salima@salima-desktop:~$ cat/dev/scd0>/home/vivek/test.iso
 bash: /home/vivek/test.iso: No such file or directory
[/HTML]Lol! here /home/vivek/test.iso is for my system. You would have to enter your details.... something like /home/salima/test.iso or something.. I wont know... /home/vivek is just an example...

---

### Post by vivek40 on 2010-08-28
Oh sorry just read that you did something like this .. ! 
Yes spaces are needed:-
cat /dev/scd0 > /home/salima/test.iso

just try copy pasting the above with all the spaces intact .. if that does not work (while it should).. try this:-

cat /dev/cdrom > /home/salima/test.iso


have fun!
vivek

---

### Post by salima on 2010-08-28
> **vivek40 said:**
> Oh sorry just read that you did something like this .. ! 
Yes spaces are needed:-
cat /dev/scd0 > /home/salima/test.iso

just try copy pasting the above with all the spaces intact .. if that does not work (while it should).. try this:-

cat /dev/cdrom > /home/salima/test.iso


have fun!
vivek

hi vivek!
yes, i really did type vivek the first time because i felt too stupid to ask if i should be typing my own name! it only seemed logical to me, but then the second time i typed my own name.

anyway, that problem is technically solved because i got the iso off the cd, even made a usb noot stick, but now i have to figure out how to get it to work.

should i open a new thread for that?

EDIT:
i am marking this thread solved, and the new thread for the cd is   called Live CD Won't Mount........if that isnt solved reasonably soon i will start a new thread on the usb issue...

---

