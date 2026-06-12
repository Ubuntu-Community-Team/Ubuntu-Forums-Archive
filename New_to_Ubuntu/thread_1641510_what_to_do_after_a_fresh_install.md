---
title: "what to do after a fresh install"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by sp-1070 on 2010-12-09
The first things to do after a clean ubuntu installation.
 

 > Run the update manager and update that thing ! Don't need to explain that one I think.
 

 > Open the synaptic package manager and install java Java is needed by various programs and site's.
 

 > Just open an mp3 and after that a little piece of film By doing that you will be prompted to install some codec's witch you will need for playing the media.
 
One could skip these 2 steps by running

 ```
sudo apt-get install ubuntu-restricted-extras
``` This is a  package containing (among the other things) Java + the most used codecs + unrar  Thank you julio_cortez for this entry

To take pictures or record with you're webcam easely 
 > install cheese the fastest way to do this is by using a terminal and insert:
 

 ```
sudo apt-get install cheese
``` This lets you install some programs directly trough the terminal instead of downloading stuff
 

 If your 'e on a netbook or notebook you will want to install:
 

 >  Jupiter This program takes charge of power settings when on battery/ac power,
 also (and this I love) it rotates your 'e screen as well as your 'e mouse.
 

 For those who want to do photo editing use gimp its Linux version of photoshop.
 

 Also you might want to install the latest version of
 

 >  Wine  This to use certain windows only applications under Linux.
 
Entry's in name of goldfissh
Pidgin witch is an instant messaging service
Skype the all known voip provider
And the Google chrome browser.

Get pidgin and skype by using this command
```
sudo apt-get install pidgim skype
```

Get chrome by google

[Megaptera]("http://ubuntuforums.org/member.php?u=534545") invites us to take a look @
[http://www.webupd8.org/2010/04/what-...untu-1004.html]("http://www.webupd8.org/2010/04/what-to-do-after-installing-ubuntu-1004.html")
and
[http://breakthebit.org/post/56438060...x-ubuntu-10-04]("http://breakthebit.org/post/564380600/pimp-my-linux-ubuntu-10-04")


 I hope this helps you out getting started with your 'e new Linux system and gets you familiar with certain ''ways of the system'' so to say.
 I hope you will enjoy using your 'e new system and please if you want to know any thing your 'e already at this forum just register and ask around.
 One of the things so great about Linux is the community helping each other is just another part of Linux.

---

### Post by Verbeck on 2010-12-09
instead of opening a mp3 file, you could install the package *ubuntu-restricted-extras* to get all the codecs> **sp-1070 said:**
> 
 ```
sudo apt-get install cheese
``` This lets you install some  programs directly trough the terminal instead of downloading stuff
 
cheese is a web cam app

---

### Post by julio_cortez on 2010-12-09
> **sp-1070 said:**
> Java is needed by various programs and site's.
 By doing that you will be prompted to install some codec's witch you will need for playing the media.
By the way, maybe you should consider also installing **ubuntu-restricted-extras** which is a package containing (among the other things) Java + the most used codecs + unrar (which you seem to have overlooked).

Then, it really depends on what you want to do with your system: I usually install audacity and mixxx among the first packages, but your mileage may vary.

---

### Post by sp-1070 on 2010-12-09
Ok thank you Verbeck changed it good notice thnx again
And juilio_cortez thnx il add what you said in the thread.

Thanks you guys

---

### Post by sp-1070 on 2010-12-09
Ok every body please leave the things you directly install after the install if has some good worth for everybody il add it

---

### Post by jakupl on 2010-12-09
> **sp-1070 said:**
> 
 
One could skip these 2 steps by running
```
 sudo apt-get install ]**ubuntu-restricted-extras**
```




should be:

```
 sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Goldfissh on 2010-12-09
Usually when I've installed, I'll add my basic programs like Chrome, Pidgin and Skype.

After I'm up and running nice and stable, I'll start adding other programs to the list.

---

### Post by Megaptera on 2010-12-09
A very useful script here that can be checked before use. Newbie friendly and has the warning:

 "Like always, remember it's not recommended running a script without knowing exactly what it does, so I invite you to look at the code before running it."

Here's what the script does:

    * add extra repositories (Medibuntu, Getdeb, etc)
    * download and install the latest updates
    * install Ubuntu Tweak
    * install codecs, web browser plugins (Java, Flash), additional support for archives (RAR, 7-Zip) and additional fonts; installs the latest Flash Player for Ubuntu 10.04 Lucid Lynx 64bit from Adobe's website
    * Gconf tweaks: move the Metacity window buttons back to the right, disable the GDM login sound, fix the update manager behavior to always show updates and enable the icons in menus and buttons
    * install GIMP (which has been removed from Ubuntu 10.04 Lucid)
    * install VLC
    * install Thunderbird email client
    * install Chromium web browser
    * install Google Chrome - the latest dev version (it will download the 32 or 64 bit version automatically - depending on your system architecture)
    * install WINE
    * install MPlayer
    * set MPlayer and Totem character encoding to Central / Eastern European (Windows-1250), you can disable this by removing lines: 64 and 69,70,71,72,73,74,75, or selecting manual configuration from the script menu
    * install Pidgin instant messaging client



It's not much, but relatively new users as well as people installing Ubuntu on multiple machines will definitely find this useful.

[http://www.webupd8.org/2010/04/what-to-do-after-installing-ubuntu-1004.html](http://www.webupd8.org/2010/04/what-to-do-after-installing-ubuntu-1004.html)

---

### Post by Megaptera on 2010-12-09
Here's some suggestions for 10.04 Netbook Edition:

[http://breakthebit.org/post/564380600/pimp-my-linux-ubuntu-10-04](http://breakthebit.org/post/564380600/pimp-my-linux-ubuntu-10-04)

---

### Post by sp-1070 on 2010-12-09
edited Thnx

---

### Post by Megaptera on 2010-12-09
You're welcome!!

---

