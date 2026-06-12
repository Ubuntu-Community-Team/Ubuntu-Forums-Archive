---
title: "I've Tried... but i cant seem to wrap my head around this..."
date: 2009-08-28
forum: New to Ubuntu
---

### Post by confused. on 2009-08-28
Ok, So I'm new to Ubuntu, but not to computers. Don't get me wrong, I'm no techy, but I like to think I generally know my way around a computer. BUT I can't for the life of me figure out how to load things on to my computer using Ubuntu! All I want to download is a silly game I used to play when I was younger. Its called Tibia. Its a little RPG game, and I've never had a problem with it... that is until now. 
When I goto the site, it gets me to download it into that little download box (I'm using firefox), and then when I try to open it, it opens into its own application window called tibia850.tgz and I can't get past that! I've read all the forums I can read, and I just don't understand!! 
In laymans terms can someone please help me?

---

### Post by Viva on 2009-08-29
Is this the tibia you are talking about? They seem to have a repository available [http://yetanother.tibiaclient.com/downloads/debian-repository]("http://yetanother.tibiaclient.com/downloads/debian-repository"). tgz files are normally source files that you need to compile yourself. Always try to find a .deb file(similar to .msi installers in windows) or a repository so that you can install the software using the package manager and get updates for the software too.

---

### Post by zipperback on 2009-08-29
There is a .deb package available that you should be able to download and install.

[http://yetanother.tibiaclient.com/downloads#debian](http://yetanother.tibiaclient.com/downloads#debian)

Ubuntu is based on Debian so the debian .deb package should probably work for you.

Are you running the 32bit or 64bit version of Ubuntu? If you're running the 64bit version, then you will probably need to download and compile the application form source because I didn't notice a 64bit .deb package.

- zipperback
:popcorn:

---

### Post by earthpigg on 2009-08-29
> **zipperback said:**
> There is a .deb package available that you should be able to download and install.

[http://yetanother.tibiaclient.com/downloads#debian](http://yetanother.tibiaclient.com/downloads#debian)

Ubuntu is based on Debian so the debian .deb package should probably work for you.

Are you running the 32bit or 64bit version of Ubuntu? If you're running the 64bit version, then you will probably need to download and compile the application form source because I didn't notice a 64bit .deb package.

- zipperback
:popcorn:

or he could repackage the 32 bit deb for 64 bit. takes 5 min.

[http://ubuntuforums.org/showthread.php?t=1070885](http://ubuntuforums.org/showthread.php?t=1070885)

:D

---

### Post by confused. on 2009-08-30
The version I'm using is Ubuntu 8.04, I'm sorry but I don't know how to find out what my bit is... I'm hopeless I know. 
So I went to both sites that were mentioned, the first one I couldn't figure out what I was supposed to do... But the second one I downloaded the .deb packages, and thats as far as I can get. The next directions it gives is "Go to that folder with terminal and type:[FONT=courier new] su -c "dpkg -i yatc_*.deb tibia-data_*.deb"", [FONT=Verdana]I know where the Terminal is, but I have NO idea how to use it. [/FONT]


[/FONT]

---

### Post by earthpigg on 2009-08-30
> **confused. said:**
> The version I'm using is Ubuntu 8.04, I'm sorry but I don't know how to find out what my bit is... I'm hopeless I know. 
So I went to both sites that were mentioned, the first one I couldn't figure out what I was supposed to do... But the second one I downloaded the .deb packages, and thats as far as I can get. The next directions it gives is "Go to that folder with terminal and type:[FONT=courier new] su -c "dpkg -i yatc_*.deb tibia-data_*.deb"", [FONT=Verdana]I know where the Terminal is, but I have NO idea how to use it. [/FONT]


[/FONT]

applications -> accessories -> terminal.

this is the terminal aka shell aka bash. this is where the magic happens.

type this to find out what version of ubuntu you are using, type this:

```
uname -a
```

example:

```
chris@mason-netbook:~$ _**uname -a**_
Linux mason-netbook 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 _**i686**_ GNU/Linux
chris@mason-netbook:~$ 
```

for our purposes, _**i686**_ and i386 and x86 all mean the same thing: 32 bit.

for our purposes, amd64 and x86-64 mean the same thing: 64 bit.



and **screw terminal commands to install that .deb files**. double click on it and tell us how that works out for ya :D

---

### Post by The Cog on 2009-08-31
> The next directions it gives is "Go to that folder with terminal and type: su -c "dpkg -i yatc_*.deb tibia-data_*.deb" 
That won't work on Ubuntu - it was written for Debian. For Ubuntu you must use sudo rather than su. The command would be more like this:
> sudo dpkg -i yatc_*.deb tibia-data_*.deb although if they are the only two .deb packages in the directory it could be simplified to
> sudo dpkg -i *.deb

---

### Post by Ms_Angel_D on 2009-08-31
deb packages are similar to exe files in that all you have to do is double click the file to run it.

but instead of downloading the deb first you should to go to system->administration->synaptic package manager and search fort the game your looking for, if by some chance it's in there you then checkmark the box next to it and click apply all done and installed.

If the game isn't in there, then you would download the .deb packages and run those as I stated above, just double click them. Just make sure the deb files you download are for Ubuntu 8.04 Hardy Heron

---

### Post by The Cog on 2009-08-31
> **Ms_Angel_D said:**
> deb packages are similar to exe files in that all you have to do is double click the file to run it.

I've never made that work if you have more than one .deb and they are mutually dependent. I tried selecting all of them and choosing File-Open but that opens multiple gdebi windows that each complain about needing other .debs. That's why I suggested using dpkg -i in this instance.

---

### Post by Ms_Angel_D on 2009-08-31
> **The Cog said:**
> I've never made that work if you have more than one .deb and they are mutually dependent. I tried selecting all of them and choosing File-Open but that opens multiple gdebi windows that each complain about needing other .debs. That's why I suggested using dpkg -i in this instance.

Yes I just wanted to follow up a bit ;)


OP: I registered & Downloaded the file tibia850.tgz I unzipped it and was able to launch the game using the file

StartTibia.sh

Just make sure the file is set to be executable and double click then click Run, and you'll be playing in no time ;).

---

### Post by confused. on 2009-09-01
YAY!! You guys ROCK!! I got it to work, I can log in and everything, the only thing is it flickers I don't know who to explain it... Its also a very small screen, I thought it was supposed to launch full screen, or at least have the option, but it doesn't. Anyone have a clue as to why? If not, its not something I can't live with, but I just figured if someone had any ideas... 
Thanks again!!

---

### Post by earthpigg on 2009-09-01
for that, you will need to see the documentation for that *specific* application.

its usually found by typing this into a terminal:
> man application-name-here
(man is short for manual)

failing that, look for other folks playing that game that have had the same problem.

---

### Post by confused. on 2009-09-02
> **confused. said:**
> Its also a very small screen, I thought it was supposed to launch full screen, or at least have the option, but it doesn't. Anyone have a clue as to why? If not, its not something I can't live with, but I just figured if someone had any ideas... 


Ok, so I figured out that part all on my own! Proud of me aren't you? Haha. But it still flickers, while I'm playing it will quickly minimize and then maximize. Its very annoying, but I'm going to bug the Tibia help forums and see if they know whats going on. 
Thanks again to everyone who helped!! You guys rock!

---

### Post by Perfect Storm on 2009-09-02
> **confused. said:**
> Ok, so I figured out that part all on my own! Proud of me aren't you? Haha. But it still flickers, while I'm playing it will quickly minimize and then maximize. Its very annoying, but I'm going to bug the Tibia help forums and see if they know whats going on. 
Thanks again to everyone who helped!! You guys rock!

That might be a compiz problem;

```
sudo apt-get install compizconfig-settings-manager emerald
ccsm
```

Click **General** category thereafter choose **General Options**.
In **General** tab, you'll see an option called; **Unredirect Fullscreen Windows**. Unselect it.

---

### Post by Jazzy_Jeff on 2009-09-02
Make sure you turn off the compiz desktop effects when playing games. Just right click on the desktop and click on the Visual Effects tab and check None.

---

### Post by confused. on 2009-09-06
You guys are awesome! Everything is perfect! I downloaded the compiz file, and figured out how to turn off the visual effects, and everything works great!
Thanks a million everyone!

---

