---
title: "1st post here, and FTP question"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by Joao Paz on 2008-12-26
Greetings, everyone

A long time user of Windows I discovered Linux and Ubuntu about a week ago, and must say I'm fascinated by it! It took me less than an hour, actually, after seeing how quickly and flawlessly Ubuntu installed on my system, how easy it was to put it online and how it detected my home network and shared folders on my windows PCs... while those didn't even saw the new one ;)
So, first of all, a big thank you to all those involved in such a great work!
I know I'll stick with Linux for a long time - and I will most probably start switching the whole system at the office to linux in about a year...

+ + +

Here's my FTP question:

I tried both ...
a) the built in solution under "Local" "Connect to Server" 
b) the gFTP application
... to access my website.

And while my settings work right away with gFTP I am getting an error with the Ubuntu Connect to Server feature:
(translated from my portuguese system, here goes)

[COLOR="Red"]**"Cannot display folder contents"**
Cannot display all the contents of "/ in
ftp.mysite.com": the file is not a directory.[/COLOR]

This error is displayed in my "file manager" (Nautilus?) after the authentication process.

Any ideas?
And I appologize if this has been addressed somewhere already. First time here and this place still looks too big for this rookie :)

Thanks!
Joao

---

### Post by albandy on 2008-12-26
it could be two things:

An old gnome bug (upgrade your system)
or a problem with active/passive connections.

---

### Post by Coder543 on 2008-12-26
What version of Ubuntu are you running? Go to System -> About Ubuntu and it should be listed in there. If you are running 8.04, try upgrading to 8.10.

---

### Post by albinootje on 2008-12-26
> **Joao Paz said:**
>  A long time user of Windows I discovered Linux and Ubuntu about a week ago, and must say I'm fascinated by it! It took me less than an hour, actually, after seeing how quickly and flawlessly Ubuntu installed on my system, how easy it was to put it online and how it detected my home network and shared folders on my windows PCs... while those didn't even saw the new one ;)


Excellent! :)

> 
This error is displayed in my "file manager" (Nautilus?) after the authentication process.

I find Nautilus nice as my local file browser, although it can be a bit slowish when having a lot of files in a directory. 
You can try Thunar or Pcmanfm as alternative file-managers.

But for quickly accessing local ftp-servers, samba-shares and sometimes ssh-sessions I prefer Konqueror over Nautilus.
It's a matter of typing in smb://username@samba-server/share-name/ or fish://username@ssh-server in Konqueror.
In Nautilus you can also enable the location-bar, and use a similar smb:// syntax but I prefer Konqueror for that.

The drawback of using Konqueror inside Ubuntu is that (afaik) you cannot copy & paste to the desktop. You need to open another Konqueror-window because Konqueror is a KDE application (The copy & paste to the desktop with Konqueror would work fine in Kubuntu of course).

Concerning ftp-sessions, if gftp works fine for you, why not stick with that ?
I also use gftp for ftp (and ssh/scp/sftp!), and I like it. :)

---

### Post by Joao Paz on 2008-12-26
Thank you, Gents

I am using 8.10 (just added it to my signature field, btw) so I think I'm on the latest - and have already done the system updates, too.

As I'm still unfamiliar with the various file types, etc, I thought it could be something about the way I partitioned my system? I believe I used all disk size to ext3, and so maybe bot having other partition formats may be causing the problem? (swap, for instance...?)

albinootje, thanks for all the tips, will try those!

As for your question "...why not stick with it?", yes, sure! But I'd like to learn this thing before going on the alternative options. There's a certain pride involved in using only the provided software option, for starters ;)

Thanks again, and I'll keep monitoring this one in case some other ideas pop-up!



Edit: ext3 and not ext2

---

### Post by albinootje on 2008-12-26
> **Joao Paz said:**
> 
I am using 8.10 (just added it to my signature field, btw) so I think I'm on the latest - and have already done the system updates, too.

As I'm still unfamiliar with the various file types, etc, I thought it could be something about the way I partitioned my system? I believe I used all disk size to ext3, and so maybe bot having other partition formats may be causing the problem? (swap, for instance...?)


