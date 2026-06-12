---
title: "I'm losing it."
date: 2010-09-21
forum: New to Ubuntu
---

### Post by bowen192 on 2010-09-21
Hi everyone.

I've recentely made the switch from Windows to Ubuntu and was loving it up until yesterday.

I downloaded the first series of Arrested Development, no problems.

Then I had to unzip the files.  My word.  My word.

I've downloaded rar, unrar and 7zip, but they cannot unrar multiple, joined, password protected files.

Any ideas before I bin the whole thing?

---

### Post by magneze on 2010-09-21
Try the 7zip forums:

[http://sourceforge.net/projects/sevenzip/forums/forum/45797](http://sourceforge.net/projects/sevenzip/forums/forum/45797)

---

### Post by sandyd on 2010-09-21
> **bowen192 said:**
> Hi everyone.

I've recentely made the switch from Windows to Ubuntu and was loving it up until yesterday.

I downloaded the first series of Arrested Development, no problems.

Then I had to unzip the files.  My word.  My word.

I've downloaded rar, unrar and 7zip, but they cannot unrar multiple, joined, password protected files.

Any ideas before I bin the whole thing?
```
sudo apt-get install unrar rar
```

then just double click the file..

---

### Post by t0p on 2010-09-21
> **bowen192 said:**
> 
I've downloaded rar, unrar and 7zip, but they cannot unrar multiple, joined, password protected files.

How curious.  I have rar and/or unrar installed (so long ago now I can't remember which) and the Archive Manager has no problem unrar-ing multiple, joined, password-protected files.  I just right-click on the first archive, select 'Extract here', and that's it.  If the archive is password-protected, it prompts me for the password.  If it's a multiple archive it just unpacks it.

> **bowen192 said:**
> 
Any ideas before I bin the whole thing?

Can you please show or tell us what actually happens when you try to unpack the archive?  A screenshot or error message would be wonderful.

---

### Post by bowen192 on 2010-09-21
> **t0p said:**
> How curious.  I have rar and/or unrar installed (so long ago now I can't remember which) and the Archive Manager has no problem unrar-ing multiple, joined, password-protected files.  I just right-click on the first archive, select 'Extract here', and that's it.  If the archive is password-protected, it prompts me for the password.  If it's a multiple archive it just unpacks it.  Can you please show or tell us what actually happens when you try to unpack the archive?  A screenshot or error message would be wonderful.

I tried initially to 'Extract here' and it just opens multiple boxes, ie one for each file.

EDIT: No it doesn't, it tries to unrar each file individually.  So instead of EP1.001, EP1.002 and EP1.003 unraring together, it does it individually.  It also asks for the password for every file, even though it's the same one.

---

### Post by bowen192 on 2010-09-21
> **sandyd said:**
> ```
sudo apt-get install unrar rar
```then just double click the file..

This opens multiple extracting files which is no use as I need to combine files.

---

### Post by -kg- on 2010-09-21
> **bowen192 said:**
> I downloaded the first series of Arrested Development, no problems.

Then I had to unzip the files.  My word.  My word.

Of course, did you ever consider the source?  Where did you get the series, and how did you download it?  Did you check any md5 checksums?  Are you sure the archive wasn't corrupted in the process of downloading it?

If the download was somehow corrupted (or perhaps downloaded from an untrustworthy source?) the packages naturally would not unzip properly.

---

### Post by cholericfun on 2010-09-21
i've done this some long time ago and can't remember exactly how i went about it.
i'm not really interested in digging out the answer, what i want to say is

if you use Linux
A: you will have to learn something 
B: you may learn something

no pain no gain.
enjoy

---

### Post by bowen192 on 2010-09-21
> **-kg- said:**
> Of course, did you ever consider the source?  Where did you get the series, and how did you download it?  Did you check any md5 checksums?  Are you sure the archive wasn't corrupted in the process of downloading it?

If the download was somehow corrupted (or perhaps downloaded from an untrustworthy source?) the packages naturally would not unzip properly.

Source is fine.  I have already d/l and unzipped in Windows 7.

---

### Post by bowen192 on 2010-09-21
> **cholericfun said:**
> i've done this some long time ago and can't remember exactly how i went about it.
i'm not really interested in digging out the answer, what i want to say is

if you use Linux
A: you will have to learn something 
B: you may learn something

no pain no gain.
enjoy

See, this is what I have a problem with.

I don't mind learning if it's going to benefit me, but I've spent two days looking to do something that should take two minutes.  I'm a believer that an OS should work for you, not the other way round.  I mean how complicated must it be if you've done it *and* forgot it?

Learning something is no use if you forget it soon after.

---

### Post by nothingspecial on 2010-09-21
Woah, calm down guys.

> **bowen192 said:**
> Source is fine.  I have already d/l and unzipped in Windows 7.

What`s the problem then?

---

### Post by bowen192 on 2010-09-21
> **nothingspecial said:**
> Woah, calm down guys.



What`s the problem then?

I've since deleted them and the laptop I currently use has no Windows installed.

Yet.

---

### Post by Rasa1111 on 2010-09-21
never had any issues youre describing. 
and I download alot of stuff. 

> Any ideas **before I bin the whole thing**?

 lol, really?
"bin the whole thing" for an arrested development show? 

ok then.

---

### Post by Jesus_Valdez on 2010-09-21
I was able to extract password protected in multiple rar files archives after installing rar and unrar in ubuntu without problems, I just right click - extract here on the firs file, then a little window ask me for a password and extract it without problems.

Did you already did the "sudo apt-get install unrar rar" thing? Are you 100% sure that the file is undamaged?

---

### Post by nothingspecial on 2010-09-21
> **bowen192 said:**
> I've since deleted them and the laptop I currently use has no Windows installed.

Yet.

Well, for now just "unzip" them in the way you have been doing.

There`s alot of people here who take offence to some of the things you`ve posted. You have to understand that you can`t just come in here saying

THIS OS SHOULD WORK LIKE I WANT IT TO, OR I`M GOING TO BIN IT

If you do that, most people here are going to say well bin it then. Why should I help?

If you want advice, you are better off asking nicely. 

If I knew how to unzip a password protected zip file I`d tell you. I`m sorry, but I don`t.

A little more tact may help.

---

### Post by Vaphell on 2010-09-21
you can also try to install windows rar in wine, somewhat lame but if it works...

---

### Post by Rasa1111 on 2010-09-21
> most people here are going to say well bin it then.

indeed.
 why help someone who doesnt care one way or the other?

Do what you must.

---

### Post by bowen192 on 2010-09-21
> **Jesus_Valdez said:**
> I was able to extract password protected in multiple rar files archives after installing rar and unrar in ubuntu without problems, I just right click - extract here on the firs file, then a little window ask me for a password and extract it without problems.

That's what I do.  I think.

I've just right clicked and 'extract here' on 3 files which are the second episode.

[http://i54.tinypic.com/2ypf7l1.jpg](http://i54.tinypic.com/2ypf7l1.jpg)

It just extracts each file separately, asking for the password each time.

---

### Post by bowen192 on 2010-09-21
> **nothingspecial said:**
> Well, for now just "unzip" them in the way you have been doing.

There`s alot of people here who take offence to some of the things you`ve posted. You have to understand that you can`t just come in here saying

THIS OS SHOULD WORK LIKE I WANT IT TO, OR I`M GOING TO BIN IT

If you do that, most people here are going to say well bin it then. Why should I help?

If you want advice, you are better off asking nicely. 

If I knew how to unzip a password protected zip file I`d tell you. I`m sorry, but I don`t.

A little more tact may help.

OK, sorry if you've taken offence.

But I've started using Ubuntu on the grounds that it is an alternative OS to Windows.

I'm just a bit disappointed that this one thing could ruin the experience for me.

Especially as I've been singing it's praises to everyone I know at the moment.  If other people ask me how you unrar something and I reply you can't, they'll never use Linux/Ubuntu again.

---

### Post by Rasa1111 on 2010-09-21
> If other people ask me how you unrar something and I reply you can't, 

 but that's the thing.. *you can. *

 People here do it everyday, numerous times a day. 

> I'm just a bit disappointed that this one thing could ruin the experience for me.

 That is of your own making.

---

### Post by aktiwers on 2010-09-21
You should just pick the first file, right-click and "extract here".
Then type in your password.

If this is not working for you, and you somehow need to join the files(this is normally not the case), you could join them like this:

```
 cat file.zip.01 file.zip.02 file.zip.03 > filejoined.zip
```

if you have a lot of files, it might be easier to just type "cat" mark all the zip files and drag'n'drop them into the Terminal. Then finish the command with "> filesjoined.zip".

Now unzip the filesjoined.zip and type in your Password.

Remember the filesjoined.zip will be stored in the folder your terminal is in (defualt is your home folder)

---

### Post by CanadianPenguin on 2010-09-21
> **bowen192 said:**
> This opens multiple extracting files which is no use as I need to combine files.

It doesn't open them, it installs them.

If you can't listen to or try our suggestions, don't ask us for help.

---

### Post by formaldehyde_spoon on 2010-09-22
I select all the files first, then right click and choose Extract Here.  Works for me...

---

### Post by mastablasta on 2010-09-22
> **aktiwers said:**
> You should **just pick the first file**, right-click and "extract here".
Then type in your password.
 
 ALWAYS only the first one. even in MS-DOS you only typed the name of first file to unrar not mark multiple files.
 
also don't use pirated material. if you like the show buy a DVD. :P

---

### Post by magneze on 2010-09-22
> **Rasa1111 said:**
> never had any issues youre describing. 
and I download alot of stuff. 



 lol, really?
"bin the whole thing" for an arrested development show? 

ok then.Indeed. OP = poor troll 0/10.

---

### Post by formaldehyde_spoon on 2010-09-22
> **mastablasta said:**
> ALWAYS only the first one. even in MS-DOS you only typed the name of first file to unrar not mark multiple files.
 
also don't use pirated material. if you like the show buy a DVD. :P

Are you replying to me??  I'm not the OP, and I don't have any trouble extracting files.....
(even though I don't select 'always only the first one' - although I did when I used DOS...)

---

### Post by sandyd on 2010-09-22
Trolls Trolls Trolls....
```

 rar e ~/Downloads/Arrested*part1.rar

```

---

