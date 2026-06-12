---
title: "Best Download Manager for Linux / Ubuntu?"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by rez182 on 2011-04-12
what is the best download manager for linux / ubuntu? something like Internet Download Manager, which i think is better than free download manager because it has the capability of resuming broken download with refresh link. i need something like that. but does not have the customisation like free download manager to allow only 1 download at a time with any number of connections per download.

any suggestions?

thanks.

---

### Post by robert shearer on 2011-04-12
well, from the command line I much prefer Aria2.
```
sudo apt-get install aria2
```

To run try..
```
aria2c -h
```   for options.

I usually just download things to the desktop then move/view/edit them from there.
In which case running aria2 with..
```
aria2c -d /home/[COLOR="Red"]yourusername[/COLOR]/Desktop [COLOR="Red"]url/file_to_download[/COLOR]
```  
works just fine.


Oh, and did I mention it's fast...

---

### Post by rez182 on 2011-04-12
it doesnt have a GUI? im not good with terminal. :(

---

### Post by d2btoo on 2011-04-12
Multiget

WEB : [http://multiget.sourceforge.net/](http://multiget.sourceforge.net/)

Note: available in the repo :)

---

### Post by rez182 on 2011-04-12
Hows FatRat? does it have resume broken download with the help of refresh link? this is the main feature i need.

---

### Post by robert shearer on 2011-04-12
> **rez182 said:**
> it doesnt have a GUI? im not good with terminal. :(

No, but neither was I to start with.;) 
Then I tried it, and some more then I was ok with the terminal. :D

We have **all** been beginners with the terminal so if you want to give it a try there will be plenty of users here to walk you through it. ):P

to try aria2 you can install it from Synaptic or software centre or just open a terminal and copy and paste..
```
sudo apt-get install aria2
```

it will ask for your password and you will see nothing as you type it then hit enter and wait while it installs.

If you get this far ok then congratulations, you have used the terminal.:D

Post back and we can take the next step if you are interested.

Oh and why from the terminal..?, because it's fast and powerful.
Did I mention it was fast...?

---

### Post by mastablasta on 2011-04-12
if you use mozilla you can try download them all plugin

---

### Post by Sidewinder1 on 2011-04-12
Hi rez, since you seem to be relatively new to Ubuntu or at least new to these forums,
(Join Date: Mar 2011) and with all due respect, might I make a suggestion?
The preffered method for downloading and installing software in Ubuntu is Synaptic Package Manager, found in: System--> Administration--> Synaptic. It will handle any dependencies and has a HUGE selection of software programs; around 30,823, last time I checked. 
I'd like to go into more detail but am a little pressed for time, right now.
If you need any help with it, you have just to ask.

HTH, 
Side

---

### Post by TimEnid on 2011-04-12
Jdownloader

---

### Post by sleepingdragon on 2011-04-12
How about *gwget? *It does support resume and continues downloads if it's restarted - but you'll need to kick a few options around in the Preferences menu. Easy to do.

---

### Post by Sinclairluvs@hotmail.com on 2011-06-29
> **robert shearer said:**
> No, but neither was I to start with.;) 
Then I tried it, and some more then I was ok with the terminal. :D

We have **all** been beginners with the terminal so if you want to give it a try there will be plenty of users here to walk you through it. ):P

to try aria2 you can install it from Synaptic or software centre or just open a terminal and copy and paste..
```
sudo apt-get install aria2
```it will ask for your password and you will see nothing as you type it then hit enter and wait while it installs.

If you get this far ok then congratulations, you have used the terminal.:D

Post back and we can take the next step if you are interested.

Oh and why from the terminal..?, because it's fast and powerful.
Did I mention it was fast...?





I need to know the next step...I need to download music to my mp3 player

---

### Post by cbowman57 on 2011-06-29
Might want to look at Steadyflow, it has a simple gui & I think it supports resume, I know you can pause & resume.

[http://www.linuxo.com/content/steadyflow-download-manager-released-ubuntu-1104-natty-narwhal](http://www.linuxo.com/content/steadyflow-download-manager-released-ubuntu-1104-natty-narwhal)

---

### Post by wolfen69 on 2011-06-29
> **rez182 said:**
> what is the best download manager for linux / ubuntu? something like Internet Download Manager, which i think is better than free download manager because it has the capability of resuming broken download with refresh link. i need something like that. but does not have the customisation like free download manager to allow only 1 download at a time with any number of connections per download.

any suggestions?

thanks.

Aria2 all the way. 

For example you would do in terminal:

```
aria2c http://releases.ubuntu.com/natty/ubuntu-11.04-desktop-amd64.iso
```

It will pull in the iso from multiple sources and put it in your home folder. I usually get blazing speeds from it.

---

### Post by robert shearer on 2011-06-30
> **Sinclairluvs@hotmail.com said:**
> I need to know the next step...I need to download music to my mp3 player

for the first half of your query see...
[http://ubuntuforums.org/showpost.php?p=10667287&postcount=2](http://ubuntuforums.org/showpost.php?p=10667287&postcount=2)

---

### Post by jtarin on 2011-07-01
> **TimEnid said:**
> JdownloaderNone compare.....use it everyday.....12hrs a day downloading.

---

### Post by vasa1 on 2011-09-12
> **robert shearer said:**
> ...
Oh and why from the terminal..?, because it's fast and powerful.
Did I mention it was fast...?

I'm trying out aria2c right now. I don't know what the emphasis on "fast" is all about. Maybe I'll learn with time ...

I had one disconnect and the resume worked but I had to intervene to get the download going again (aria2c -c "url") even though the net reconnected itself.

FDM (in Windows) would resume by itself if the connection resumed by itself.

---

### Post by Enigmapond on 2011-09-12
> **jtarin said:**
> None compare.....use it everyday.....12hrs a day downloading.

+1000 for Jdownloader. I've tried them all and this is the most versatile one available but with Linux AND 'doze...

---

### Post by ilovelinux33467 on 2011-09-12
KGet. I use it a lot and I find it brilliant.

---

### Post by _d_ on 2011-09-12
I've been a personal fan of GWGet, but maybe I'll check out JDownloader later on today. :p

---

### Post by m4k4n2 on 2011-09-12
Hello, I'm new in this forum and in Linux. I'm using 10.04 Ubuntu (Lucid Lynx). My question is what are the differences between download accelerator (eg. JDownloader) and firefox addon (eg. downloadthemall). Which one is better for a newbie? Any tips would be helpful. TQ.

PS: Sorry my English is poor because it is not my native language.

---

### Post by raja.genupula on 2011-09-12
d4x is my choice , but i don't why i am not getting it in 11.04. 
now i am moving with wget and curl

---

### Post by adnan-kamili on 2012-09-15
You can try out flareGet, which is the fastest download manager for Linux.
[http://sourceforge.net/projects/flareget/](http://sourceforge.net/projects/flareget/)

---

### Post by houseworkshy on 2012-09-15
I use a browser pluggin for firefox called DownThemAll.  Quick, easy, splits to segments, resumes ( if you let it keep it's part files), and most handy of all it has checksum support so one knows that a file is borked *before* actually downloading it.   I have no idea how it can do this but it does.

---

### Post by Elfy on 2012-09-15
Old thread closed.

---

