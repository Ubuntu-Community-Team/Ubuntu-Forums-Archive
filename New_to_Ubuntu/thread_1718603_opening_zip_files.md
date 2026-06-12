---
title: "opening zip files"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by rootessa on 2011-03-31
I'm beginning to think I'm just never going to understand 
linux. 5 months and I'm still confused. I've downloaded 10 zip files to unbuntu 10.10. which I'm trying to figure out how to open. Seems if you look 10 places online for linux instructions you find 10 different answers! 5 months and I still can't update Java but that's a different day!

SO...... I looked for info and saw  I'm supposed to install zip and unzip thru the terminal. I tried that and it's already installed. I've just updated to 10.10 if that matters.
-Looked for directions as to how to open the files and found:
     -double click file
     -open
     - click extract
      -choose folder to unzip files into
     -window will popup w/ progress bar
OK so all that went as it should have. It said something like extraction successful at that point. The instructions said I'd then see a button which would take me to extraction folder. That wasn't an option offered. So now I don't have any idea what I'm supposed to do next. I've tried several things and just end up feeling like a dog chasing it's tail. I'd really appreciate any suggestions. Giving up isn't really an option. :D Thanks in advance!

---

### Post by wojox on 2011-03-31
The extracted folder should be in the same directory as the .zip file. Press Ctrl+H to see if it's hidden.

---

### Post by Enigmapond on 2011-03-31
You need to install rar, unrar, and ubuntu-restricted-extras. This should fix both your zip and java problems.

---

### Post by vanadium on 2011-03-31
In a fresh, standard Ubuntu install, you can simply unzip a zip file by right-clicking it and choosing "Extract here". All files in the archive will be extracted into a folder with the same name as the zip file (without the zip extension).

Double clicking a zip file will open it. With drag-and-drop to a folder, you can extract individual files. 

This feature is there by default.

---

### Post by rootessa on 2011-03-31
Thanks! SO, I installed rar, unrar and ubuntu restricted. I did the "which" at the terminal to make sure they installed. Restarted the computer,went back thru the whole process of trying to open the zipfile and when it got tothe extracting bar it couldn't do it and I got an error message which I was going to share here but the computer crashed and I lost the message. Since I've now spent 6 hours trying to accomplish this simple task I'm not going to try it again today. The ubuntu restricted info did say it would install 
java. I tried to open the application I've been unable to open and still nothing. still doesn't work. As I was trying to open the zip file for the umpteenth time, it occured to me that I have numerous zip files fromthe same person, same source as the ones I'm currently trying to open. I didn't have any problem opening them in the same manner as the ones I've tried to open today. The only difference is that I've updated to 10.10 since then. I had a problem with my sound after the update which I figured out on my own. Wondering if this could be the cause of this problem? If there was a smiley pulling out it's hair it would be inserted here ------>:confused:   lol! }(*,)

---

### Post by wolfen69 on 2011-03-31
Try
```
sudo apt-get install p7zip-full
```
then right click "extract here".

---

### Post by rootessa on 2011-04-02
Well, Thanks again! I've had 3 days of Internet problems so just getting back to this project today.I've tried everything to open these files and still can't. I have 10 other zip files from the same source as the ones I'm trying to open (also 10) and those I can open without any problem. Of the 10 new ones, I did get one open and that one is a video which works. Another of the 10 is a camtasia video which I can get the file open (finally) but  the video doesn' t work....meaning, I have a file with a camtasia logo and nothing else. I suspect they're all camtasia videos.
These are videos which have been sent and sold to others multiple times so at this point, I can only conclude that there's a problem with the way this machine has downloaded them. Back to the drawing board. I'm thinking I need to dump the files and try again. omg this is SO frustrating!

---

### Post by rootessa on 2011-04-02
downloaded zip file again. Extracted. Says extraction successful. Click to open.  Document viewer pops up with red bar which says unable to open document. zip file archive not supported. This tells me it's trying to open the file using the wrong viewing format? Grrrrrrr!

---

### Post by rootessa on 2011-04-03
Thank you.I've given up.

---

### Post by CleveRuse on 2011-06-08
Just for the record ...ur not the only one. I'm running 11.04 (Natty), with the latest 7zip installed. I had already tried everything stated above, but no matter wut I try, I get an "Error" message. Which I find even more odd since I CAN open both ' .tar ' and ' .tar.gz ' files with no problem. ( haven't tried ' .rar ' files yet )

 It's sad cuz, all things considered, I really dig Ubuntu over its Counterparts. But God, ...I've never known so MANY problems on Windows, or Mac (of caorse)! Every - Single - Day, without fail, I have an issue! (Mostly w/ Compiz) ...but let me save my many other complaints for another post...

Anyway, I just thought u should know... Ur Misery definitely has Company! ;) 

