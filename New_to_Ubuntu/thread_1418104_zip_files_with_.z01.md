---
title: "zip files with .z01"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by steven198807 on 2010-02-28
Hi i'm very new to Linux and finding command line horrible but still trying to use it the best i can.

I got a small problem i need to get some of my files out off a zip file created with .zip .z01 .z02 .z03 etc all the way up to .z13.

So far i have tried 7zip but that did not work, i tried to wine winzip but i could not finish the install, then i found a website with command line to do it, however i am a little stuck.

After that i have cd in the command to my folder with the files in side and the file is called Back up.zip
it does have a space in the name not sure if that effects it, i am told use these commands

hendra-k@server $ cat zipfiles.* > zipfiles-full.zip
hendra-k@server $ zip -F zipfiles-full.zip
hendra-k@server $ unzip zipfiles-full.zip

I tried but not sure if i am writing it correctly, it returns error
cat: zipfiles.*: No such file or directory
cat: up.zip: No such file or directory

this is the command i tried 
cat zipfiles.* > Back up.zip

please help me write this correctly so i can my wow patches from my files,the zip file does work in windows xp, but i need in Linux.

---

### Post by spectralblue on 2010-02-28
Which Linux distro are you using? Ubuntu, Kubuntu, etc? Don't you have Archive Manager or Ark? Usually clicking or double clicking the zip file is good enough with most linux distros. 

If you don't have an archive manager in your desktop, install it. 

If you like the command line. To unzip, the command is

```
unzip filename.zip
```replace file name with the name of the file you're trying to unzip. If it has spaces, make sure you enclose it in quotation marks, for example: 

```
unzip "filename with space.zip"
```You don't have to join the zipfiles that you have to unzip them! 

If you're having a bit of trouble with this, why not just unzip the file in windows, copy the ones that you want to a CD or USB?

---

### Post by steven198807 on 2010-02-28
> **spectralblue said:**
> Which Linux distro are you using? Ubuntu, Kubuntu, etc? Don't you have Archive Manager or Ark? Usually clicking or double clicking the zip file is good enough with most linux distros. 

If you don't have an archive manager in your desktop, install it. 

If you like the command line. To unzip, the command is

```
unzip filename.zip
```replace file name with the name of the file you're trying to unzip. If it has spaces, make sure you enclose it in quotation marks, for example: 

```
unzip "filename with space.zip"
```You don't have to join the zipfiles that you have to unzip them! 

If you're having a bit of trouble with this, why not just unzip the file in windows, copy the ones that you want to a CD or USB?

Ubuntu 9.10
i tryed archive manager but i get error below, also the the file was tested on windows xp but i do have xp to transfer plus its like 8gb unziped and i only have 4gb dvds, so i really need to unzip it in linux. i tryed your command but i got the same error as archive manager.
warning [Back up.zip]:  zipfile claims to be last disk of a multi-part archive;
  attempting to process anyway, assuming all parts have been concatenated
  together in order.  Expect "errors" and warnings...true multi-part support
  doesn't exist yet (coming soon).
file #1:  bad zipfile offset (local header sig):  4
file #2:  bad zipfile offset (local header sig):  42
file #3:  bad zipfile offset (local header sig):  17769421
file #4:  bad zipfile offset (lseek):  373309440
file #5:  bad zipfile offset (local header sig):  373309507
file #6:  bad zipfile offset (lseek):  577085440
file #7:  bad zipfile offset (EOF):  577092836
file #8:  bad zipfile offset (EOF):  577093356
file #9:  bad zipfile offset (lseek):  577093632
file #10:  bad zipfile offset (local header sig):  577093951
file #11:  bad zipfile offset (local header sig):  577094210
file #12:  bad zipfile offset (local header sig):  577094415
file #13:  bad zipfile offset (local header sig):  577094678
file #14:  bad zipfile offset (local header sig):  577094957
file #15:  bad zipfile offset (local header sig):  577095262
file #16:  bad zipfile offset (local header sig):  577095606
file #17:  bad zipfile offset (local header sig):  577096027
file #18:  bad zipfile offset (local header sig):  577096316
file #19:  bad zipfile offset (local header sig):  577096597
file #20:  bad zipfile offset (local header sig):  577096827
file #21:  bad zipfile offset (local header sig):  577097175
file #22:  bad zipfile offset (local header sig):  577097533
file #23:  bad zipfile offset (local header sig):  577097898
file #24:  bad zipfile offset (local header sig):  577098513
file #25:  bad zipfile offset (local header sig):  577098829
file #26:  bad zipfile offset (local header sig):  577099157
file #27:  bad zipfile offset (local header sig):  577099449
file #28:  bad zipfile offset (local header sig):  577099758
file #29:  bad zipfile offset (local header sig):  577100087
file #30:  bad zipfile offset (local header sig):  577100462
file #31:  bad zipfile offset (local header sig):  577100740
file #32:  bad zipfile offset (local header sig):  577101043
file #33:  bad zipfile offset (local header sig):  577101533
file #34:  bad zipfile offset (lseek):  577101824
file #35:  bad zipfile offset (local header sig):  577102368
file #36:  bad zipfile offset (local header sig):  577102709
file #37:  bad zipfile offset (local header sig):  577103335
file #38:  bad zipfile offset (local header sig):  577103729
file #39:  bad zipfile offset (local header sig):  577104036
file #40:  bad zipfile offset (local header sig):  577104402
file #41:  bad zipfile offset (local header sig):  577104827
file #42:  bad zipfile offset (local header sig):  577105455
file #43:  bad zipfile offset (local header sig):  577105824
file #44:  bad zipfile offset (local header sig):  577106106
file #45:  bad zipfile offset (local header sig):  577106325
file #46:  bad zipfile offset (local header sig):  577106608
file #47:  bad zipfile offset (local header sig):  577106891
file #48:  bad zipfile offset (local header sig):  577107171
file #49:  bad zipfile offset (lseek):  577118208
file #50:  bad zipfile offset (lseek):  644554752
file #51:  bad zipfile offset (lseek):  654426112
file #52:  bad zipfile offset (lseek):  659456000
file #53:  bad zipfile offset (lseek):  664862720
file #54:  bad zipfile offset (lseek):  725762048
file #55:  bad zipfile offset (lseek):  726794240
file #56:  bad zipfile offset (lseek):  224632832
  inflating: Back up/Steven/web key.txt

