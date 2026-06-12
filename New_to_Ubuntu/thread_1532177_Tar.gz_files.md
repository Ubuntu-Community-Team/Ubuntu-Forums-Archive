---
title: "Tar.gz files?"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by momrocker on 2010-07-16
Hey guys, I used to fiddle around with 9.10 awhile back, and for this second time through a linux operating system, I want to start learning more and actually get the full potential of my system instead of treating it like windows and going nowhere (like I was :P).  Well, the first problem I'm having is my wireless adapter (a Belkin's basic N usb adapter). I'm trying to get ndiswrapper (I think that's the name) but since I cant use aptitude when I don't have internet I decided to download a tar file and extract it with the archive manager. The only bad thing is that I have no idea where to go from there, and it wont let me run ndiswrapper from the terminal if i enter it in. I tried to do tar zxvf (or whatever it is, I'm not on my Xubuntu computer at the moment) but it keeps telling me that it cant find the archive, even though I directed the terminal straight to the flash drive.  So, since I'm a n00b at tar files, could some people maybe link me to some useful articles or help me out with what I should do? Any advice is greatly appreciated!

---

### Post by Drenriza on 2010-07-16
if you do

```
tar -xzfv filename
```

can you then give an copy paste of the output?

---

### Post by drpjkurian on 2010-07-16
Hi
Tar files can be explained as group of files which are required for the programme. They neither compiled nor executable ones.
So the first basic step is to 
1. Read the 'Read me' file and 'Installation file' 

2. See whether you require any dependency package. If so install it from synaptic package manager

3. Untar the file to any location say 'Desktop'

4. use the command ```
cd Desktop
```

5 . Use the command ```
cd **[COLOR="Red"]'Filename'[/COLOR]**
```
the letters in red should match the folder name

6. Use the command ```
make && make install
```
to install

---

### Post by momrocker on 2010-07-16
I wont be at a computer with Ubuntu till later today. But that info was really helpful bro, I'll try it out and be sure to tell you the results when I can. The only problem is that I wont be able to download any dependency files since I dont have internet XD will it be almost required that I get them before I can install tar files, or is it possible it will be OK without it?

---

### Post by digitalcitizenx on 2010-07-16
> **momrocker said:**
> I wont be at a computer with Ubuntu till later today. But that info was really helpful bro, I'll try it out and be sure to tell you the results when I can. The only problem is that I wont be able to download any dependency files since I dont have internet XD will it be almost required that I get them before I can install tar files, or is it possible it will be OK without it?

You may need the Ubuntu repository DVD.

[linky]("http://goinggnu.wordpress.com/2010/05/12/ubuntu-10-04-repository-dvd-isos-are-available/")

---

