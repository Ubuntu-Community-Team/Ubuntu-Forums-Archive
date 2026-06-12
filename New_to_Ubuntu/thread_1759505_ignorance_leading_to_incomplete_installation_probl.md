---
title: "ignorance leading to incomplete installation problems"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by tandrew on 2011-05-15
while attempting to find a way to play wav files i downloaded a command recommended from another forum and it refuses to install and now i get message that i cannot install any kind of software because this particular installation was not completed....however, it will not complete.  Below is the command, any help would be appreciated.  Ubuntu was installed on my computer by a relative who has since moved away and I am not really up to snuff on computer technology to deal with all of this, so soon it will back to MS windows.
thanks for any help.

                     pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }  sudo aptitude install ubuntu-restricted-extras libdvdcss2 libdvdread3 w32codecs gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-pitfdll non-free-codecs

---

### Post by Rocket2DMn on 2011-05-15
Can you please post the error message that you get when you try to install something?

---

### Post by Larkspur on 2011-05-15
Hi Tandrew, I don't have experience of this particular problem, but until someone with more knowledge comes along, try entering:

```
sudo aptitude update
```

And then try your command again.  If that doesn't work, copy whatever it says in the terminal into your reply.

---

### Post by tandrew on 2011-05-15
Now when i click 'install' i get the spinning wheel that goes on forever, but if i click on that i get the message 'waiting for other software managers to quit'

---

### Post by alphacrucis2 on 2011-05-15
> **tandrew said:**
> Now when i click 'install' i get the spinning wheel that goes on forever, but if i click on that i get the message 'waiting for other software managers to quit'

Probably means you have more than one package installer running. You can only have one of, update manager, ubuntu software centre, synaptic etc running at a time.

---

### Post by tandrew on 2011-05-15
i will try this....when i attempt to install the original command, i get a window that is stuck on the message that has something to do with ttf-fonts-installer

---

### Post by tandrew on 2011-05-15
how do i stop it?

---

### Post by alphacrucis2 on 2011-05-15
> **tandrew said:**
> i will try this....when i attempt to install the original command, i get a window that is stuck on the message that has something to do with ttf-fonts-installer

Is that the one where you have to use the tab key to highlight OK and hit enter to accept the licence?

---

### Post by tandrew on 2011-05-15
this is screen info when i do the above command of sudo aptitude update

tandrew@tandrew-laptop:~$ sudo aptitude update
[sudo] password for tandrew: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)

---

### Post by tandrew on 2011-05-15
yes
only in my ingorance i didn't know how to do that......

---

### Post by tandrew on 2011-05-15
> **alphacrucis2 said:**
> Is that the one where you have to use the tab key to highlight OK and hit enter to accept the licence?

sorry, yes that is the one, and i did not know how to activate the OK and just closed the window after waiting forever

---

### Post by tandrew on 2011-05-15
should i attempt to reinstall now that I have this little piece of information?

---

### Post by tandrew on 2011-05-15
> **tandrew said:**
> sorry, yes that is the one, and i did not know how to activate the OK and just closed the window after waiting forever

when i attempt to reinstall the original command, terminal will not take it and I get the same last four lines that are in the screen shot i sent earlier.....is it time to take to pro's somewhere?

---

### Post by alphacrucis2 on 2011-05-15
> **tandrew said:**
> when i attempt to reinstall the original command, terminal will not take it and I get the same last four lines that are in the screen shot i sent earlier.....is it time to take to pro's somewhere?

If you log out and log back in, that should kill any install progs that are running in the background. Try that and then rerun the command

---

### Post by tandrew on 2011-05-15
> **tandrew said:**
> sorry, yes that is the one, and i did not know how to activate the OK and just closed the window after waiting forever

> **alphacrucis2 said:**
> If you log out and log back in, that should kill any install progs that are running in the background. Try that and then rerun the command

ok, i know this takes me deeper into the woods, but i don't know what you mean by log out and log back in. on my computer i just turn it on and off...it automatically logs in (I guess), or are you talking about a process that happens in terminal

---

### Post by alphacrucis2 on 2011-05-16
> **tandrew said:**
> ok, i know this takes me deeper into the woods, but i don't know what you mean by log out and log back in. on my computer i just turn it on and off...it automatically logs in (I guess), or are you talking about a process that happens in terminal

Oh. Mine is set up for me to enter a user code and password to log in. If I select logout from the menu for the power button in the top right hand corner then it takes me back to the login screen. Part of that process shuts down all the programs started since login. Not sure how to get the same effect if your install is set up to auto login. A shutdown and restart will achieve the same thing (probably quicker than trying to work out what you have running) - I'm assuming you are using Natty (11.04), which has made it a little bit obscure to figure out all the things you have running but you can cycle through them via ALT-TAB. IMO this is one of the weaknesses of the new UNITY interface, especially for newbies.

---

