---
title: "make .iso from folder &amp; file a bug"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by gigenieks on 2011-08-14
Hello all,


I made earlier thread  [[COLOR="Navy"]Getting most of XP SP3[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1822340")
and one of suggestions was to [COLOR="DarkRed"]**use nLite**[/COLOR] application ([read this post]("http://ubuntuforums.org/showpost.php?p=11139225&postcount=4"))

So, I rebooted to Windows 7. Downloaded nLite and started "stripping down functions etc" when it (nLite) finished I rebooted in Xubuntu to try install my new XP.

Then I found out that nLite didn't make an .iso file instead some folders and files (which would be inside .iso file).


[SIZE="3"]What now?[/SIZE]
Now I need to make an .iso file from folder (which contains all necessary files).
So I googled & asked in #xubuntu channel in IRC. I found following:

[Also found this thread (2011 March): Creating an ISO from a VIDEO_TS directory]("http://ubuntuforums.org/showthread.php?t=1701026")
> **cchhrriiss121212 said:**
> I've used xfburn many times for this task, and it has yet to fail on me:
Select new data composition
Add the video_ts and audio_ts
Burn
I have different case... :frown:

And some others (didn't really find answer to my issue):
[LIST]
[*][making a bootable DVD from non ISO file?]("http://ubuntuforums.org/showthread.php?t=1765243")
[*][creating bootable ISO image]("http://ubuntuforums.org/showthread.php?t=1821210")
[*][Compressed folder -> ISO for BIOS flash???]("http://ubuntuforums.org/showthread.php?t=1488091")
[/LIST]


[COLOR="Purple"]**I concluded that I have 2 options:**[/COLOR]
[LIST]
[*]Xfburn
[*]Terminal - "genisoimage" command
[/LIST]

Guy called Sysi (in IRC) provided me with this guide --->
[[COLOR="Navy"]**Using Xfburn to Create ISO Images (Xfce)**[/COLOR]]("http://www.tuxarena.com/static/tut_iso_ubuntu.php#xfburn")



I tried it. I think I found a bug, read what happened in last 4 times --->


**1st try:**
Presse "Add" 'nLite XP' directory, there was small window named "Adding files to th.." in bottom there was bar which slowly added megabytes when it got to ~170 or so MB, that bar flashed (very fast) to 215.22 MB (folder is 215.6MB big)


**2nd try:**
This time in bottom bar megabytes were counting faster. But around 176MB window "Adding files to th" closed and that all... 


So, I File > Close composition & New Data composition
something weird happened - Xfburn just closed.. I had to open it again. :shock:


**3rd try:** Around 175MB bottom screen (bar) flashes (very fast) and it says again 215.22MB

Also it was like Xfburn was still loading something at bottom bar (215.22MB screen) wasn't static (meaning it moved constantly; that's why I say "still loading")

**4rd try:** Around 50MB Xfburn just closes and nothing happens.
**_See attachments!_**


So definitely something is wrong (bug?). I just can't make an .iso with Xfburn that way... ](*,)
And if so, it's a bug, how can I file one? Where? What info I need to provide?
[COLOR="DarkRed"][B]Can someone explain how one test and file bug? :-k
[/B][/COLOR] (want to slowly get involved helping too) 



Also I still need to create that .iso file, so I could try to **install that XP on Virtual Box**. ;)
I could try meanwhile to use [COLOR="Purple"]**"genisoimage"**[/COLOR] command in terminal, but need some help with that.
I typed:
```

man genisoimage

```
and got almost 2000 lines of manual :D
A bit too much for me..


[&#65279;Create an .iso from the ubuntu files (2007):]("http://ubuntuforums.org/showthread.php?t=499730")
> **Herman]
I also know that you can make a folder full of files into an .iso file using the mkisofs command, but when I type 'man mkisofs' in a terminal these days I get: genisoimage instead.

&#65279 said:**
> **be able to create .iso images that way for making bootable CDs**[/COLOR] if we learn the right options to put with one of those the commands.

The mkisofs command is **being replaced with the genisoimage command** in Linux, 
I don't know why, but we're being encouraged to switch over to genisoimage from now on. The options seem to all be the same, and the manual pages look almost the same too.


&#65279;I have added a new article about making .iso files here, [genisoimage commands for making .iso file to make CDs and DVDs]("http://users.bigpond.net.au/hermanzone/p10.htm#genisoimage_commands")..

Link is outdated..
Need some help guys :)


