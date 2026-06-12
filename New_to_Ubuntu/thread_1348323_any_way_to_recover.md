---
title: "any way to recover??"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by keelay42 on 2009-12-07
Well, like a dumbass I just deleted EVERYTHING. I was TRYING to set my partitioning after formatting the windows partition, and hit the "device" button in GParted. 
 Any way to recover my stuff?

---

### Post by alwayshere on 2009-12-07
ya may be able to get some of ya files back using photorec

---

### Post by keelay42 on 2009-12-07
all im interested in is my pics and music. 
what is photorec, and how would i go about using it?

---

### Post by alwayshere on 2009-12-07
photorec will do what you want .I used it to recover all my music i deleted by mistake.

heres a link that may help

[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)


to install photorec    

sudo apt-get install testdisk



to open photorec type "photorec"

---

### Post by keelay42 on 2009-12-07
says cannot find the package...
any other way?

---

### Post by alwayshere on 2009-12-07
go to "system" then "administration" then "software sourses"

in the screen you see there tick all the boxes 

in the "Download from " drop box ,set to main server 

then in the terminal put 

sudo apt-get update

let that do its thing then put

sudo apt-get install testdisk

then again put 

sudo apt-get update

and let it do its thing 

then  type 

photorec 

then press enter

---

### Post by keelay42 on 2009-12-07
how do I specify that where to save to?

---

### Post by keelay42 on 2009-12-07
trying to create a partition to save to, and it wont create one! WTF?? keeps giving error trying to format to ext4. it wont take a format. wtf? this is pissing me off so bad

---

### Post by louieb on 2009-12-07
Damn good thing you did not format. If all you did was write a new disk label testdisk should be able to restore your partition table. Get a [SystemRescueCd]("http://www.sysresccd.org/Main_Page") and check the rescure examples on the testdisk wiki. [TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk")

  know it frustrating . Take a deep breath - there is a good chance you can get your data back.

---

### Post by keelay42 on 2009-12-07
yea but now I have no way to download or burn. I am on the live cd and thats all i have. i got photorec working, but i run out of storage space after about 20 seconds. what should i do. All i REALLY want is my pics and music ( about 8 gigs of pics and 9 gigs of music)

---

### Post by margni on 2009-12-07
> **keelay42 said:**
> yea but now I have no way to download or burn. I am on the live cd and thats all i have. i got photorec working, but i run out of storage space after about 20 seconds. what should i do. All i REALLY want is my pics and music ( about 8 gigs of pics and 9 gigs of music)

Just a shot... why not copy them to a thumbdrive, and move them to another computer?  Maybe, maybe not?

---

### Post by keelay42 on 2009-12-07
impatience owns me. Re-installing 9.10, and gonna try photorec after that, so i will have somewhere to freaking put the stuff it DOES find

---

### Post by keelay42 on 2009-12-07
> **margni said:**
> Just a shot... why not copy them to a thumbdrive, and move them to another computer?  Maybe, maybe not?
  
No thumbdrive, all I have is the 2 gig card in my phone, which will not mount. no network to transfer crap to. nothing. dammit

---

### Post by lotharmat on 2009-12-07
> **keelay42 said:**
> impatience owns me. Re-installing 9.10, and gonna try photorec after that, so i will have somewhere to freaking put the stuff it DOES find

Woah!!!

Will that not write over the data you want to save?
Erasing data is one thing but writing over it too - world of pain!

---

### Post by keelay42 on 2009-12-07
> **lotharmat said:**
> Woah!!!

Will that not write over the data you want to save?
Erasing data is one thing but writing over it too - world of pain!

Yea, I recovered about %40 of everything, but most of my music is broken. dammit. anyone know how to delete the stuff photorec recovers and saves. they all have this padlock icon above the recfolder.

---

### Post by alwayshere on 2009-12-11
find ya files and  go to properties and change file permissions and change file permissions to create and delete
if this dont work try below 




sudo nautilus

then ya password 

a window will pop up use that to find ya files and  go to properties and change file permissions and change file permissions to create and delete

---