### Post by tandrew on 2011-05-16
> **alphacrucis2 said:**
> Oh. Mine is set up for me to enter a user code and password to log in. If I select logout from the menu for the power button in the top right hand corner then it takes me back to the login screen. Part of that process shuts down all the programs started since login. Not sure how to get the same effect if your install is set up to auto login. A shutdown and restart will achieve the same thing (probably quicker than trying to work out what you have running) - I'm assuming you are using Natty (11.04), which has made it a little bit obscure to figure out all the things you have running but you can cycle through them via ALT-TAB. IMO this is one of the weaknesses of the new UNITY interface, especially for newbies.

i will see what i can do in the few remaining minutes of being awake....thanks for all of your help.  I will let you know how it turns out.

---

### Post by tandrew on 2011-05-16
> **Rocket2DMn said:**
> Can you please post the error message that you get when you try to install something?

window titled "PACKAGE OPERATION FAILED the installation or removal of a software package failed.

E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package. (due to missing arch): 

thanks
tom

---

### Post by Swagman on 2011-05-16
Try a simple

```
sudo dpkg --configure -a
```


If that doesn't fix it you will have to go deeper..

ie:

```
sudo gedit /var/lib/dpkg/status
```

The above (second) command will open dpkg list of everything you installed.

Search for your broken package ttf-mscorefonts

Mine reads

> 
Package: ttf-mscorefonts-installer
Status: install ok installed
Priority: optional
Section: contrib/fonts
Installed-Size: 216
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: msttcorefonts
Version: 3.2ubuntu2
Replaces: msttcorefonts (<< 2.6)
Provides: msttcorefonts
Depends: wget, cabextract, xfonts-utils, defoma, debconf (>= 0.5) | debconf-2.0
Recommends: ttf-liberation, x-ttcidfont-conf
Conflicts: msttcorefonts (<< 2.6)
Conffiles:
 /etc/defoma/hints/ttf-mscorefonts-installer.hints 26fd3c37389de3bfdd85044d0a50fd4f
Description: Installer for Microsoft TrueType core fonts
 This package allows for easy installation of the Microsoft True Type
 Core Fonts for the Web including:
 .
   Andale Mono
   Arial Black
   Arial (Bold, Italic, Bold Italic)
   Comic Sans MS (Bold)
   Courier New (Bold, Italic, Bold Italic)
   Georgia (Bold, Italic, Bold Italic)
   Impact
   Times New Roman (Bold, Italic, Bold Italic)
   Trebuchet (Bold, Italic, Bold Italic)
   Verdana (Bold, Italic, Bold Italic)
   Webdings
 .
 You will need an Internet connection to download these fonts if you
 don't already have them.
 .
 NOTE: the package ttf-liberation contains free variants of the Times,
 Arial and Courier fonts. It's better to use those instead unless you
 specifically need one of the other fonts from this package.
Original-Maintainer: Thijs Kinkhorst <thijs@debian.org>


You might have to highlight.. remove & save to recover your systm.

**Don't just go ahead and do this willy-nilly**

I've only done it once (with another dpkg issue) and am not sure enough in the process.

Wait for someone a bit more experienced than me to verify what I just said.. or...

Do it on your own head !!

---

### Post by tandrew on 2011-05-16
> **Swagman said:**
> Try a simple

```
sudo dpkg --configure -a
```
If that doesn't fix it you will have to go deeper..

ie:

```
sudo gedit /var/lib/dpkg/status
```The above (second) command will open dpkg list of everything you installed.

Search for your broken package ttf-mscorefonts

Mine reads



You might have to highlight.. remove & save to recover your systm.

**Don't just go ahead and do this willy-nilly**

I've only done it once (with another dpkg issue) and am not sure enough in the process.

Wait for someone a bit more experienced than me to verify what I just said.. or...

Do it on your own head !!
thanks
this is what i get when i do the second command:
Package: ttf-mscorefonts-installer
Status: install reinstreq half-installed
Priority: optional
Section: contrib/fonts
Version: 3.2ubuntu0.1

---

### Post by Swagman on 2011-05-16
I'd try a remove and reinstall on that.

You can do it in the cli (Terminal) or via synaptic (System/Administration/Synaptic)

First try the Edit menu.. Fix broken packages... If that doesn't work then..

Enter ttf-mscore in the search and right click on the resulting "ttf-mscorefonts-installer" and select "Mark for complete removal"

[img]http://img808.imageshack.us/img808/228/ubuntu188.jpg[/img]

Click apply

Close Synaptic... I'd do a shutdown & restart and go into Synaptic and using the same technique... Reinstall ttf-mscorefonts

---

### Post by tandrew on 2011-05-17
swagman,
thanks so much for your help, your solution led, eventually, to solving my problem.  I tried to remove but machine suggested reinstallation....downloaded package again from Ubuntu page, synaptic considered it an upgrade and it was installed without a problem
thanks again
tom

---

