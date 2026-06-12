---
title: "Help with aim for a real noobie"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by troegs on 2009-02-04
I'm trying to get a few of my "necessary" programs installed but am running into an issue with my first one (AIM). I've seen some threads on how to install but to be honest the command line talk is somewhat confusing. I've followed the instructions but after doing the gunzip my terminal went absolute crackpot nuts for a solid 10 seconds. As far as I could tell it was outputting the actual code into terminal. Is this really the only way to install apps? I knew that linux based OSs were geared towards the more computer savvy but something tells me there's gotta be a better way.

I should say that I'm not actually a total linux newb. I am a CS student and use linux on a daily basis however I've never installed anything on it as I use the school computers whenever I'm doing anything and the only programs I use are a development environment for programming and the terminal for compiling, submitting programs, and a few other minor tasks.

Any help would be greatly appreciated. 

T.

---

### Post by tarps87 on 2009-02-04
You can download the deb file (debian installer) then type
```
sudo dpkg *packageName*
```
double clicking the file should also work

Your terminal was probably listing all the files extracted.

The deb I'm looking at can be found here:
[http://www.aim.com/get_aim/linux/latest_linux.adp](http://www.aim.com/get_aim/linux/latest_linux.adp)

---

### Post by DougieFresh4U on 2009-02-04
> **tarps87 said:**
> You can download the deb file (debian installer) then type
```
sudo dpkg *packageName*
```
double clicking the file should also work

Your terminal was probably listing all the files extracted.

The deb I'm looking at can be found here:
[http://www.aim.com/get_aim/linux/latest_linux.adp](http://www.aim.com/get_aim/linux/latest_linux.adp)

I have never been able to get those files to work.
So installed AIM via WINE, although it's an older one (5.9) it works.

---

### Post by SpenceMakesSense on 2009-02-04
Whats wrong with pidgin? or is it not installed on your computer
if you want to try it out it may suit your needs considering they havent made a new version of aim for linux in awhile.

If you didnt know,pidgin is just a program that can use different IM protocols like aim and yahoo
```
sudo apt-get install pidgin
```
if your running ubuntu its under applications-internet

---

### Post by stchman on 2009-02-04
> **troegs said:**
> I'm trying to get a few of my "necessary" programs installed but am running into an issue with my first one (AIM). I've seen some threads on how to install but to be honest the command line talk is somewhat confusing. I've followed the instructions but after doing the gunzip my terminal went absolute crackpot nuts for a solid 10 seconds. As far as I could tell it was outputting the actual code into terminal. Is this really the only way to install apps? I knew that linux based OSs were geared towards the more computer savvy but something tells me there's gotta be a better way.

I should say that I'm not actually a total linux newb. I am a CS student and use linux on a daily basis however I've never installed anything on it as I use the school computers whenever I'm doing anything and the only programs I use are a development environment for programming and the terminal for compiling, submitting programs, and a few other minor tasks.

Any help would be greatly appreciated. 

T.

Pidgin is a multi-protocol IM client like Trillian.  Pidgin handles AIM, MSN, YIM, and many others.

Pidgin is installed by default.

---

### Post by troegs on 2009-02-04
Thanks for all the replies and yes, after close examination, I am a tool. Pidgin does in fact come pre-installed and thus my frantic noob spam of forums throughout the internet were simply a bold flag placed in the ground of the world wide web of my ubuntu noobishness. Thanks for taking your time to reply, and sorry I wasted it with my question.

On a side note I am curious. Are the majority of programs installed via the terminal? Just curious.

Also @ Tarps. Whatever I did, the terminal definitely wasn't listing the files. It looked pretty much like when you try and open a program via word or some text editor. only it was rushing past the screen. Zig zags of random numbers, letters, and indistinguishable digits. As mentioned before though a Linux noob, I am a programmer. Pretty sure it was code. Just hope I didn't foul anything up my first 20 minutes of using linux.

Thanks again for all the replies,
T.

---

### Post by Tomatz on 2009-02-04
> **troegs said:**
> Thanks for all the replies and yes, after close examination, I am a tool. Pidgin does in fact come pre-installed and thus my frantic noob spam of forums throughout the internet were simply a bold flag placed in the ground of the world wide web of my ubuntu noobishness. Thanks for taking your time to reply, and sorry I wasted it with my question.

On a side note I am curious. Are the majority of programs installed via the terminal? Just curious.

Also @ Tarps. Whatever I did, the terminal definitely wasn't listing the files. It looked pretty much like when you try and open a program via word or some text editor. only it was rushing past the screen. Zig zags of random numbers, letters, and indistinguishable digits. As mentioned before though a Linux noob, I am a programmer. Pretty sure it was code. Just hope I didn't foul anything up my first 20 minutes of using linux.

Thanks again for all the replies,
T.

Have a look at this ;)

[http://video.google.co.uk/videoplay?docid=-7056097566237493627](http://video.google.co.uk/videoplay?docid=-7056097566237493627)

---

### Post by troegs on 2009-02-04
Heh, I'd love to however everytime I browse to a page and the "plugin needed" message comes up for flash, the install fails and so thus far I can't view flash. Any help with this?

---

### Post by Tomatz on 2009-02-04
> **troegs said:**
> Heh, I'd love to however everytime I browse to a page and the "plugin needed" message comes up for flash, the install fails and so thus far I can't view flash. Any help with this?

Open a terminal and copy and paste the following text in to it.

```
sudo apt-get install flashplugin-nonfree
```

Now **_close firefox_** and press **return**.

Now you can watch the video. 

Also you could install flashplayer *(flashplugin-nonfree)* in the synaptic package manager which is a GUI based installer. Its just easier to give command based instructions on the forums as its just one operation to explain rather than explaining what menu to go to or what button to press etc.

---

### Post by troegs on 2009-02-04
will do. thanks. Also after I posted the question I found something detailing that said to go to the add/remove in applications, then select all available applications then search for ubuntu-restricted-applications. What am I getting myself into there? Is this something I should be doing? 

I'll be doing the terminal stuff in between checking back. thanks for the fast replies tomatz

---

### Post by davidwaine on 2009-02-04
Or get the official .deb here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

download and click to install

---

### Post by donkyhotay on 2009-02-04
> **troegs said:**
> On a side note I am curious. Are the majority of programs installed via the terminal? Just curious.

Depends, I personally use synaptic (a GUI program) for most of my install/uninstall needs but when helping someone unfamiliar with computers it is usually easier to have them copy/paste
```
sudo apt-get install pidgin
```
then it is to say, launch synaptic, refresh, search for pidgin, etc...

On the other hand if you're not installing something from the repositories (such as from source for example) then you are almost always going to be using the CLI.

---

### Post by troegs on 2009-02-04
I put in the command you told me to and this was the output:

chris@ichabod:/$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

assuming this meant it didn't work. Did I get something wrong?

---

### Post by troegs on 2009-02-04
> **davidwaine said:**
> Or get the official .deb here:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

download and click to install

just curious. As stated I'm a new linux owner. I'm seeing this .deb a lot. what exactly i that?

---

### Post by newbee70 on 2009-02-04
> **troegs said:**
> I put in the command you told me to and this was the output:

chris@ichabod:/$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

assuming this meant it didn't work. Did I get something wrong?


Go to 

applications / "add /remove" / select all packages at top

search for adobe:   adobe flash 10 is available. install it.

---

### Post by davidwaine on 2009-02-04
It is a file type for programs that install under debian based linux distributions including ubuntu. It is similar to the .exe files you will have seen in windows.

---

### Post by troegs on 2009-02-04
thanks for the definition of deb. I ended up just doing an install of all restricted extras which did include flash. 

Thanks again for all your help.

Gotta love how cool the community is.

---

### Post by tarps87 on 2009-02-05
> **troegs said:**
> Also @ Tarps. Whatever I did, the terminal definitely wasn't listing the files. It looked pretty much like when you try and open a program via word or some text editor. only it was rushing past the screen. Zig zags of random numbers, letters, and indistinguishable digits. As mentioned before though a Linux noob, I am a programmer. Pretty sure it was code. Just hope I didn't foul anything up my first 20 minutes of using linux.


That does sound like machine code, I'm not sure what caused that but it doesn't sound like it damaged your install. If you want you can post the command you used and I will try and work out what happened.
I noticed you were studying CS, could I ask were? I'm interested in knowing what uni's are using Linux. I'm on a sandwich year as part of my course ad the Uni of Herefordshire who are also using Linux (openSuse)

---

