---
title: "Deleted home folder Help!!!!!"
date: 2011-03-08
forum: New to Ubuntu
---

### Post by Vege 4wd on 2011-03-08
Need help!
  I accidentally deleted my home folder when I was trying to change user settings while attempting to set up a samba file share.  I have not backed it up for some as my system has been the most stable I have ever used.:confused:#-o

Anyway I really need to get files back. Is there anyway I can restore my home folder or at least recover some files?

any ideas would be greatly appreciated. Please help!!!!

---

### Post by PunkLV on 2011-03-08
I assume that you have deleted it using the **rm**. Well..sad news for you I've got here.
However, by 'change user settings' what exactly do you mean?

---

### Post by restorator on 2011-03-08
If you deleted them via nautilus you may find your files in the trash bin. If they are, just restore them from there.

---

### Post by Old *ix Geek on 2011-03-08
> **Vege 4wd said:**
> I accidentally deleted my home folder when I was trying to change user settings while attempting to set up a samba file share.WHAT did you do? HOW did you do it? Please be very specific. "Trying to change user settings while attempting to set up a samba file share" should have, in no way, removed your home directory. So please be very specific about EXACTLY where you were, what you did, how you did it--and why you're under the impression your home directory no longer exists.
> I have not backed it up for some as my system has been the most stable I have ever used.:confused:#-oYes, the beauty of using a REAL operating system! :D

---

### Post by Vege 4wd on 2011-03-08
Thanks for replies. 
I am away from pc so will try suggestions when home.

I was trying to delete a user profile in samb. i also had my user log in box open.
i think i must have been in the user log instdead. Anyway when i reboot the system was reset to  standard. i have my applications but no settings or home folder.
typing on phone so hard to give detail. Questions welcome.

---

### Post by PunkLV on 2011-03-08
Well, not untill you properly describe in detail your actions prior to reboot you will get much help.

---

### Post by Vege 4wd on 2011-03-08
Ok I will give as much detail as I remember. 
Using GUI I tried to set up a samba file share. 
I downloaded and open an app called gamin samba. While this was open I also had the users and groups open.   Just woke up so not fully alert.

Anyway with both these dailog boxes open I deleted a user in the gamin samba box.
While doing this I went back to user box to check passwords etc. 
Last thing I remember was clicking on a box that gave me options to close with or without the home folder. 

I assume this was from the user groups box and I deleted the home folder to my only user account. 

My last backup with lucky backup was a couple of months ago and need to access some files.

---

### Post by gekken on 2011-03-09
> **Vege 4wd said:**
> Ok I will give as much detail as I remember. 
Using GUI I tried to set up a samba file share. 
I downloaded and open an app called gamin samba. While this was open I also had the users and groups open.   Just woke up so not fully alert.

Anyway with both these dailog boxes open I deleted a user in the gamin samba box.
While doing this I went back to user box to check passwords etc. 
Last thing I remember was clicking on a box that gave me options to close with or without the home folder. 

I assume this was from the user groups box and I deleted the home folder to my only user account. 

My last backup with lucky backup was a couple of months ago and need to access some files.

Open a terminal -

Applications - Accessories - Terminal

type in .local/share/Trash/files <-- the "." is important

is there anything in there?

---

### Post by Vege 4wd on 2011-03-09
Hi, ran the code. No such file or directory.
  I tried several times in case of mistyping.

---

### Post by gekken on 2011-03-09
> **Vege 4wd said:**
> Hi, ran the code. No such file or directory.
  I tried several times in case of mistyping.

OK, add /home/YOURUSERNAMEHERE/.local/share/Trash

if nothing; then yup, you deleted your /home folder. 

all may not be lost! IF you have a dedicated real-deal nerd around, you could have them try one of the many disk recovery/computer forensics distros out there

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) (etc)

it is NOT easy, read the docs, but totally worth it. If you get it to work, you can make tons of money on craigslist. (just saying)

---

### Post by Vege 4wd on 2011-03-09
Yeah it is gone.
 I'll give the link a go. Thanks.

---

### Post by Vege 4wd on 2011-03-09
Hi I came accross a program that sounds promising after a google search called scalpel.
Then I ran this code: ```
**scalpel /dev/sda1 -o output**
```

This returned the following error: 

```
The configuration file didn't specify any file types to carve.
(If you're using the default configuration file, you'll have to
uncomment some of the file types.)

```

Any ideas of what I can do next? 
I have tried to do several things but do not seem to be able to get anything to work at the moment.

---

### Post by Vege 4wd on 2011-03-09
Ok! I think I am making progress. After looking at the advice given I have tried to make live cd with gpart and FDOEM. Made using unetbootin. Formatted to ext 3.

All seems to go well however laptop will not boot from the flash drive. I have moved usb to top of boot order but it will not boot past the acer screen with the flash drive attatched. I can't even access the boot the order. If i remove flash drive nothing happens and I have to manually turn off and on the reboot. ](*,)

Once again thanks for all the input and I would appreciate any suggestions.

---

### Post by layr on 2011-07-28
Going to hijack this topic. I managed to F up (read: delete) my home folder too. Gave testdisk a go, found the folder, but none of the contents i'm interested in showed up. Better just forget about it?

If some of you is thinking 'how the hell can anyone accidentally delete home folder' (i know i would have:D):
i have one text file containing some of the terminal commands for wine. I was going to delete all the programs installed under wine with:
```
cd $HOME
rm -rf .wine
```As i copied these lines from the text file, i somehow pasted those lines twice, ending up with cd $HOME
rm -rf .winecd $HOME rm -rf .wine. A day full of fail:D

---

### Post by sirgogo on 2011-07-28
If you did a rm -rf, you can't recover your files (I'm pretty sure).

Anyway, not sure if this was the intent of your original post, but if you want to fix it...
Log in as root, delete your user, and re-add your user (using the gui utility). 

You can also try browsing your filesystem before doing that. Open a terminal window and run
```
$ updatedb
$ locate .Trash 
```
and it will list all the files/folders with .Trash in the path or name. Useful feature. Also, in Nautilus, Control+H shows hidden files (all files with a "." before the name--this is linux's way of hiding files).

---

