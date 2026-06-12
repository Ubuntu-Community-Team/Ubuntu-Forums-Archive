---
title: "cant save /etc/X11/xorg.conf"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Oathanvil on 2011-02-20
How can I fix this?

ERROR:
You do not have adequate permission to open the existing X configuration file '/etc/X11/xorg.conf' for writing. You must be 'root' to modify the file.

Nvidia 470 GTX graphics card.

Trying to install BETA: NVIDIA-Linux-x86-270.18.run  Long story why I am not now using the WHQL as I am using a new ASUS Crosshair IV Motherboard that supports up to 5 different GPU's live at the same time. For ubuntu I just have the one card installed.
The chipset is running a RAID0 my Win7 boots on as well and ubuntu has issues reading the RAID0 array with the WHQL installed driver.

The issue is resolved with the Beta release Nvidia Driver.

Now all I would like to do is be able to save my xorg.conf file. I can open a Terminal and log in as sudo su but that has nothing to do with getting permission to save the /etc/X11/xorg.conf

It wont accept the fact I am logged as admin under / root partition.

anyone thank you.

Also how does one run the downloaded Linux driver from the desktop Downloads folder in ubuntu? If I try to allow the .exe to run it shows a working ubuntu icon then that goes away and nothing happens.

Not sure how the below programs work?
[http://en.opensuse.org/SDB:Starting_YaST](http://en.opensuse.org/SDB:Starting_YaST)

---

### Post by asmoore82 on 2011-02-20
> **Oathanvil said:**
> If I try to allow the ***.exe*** to run …
Is this a figure of speech?

---

### Post by owenll on 2011-02-20
you could try
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by coffeecat on 2011-02-20
If you've been running Opensuse before, you are probably trying to follow the suse admin model. for Ubuntu's, read this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

To edit xorg.conf. simply:

```
gksudo gedit /etc/X11/xorg.conf
```Don't use:

```
sudo gedit /etc/X11/xorg.conf
```Although you may get away with it with gedit, sudo rather than gksu/gksudo  can cause real problems with other graphical apps. See the link for details. 

> **Oathanvil said:**
> 
Not sure how the below programs work?
[http://en.opensuse.org/SDB:Starting_YaST](http://en.opensuse.org/SDB:Starting_YaST)

If you mean in Opensuse, you'll have to ask on an Opensuse forum. If you mean in Ubuntu, Yast is a Suse utility. I don't believe it's been ported to Ubuntu.

---

### Post by owenll on 2011-02-20
> **coffeecat said:**
> Don't use:

```
sudo gedit /etc/X11/xorg.conf
```Although you may get away with it with gedit, sudo rather than gksu/gksudo  can cause real problems with other graphical apps.
I've used it for years without problems - just read the stuff in the link - :redface: point taken - sorry for the bad advice.

---

### Post by Oathanvil on 2011-02-20
[FONT=Verdana]thank you to all who replied I can certainly look at the follow up advice in the post you provided but my main issue is I am not able to save the graphics configuration.[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]I did not mean to post so it looked like a figure of speech in the first post![/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]**/etc/X11/xorg.conf** [/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]is found when saving the graphic interface and says I do not have permission.[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]I find it extremely funtastic that there is 9000 million posts on this issue but no one has an answer, and or there is 500 different answers and most of them seem to work! but try to remember the last FIX you did so you can back that up if you need to search it out again.[/FONT]
[FONT=Verdana][/FONT] 
[FONT=Verdana]I am getting lost in the mud my bad I guess![/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]A computer relies on the graphics card to display everything related to software & games, how Ubuntu would not have taken steps to resolve graphics card driver issues within their own UI sort of defeats the whole purpose of the ubuntu operating system.[/FONT]
[FONT=Verdana] [/FONT]
[FONT=Verdana]The drivers are freely supplied by Nvidia for LINUX yet Linux wont allow them to function within their own OS.[/FONT]
 
I wish to also play :guitar:the Ubuntu laurels one day but I am not there yet!

---

### Post by G4Oblivion on 2011-02-20
If its a permissions issue and nothing else works you can lower the req permissions.

CAUTION: This will allow anyone/anything to read, write and execute the selected folder/file.

Open up the terminal and enter:
```
$ sudo chmod 777 /etc/X11/xorg.conf
```Once you have done what you needed to it put the permissions back to default by entering this:
```
$ sudo chmod 7**44** /etc/X11/xorg.conf
```I'm sure theres a better way to go about it, but I'm new to ubuntu/linux and thats the easiest way I know.

755 may be a little lax, I'm not sure what the default for xorg.conf is. 755 allows read, write and execute to root and read and execute for everyone else.
755 is default for most files & folders. EDIT: After thinking about it, I believe default for xorg.conf is 744. Read, write and execute for root and read for everyone else.

(I had to mess with the xorg.conf to underclock my gfx card on my laptop.)

---

### Post by Oathanvil on 2011-02-20
Picture of original issue!
[ATTACH]183971[/ATTACH]

WoW thank you G4Oblivion that got me past the user privliges issue and now it says!

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.

LOL I am trying just not certain how to program the terminals yet.

I suppose I should just delete that backup file so I can save a new xorg.conf not sure why its trying to write to the backup folder when there is a Valid xorg.conf file to write to?

A picture also included of where I am at now!
[ATTACH]183972[/ATTACH]

---

### Post by kevdog on 2011-02-20
I'll even throw another one into the mix

gksu will work in place of gksudo.  

It will save you a few letter typing, and if memory servers me correctly, gksudo is actually an alias for gksu.  The gk part refers to the gnome toolkit.  If you were using kde or Kubuntu, the command would then be kdesu, rather then gksu.  

Just some interesting tidbits.

---

### Post by G4Oblivion on 2011-02-20
This *should* work.

```
gksudo nvidia-settings
```

---

### Post by Oathanvil on 2011-02-20
RESOLVED! Holy Cows Batman I mean thank you thank you G4Oblivion! 
 
Ok so I Enter a Terminal typed in --> 
 
sudo su - 
 
then 
 
your command given --> 
 
gksudo nvidia-settings

Saved the xorg.conf with no error, issue resolved.

---

### Post by G4Oblivion on 2011-02-20
Glad it worked! :D

I thought it should have popped up the authentication prompt thing by default, though. (scratches head)

Worked out in the end :p

---