Note: For tenacity's sake, its a good thing I'm so OCD.

---

### Post by CleveRuse on 2011-06-08
Hey, I just tried "Xarchiver'', and guess wut? ....it still won't extract anything.

---

### Post by gandaran on 2011-06-08
install [peazip]("http://www.peazip.org/peazip-linux.html") download the .deb package, install, then open the peazip gui from the applications menu, if peazip still cannot open the archives then the archives are corrupt.

---

### Post by CleveRuse on 2011-06-13
thentiallqnx for the suggestion, i'd try it but apparently my PC doesnt like this app? IDK, i was notified by a prompt that it could potentially harm my computer, and then 'software Center' said that "packages that violate the standards of quality" aren't allowed to be installed.

But of coarse it shouldnt be necessary.The stock app sould do the trick ...and if theres something wrong w/ 'Archive Manager', then definately 'Xarchiver' should not fail also!

It MUST be the the ...Oh i have no clue, but i want it fixed. Ive been on Ubuntu for over a month now, and can honestly say, I cant imagine going a whole day without some sort of problem. Im sure there are fixes for most promlems but for someone trying to learn linix for the 1st time , maybe this one just isnt for me.

---

### Post by dFlyer on 2011-06-13
Strange, because I've been on Ubuntu since 2006 and have had very few problems over the years. Most problems I've had have been from programs I did not get from the archives, but most of those problems are usually solved in a matter of minutes or maybe an hour or two, not days or weeks. I find Ubuntu very stable and usable. One thing I remind others is that Ubuntu is not Windows. Beginner should take it slow and enjoy the OS. When help is needed it is available usually on this forum. If you can't get the answers on the forum remember google is your friend. Also some programs that are not in the archives have there own web site that can solve most all your problems with there programs.

---

### Post by rootessa on 2011-07-24
Well, it's now almost exactly 4 months later and I've tried everything on this thread and I still can't open a zip file. ](*,)What I've had to resort to doing is contacting the person who sent the zip file to me and have them send an unzipped version of the file to me. Problem is, I just spend 157.00 on a package that came as a download of zip files and I'm not sure he can send me unzipped versions.
I realize Linux isn't Windows and  I've spent dozens of hours in the Linux forums learning Linux and in most things I've been successful......................just not this. I've just spend yet another day of my life trying to unzip files and"it just ain't happenin'  kids". 
Thanks to all of you who attempted to help!

---

### Post by jjjB on 2011-07-28
I'm sorry if I'm missing something, but tar should be able to do this.

Open a command console and type

tar -xzvf YOUR_FILE_NAME

if you want to know what these flags do, type

man tar

to get the manual page for that program.

* * * EDIT * * *
Just as a thought, if you're new to the command line world; inside of a man page you can use

/-x

to search for the string "-x"

hit 'n' for the next occurrence and 'shift + n' for the previous.

Apologies if this is old hat to you.

---

### Post by beew on 2011-07-28
> **jjjB said:**
> I'm sorry if I'm missing something, but tar should be able to do this.

Open a command console and type

tar -xzvf YOUR_FILE_NAME

if you want to know what these flags do, type

man tar

to get the manual page for that program.

* * * EDIT * * *
Just as a thought, if you're new to the command line world; inside of a man page you can use

/-x

to search for the string "-x"

hit 'n' for the next occurrence and 'shift + n' for the previous.

Apologies if this is old hat to you.'


All you need is to right click and choose "extract here" with Ubuntu's default GUI achiever, same for .zip, tar.gz, tar.bz2 and a whole bunch or other things which you need to use different options if you use the command lines. For .rar you need to install unrar (no free) from Synaptic. You don't need to make things unnecessarily intimidating for new users. :)

---

### Post by AgentZ86 on 2011-07-28
I really don't understand why it's doing that.
Unzipping files in linux is simpler then windows because windows does not have any unzipping capability by default.

However, if your trying unzip a self extracting .exe file this might be a different story.

But by default the typical and simple process is to (right click) the zip file and there is a menu item to (extract)

(right click)
(extract here)

All this console commands and downloads etc. I'm not sure why you need to do that unless you just want to learn to do it from the console terminal ?

Also rar files should unzip also no problem.

If you need a rar unzipper you could also download ARK which is the program to unzip .zip and .rar files no problems

But It's included in Ubuntu so no need to download it but you can check if it's install by going to

Applications/Ubuntu Software center and check your installed list to be sure it's installed or search ARK and you will see it with a check mark next to it.

One of the reasons I use linux is because there is so many things installed by default that windows does not have without hunting around the net for it.

I'm very sorry your having trouble with this, but can you please post 1) of your files here or a link to download, so we may be able to download and also try to unzip and see what might be the problem.

---

