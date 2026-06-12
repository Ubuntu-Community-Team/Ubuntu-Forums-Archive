---
title: "problems un resolved"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by D BRUCE on 2010-04-28
Hello all
I installed ubuntu9.04 1 year back on my machine but I didn't understand the system
at all.I gave up for some time.Now I want to be a serious Linux user.

I need help in following three problems

1) How to connect to internet through my broadband modem.I've downloaded and used    
    modem scanner but it didn't work.

2) How to write shell scripts and execute?.I tried vi command but I didn't understand the 
    result and not able to use the editor.

3) How can I install media players to play mp3 songs?.I already posted it and got good 
    responses but I downloaded the tar files offline and tried to install but that didn't work  
    installation process in Linux is very new to me.

Please help me to get out of these situations.

regards
D Bruce

---

### Post by D BRUCE on 2010-04-28
Hello all
I installed ubuntu9.04 1 year back on my machine but I didn't understand the system
at all.I gave up for some time.Now I want to be a serious Linux user.

I need help in following three problems

1) How to connect to internet through my broadband modem.I've downloaded and used    
    modem scanner but it didn't work.

2) How to write shell scripts and execute?.I tried vi command but I didn't understand the 
    result and not able to use the editor.

3) How can I install media players to play mp3 songs?.I already posted it and got good 
    responses but I downloaded the tar files offline and tried to install but that didn't work  
    installation process in Linux is very new to me.

Please help me to get out of these situations.

regards
D Bruce

---

### Post by D BRUCE on 2010-04-28
I really didnt' get it. Is there any mistake????

---

### Post by lockalidiot on 2010-04-28
1. Lets wait until someone wise shows up.

2. Same.

3. Install ubuntu-restricted-extras with terminal command:

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Steven_S on 2010-04-28
(same question as [http://ubuntuforums.org/showthread.php?t=1464452](http://ubuntuforums.org/showthread.php?t=1464452) with the same poster)

---

### Post by thebigob on 2010-04-28
> **D BRUCE said:**
> 
1) How to connect to internet through my broadband modem.I've downloaded and used    
    modem scanner but it didn't work.

We will need more information on this. What kind of modem do you have what version of Ubuntu are you using? How are you connecting the modem to your machine?

> **D BRUCE said:**
> 
2) How to write shell scripts and execute?.I tried vi command but I didn't understand the 
    result and not able to use the editor.

Try on line guides for example:
[http://www.freeos.com/guides/lsst/](http://www.freeos.com/guides/lsst/)


> **D BRUCE said:**
> 
3) How can I install media players to play mp3 songs?.I already posted it and got good 
    responses but I downloaded the tar files offline and tried to install but that didn't work  
    installation process in Linux is very new to me.
 

lockalidiot is correct and his code will achieve what you are looking for

---

### Post by tom.swartz07 on 2010-04-28
> **D BRUCE said:**
> Hello all
I installed ubuntu9.04 1 year back on my machine but I didn't understand the system
at all.I gave up for some time.Now I want to be a serious Linux user.

I need help in following three problems

1) How to connect to internet through my broadband modem.I've downloaded and used    
    modem scanner but it didn't work.

2) How to write shell scripts and execute?.I tried vi command but I didn't understand the 
    result and not able to use the editor.

3) How can I install media players to play mp3 songs?.I already posted it and got good 
    responses but I downloaded the tar files offline and tried to install but that didn't work  
    installation process in Linux is very new to me.

Please help me to get out of these situations.

regards
D Bruce

Hey D Bruce,

Welcome (back) to Ubuntu!

Could you give more information about your modem and what specifically the problem is?



In order to play mp3 files, you need to install the proper codecs. Open up the software center from the applications menu, and install Ubuntu-restricted-extras. This installs many closed source applications, such as Java, Flash, and mp3 codecs. 

You dont only have to use vi for writing code. Gedit works great, you could open it up and change the format highlighting at the bottom of the app.


Hope this helps!

---

### Post by 3rdalbum on 2010-04-28
> **D BRUCE said:**
> 1) How to connect to internet through my broadband modem.I've downloaded and used    
    modem scanner but it didn't work.

Connect your computer via Ethernet cable to the broadband modem, and Ubuntu should get a connection automatically. If you find that you can't access websites, then the router isn't correctly passing DNS information - you can go to System > Preferences > Network Connection, select your Ethernet entry under Wired, click Edit and go to IPv4 Settings tab, change the method to "Automatic (DHCP) Addresses Only" and enter the following in the DNS field:

```
208.67.220.220
```

Disconnect and reconnect and you'll be up and running.

> 2) How to write shell scripts and execute?.I tried vi command but I didn't understand the 
    result and not able to use the editor.

Vi is not easy to use for beginners. You can create shell scripts in Gedit (Applications > Accessories > Text Editor) or with the 'nano' command.

> 3) How can I install media players to play mp3 songs?.I already posted it and got good 
    responses but I downloaded the tar files offline and tried to install but that didn't work  
    installation process in Linux is very new to me.

Get your internet connection first, and then go to Synaptic Package Manager and hit the reload button, so you have a list of what files are in the repositories. Then install the "ubuntu-restricted-extras" package from Synaptic and you'll have Flash, Microsoft fonts, Java, MIDI playback, MP3 playback and all sorts of other video and audio format support.

In Linux you don't "download the tar files and install" unless there's no other option. Usually tar.gz archives contain the source code of the program, which needs to be compiled first. And I don't believe any media players except possibly VLC will actually include inbuilt codecs, they all use the ones installed in the system.

Stick to the repositories (Ubuntu Software Center or Synaptic Package Manager, they are both frontends for the same set of repositories). Installing from the repositories is more correct, and it's easier. In short, it's Better with a capital B.

---

### Post by alphacrucis2 on 2010-04-28
> **D BRUCE said:**
> Hello all
I installed ubuntu9.04 1 year back on my machine but I didn't understand the system
at all.I gave up for some time.Now I want to be a serious Linux user.

I need help in following three problems

1) How to connect to internet through my broadband modem.I've downloaded and used    
    modem scanner but it didn't work.

If it is an ethernet connection from the modem to the PC it should be automatic. You don't normally have to download anything in most cases.

> 2) How to write shell scripts and execute?.I tried vi command but I didn't understand the 
    result and not able to use the editor.

vi is a subject all of its' own. Best look up the various online tutorials that explain it. For basic stuff just use the gedit gui editor. Similar for bash scripts, you aren't going to learn that on a forum. A tutorial is what you want for that. By all means ask here on specific questions.


> 3) How can I install media players to play mp3 songs?.I already posted it and got good 
    responses but I downloaded the tar files offline and tried to install but that didn't work  
    installation process in Linux is very new to me.


No need to download tar files. Just use the package manager. There are plenty of mp3 players such as Rythmbox (comes already installed), Banshee, Songbird, Amarok. Just install the later ones via the package manager.

---

### Post by philinux on 2010-04-28
Threads merged.

---

### Post by eriktheblu on 2010-04-28
1. I think the people who can help you need more info. Brand and model of the modem would be helpful.

2. I've not yet attempted vi. For scripts I use Gedit or Nano when I'm feeling nerdy. Since I'm still a beginner with Bash, I won't attempt to instruct you there. Make sure you set your script's properties to executable (either graphically, or with chmod)

3. The default media player will play mp3s just fine if you have the proper codec installed. Easiest way is the restricted extras package as stated above. However, since your modem doesn't work, it's doubtful you can access the repositories. Anyone know where D BRUCE might download a .deb?

---