It's unlikely that this error was about your partitioning of the disk.
Nautilus is just a little ... buggy .. from time to time. :| :)

> 
As for your question "...why not stick with it?", yes, sure! But I'd like to learn this thing before going on the alternative options. There's a certain pride involved in using only the provided software option, for starters ;)


Good! The more eyeballs to squeeze bug the better :)

[https://bugs.launchpad.net/nautilus](https://bugs.launchpad.net/nautilus)

[http://en.wikipedia.org/wiki/Linus's_Law](http://en.wikipedia.org/wiki/Linus's_Law)
"given enough eyeballs, all bugs are shallow"

---

### Post by albandy on 2008-12-26
I'm completely sure that the problem is not in your file system. I'm using a single ext3 partition too.

I think your site requires active mode, and nautilus uses passive by default and you can't change it.

To test it simply enter ftp from command line:

for example:

ftp ftp.mydomain.com
user: [email]myuser@mydomain.com[/email]
password: **********

now type ls, if works then type passv
now type ls again, if not works your site needs active mode

---

### Post by Joao Paz on 2008-12-26
Thanks, Albandy!
(that was my first console command! :P)

I was able to log in to my website, and both modes worked. The ls command, at least. I tried a couple of times and was able to list in both modes.
Thanks a bunch anyway!

---

### Post by Kellemora on 2008-12-26
Hi JP

This may be an oversimplification, but since I didn't know it when I first started using Ubuntu, it's what caused me a similar problem.

When a file IS a directory, it needs to be followed with /
EG:  /homes/elmstreet/ to open all the homes listed on elm street.

But if I wanted to FTP a certain file in that folder I didn't use the /
EG:  /homes/elmstreet/eightnineteen

If I did use the / I would get the error that 'The File is NOT a Directory".  Or in some cases "Directory Not Found".

I hope it's this simple for your problem!

TTUL
Gary

---

### Post by moredhel on 2008-12-26
Just for the heads up, I find the program filezilla far more satsfactory to use compared to gftp. It's crossplatform too - meaning you can use it when you are stuck on windows too!

---

### Post by Joao Paz on 2008-12-26
> **Kellemora said:**
> Hi JP

This may be an oversimplification, but since I didn't know it when I first started using Ubuntu, it's what caused me a similar problem.

When a file IS a directory, it needs to be followed with /
EG:  /homes/elmstreet/ to open all the homes listed on elm street.

But if I wanted to FTP a certain file in that folder I didn't use the /
EG:  /homes/elmstreet/eightnineteen

If I did use the / I would get the error that 'The File is NOT a Directory".  Or in some cases "Directory Not Found".

I hope it's this simple for your problem!

TTUL
Gary

Hi Gary, thanks!

Well I tried ...but I'm getting slight variations of the same original error message. I tried it in front of the ftp server, in the folder field, in both, even before and after ... :)

Will keep trying, maybe there's something right in front of me that I'm just not seeing...!

---

### Post by Joao Paz on 2008-12-26
> **moredhel said:**
> Just for the heads up, I find the program filezilla far more satsfactory to use compared to gftp. It's crossplatform too - meaning you can use it when you are stuck on windows too!

Thanks, Moredhel

I use it too on Windows, and saw it on the Ubuntu applications list, but its "popularity" wasn't so good, so I gave gFTP a go. But will try Filezilla in Linux too!

---

### Post by moredhel on 2008-12-26
It's popularity isn't as high because it was only available for linux after v3 when he ported it to gtk :)

---

### Post by AlbertFruend on 2009-03-05
Just to throw my 2 cents in...

I've struggled with exactly the same thing - Nautilus is useless as an ftp client if the ftp server won't operate in passive mode.  I ended up going with Filezilla as it gives you the option of running in active mode only. 

Filezilla does not, of course, offer as tight an integration with the desktop.  

I hope this is addressed in a future release - to me it's a big drawback.  If someone knows of a way to configure Nautilus to change this default behavior, please let me know.  I can't find it.

---