i know the file works on windows, but sadly i dont have access to windows for a while( saving cash for windows 7)

---

### Post by spectralblue on 2010-02-28
Looks like a bad compression. I know this happens a lot with zip files - where it works in one system, but it doesn't on another. If you still have access to the original files (the unzipped files), compress them again under a new file name, or use WinRar or 7zip instead and see if that works? 

Otherwise, perhaps buy a bigger flash key? Good luck!

---

### Post by steven198807 on 2010-02-28
> **spectralblue said:**
> Looks like a bad compression. If you still have access to the original files (the unzipped files), compress them again under a new file name, or use WinRar or 7zip instead and see if that works?

i gave the disk to a friend and he is able to open it on windows xp again so its not broken, i tried to install winrar and 7zip none installed in wine or worked for me also tryed 7zip in linux that also did not work.

i read online linux has a problem with this type of zip but no answers expect for
hendra-k@server $ cat zipfiles.* > zipfiles-full.zip
hendra-k@server $ zip -F zipfiles-full.zip
hendra-k@server $ unzip zipfiles-full.zip

but im not sure how to write mine in that format, im really stuck and pulling my hair out:)

---

### Post by oldos2er on 2010-02-28
Have you tried **zip -FF "file name.zip"** then **unzip "file name.zip"** ?

---

### Post by steven198807 on 2010-03-01
> **oldos2er said:**
> Have you tried **zip -FF "file name.zip"** then **unzip "file name.zip"** ?

Problem is fixed, i went out and got a copy of windows xp and now extracted.

I wish unbuntu the best of luck.
I like that fact it installed my belkin wirless for me as its been a pain in the bum in the pass.

I would recommend that a device manager should be created for it.
Also i think a app should be made to install apps you have to download from sites.
I think there should be a gui update to make it look more nice.
Finaly i would also like to see when you right click a file you could click delete to delete the file.

Linux is nice but i belive windows is better for me because i find it easyer and cleaner looking and open office is not as nice as office2007, and i find it faster to click then command.

Maybe one day ill try unbuntu/linux again but untill then i wish the best of luck and hope one day that linux can be come a windows/mac rival/killer.

---

### Post by spectralblue on 2010-03-01
> **steven198807 said:**
> i gave the disk to a friend and he is able to open it on windows xp again so its not broken, i tried to install winrar and 7zip none installed in wine or worked for me also tryed 7zip in linux that also did not work.

i read online linux has a problem with this type of zip but no answers expect for
hendra-k@server $ cat zipfiles.* > zipfiles-full.zip
hendra-k@server $ zip -F zipfiles-full.zip
hendra-k@server $ unzip zipfiles-full.zip

but im not sure how to write mine in that format, im really stuck and pulling my hair out:)


I'm not sure either cause I rarely use zip files lol. 

But looking from that command that you gave above, with a file name Back up.zip the command would be like this:
```

cat "Back up.*" > zipfiles-full.zip
zip -F zipfiles-full.zip
unzip zipfiles-full.zip
```

Try to avoid spaces when you're creating files, underscores are better, as some commands cannot handle spaces.

---

### Post by steven198807 on 2010-03-02
> **spectralblue said:**
> I'm not sure either cause I rarely use zip files lol. 

But looking from that command that you gave above, with a file name Back up.zip the command would be like this:
```

cat "Back up.*" > zipfiles-full.zip
zip -F zipfiles-full.zip
unzip zipfiles-full.zip
```Try to avoid spaces when you're creating files, underscores are better, as some commands cannot handle spaces.

I did try that in the end but that didnt work for me lol
but thanks for trying to help.

---

### Post by shihkster1015 on 2010-03-02
doesn't this mean that there's a few files?
and .z01's just one of the series?

---

### Post by Mark Phelps on 2010-03-02
> **shihkster1015 said:**
> doesn't this mean that there's a few files?
and .z01's just one of the series?

Yes ... but WinRAR in MS Windows world is able to automatically find all of the other parts of the .ZIP file and extract them -- simply by right-clicking the first file of the series.

In Ubuntu, I found a java-based file joiner (HJ-Split) which I could use to join all the .znn parts into one file and then unzip that.

At least in my case, the Archive Manager was unable to extract zip files that consisted of separate files -- like these.

---

### Post by tripmix on 2010-09-20
HJ-Split would just do the same as the cat * > command in this case. An issue I've encountered with this approach is I need to rename whatever.zip to whatever.z00 then do cat whatever.z* > new.zip otherwise the data gets put into the new zip in the wrong order.

Simple test:
```
echo "line 1" > test.z00
echo "line 2" > test.z01
cat test.z* > archive
cat archive
mv test.z00 test.zip
cat test.z* > archive
cat archive
```
See how line 1 and 2 change place because cat * lists the files alphabetically.

---

### Post by stoian on 2012-11-03
i had the same problem. a zip archive split in volumes:

```
myfile.z01
myfile.z02
myfile.zip
```

the right command to create one zip file:

```
zip -F myfile.zip --output big_archive.zip
```

hope this helps. the resulting archive can now be handled in linux.

---

