---
title: "Ubuntu Permissions Problems on MacBook"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by DayneOram on 2010-08-31
My MacBook has had some big problems, and all I can get it to do is boot up with the Mac OS X install disk, or the DVD I put ubuntu on earlier. Otherwise I get the grey screen with a folder and question mark flashing on the screen. I am unable to reinstall OS X because of the error, so we (I and a guy on this site) have worked out I need to backup my files using ubuntu, format the computer and then reinstall the OS.

I don't have an external hard drive, but I found ubuntu allows me to use my iPhone in the same way. I have backed up most of my files now, but I cannot access the main folders; 
Desktop, Documents, Downloads, Library, Movies, Music or Pictures and I get the following message: 
"The Folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "_____".

Another problem is to put these files back onto my newly formatted MacBook, I will have to access my iPhone using ubuntu, and I can't put items onto the Macintosh HD because I get the message; "Error while copying to '(name)'.
The destination is read-only.

How do I sort the permissions and stop it being read only??!!

Please help, this is REALLY important!
My MacBook has had song big problems, and all I can get it to do is boot up with the Mac OS X install disk, or the DVD I put ubuntu on earlier. Otherwise I get the grey screen with a folder and question mark flashing on the screen. I am unable to reinstall OS X because of the error, so we (I and a guy on this site) have worked out I need to backup my files using ubuntu, format the computer and then reinstall the OS.

I don't have an external hard drive, but I found ubuntu allows me to use my iPhone in the same way. I have backed up most of my files now, but I cannot access the main folders; 
Desktop, Documents, Downloads, Library, Movies, Music or Pictures and I get the following message: 
"The Folder contents could not be displayed.
You do not have the permissions necessary to view the contents of "_____".

Another problem is to put these files back onto my newly formatted MacBook, I will have to access my iPhone using ubuntu, and I can't put items onto the Macintosh HD because I get the message; "Error while copying to '(name)'.
The destination is read-only.

How do I sort the permissions and stop it being read only??!!

Please help, this is REALLY important!

Oh, and I'm new to ubuntu, so I will have no idea what you're talking about if you go all technical.

---

### Post by mapes12 on 2010-08-31
You need Super User permissions. Boot using the UBU Live CD or DVD. Go Applications>Accessories>Terminal and with you iPhone plugged in and recognised type ```
gksudo nautilus
```you will be asked for your Ubu password. Enter it. You will now have a GUI where you will have permission to move anything. Drag n drop to your iPhone.

Reinstall Mac OS X and copy back your stuff.

---

### Post by DayneOram on 2010-08-31
> **mapes12 said:**
> You need Super User permissions. Boot using the UBU Live CD or DVD. Go Applications>Accessories>Terminal and with you iPhone plugged in and recognised type ```
gksudo nautilus
```you will be asked for your Ubu password. Enter it. You will now have a GUI where you will have permission to move anything. Drag n drop to your iPhone.

Reinstall Mac OS X and copy back your stuff.

What's my ubuntu password? I don't remember choosing one?

Thanks for the help by the way

EDIT: No password required.  I can now view everything but I can't move or copy anything still!

Also, this doesn't solve the problem of not being able to put files on the macintosh HD. But this is progress all the same! Thanks!

---

### Post by mapes12 on 2010-08-31
If it doesn't ask for one then you should be good to go without it. The main thing is being able to get to Terminal.

---

### Post by nothingspecial on 2010-08-31
This is just the benefit of my experience with a Mac formatted iPod and Ubuntu. I have never had a Mac, and probably never will.

Mac uses a file system hfs+ or hfsplus

It doesn`t support linux file permissions. It will always mount read only, meaning you cannot copy stuff to it or from it unless you use some hacks which I don`t personally know about.

I believe some linux distributions enable hfs+ support but Ubuntu does not.

Other than that, I can`t really help you.

Use a search engine "hfs+ (or hfsplus) and linux"

Sorry I could not be more help, but untill someone who knows about this stuff comes along, this may be of some use.

No offence to mapes12 btw, I just remember that using sudo (acting as root) didn`t help. I could be wrong or things may have changed. I`m just saying what I know.

Cheers

---

