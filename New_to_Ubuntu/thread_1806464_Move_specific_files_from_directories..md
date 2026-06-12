---
title: "Move specific files from directories."
date: 2011-07-17
forum: New to Ubuntu
---

### Post by Neoncamouflage on 2011-07-17
Alright guys, maybe this is super simple, but I can't for the life of me figure it out and neither can anyone I asked in IRC. Found it ridiculous to make a forum post about it, but here it is.

I'm trying to search all directories in my /Downloads file, in all those directories/subdirectores dig out any .iso files, and move them to another directory in Downloads called Disc_Images.

```
mv ~/Downloads/*.iso ~/Downloads/Disc_Images
```

This moves all the .iso files that are in /Downloads itself to /Disc_Images, which helped, but it won't search through other directories, and directories within directories. To my knowledge the mv command has no recursive feature that I could use. Does anyone know what I can do other than searching every directory and moving each file individually?

---

### Post by westie457 on 2011-07-17
Copy then paste this into a terminal```
info coreutils 'mv invocation'
```
for ideas on what you want to do.

The command you are using needs some options/arguments to run properly.

---

### Post by ercferret18 on 2011-07-17
Try this:

```
for file in `find ~/Downloads`
do
if echo $file | grep ".iso"
then
mv $file *DESTINATION*
fi
done
```

---

### Post by Neoncamouflage on 2011-07-17
ercferret18:

I used that code and it located the .iso files (as well as every file containing the letters "iso"), but every time it tried to move them it said that there was no file or directory.

---

### Post by ercferret18 on 2011-07-17
can you post exactly what it said when you entered that code?

---

### Post by Neoncamouflage on 2011-07-17
My bad. Here it is:

```
HDV1.iso
mv: cannot stat `HDV1.iso': No such file or directory
(Webisodes,
mv: cannot stat `(Webisodes,': No such file or directory
Webisodes,
mv: cannot stat `Webisodes,': No such file or directory
HDV2.iso
mv: cannot stat `HDV2.iso': No such file or directory
SemCourse.iso
mv: cannot stat `SemCourse.iso': No such file or directory
Advisor.url
mv: cannot stat `Advisor.url': No such file or directory
```

---

### Post by ercferret18 on 2011-07-17
That's weird...

Can you type this into a terminal and post what it says?
```
cd ~/Downloads
find ~/Downloads | grep ".iso"
```

---

### Post by Neoncamouflage on 2011-07-17
```
/home/chris/Downloads/Disk_Images/Backtrack5_32bit_Gnome.iso
/home/chris/Downloads/Disk_Images/Ubuntu_10.04LTS_32bit.iso
/home/chris/Downloads/Disk_Images/Ubuntu_10.10_32bit.iso
/home/chris/Downloads/Disk_Images/WXP_32bit.iso
/home/chris/Downloads/Disk_Images/W7U_32bit.iso
/home/chris/Downloads/Disk_Images/W7U_64bit.iso
/home/chris/Downloads/Unsorted/HDV_S1/HDV1.iso
/home/chris/Downloads/Unsorted/HDV_S1/HDV2.iso
/home/chris/Downloads/Unsorted/Windows 7 Ultimate - 32 Bit (Auto Activation) - Cracked/TSV Torrents/Lost Season 1, 2, 3, 4, 5, & 6 HDTV DVD Box-set + Extras (Webisodes, Deleted Scenes, Interviews etc.).torrent
/home/chris/Downloads/Unsorted/Windows 7 Ultimate - 32 Bit (Auto Activation) - Cracked/TSV Torrents/SGU Stargate Universe Season 1 & 2 HDTV + Extras (Kino Webisodes, Interviews).torrent
/home/chris/Downloads/Unsorted/Windows 7 Ultimate (32 Bit)/Helpfull Microsoft Links/Windows 7 Upgrade Advisor.url
/home/chris/Downloads/Unsorted/Windows 7 Ultimate (32 Bit)/Windows 7 Ultimate (32 Bit)/Windows 7 Ultimate (32 Bit).iso
/home/chris/Downloads/Unsorted/Temp_File_11/SemCourse.iso

```

There it is. Shows the .iso files are indeed there, just for some reason unwilling to move.

---

### Post by ercferret18 on 2011-07-17
Yeah, the script I gave you doesn't work when you have spaces in the filenames. Here's what you can do (from the Downloads directory):

```
mv Unsorted/HDV_S1/*.iso Unsorted/*.iso Unsorted/Temp_File_11/*.iso Disk_Images
```

---

### Post by idoitprone on 2011-07-17
> **ercferret18 said:**
> Try this:

```
for file in `find ~/Downloads`
do
if echo "$file" | grep ".iso"
then
mv "$file" *DESTINATION*
fi
done
```

does quotes fix the issue?

---

### Post by ercferret18 on 2011-07-17
> **idoitprone said:**
> does quotes fix the issue?
No, because the command will still come out spaced apart, even with quotes

---

### Post by idoitprone on 2011-07-17
> **ercferret18 said:**
> No, because the command will still come out spaced apart, even with quotes

really? I thought the double quotes will automatically add back slashes to spaces

because I am pretty sure this test case works or else bash shell has less functionality

```
mkdir 2
touch "1 1"
mv "1 1" 2
cd 2
ls
1 1
```

---

### Post by Neoncamouflage on 2011-07-17
Yeah, using the grep command I saw there were far fewer than I originally thought (next job is figuring out where the missing ones are), so I just moved them all manually with that. Thanks for the help. No idea why I didn't think of that from the start...

---

### Post by ercferret18 on 2011-07-17
> **idoitprone said:**
> really? I thought the double quotes will automatically add back slashes to spaces

because I am pretty sure this test case works or else bash shell has less functionality

```
mkdir 2
touch "1 1"
mv "1 1" 2
cd 2
ls
1 1
```

That will work. However, in the script the 'find' command gives out a list of files separated by newlines **and** spaces, and bash has no way to tell the difference (as far as I know).

---

### Post by Zebediah49 on 2011-07-17
> **ercferret18 said:**
> That will work. However, in the script the 'find' command gives out a list of files separated by newlines **and** spaces, and bash has no way to tell the difference (as far as I know).

True.  That's why you should use a while loop.  Also, why use find and then grep each individually.  Might as well let find do that too:

```

find ~/Downloads -name \*.iso | while read $file
do
mv $file DESTINATION
done

```

Note that I'm pretty sure you can use -exec with find to do it all in one [much cleaner] step, but I'm not as comfortable with that.  I'd guess
find ~/Downloads -name \*.iso -exec mv {} DESTINATION
but I'm not positive.

---

### Post by ercferret18 on 2011-07-17
> **Zebediah49 said:**
> True.  That's why you should use a while loop.  Also, why use find and then grep each individually.  Might as well let find do that too:

```

find ~/Downloads -name \*.iso | while read $file
do
mv $file DESTINATION
done

```

Note that I'm pretty sure you can use -exec with find to do it all in one [much cleaner] step, but I'm not as comfortable with that.  I'd guess
find ~/Downloads -name \*.iso -exec mv {} DESTINATION
but I'm not positive.
Yeah... That's what I meant to say :)

---

### Post by coffee412 on 2011-07-18
Hello, I was just browsing thru and saw your post. A few days ago I got done recovering a bunch of jpgs and other files from a customer. I used testdisk to do it. However, It created about 400 directories and the files were all scattered thru them. So, I wrote a script to search the directories and copy all the jpgs to a certain directory. I think that is the same thing you are trying to do from your post. Therefore, Here is my short little script:


> #!/bin/bash
for i in $( locate /home/coffee/Downloads/tony/*.jpg ); 
do
cp "$i" /home/coffee/Downloads/tony-jpg 
done


Correct the files paths as needed.


coffee

---

