---
title: "Linux headstart !!"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by vamsi_spr on 2010-12-23
hello guys , am very like noob to the Linux world , i recently installed ubuntu 10.10 on my laptop(along with already installed windows7) , so i have certain queries ... 

(i) I bought fifth edition of 'running linux' , is this book enough to gain good knowledge on all flavors of linux and can i master ubuntu too ??

(ii) I installed wine and i have no clue how to use it , can i find any tutorial on wine ??

(iii) i want to set a private and secure wi-fi network so that i can use it even on windows7.

---

### Post by mastablasta on 2010-12-23
> **vamsi_spr said:**
> hello guys , am very like noob to the Linux world , i recently installed ubuntu 10.10 on my laptop(along with already installed windows7) , so i have certain queries ... 
 
(i) I bought fifth edition of 'running linux' , is this book enough to gain good knowledge on all flavors of linux and can i master ubuntu too ??
.
 
Free books available on the net to learn more :
 
Ubuntu Manual
Ubuntu pocket guide
Linux command line (for advanced info on commands)
 
> 
(ii) I installed wine and i have no clue how to use it , can i find any tutorial on wine ??
 
 
Each application has it's own wine tutorial available on how to install it. check here for your application compatibility and tutorial: [http://appdb.winehq.org/](http://appdb.winehq.org/)
> 
(iii) i want to set a private and secure wi-fi network so that i can use it even on windows7.
Network is usually set on router. if you mean file sharing - it is done the same/similar way as in windows. right click on folder you want to share, select propperties and define sharing policy in appropriate menu.

---

### Post by vamsi_spr on 2010-12-23
Thank u masta but can u be more specific and lucid on wine ?? ...I installed wine in order to run my wordweb on it but it gives the following error "The file '/media/4E7EE0A17EE08357/Program Files/WordWeb/wwnotray.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit." !!

---

### Post by matt_symes on 2010-12-23
Hi

> **vamsi_spr said:**
> Thank u masta but can u be more specific and lucid on wine ?? ...I installed wine in order to run my wordweb on it but it gives the following error "The file '/media/4E7EE0A17EE08357/Program Files/WordWeb/wwnotray.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit." !!

Right click on the executable in the nautilus file browser and select properties then select the permissions tab. Check the "Allow executing file as program" check box and then try again.

You can also do this  from the terminal. Type (case sensitive)

```
chmod 755 /path/to/executable.exe
```in this case it would be 

```
chmod 755 /media/4E7EE0A17EE08357/Program\ Files/WordWeb/wwnotray.exe
```

Notice the escaped space above or you can type

```
chmod 755 "/media/4E7EE0A17EE08357/Program Files/WordWeb/wwnotray.exe"
```

without the escaped space.

Kind regards

---

