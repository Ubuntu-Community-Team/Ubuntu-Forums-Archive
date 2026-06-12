---
title: "Installing Ubuntu"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by Jasper7g on 2010-01-14
*I downloaded Ubuntu 9.10 and burned the file to a CD. How do I install it? Never had a problem with the previous version. *

---

### Post by I8NY on 2010-01-14
did u burn the iso file on the disc or did u burn the iso disc image?  if u just burned the iso file on then it won't work.  If u burned the iso disc image then reboot w/ the disc in and it should read the cd if the BIOS if set to.

---

### Post by Jasper7g on 2010-01-14
I have no idea. I just downloaded a file (689megs). What is ISO?

---

### Post by sliketymo on 2010-01-14
[http://ask-leo.com/what_are_iso_files_and_how_do_i_open_them.html](http://ask-leo.com/what_are_iso_files_and_how_do_i_open_them.html)

---

### Post by tom.swartz07 on 2010-01-14
> **Jasper7g said:**
> *I downloaded Ubuntu 9.10 and burned the file to a CD. How do I install it? Never had a problem with the previous version. *
[http://www.psychocats.net/ubuntu/burn](http://www.psychocats.net/ubuntu/burn)

then installing
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by I8NY on 2010-01-14
for burning a ISO i like using DVD decrypter but save your self a cd and use unetbootin to burn it on a USB thumb drive :D

---

### Post by Jasper7g on 2010-01-14
I downloaded the file from [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

I see the instructions:

"After the ISO file has finished downloading, you will have to burn the file to CD. The ISO file will usually require a special application to burn. Click the link below to find detailed instructions."

Now I assume that would be the ISO file that I downloaded ??? What is the "special application" for burning? With 8.04 I just downloaded the file, burned it onto a CD and it installed without any problem. Whatever I have now won't work. I'm baffled.

---

### Post by tom.swartz07 on 2010-01-14
> **Jasper7g said:**
> I downloaded the file from [http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

I see the instructions:

"After the ISO file has finished downloading, you will have to burn the file to CD. The ISO file will usually require a special application to burn. Click the link below to find detailed instructions."

Now I assume that would be the ISO file that I downloaded ??? What is the "special application" for burning? With 8.04 I just downloaded the file, burned it onto a CD and it installed without any problem. Whatever I have now won't work. I'm baffled.

any program that could burn cd image files works.
the link there only describes programs that you could use.


you could use anything to burn the image, as long as its not a 'data cd'

---

### Post by running_rabbit07 on 2010-01-14
> **tom.swartz07 said:**
> [http://www.psychocats.net/ubuntu/burn](http://www.psychocats.net/ubuntu/burn)

then installing
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

+2 My dog agrees, too.

---

### Post by d3v1150m471c on 2010-01-14
> **Jasper7g said:**
> *I downloaded Ubuntu 9.10 and burned the file to a CD. How do I install it? Never had a problem with the previous version. *

As long as you properly burned the .iso image, reboot your computer, when your options for your bios comes on, like "press F12 for the boot menu", or something of the like appears then select it and set it to boot from cd. Make sure the disk is in and set it to boot from cd. Rock and roll.

---

### Post by Merk42 on 2010-01-14
> **Jasper7g said:**
>  With 8.04 I just downloaded the file, burned it onto a CD and it installed without any problem. Whatever I have now won't work. I'm baffled.

Okay so you've done this before.

So what isn't happening this time?
It should be just like 8.04, pop the disc in install.

Is it not booting from the disc? (check BIOS to see that your computer is set that way)
Is it installing then crashing? (select 'check disk for errors' when you boot from the CD, or check the md5sum of the iso)

---

### Post by prshah on 2010-01-14
> **Jasper7g said:**
> I have no idea. I just downloaded a file (689megs). What is ISO?

An ISO file is an image of a CD. The image contained within the ISO has to be burnt to a CD, not the ISO file itself.

Usually, most CD burning programs contain an option to burn the ISO image, which will be called "burn ISO", "write image", or words to that effect.

In most cases, just right-clicking the ISO will yield such an option (In ubuntu it's called "Write to Disc").

You will know you have burnt it correctly if, when you insert the CD and see a whole bunch of files and folders rather than just the single ISO file.

---

### Post by Jasper7g on 2010-01-14
Okay, one more try. The file  downloaded was unbuntu-9.10-desktop-1=i386

I burned it on to a CD with Nero. It will not start when I reboot with the disk in the drive. I did as suggested and used F12 to get it to boot from the CD.. no joy there either. 

I want to install it within Windows (the horrible Vista) and I noticed when visiting one of the sites someone recommended the instructions were for XP....does it make any difference. 

Maybe I'll have to resort to installing 8.04 and getting the upgrade....if it still automatically 
does it. What a bummer! Installations should be simple.

---

### Post by pirateghost on 2010-01-14
> **Jasper7g said:**
> Okay, one more try. The file  downloaded was unbuntu-9.10-desktop-1=i386

I burned it on to a CD with Nero. It will not start when I reboot with the disk in the drive. I did as suggested and used F12 to get it to boot from the CD.. no joy there either. 

I want to install it within Windows (the horrible Vista) and I noticed when visiting one of the sites someone recommended the instructions were for XP....does it make any difference. 

Maybe I'll have to resort to installing 8.04 and getting the upgrade....if it still automatically 
does it. What a bummer! Installations should be simple.

installations are extremely simple.

first of all what file extension does the file have?  .iso? .exe?

you say you want to install it within windows?  like WUBI?  Or in a Virtual Machine?

it isnt rocket science to burn a cd.  in windows i prefer a program called imgburn, dblclick the .ISO file and it will burn it


HOWEVER, like someone else suggested, just use UNETBOOTIN and make a bootable thumbdrive...dont waste the cds...

---

### Post by Jasper7g on 2010-01-14
When I look at the file all I see is *unbuntu-9.10-desktop-1=i386*

---

### Post by Jasper7g on 2010-01-14
Oh, and the words "Disk image file"

---

### Post by pirateghost on 2010-01-14
> **Jasper7g said:**
> When I look at the file all I see is *unbuntu-9.10-desktop-1=i386*
so why dont you UNHIDE the file extensions that microsoft is so adamant about thinking you need to be hidden from?

in your windows explorer window, click on organize on the left hand side and then click on folder and search layout

click on the view tab
UNCHECK the option to hide extensions for known file types

OR


you could simply RIGHTCLICK on the file and click on properties.....it will tell you why type of file it is

---

### Post by Jasper7g on 2010-01-14
Ah! Thank you. It is an ISO file. I bet you can't imagine how much  hate Vista. Microsoft had a nerve to expect to be paid for it, they should pay us for using it. 

Okay, I still don't understand why it doesn't boot. I have another computer with XP on it, I'll try that. 

Thanks to everyone for their advice. You can see I'm not a geek!

---

### Post by mastablasta on 2010-01-15
To propperly burn an image file in Nero Burning rom you need to go to File->new and then open your image file. It iwll then give th option to write it to CD. 
 
After it's done the CD will contain many files and folders and only then you can boot from the CD.

---

### Post by d3v1150m471c on 2010-01-15
Use the proper .iso burning instructions provided by ubuntu. .iso images have to be burned a specific way, so you cannot just slap it on a disk and then boot it. 

Here, check this out:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