P.S. If you didn't understand something (especially those 4 tries with Xfburn) - just ask. I will try to explain it better. 
This guy explained it very good --->
> **amjjawad said:**
> We can read your post but we CAN NOT read your mind.

So please ask if my post is confusing. ;)

---

### Post by TeoBigusGeekus on 2011-08-14
To create an iso image of a directory
```
mkisofs -o imagename.iso -J /path/foldername/
```

---

### Post by gigenieks on 2011-08-14
There is no "mkisofs" command, I have only "genisoimage".

---

### Post by TeoBigusGeekus on 2011-08-14
Can you post us the output of
```
which mkisofs
```
?

---

### Post by gigenieks on 2011-08-14
Sure:
```

/usr/bin/mkisofs

```
it appears I was wrong.

Before that typed:
```

man mkisofs

```
got:
```

No manual entry for mkisofs

```

---

### Post by TeoBigusGeekus on 2011-08-14
You have mkisofs installed; proceed with the command I gave you.

---

### Post by gigenieks on 2011-08-14
O.K. here is how it went --->

typed following
```

gigenieks@juris-study-pc:~$ mkisofs -o "nLite XP SP3" -J /home/gigenieks/Downloads/"nLite XP"

```
[See output for my command!]("http://pastebin.ubuntu.com/665778/")

