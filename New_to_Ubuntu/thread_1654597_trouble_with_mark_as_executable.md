---
title: "trouble with mark as executable"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by x-hex-x on 2010-12-28
Hey my name is Hex and i am fairly new to Linux, ive had it for just over a month now and know some stuff here and there but i digress, to the problem...

before i changed to linux i was on windows 7 and used a program called camtasia studio, unfortunately i was un able to convert my recorded files before i switched, so my question is this is there a program i can use to convert the .camrec files to .avi

if not that id obviously just run camtasia through wine, but for some reason i cant mark the camtasiastudio.exe file as executable and when i click it it just unclicks even as root, ive read through several threads with no luck, if i could at lest get some insight to my problem i would be more than happy, thank you and sorry for the wall of text. 

all the best hex.

---

### Post by davidmohammed on 2010-12-28
.camrec is a proprietary format - you need to use camtasia to convert it.

looking at [winehq]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=7983") there is one particular version that works.  However saying that, wine has move on since that version on that list - so either wine1.2 or wine1.3 may work better.

---

### Post by mcduck on 2010-12-28
> **x-hex-x said:**
> Hey my name is Hex and i am fairly new to Linux, ive had it for just over a month now and know some stuff here and there but i digress, to the problem...

before i changed to linux i was on windows 7 and used a program called camtasia studio, unfortunately i was un able to convert my recorded files before i switched, so my question is this is there a program i can use to convert the .camrec files to .avi

if not that id obviously just run camtasia through wine, but for some reason i cant mark the camtasiastudio.exe file as executable and when i click it it just unclicks even as root, ive read through several threads with no luck, if i could at lest get some insight to my problem i would be more than happy, thank you and sorry for the wall of text. 

all the best hex.
Is the file on your linux hard drive when you try to set it to executable?

Windows filesystems (FAT and NTFS) don't support such file ownerships and permisisons like they are used on Linux/Ubnix operating systems. And all optical medias are read-only filesystems as well, so you can't change permissions of those either.

Anyway, you don't really need to set a .exe file executable to run it with Wine. It's not the .exe file you execute, but Wine instead. ;)

You can simply right-click the .exe file and choose to open it with Wine. Or open a terminal and run "wine /path/to/yourprogram.exe"

---

### Post by x-hex-x on 2010-12-28
[/QUOTE]Anyway, you don't really need to set a .exe file executable to run it with Wine. It's not the .exe file you execute, but Wine instead. ;)

You can simply right-click the .exe file and choose to open it with Wine. Or open a terminal and run "wine /path/to/yourprogram.exe"[/QUOTE]

all ready tired that and also the file i wish to open with wine is camtasiastudio.exe its installed on my external harddrive

---

### Post by davidmohammed on 2010-12-28
open a terminal window

type 

wine <path to filename.exe>

copy and paste the display output here.

---

### Post by x-hex-x on 2010-12-28
john@Coheed:~$ wine ~/media/Butler/pcJUNK/CamtasiaStudio.exe
Warning: could not find DOS drive for current working directory '/home/john', starting in the Windows directory.
wine: cannot find '/home/john/media/Butler/pcJUNK/CamtasiaStudio.exe'

i know it says can not find but i have double and triple checked that, what i typed was correct

Edit: Butler is the name for my external harddrive

---

### Post by universaly on 2010-12-28
Hey hex, im just as new as you are to the whole linux world, but here is a suggestion!
download virtual box and install your windows 7 there. then you can install your camstia and you know the rest.

---

### Post by davidmohammed on 2010-12-28
try 

cd ~/media/Butler/pcJUNK/

then

wine CamtasiaStudio.exe


also 

type winecfg
what version of wine is displayed in the About tab.

try also

cd ~/
mv .wine .wine_backup
winecfg

then repeat the first two commands at the top

---

### Post by davidmohammed on 2010-12-28
...


the patch ~/media... seems strange

are you sure its not

/media/....

i.e. missing the ~/

---

### Post by x-hex-x on 2010-12-28
Right info from what i just tried, also tried with out the ~/ and just /media but still the same outcome, also tried opening the camtasiastudio.exe by right clicking then open with wine and nothing happens as its not marked as executable 
also my wine is 1.2.1

john@Coheed:~$ cd ~/media/Butler/pcJUNK/
bash: cd: /home/john/media/Butler/pcJUNK/: No such file or directory
john@Coheed:~$ wine CamtasiaStudio.exe
Warning: could not find DOS drive for current working directory '/home/john', starting in the Windows directory.
wine: cannot find L"C:\\windows\\system32\\CamtasiaStudio.exe"
john@Coheed:~$ winecfg
Warning: could not find DOS drive for current working directory '/home/john', starting in the Windows directory.
john@Coheed:~$

---

### Post by daimaru on 2010-12-28
i'm not sure you can start a windows program.exe file with wine, that was installed under windows to some drive.. **[COLOR=Red]you have to get the camtasia setup file[/COLOR]** and execute that with wine , install camtasia , hope it works in wine and then play your recorded videos.

---

### Post by x-hex-x on 2010-12-28
> **daimaru said:**
> i'm not sure you can start a windows program.exe file with wine, that was installed under windows to some drive.. **[COLOR=Red]you have to get the camtasia setup file[/COLOR]** and execute that with wine , install camtasia , hope it works in wine and then play your recorded videos.

