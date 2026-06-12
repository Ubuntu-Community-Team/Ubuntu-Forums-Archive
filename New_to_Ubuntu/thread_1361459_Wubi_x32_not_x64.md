---
title: "Wubi x32 not x64"
date: 2009-12-22
forum: New to Ubuntu
---

### Post by asnbd on 2009-12-22
[CENTER]hi,[/CENTER]
 
i'm trying to install ubuntu on my windows vista ultimate. but wubi.exe i downloaded from your website only downloads "amd x64" version of the software.
 
i have searched the web for downloadinfg a "intel x32" verson of ubuntu but in vain.
 
does anyone know where and how i can find the wubi.exe that's for intel x32?
 
and how do i make a copy of the downloaded software so next time i can use the saved files and install ubuntu on another windows machine?
 
thanks.
 
ed

---

### Post by bodhi.zazen on 2009-12-22
I suggest you download the 32 bit desktop iso and the wubi.exe is on the iso.

---

### Post by asnbd on 2009-12-24
hi,
 
could you be more specific?
 
i'm not sure what to do...
 
thanks.

---

### Post by saidinesh5 on 2009-12-24
@asnbd 
well you can simply download the Ubuntu 32bit iso file(inside the iso, there is a wubi installer too), and use that (mount it in windows using "daemon tools" or "power iso")to install ubuntu 32 bit :) 

gLuck :)

---

### Post by @B6Mwu8fN9M on 2009-12-24
You don't have to download Wubi itself. Download the 32bit Ubuntu ISO and burn it to a CD. When you put it into your computer when Windows is loaded, you will get a dialog box which allows you to install Ubuntu using Wubi. 

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by 3rdalbum on 2009-12-24
You might as well just download the Ubuntu ISO; it has Wubi on it that will install whatever version of Ubuntu you have chosen.

One point though: The reason why Wubi was downloading a 64-bit version is because your CPU can handle 64-bit. Yes, it says "amd64", but it works on Intel 64-bit processors too. If your CPU was 32-bit-only, Wubi would have downloaded the 32-bit version of Ubuntu.

---

### Post by asnbd on 2009-12-25
thanks.

i'll try to install the ubuntu on my windows.

---

### Post by asnbd on 2009-12-25
hi,
 
i downloaded the ubuntu .iso(i think is a 32 bit version), and find there is a "wubi" in the disk(i burned the .iso to dvd). but when i click on the wubi in the .iso dvd, it still trys to download the "64 bit" version.
 
is the copy of ubuntu .iso i downloaded correct?
 
how do i make the wubi to install the 32 bit version of ubuntu?
 
do i need to delete the 64 bit ubuntu files i downloaded before i'm trying to install the 32 bit version?
 
btw, what's power .iso? where can i get it? and how do i use it?
 
thanks.
 
ed

---

### Post by aley on 2009-12-25
I have a question, I am looking for a 64bit version of ubuntu but the only one I can find on the website is a 64bit server version and a 32bit desktop version is there a 64bit desktop version?

---

### Post by aley on 2009-12-25
any help would be grateful 
 
Alex

---

### Post by asnbd on 2009-12-25
i deleted the old downloaded 64 bit folder "ubuntu" on my computer.
 
but i run the "wubi" in my .iso dvd and still cannot make it install the 32 bit version.
 
it still shows that it's using wubi 64 and trys to download the files from the web.
 
thanks.

---

### Post by aley on 2009-12-25
I have just found out how so please forget my last post 
 
Thank you Alex

---

### Post by 3rdalbum on 2009-12-25
> **asnbd said:**
> i deleted the old downloaded 64 bit folder "ubuntu" on my computer.
 
but i run the "wubi" in my .iso dvd and still cannot make it install the 32 bit version.
 
it still shows that it's using wubi 64 and trys to download the files from the web.
 
thanks.

I've never heard of this happening, so I can't prescribe a solution - maybe it's a good time to back up your data and install Ubuntu as a real dual-boot setup?

---

### Post by lloyd_b on 2009-12-25
> **asnbd said:**
> i deleted the old downloaded 64 bit folder "ubuntu" on my computer.
 
but i run the "wubi" in my .iso dvd and still cannot make it install the 32 bit version.
 
it still shows that it's using wubi 64 and trys to download the files from the web.
 
thanks.

Try this:

1.  Open a command prompt under Windows ("Start" -> "Programs" -> "Accessories" -> "Command Prompt").
2.  "cd" into the directory where you have the wubi executable
3.  type "wubi --32bit"

