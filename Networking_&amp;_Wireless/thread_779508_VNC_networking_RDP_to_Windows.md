---
title: "VNC networking RDP to Windows"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Malikius on 2008-05-02
Here's my problem. I need to be able to Remote desktop back and forth between Ubuntu and Windows (VNC)installed. I have read all the different threads and now of them have any Tutorials (step by step) instructions. 

I want to be able to work on a Ubuntu desktop from my Windows laptop and vise versa. Need to get a tutorial that isn't complicated and confusing with all sorts of codes to use. Just a straight forward setup so I can print it out and use it on all 6 of my systems. Is there such an animal available to Newbees? 

Please help me. I am wanting to switch entirely over to Linux but I still have people in the house that are hard core Windows users and I have to maintain the household networks. So, I need to be able to remote desktop to all the different OS's so that I am not running all over the house. This is my delema. Can or will anybody help me in this manner?

---

### Post by firedrow on 2008-05-02
Well Ubuntu to Windows is simple.  Turn on Remote Desktop Connection on Windows (Right-click My Computer, Remote tab, second check box).  Then use TSClient (Terminal Services Client) to connect to RDP for the Windows machine.  Or setup a VNC server on Windows, I recommend TightVNC, and you can still use TSClient for VNC, just change the protcol.

Now I can't tell you off the top of my head, but lookup "VNC server linux" or even "VNC Server Ubuntu" and you should be able to find a number of guides on setting up VNC server for you Ubuntu system.  Then you can use a VNC Viewer, again TightVNC is my suggestion, to login to your Ubuntu box.

Need more help, just ask.

---

### Post by Malikius on 2008-05-18
I tried a search for both of those options and got an error on the search for both. :( 

Sorry to be so dumb but I am new to Ubuntu and Linux. I also don't understand which file extensions are easiest to work with to install. Noticed that alot of things on this site are geared towards coding. 

HELP.

---

### Post by tact on 2008-05-18
> **Malikius said:**
> I tried a search for both of those options and got an error on the search for both. :( 

Sorry to be so dumb but I am new to Ubuntu and Linux. I also don't understand which file extensions are easiest to work with to install. Noticed that alot of things on this site are geared towards coding. 

HELP.

Are you using ubuntu Hardy?
System>Preferences>Remote Desktop
...then check the appropriate boxes for what you want the remote to be able to do.

Other variants of ubuntu (Gutsy/Feisty) may be similar.

Cheers

---

### Post by tact on 2008-05-18
> **Malikius said:**
> I tried a search for both of those options and got an error on the search for both. :( 

Sorry to be so dumb but I am new to Ubuntu and Linux. I also don't understand which file extensions are easiest to work with to install. Noticed that alot of things on this site are geared towards coding. 

HELP.

Not sure what you mean by - "I also don't understand which file extensions are easiest to work with to install."

But just guessing here's a tip...
Linux and Windows worlds are very different.   The way you do things in windows is often not how the same thing is done in linux.  This is not bad.  Its just different ways of thinking.

e.g. In windows-think when you want some software for a specific job you google around, and find a file to download and hope its not virus or malware infected.  That file may be zipped and so you need to unzip it to a temp directory, scan for nasties, etc...  eventually you click on an installer and it installs and you clean up deleting temp folders and downloaded archives.

In ubuntu (and most other linux distros) your first resort NOT to search the internet, or google - it is: 
System>Administration>Synaptic Package Manager    or....
Applications>Add-Remove

...because there is a massive number of software packages stored in "repositories" that you access quickly and easily and safely this way.  Software for almost every need.

Thats very different to windows-think huh?  And you don't need to know about file types for installation - because when you mark a package for installation it is downloaded, unpacked, installed and cleaned up after automatically.

Occasionally you will find some software you think you just MUST have and its not yet in the ubuntu software repositories yet (always look to check first!)...  In this case you do need to know a little more about package types:
-  First look in Synaptic or Add/Remove to see if your software is in the repo
-  Next option for ease of use is to see if the software you want is packaged in *.deb because you can download these, double click on the deb and it will install for you.
-  After the above two options it gets messy and you will have to google for more info but basically you could look for *.rpm next... 
-  Then of course comes "rolling your own" - compiling from source.

---

