---
title: "Cannot get Sigil to install"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by Elaphae on 2011-06-05
I am a beginner at Ubuntu using Maverick 10. I have a problem when trying to use the terminal for an install. (As an example Wine installed, I think but does not work so I am not positive of success). Tonight as I was about to post this question I managed to install Firefox 4 from the instructions given at the sticky message and it looked like it failed (would not take the last command) but Firefox 4 was there when I opened the browser. I suppose I really don't know what I did other than cut and paste the code from the thread.

I have now wasted several hours trying, without success to install Sigil. I have tried all 3 versions that are suggested at the downloads page. Last one I tried is Sigil-0.4.0RC1-Linux-Setup.bin I tried the x64 vers first but decided that maybe it was not compatible.

If it is of any use:
I followed the directions given at:
[http://web.sigil.googlecode.com/hg/intro.html#linux](http://web.sigil.googlecode.com/hg/intro.html#linux)
and checked the box to make the file executable. Tried to do the rest...

Then tried both copy/paste and directly typing in the commands. I always get this, no matter what version:
:~$ chmod +x Sigil-0.4.0RC1-Linux-x64-Setup.bin
chmod: cannot access `Sigil-0.4.0RC1-Linux-x64-Setup.bin': No such file or directory
:~$ 

I must be missing something but am too new to Ubuntu to know what. I have also tried to open the file with Autorun and Archive Manager - fail. 

All past additions made to the basic Ubuntu install except for the (nonworking?) wine have been through the Ubuntu Software Center. Sigil is not listed there, nor is any other ebook editor/creator I can find.

I also typed in:
uname -m
i686

as I thought the information might help.

I come to Ubuntu from using Apple G4 80% of the time and Windows XP 20%. I have even taught basic computer use and Internet classes to other adults. I don't think I used the Apple OS command line more than twice in 10 years and am very used to programs simply working when downloaded. My fault for not learning more.

I must be missing something basic, but am too much a beginner to see it. I need to edit several files into ebooks, can anyone help me get this program installed? (I would much rather have it working right now than wine - don't even have to have wine. But I need an ebook editor).

I am using a home built computer with dual boot (I still need Windows for gaming (which was why I wanted wine above). Ubuntu 10.10 works fine, as does GIMP and OpenOffice.

Help please?

---

### Post by ExileAmongYou on 2011-06-05
chmod +x does the same thing as right clicking on a file and going to Properties to make it executable, so if you've already done that you don't actually need to chmod it.
I suspect that the reason you were having problems with the terminal command is you hadn't navigated to the folder the install file was in with cd. E.g. if you downloaded the file to your Downloads file, you would have to type
```
cd Downloads
```
to get to the Downloads folder, then run the chmod command.

If you can get yourself to the folder the file is in using the terminal, then you can run the install command:
```
sudo ./installer.bin
```
A good way to check that it's working is to type the 'sudo ./' part, then start typing the first part of the installer's filename, then press Tab. If you're in the right folder, the terminal should fill in the rest of the filename for you.

---

### Post by Elaphae on 2011-06-05
> **ExileAmongYou said:**
> chmod +x does the same thing as right clicking on a file and going to Properties to make it executable, so if you've already done that you don't actually need to chmod it.
I suspect that the reason you were having problems with the terminal command is you hadn't navigated to the folder the install file was in with cd. E.g. if you downloaded the file to your Downloads file, you would have to type
```
cd Downloads
```
to get to the Downloads folder, then run the chmod command.

If you can get yourself to the folder the file is in using the terminal, then you can run the install command:
```
sudo ./installer.bin
```
A good way to check that it's working is to type the 'sudo ./' part, then start typing the first part of the installer's filename, then press Tab. If you're in the right folder, the terminal should fill in the rest of the filename for you.
I tried the above with this result:
bob@Denver:~$ ./installer.bin
bash: ./installer.bin: No such file or directory

I then tried:
bob@Denver:~$ cd Downloads
bob@Denver:~/Downloads$ ./installer.bin
bash: ./installer.bin: No such file or directory

Thinking that using the file name rather than ./installer.bin I tried:
bob@Denver:~/Downloads$ sudo ./Sigil-0.4.0RC1-Linux-Setup.bin
[sudo] password for bob: 
bob@Denver:~/Downloads$ 

Painful beginner's errors. It worked. I must have been adding an extra space or something before. Thanks for the help!

---

### Post by KarenAK on 2011-07-31
Thank you - that was helpful :-)

---