This tells wubi that you want to install the 32 bit version.  It *should* use that iso that you downloaded, but if not it will be retrieving the 32 bit version rather than the 64 bit version.

Lloyd B.

---

### Post by unmole on 2009-12-25
> **aley said:**
> I have a question, I am looking for a 64bit version of ubuntu but the only one I can find on the website is a 64bit server version and a 32bit desktop version is there a 64bit desktop version?

Here you go [http://releases.ubuntu.com/karmic/ubuntu-9.10-desktop-amd64.iso](http://releases.ubuntu.com/karmic/ubuntu-9.10-desktop-amd64.iso)

---

### Post by asnbd on 2009-12-25
hi,
 
i opened command prompt. went to d: drive. and entered wubi 32bit.
 
it still runs "download ubuntu-9.10-amd64.iso torrent"
 
thanks

---

### Post by lloyd_b on 2009-12-25
> **asnbd said:**
> hi,
 
i opened command prompt. went to d: drive. and entered wubi 32bit.
 
it still runs "download ubuntu-9.10-amd64.iso torrent"
 
thanks

The command is "wubi --32bit" (wubi<space><dash><dash>32bit).

Lloyd B.

---

### Post by asnbd on 2009-12-25
it changed to 32bit install. thanks.
 
but why is it still showing "download ubuntu torrent"? isn't the files it needs on the .iso dvd?
 
thanks.

---

### Post by lloyd_b on 2009-12-25
> **asnbd said:**
> it changed to 32bit install. thanks.
 
but why is it still showing "download ubuntu torrent"? isn't the files it needs on the .iso dvd?
 
thanks.

Ideally, it should.  When I installed Wubi, I had the .iso file in the same directory as wubi.exe, and it recognized it and installed from there.  I've never tried it with a burned cd/dvd though.

Lloyd B.

---

### Post by asnbd on 2009-12-26
hi,
 
i have used the wubi.exe in the .iso dvd i burned to install the 32bit ubuntu on my windows.
 
but what shouldl i do next?
 
it's the first time i try to use ubuntu(linux). so i have no idea how to get the installed ubuntu run.
 
any suggestions would be appreciated

---

### Post by lloyd_b on 2009-12-26
> **asnbd said:**
> hi,
 
i have used the wubi.exe in the .iso dvd i burned to install the 32bit ubuntu on my windows.
 
but what shouldl i do next?
 
it's the first time i try to use ubuntu(linux). so i have no idea how to get the installed ubuntu run.
 
any suggestions would be appreciated

So the install process ran?  But it's still booting Windows?

If so, [read this thread]("http://ubuntuforums.org/showthread.php?t=1363225") - there's a bug in Wubi that can cause this, with a relatively simple fix (included in the thread).

Lloyd B.

---

### Post by unmole on 2009-12-26
Sorry posted in the wrong thread

---

### Post by asnbd on 2009-12-26
hi,
 
i did not edit the boot.ini on my computer. used the edit command and it did not alow me to edit the file.
 
but now i boot my computer, inter "windows", there's a choice of windows vista OR ubuntu.
 
i selected boot into ubuntu, and the computer went down with a message showing, not fab2 or something like that. (sorry, but i don't remember the exact message)
 
so what should i do now?
 
and why the boot menu showed up without my editing the boot.ini file?
 
ed
 
ps. where is the ubuntu exactlly installed? i didn't partition or see the installation process. thanks.

---

### Post by asnbd on 2009-12-26
the error message was:

try (hd0, 0) non-MS skip
try(hd0, 1) non-MS skip
try(hd0, 2) ext2

thanks

---

### Post by lloyd_b on 2009-12-27
> **asnbd said:**
> hi,
 
i did not edit the boot.ini on my computer. used the edit command and it did not alow me to edit the file.
 
but now i boot my computer, inter "windows", there's a choice of windows vista OR ubuntu.
 
i selected boot into ubuntu, and the computer went down with a message showing, not fab2 or something like that. (sorry, but i don't remember the exact message)
 
so what should i do now?
 
and why the boot menu showed up without my editing the boot.ini file?
 
ed
 
ps. where is the ubuntu exactlly installed? i didn't partition or see the installation process. thanks.

Sorry, but you've reached the limits of my experience with this problem.  I would suggest starting a new thread, with a subject more appropriate to the problem that you're having now.

As for *where* Ubuntu is installed - look in C:\Ubuntu\disks - the files in there are your root and swap disks (Wubi, via some trickery, encapsulates the ext filesystem inside of NTFS, which is why no partitioning is required).

Lloyd B.

---