### Post by vamsi_spr on 2010-12-23
Thank u matt , i tried clicking on the check box but the tick mark flashes and disappears , then i tried the terminal method but the problem still persists :( !!

---

### Post by matt_symes on 2010-12-23
Hi

What is the output of (at a terminal)
[FONT=monospace]

[/FONT]```
ls -l /media/4E7EE0A17EE08357

```

That is a small L above -(small L). How is the drive formatted? NTFS, FAT, EXT..

Kind regards

---

### Post by vamsi_spr on 2010-12-23
output:
-rw------- 1 vamsi vamsi         24 2009-06-11 03:12 autoexec.bat
-rw------- 1 vamsi vamsi         10 2009-06-11 03:12 config.sys
lrwxrwxrwx 2 vamsi vamsi         60 2009-07-14 10:23 Documents and Settings -> /media/4E7EE0A17EE08357/Users
-rw------- 1 vamsi vamsi 1555537920 2010-12-23 12:02 hiberfil.sys
drwx------ 1 vamsi vamsi          0 2010-12-07 09:38 MSOCache
drwx------ 1 vamsi vamsi       4096 2010-11-30 22:26 New folder
-rw------- 1 vamsi vamsi 2074054656 2010-12-23 12:02 pagefile.sys
drwx------ 1 vamsi vamsi          0 2009-07-14 08:07 PerfLogs
drwx------ 1 vamsi vamsi       4096 2010-12-07 09:39 ProgramData
drwx------ 1 vamsi vamsi      12288 2010-12-07 09:47 Program Files
drwx------ 1 vamsi vamsi          0 2010-11-30 21:25 Recovery
drwx------ 1 vamsi vamsi          0 2010-11-30 21:29 $Recycle.Bin
drwx------ 1 vamsi vamsi       4096 2010-12-19 21:24 SampleCodes
drwx------ 1 vamsi vamsi       8192 2010-12-14 09:46 System Volume Information
drwx------ 1 vamsi vamsi       4096 2010-11-30 21:29 Users
drwx------ 1 vamsi vamsi      24576 2010-12-07 09:46 Windows

drive format :NTFS

---

### Post by chaanakya_chiraag on 2010-12-23
There's your problem...NTFS cannot store Linux permissions.  Can you try copying the exe file to your Desktop and *then* try right-clicking it -> Properties -> Permissions -> Allow owner to execute.  Then double-click the exe file *on your Desktop* and you should be good to go.

---

### Post by matt_symes on 2010-12-23
Hi
[FONT=monospace]
Sorry mate. I meant to get the output of (its been a log day)

[/FONT]```
ls -l /media
```Looking to see if you have ownership of the mount point.[FONT=monospace]

[FONT=Verdana]EDIT: Missed the NTFS bit[/FONT][/FONT]

Kind regards

---

### Post by madjr on 2010-12-23
> **vamsi_spr said:**
> hello guys , am very like noob to the Linux world , i recently installed ubuntu 10.10 on my laptop(along with already installed windows7) , so i have certain queries ... 

(i) I bought fifth edition of 'running linux' , is this book enough to gain good knowledge on all flavors of linux and can i master ubuntu too ??



the book will help, but to really be up to date you'll need these websites:

[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
[http://www.phoronix.com/](http://www.phoronix.com/)
[http://www.webupd8.org/](http://www.webupd8.org/)


if you would like to try an open source alternative to wordweb, here it is:
[http://alternativeto.net/software/artha/](http://alternativeto.net/software/artha/)


more on wine:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by vamsi_spr on 2010-12-23
> **matt_symes said:**
> Hi
[FONT=monospace]
Sorry mate. I meant to get the output of (its been a log day)

[/FONT]```
ls -l /media
```Looking to see if you have ownership of the mount point.[FONT=monospace]

[FONT=Verdana]EDIT: Missed the NTFS bit[/FONT][/FONT]

Kind regards
output: drwx------ 1 vamsi vamsi 12288 2010-12-10 10:15 4E7EE0A17EE08357
            drwx------ 1 vamsi vamsi  4096 2010-11-30 21:27 System Reserved

---

### Post by vamsi_spr on 2010-12-23
> **chaanakya_chiraag said:**
> There's your problem...NTFS cannot store Linux permissions.  Can you try copying the exe file to your Desktop and *then* try right-clicking it -> Properties -> Permissions -> Allow owner to execute.  Then double-click the exe file *on your Desktop* and you should be good to go.

Tried ..This time i could tick the checkbox but the file is not running :( !!

---

### Post by vamsi_spr on 2010-12-23
> **madjr said:**
> 


if you would like to try an open source alternative to wordweb, here it is:
[http://alternativeto.net/software/artha/](http://alternativeto.net/software/artha/)



Thanks mate but this link contains wordweb for the same old windows platform, no linux alternative is found.

---

### Post by scorchgeek on 2010-12-23
For me, at least, I have to right-click the executable and select "Open with Wine Windows Program Loader" rather than just double-clicking it.

---

### Post by scorchgeek on 2010-12-23
> **vamsi_spr said:**
> Thanks mate but this link contains wordweb for the same old windows platform, no linux alternative is found.

This program is available through the package manager, try
```
sudo apt-get install artha
```
in terminal.

---

### Post by matt_symes on 2010-12-23
Hi

First that mount point is fine.

Next have you seen

[http://www.winehq.org/](http://www.winehq.org/)

It has a database all apps that will run in wine and it also has documentation for wine.

Looking at you app it should work

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7552&iTestingId=15301](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7552&iTestingId=15301)

Anyhow, when you install wine you first need to configure it. You can do this from the command line by typing 

```
winecfg
```or you can get to it from the wine  menu. Have you done that yet?

Also, you can install from the command line by doing something like this...

```
cd ~/Desktop
wine program_name.exe
```The first command will move you to your desktop and the second command will install a program called program_name.exe into wine. You need to change the directory and program name as required. The advantage of doing it this way is you get any errors displayed i the terminal and it can help you see what is going on.

Have a look at section 3.2 here

[http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f](http://wiki.winehq.org/FAQ#head-f3515230c198befe0279d32c448d9c8da63be66f)

BTW:

After chmoding a file you can see if the executable bit is set by typing

ls -l

That is _*ls dash small L*_. If you get something like this below with the bold x then it is executable for your user. The rest are for group and everyone.

-rw**x**r-xr-x  1 matthew matthew     0 2010-12-23 18:33 wwnotray.exe

Kind regards

---

### Post by vamsi_spr on 2010-12-23
> **matt_symes said:**
> 

```
cd ~/Desktop
wine program_name.exe
```


It gives me the following error :

err:module:import_dll Library wweb32.dll (which is needed by L"Z:\\home\\vamsi\\Desktop\\wweb32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\vamsi\\Desktop\\wweb32.exe" failed, status c0000135

---

### Post by vamsi_spr on 2010-12-23
> **scorchgeek said:**
> This program is available through the package manager, try
```
sudo apt-get install artha
```in terminal.

Thanks mate artha is a useful alternative but it lacks the feature of saving words :( !!

---

### Post by matt_symes on 2010-12-23
Hi

Sorry to hear you are still having problems. I am going to try to install it on my laptop. 

So first things first.

The program you want to install is called wordweb?

I have found a web site here you can download it from 

[http://wordweb.info/free/](http://wordweb.info/free/)

but there are two versions; the free version and the pro version.

What version are you trying to install and is this the correct program?

If it is the correct program is it the correct program version?

Kind regards

---

### Post by vamsi_spr on 2010-12-23
> **matt_symes said:**
> Hi

Sorry to hear you are still having problems. I am going to try to install it on my laptop. 

So first things first.

The program you want to install is called wordweb?

I have found a web site here you can download it from 

[http://wordweb.info/free/](http://wordweb.info/free/)

but there are two versions; the free version and the pro version.

What version are you trying to install and is this the correct program?

If it is the correct program is it the correct program version?

Kind regards

Its the free version and if u haven't used it before, it really rocks !!

---

### Post by matt_symes on 2010-12-24
Hi

Right i have just downloaded the free version here

[http://www.wordweb.co.uk/free/](http://www.wordweb.co.uk/free/)

It takes me to this page here

[http://download.cnet.com/WordWeb/3000-2279_4-10003201.html?part=dl-WordWeb&subj=dl&tag=button](http://download.cnet.com/WordWeb/3000-2279_4-10003201.html?part=dl-WordWeb&subj=dl&tag=button)

and i select download now. This downloads a file called wordweb6.exe into my ~/Downloads folder. 

```
matthew@matthew-laptop:~/Downloads$ ls -l wordweb6.exe 
-rw-rw-rw- 1 matthew matthew 18711752 2010-12-24 04:54 wordweb6.exe
matthew@matthew-laptop:~/Downloads$ 
```

In the terminal i then make it executable and the check it.

```
matthew@matthew-laptop:~/Downloads$ chmod 777 wordweb6.exe 
matthew@matthew-laptop:~/Downloads$ ls -l w*
-rw**x**rw**x**rw**x** 1 matthew matthew 18711752 2010-12-24 04:56 wordweb6.exe
matthew@matthew-laptop:~/Downloads$
```

Notice the bold x above.

I then move it into the C drive under wine.

```
mv wordweb6.exe ~/.wine/drive_c
```

It seems to need this step.

I then run it under wine

```
matthew@matthew-laptop:~/Downloads$ wine ~/.wine/drive_c/wordweb6.exe 
```

It then runs the installer and installs the application. I can then run it from Applications->Wine->Program Files->WordWeb

See attached screen shot. Does that look correct?

Kind regards

---

### Post by vamsi_spr on 2010-12-24
but i already have that .exe file :O

---

### Post by vamsi_spr on 2010-12-24
> **matt_symes said:**
> Hi

Right i have just downloaded the free version here

[http://www.wordweb.co.uk/free/](http://www.wordweb.co.uk/free/)

It takes me to this page here

[http://download.cnet.com/WordWeb/3000-2279_4-10003201.html?part=dl-WordWeb&subj=dl&tag=button](http://download.cnet.com/WordWeb/3000-2279_4-10003201.html?part=dl-WordWeb&subj=dl&tag=button)

and i select download now. This downloads a file called wordweb6.exe into my ~/Downloads folder. 

```
matthew@matthew-laptop:~/Downloads$ ls -l wordweb6.exe 
-rw-rw-rw- 1 matthew matthew 18711752 2010-12-24 04:54 wordweb6.exe
matthew@matthew-laptop:~/Downloads$ 
```In the terminal i then make it executable and the check it.

```
matthew@matthew-laptop:~/Downloads$ chmod 777 wordweb6.exe 
matthew@matthew-laptop:~/Downloads$ ls -l w*
-rw**x**rw**x**rw**x** 1 matthew matthew 18711752 2010-12-24 04:56 wordweb6.exe
matthew@matthew-laptop:~/Downloads$
```Notice the bold x above.

I then move it into the C drive under wine.

```
mv wordweb6.exe ~/.wine/drive_c
```It seems to need this step.

I then run it under wine

```
matthew@matthew-laptop:~/Downloads$ wine ~/.wine/drive_c/wordweb6.exe 
```It then runs the installer and installs the application. I can then run it from Applications->Wine->Program Files->WordWeb

See attached screen shot. Does that look correct?

Kind regards

gives the following error :

err:module:import_dll Library wweb32.dll (which is needed by L"C:\\wweb32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\wweb32.exe" failed, status c0000135

---

### Post by matt_symes on 2010-12-24
Hi

Did you follow all my steps exactly? From start to finish?

I ask because using all those steps i installed the program as the screen shot shows.

EDIT: Read the post below first as well.

Kind regards

---

### Post by matt_symes on 2010-12-24
Hi

Also have you configured wine?

Applications->wine->Configure wine.

On the applications page set windows version to windows XP.
On the audio tab select alsa check box; hardware acceleration -> emulation
On the drives tab did you add ../drive_c ( and any other drives you want) (what does auto detect provide)

Kind regards

---

### Post by vamsi_spr on 2010-12-24
yes , except that i did it with already installed file ...anyways u gave command to move the file to c_drive....there is no drive named c i could see and there are drives named file system and system reserved can i know how it works in linux ??

---

### Post by matt_symes on 2010-12-24
Hi

It's not c_drive; it also not c; it's drive_c. One word.

Open nautilus. Places->Home directory.

Press ctrl and h at the same time.

This will show the hidden files. Look for a directory called .wine (that is dot wine) and double click it.

Inside that folder is another folder called drive_c. Double click on that folder and place the executable inside there.

Kind regards

---

### Post by vamsi_spr on 2010-12-24
whats nautilus ?

---

### Post by chaanakya_chiraag on 2010-12-24
It's the thing that lets you look at your files...as matt said, click on Places->Home

---

### Post by matt_symes on 2010-12-24
I have help the OP with an IM session so this thread is [SOLVED]

---

### Post by madjr on 2010-12-24
> **vamsi_spr said:**
> Thanks mate artha is a useful alternative but it lacks the feature of saving words :( !!

why dont you ask for the feature you need?

open source is about participation, even if its just to suggest features for future versions or give some support to people in need :)

---

