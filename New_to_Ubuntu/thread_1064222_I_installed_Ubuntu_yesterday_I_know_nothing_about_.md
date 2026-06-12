---
title: "I installed Ubuntu yesterday I know nothing about it, What should I know, do, install"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by djini on 2009-02-08
Yep the title say's it all. I have been able to navigate around the main interface, havn't installed anything or messed around with command lines. I am running this as a secondary computer on old hardware.

(btw whats up with the thread prefix's?)

---

### Post by cyfur01 on 2009-02-08
This largely depends on what you hope to use Ubuntu for. A decent starting place for coming to grips with the basics of Ubuntu would be this free manual:
[http://www.ubuntupocketguide.com/download2.html]("http://www.ubuntupocketguide.com/download2.html")
It talks a bit about basic Ubuntu usage and management, and starts into command-line usage, etc.

---

### Post by feisty on 2009-02-08
in terminal:
sudo apt-get update
sudo apt-get moo

fire up firefox and install:
adobe flash player
adobe reader
new themes
new icons 
new background

open synaptic and search:
gstreamer and install mp3 and avi plugins
install wine
install opera
install [conky]("http://ubuntuforums.org/showthread.php?t=281865")
vlc
.
.

---

### Post by jakupl on 2009-02-08
> **feisty said:**
> 
sudo apt-get moo


X)

although you do not need sudo for that command :)

---

### Post by Osamabingandhi on 2009-02-08
Start to install programs you've need. Some great programs is: Ktorrent, Amarok, amsn, K3b, Skype, VlC, screenlets, Wine for windows-program, Samba for windows share, Compiz for effects. Codecs for mp3 and video, I usually just use the ones that the movieplayer installs by itself when it try to play a video it doesn't recognize. 

If you have a windows machine install samba and share folders in ubuntu so you can reach them from the windows. Just check the firewall in ubuntu and windows so it doesn't block the connection.

Then see if drivers for your graphic card is installed. Best it nvidia.

All i have to say is that ubuntu is really really good nowadays. Some small problems still but mostly things work now.

---

### Post by steveneddy on 2009-02-08
Just use it as you would any other computer?

What do you usually do on a computer?

Read the links in my sig for further instructions.

---

### Post by djini on 2009-02-08
Thanks everybody! this would be used primarilly for web browsing and doing stuff with my cowon D2

btw.

(add stuff with open office and the like to the above list)

---

### Post by mandeepsmagh on 2009-02-08
It all depends on your needs. Generally installing Amarok, VLC is a good starting point.

---

### Post by bgates on 2009-02-08
I will tell you my number one noob mistake so you can avoid it.  (The fact that I support Windows full time may provide some insight into why I was trying to do this...)

When I first installed Ubuntu, I would think of an application I wanted.  I would go to the website for the application, and download the source.  I would compile it.  Often, I received a message that there were dependencies I did not have installed.  So I would search the website of the dependency, and download the source for that and compile it.  Maybe it would report a dependency not present as well, so I would go and search that and compile it.  Return to compiling original application, find it was missing yet another dependency.  Repeat, etc.

While it does work to do it that way, I would inevitably, after an hour or two, realize I could have just used apt-get or Add/Remove... (one time I even did this for an application that was already installed and I simply wanted to upgrade it).

---

### Post by yeats on 2009-02-08
> **bgates said:**
> 
When I first installed Ubuntu, I would think of an application I wanted.  I would go to the website for the application, and download the source.  I would compile it.  Often, I received a message that there were dependencies I did not have installed.  So I would search the website of the dependency, and download the source for that and compile it.  Maybe it would report a dependency not present as well, so I would go and search that and compile it.  Return to compiling original application, find it was missing yet another dependency.  Repeat, etc.

I'll add that it's very easy to bork up your installation this way, too.  There was a game I wanted to try out that was only available from source, and by the time I had gotten through updating seven or so shared libraries, my installation would not work correctly!  The repository version may not always be bleeding edge, but it's better to start there. :-)

---

### Post by jrusso2 on 2009-02-08
> **djini said:**
> Yep the title say's it all. I have been able to navigate around the main interface, havn't installed anything or messed around with command lines. I am running this as a secondary computer on old hardware.

(btw whats up with the thread prefix's?)

First thing I do is get all them restricted drivers working.  Then the  codecs, DVD, Flash and Java running and working with Firefox.

---

### Post by djini on 2009-02-08
Thanks everyone for the fast replies (suppose it;s the only kind one will get on this form) Are all apps available through add remove apps?

---

### Post by djini on 2009-02-08
> **jrusso2 said:**
> First thing I do is get all them restricted drivers working.  Then the  codecs, DVD, Flash and Java running and working with Firefox.

restricted drivers????

---

### Post by bgates on 2009-02-08
> **djini said:**
> Thanks everyone for the fast replies (suppose it;s the only kind one will get on this form) Are all apps available through add remove apps?

No, they are all not.  However, a vast plethora of apps that will do what you want in *most* situations, are.  The only thing I had to really go out of my way to install was a Citrix client for work, and even that I think had a .deb or something, so it didn't have to be compiled.  YMMV depending on the apps you need to use.

Also some apps are in repositories that are not in sources.list by default, but if you add them then the apps will be in Add/Remove.  Be careful that repositories you add are trustworthy.

---