okay tried just running the installation program for camtasia but once again same problem, its saying its not set as executable but its not letting me actually set it as executable, hmmmmm

---

### Post by davidmohammed on 2010-12-28
Is the installation on a CD?

If so, copy the contents of the CD into a folder on your desktop.
You can then mark the "setup.exe" or whatever that starting file is as executable - right click - properties - set to execute in one of the tabs displayed.

---

### Post by theozzlives on 2010-12-28
> **davidmohammed said:**
> try 

cd ~/media/Butler/pcJUNK/

then

wine CamtasiaStudio.exe


also 

type winecfg
what version of wine is displayed in the About tab.

try also

cd ~/
mv .wine .wine_backup
winecfg

then repeat the first two commands at the top

I don't think the OP should mark the thread as solved until they find a solution that works.

I don't mess with wine, I just keep a Windows 7 box for Windows programs. Dual boot and Virtual Box are two other options.

---

### Post by x-hex-x on 2010-12-28
> **davidmohammed said:**
> Is the installation on a CD?

If so, copy the contents of the CD into a folder on your desktop.
You can then mark the "setup.exe" or whatever that starting file is as executable - right click - properties - set to execute in one of the tabs displayed.

no the installation is on butler, but every time i try to mark any folder in butler as executable it does not work even as root

---

### Post by davidmohammed on 2010-12-28
a blanket statement such as "dont mess with wine" seems a bit off - especially to the wine developers.

I find its worth messing around for a short while seeing if the windows program works in wine.  Only when this fails would I use such a heavyweight option such as virtualbox.

---

### Post by davidmohammed on 2010-12-28
> **x-hex-x said:**
> no the installation is on butler, but every time i try to mark any folder in butler as executable it does not work even as root

previously you tried but the cd command said could not find the directory...

should you be typing

cd /media/Butler/pcJUNK/


to find the correct folder?

I dont know what this exe is - is it a single executable that you run or do you have to install the application via a setup.exe?

if its the former - just copy the exe to ubuntu
if its the latter - copy the installation disk/folder/whatever to ubuntu.

put it into a folder you know
cd ~/<folder>
make the exe executable
chmod +x <exe name>

then use wine
wine <setup.exe/application.exe>

---

### Post by x-hex-x on 2010-12-28
> **davidmohammed said:**
> previously you tried but the cd command said could not find the directory...

should you be typing

cd /media/Butler/pcJUNK/


to find the correct folder?

I dont know what this exe is - is it a single executable that you run or do you have to install the application via a setup.exe?

if its the former - just copy the exe to ubuntu
if its the latter - copy the installation disk/folder/whatever to ubuntu.

put it into a folder you know
cd ~/<folder>
make the exe executable
chmod +x <exe name>

then use wine
wine <setup.exe/application.exe>

its just the program not the setup so tried moving it but with it being installed to butler, when its move it wont work, also just tried cd /media/Butler/pcJUNK/ and said no such file or directory, does any one know how i can mark it as executable?

---

### Post by davidmohammed on 2010-12-28
It sounds like you have installed this on some PC called butler.

Marking it as executable will not help you.  You need to reinstall it in wine from the original media (or copy the media contents to ubuntu)

If you head off to the virtualbox route as the previous poster recommended - you will still need the installation media to install within the windows guest.

---

### Post by x-hex-x on 2010-12-28
> **davidmohammed said:**
> It sounds like you have installed this on some PC called butler.

Marking it as executable will not help you.  You need to reinstall it in wine from the original media (or copy the media contents to ubuntu)

If you head off to the virtualbox route as the previous poster recommended - you will still need the installation media to install within the windows guest.

yeah manged to install it on linux but now when i go to play files in it it says no codec available to render the file, any thoughts???

---

### Post by davidmohammed on 2010-12-28
googling that error brings up various stuff.

suggest type

winetricks

then install windows media player 10 from the window that is displayed.

---

### Post by x-hex-x on 2010-12-28
thing is if i install wmp, it wont be able to play the files as there camrec, and i cant convert them as the codec thing is missing i think it may be flash i need for it i dont know, its a wild guess

---

### Post by davidmohammed on 2010-12-28
you have installed camrec - correct?

Therefore you can install WMP as well as Flash as well - it wont affect the camrec install.

You can install both WMP and Flash from winetricks.

---

### Post by wojox on 2010-12-28
Add Medibuntu Repository AND the medibuntu keyring:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

Install non-free-codecs:

```
sudo apt-get install non-free-codecs
```

This is what you get:

```
cabextract gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse libavcodec-extra-52 libavutil-extra-50 libfaac0 libmjpegtools-1.9 libmp3lame0 libmp4v2-0 libopenjpeg2 libquicktime1 libx264-98 libxvidcore4 non-free-codecs ttf-mscorefonts-installer ubuntu-restricted-extras unrar w32codecs
```

---

### Post by x-hex-x on 2010-12-28
finally got it don, the camrec files dont play in camtaasia but i can now convert them to avi then i have to use avidemux to play them correctly and properly, thank you to every one that helped sorry for being a pain

---

### Post by kroq-gar78 on 2010-12-28
If your problem is solved, mark this thread as solved by selecting "Thread tools" near the upper right of the top post and then "Mark this thread as solved"

---