So it made a file in /home/gigenieks named "nLite XP SP3"
[COLOR="Purple"]**Kind: Unknown**[/COLOR] (doesn't detect like .iso)

O.K., whatever. Proceed making Virtual Machine with newly created file by mkisofs. 
When I had to choose "a virtual CD/DVD drive" it didn't show "nLite XP SP3" I had to set **"All files"** to see it.

And, finally, when I tried to launch (install that XP) I got error.

Added pictures in attachment, see them for details!

---

### Post by TeoBigusGeekus on 2011-08-14
Try again with
```
mkisofs -o "nLite XP SP3.iso" -J "/home/gigenieks/Downloads/nLite XP/"
```

---

### Post by gigenieks on 2011-08-14
Done.
Kind: raw CD image

Virtual Box didn't show previous error. And also didn't start install.
My guess is that .iso is not bootable.
See attach.

---

### Post by TeoBigusGeekus on 2011-08-14
> **gigenieks said:**
> 
My guess is that .iso is not bootable.


In that case, see [this]("http://www.g-loaded.eu/2007/04/25/how-to-create-a-windows-bootable-cd-with-mkisofs/").

---

### Post by gigenieks on 2011-08-14
I'm not that good with Linux yet.
It's too complicated, didn't understand what **exactly** I have to type!

And this part is like chinese for me:
> 
This tip assumes that the boot image which is used in the Microsoft bootable CDs is available and that it has been placed in a cdboot/ subdirectory under the windows installation files root dir:

    ```
cdboot/msboot.img
    other_dir/some_other_file
    file1
    file2
```

:confused:

---

### Post by gigenieks on 2011-08-15
bump

---

### Post by gigenieks on 2011-08-15
Did I report bug fine? 
[https://bugs.launchpad.net/ubuntu/+source/xfburn/+bug/826675](https://bugs.launchpad.net/ubuntu/+source/xfburn/+bug/826675)

(see my #1 post in this thread)

---

### Post by gigenieks on 2011-08-15
bump

---

### Post by anewguy on 2011-08-15
I'll need to do a LOT of reading to see if I can help.  In the mean time, keep in mind a forum rule (I was written up for violating it a few years ago):  Don't bump your thread more than once in 24 hours.  If you have USEFUL information to post, do so, but don't just bump the thread.  The reason is that it's an all-volunteer forum with people of all levels of skill.  Someone who knows how to help you may not be available at any given time.  And remember - everyone had an "emergency". ;)

I'll start looking around and see what I can find.  It will probably take me quite a while to get back to you as I'm going to be in and out.  I also can't say I'll have a solution when I do post back.

Dave ;)

---

### Post by anewguy on 2011-08-17
I also tried what was in that link with no good results:

[LIST]
[*]made a folder called testiso in my home folder
[*]downloaded the win32 zip file as instructed and extracted all to the new folder (~/testiso)
[*]created a subfolder called cdboot (~/testiso/cdboot)
[*]copied my iso image to that folder
[*]just copied and pasted the command from the link into a terminal window, and got the following:
[LIST]
[*]genisoimage: Permission denied. Unable to open disc image file '../winsp.iso'.
[/LIST]
[*]I also noticed that when this ran it was going through all kinds of my linux folders (the image file is the iso for 11.04 livecd - didn't expect it to boot correctly, but I was using it to test this process).[/LIST]

When I ran this prefaced with sudo it then claims it can't find the iso image file.

I noticed the date from this is 2007.  I suspect there is either something in this process that no longer applies or else something else is not being explained that needs to happen.

I will need to do a lot more research before I can know much about any of this.  For instance, why are Windows exe's being included?  Can't if just be some type of Linux auto-boot disk?

I've looked at the 10.04LTS desktop LiveCD showing hidden files, and I can't for the life of me figure out how it boots stand alone.  I know all about autorun.inf for the Windows side, but what exactly happens when the system boots the LiveCD?  Couldn't this same procedure be used to build the bootable CD the OP wants?

Hoping some one can explain this and therefore help the OP.

Dave ;)

---

### Post by anewguy on 2011-08-17
Try following this link instead:

[http://www.stchman.com/boot_cd.html]("http://www.stchman.com/boot_cd.html")

I did as it said - downloaded the dos boot floppy image, then copied the files from a non-bootable Windows 98SE CD into the same folder.  Then I ran k3b, pointing it to the dos boot floppy image first, then to the Windows 98SE files.  Burned a CD and it auto-booted to the DOS command line.  If I had wanted to I could have installed Windows 98SE then.

What I don't think this provides is a method for your own autoexec.bat to auto-start some process.

I'm going to assume that the slip-streaming you are doing also creates some kind of file to start the installation?

For you, do the above, but replace the Windows98SE stuff with the folder containing your slip-streamed Windows XP.  After you burn it, boot it, then go to the drive specified by the MSCDEX (?) line.  You should see all of your Windows XP stuff.

Dave ;)

---

### Post by gigenieks on 2011-08-17
OK, I tried to do that in Kubuntu:

Made a .iso file from folder:
```

mkisofs -o "nLite XP SP3.iso" -J "/home/gigenieks/Downloads/Virtual Box/nLite XP in Kubuntu/"

```

Same (if one want to check output it is here - [paste.ubuntu.com]("http://paste.ubuntu.com/668544/"))

I still think that it is possible to make bootable .iso using terminal.
Maybe those errors have to do something with that:
> **'Terminal']
Warning: creating filesystem with Joliet extensions but without Rock Ridge
         extensions. It is highly recommended to add Rock Ridge.

I: -input-charset not specified, using utf-8 (detected in locale settings)
[/QUOTE]

[QUOTE]
genisoimage: Directories too deep for '/home/gigenieks/Downloads/Virtual Box/nLite XP in Kubuntu/I386/ASMS/5100/MSFT/WINDOWS/SYSTEM/DEFAULT' (7) max is 6 said:**
> 
I realy have no clue.. :confused:
Someone?


Anyway, when I tried to install with newly created .iso in Virtual Box - same result as in [post #7 (see picture)]("http://ubuntuforums.org/showpost.php?p=11150967&postcount=9")


Thank you, anewguy, for link, but it is not what I need.
[QUOTE]
Hit the "Burn" button.
After the burn process is done the CD is now bootable!


I don't need bootable CD or DVD disc. I need bootable .ISO (is there such thing as bootable .iso and non-bootable .iso? :confused:), because Virtual Box is installing OS with .ISO without directly inserted CD in CD/DVD drive.

It would probably work, if I would install XP in dual-boot, but I don't need that. [COLOR="DarkRed"]**_I need to install slip-streamed XP [COLOR="Navy"]in Virtual Box environment.[/COLOR]_**[/COLOR] ;)

---

### Post by anewguy on 2011-08-17
Well, you DIDN'T do what the link I posted said.  You need to download the bootable floppy image (no, you're not making a floppy!) and extract the image file to some folder.  Now put the FILES AND FOLDERS into this same folder.  Start k3b - follow the instructions for selecting the boot image, then add the file and folders.  Burn the result - but the output CAN BE AN ISO IF YOU JUST SELECT IT.

Nowhere were you supposed to use mkisofs - you are to use k3b instead.  Please read the link, and read my post.  Forget what you were using before - try this.  You can direct the output of k3b to an ISO image file which  will boot in the VM - probably to a DOS prompt.  At that point just execute the batch file or program that was supposed to be auto-started on your previous attempts - it should start the install of XP within a virtual machine.

========

FOR THE FOLLOWING YOU CAN USE ISO IN PLACE OF CD:

Is it going to just boot and start the XP install?  No.  But it will load the floppy image, boot it and run it's autoexec.bat which will include the cd drivers and load mscdex to provide the access.  At that point just cd to the appropriate folder (if needed) on the cd, and then execute the installation batch file, program, whatever.  It will at least let you do that.  To do more than that, I think you would have to create your own bootable floppy image with an updated autoexec to log to your cd and execute the installation program/batch file.

There is also the other way - probably preferred - where the boot sector is created on the CD pointing to whatever must boot your system and execute you installation program/batch file.  I have not found any more information on doing this.

The point is that if you follow the instructions, you'll have a bootable CD.  You will be able to start your installation process.

=====

All of the above referencing a CD can be an ISO if you follow the instructions and just tell k3b to output to an image file.

EDIT:  Just in case you don't know, an ISO is just an image file of something like a CD.  Most CD burning programs, like k3b, let you burn to an image file (you can later burn the file to a CD if you want to).  To make a CD itself bootable, there is very specific information that has to be in the first block of the CD.  This isn't as simple as it might sound.  This is why I recommend using the way here - the bootable CD then manually specifying what to run.  The boot block of the CD is created by k3b when you specify it is to be bootable and to use the floppy image as what to boot.  That floppy image, if you're not familiar with the old days of DOS, contains the system files needed to boot up DOS.  It will also have a customized autoexec.bat file - a command list of things to do after the system is booted.  That autoexec file is where you would normally have things like "d:\win98\setup.exe" to automatically start the Win98SE installation in the sample I provided above.  If you need a custom autoexec.bat file, you'll need the actual files on the bott floppy image, and then you'll have to create an ISO image of the floppy after you've made the changes.  So, don't make an ISO and THEN try to make it bootable - the ISO is the image.  So the files, etc., you make the ISO from must include everything for boot.  If you follow the link and my example posted prior, you will find this method easy to use without needing to learn a lot of extra stuff and it will still accomplish what you want.

Remember:  Get the bootable floppy image file and extract the image file.  Put all the files you want on the CD image in a folder.  Using k3b, start new project, say you want it bootable and point it to the extracted bootable floppy image.  The just copy all the files/folders you want on the CD image into the k3b file window, then select burn and change the output to file (ISO or IMG file).  Now start up your vm, pointing the CD to virtual CD image (the ISO or IMG file created from the k3b burn).  It will boot.

---

### Post by gigenieks on 2011-08-18
Thank you! Will reply as soon as I can. (seems like few days; right now a bit bussy)

---

### Post by anewguy on 2011-08-24
Have you had time to do this?  Hopefully it did what you needed done.

Dave ;)

---

