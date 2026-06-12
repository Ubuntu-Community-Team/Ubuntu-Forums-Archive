---
title: "Chromium and Save"
date: 2010-02-27
forum: New to Ubuntu
---

### Post by majnu on 2010-02-27
Hi,
 
I have XBMC Live installed and I am following this method to get Chromium launched through XBMC, but I have hit a snag. This is what I am doing:-
 
To install chrome on your system follow this steps:

First you need to edit the /etc/apt/sources.list file

sudo nano /etc/apt/sources.list

then add this two lines:

deb [[COLOR=#22229c]http://ppa.launchpad.net/chromium-daily/ppa/ubuntu[/COLOR]]("http://ppa.launchpad.net/chromium-daily/ppa/ubuntu") karmic main
deb-src [[COLOR=#22229c]http://ppa.launchpad.net/chromium-daily/ppa/ubuntu[/COLOR]]("http://ppa.launchpad.net/chromium-daily/ppa/ubuntu") karmic main

**save an exit the file**. Now add the GPG key using the following command:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5

And finally:

sudo apt-get update
sudo apt-get install chromium-browser

that's all.
 
From the bolded text I can not see any option to save and exit from the Terminal interface. How do I do it please and what button presses do I enter.
 
Any help will be appreciated. Thanks

---

### Post by majnu on 2010-02-27
bump

---

### Post by Wardje on 2010-02-27
CTRL+X to exit. You'll be prompted to save changes, press "y", then press enter to confirm the filename


Alternatively (and for future reference), pressing CTRL+O just saves it.

---

### Post by skymera on 2010-02-27
Alternatively you can replace nano with gedit for a GUI interface.

---

### Post by themusicalduck on 2010-02-27
To save the file press Ctrl + O and to exit press Ctrl + X

There's a list of the useful shortcuts at the bottom when nano runs. (Although they aren't clear at all. ^ means Ctrl and then the letter is the shortcut.. and WriteOut is a pretty weird way to say "save file")

---

### Post by majnu on 2010-02-27
thank you very much everyone. :D
 
I will try that and report back .

---

### Post by majnu on 2010-02-28
> **skymera said:**
> Alternatively you can replace nano with gedit for a GUI interface.
 
That command did not work. Anyway I have the following problem when running that script. Also I copied the below text all word for word and did not miss a space or type anything incorrectly. Please ignore the hyperlinks for some reason it puts them in, but I did type in Karminc Main.

deb [[COLOR=#22229c]http://ppa.launchpad.net/chromium-daily/ppa/ubuntu[/COLOR]]("http://ppa.launchpad.net/chromium-daily/ppa/ubuntu") karmic main
deb-src [[COLOR=#22229c]http://ppa.launchpad.net/chromium-daily/ppa/ubuntu[/COLOR]]("http://ppa.launchpad.net/chromium-daily/ppa/ubuntu") karmic main 
 
When I run **sudo apt-get update**

I get:- 

{ W:failed tp fetch [[COLOR=#22229c]http://ppa.launchpad.net/chromium-da...86/packages.gz[/COLOR]]("http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/karmin/main/binary-i386/packages.gz") 404 not found

E: some index files failed to download, they have been ignored, or old ones used instead.}

---

### Post by Soul-Sing on 2010-02-28
404 looks like a server faillure, try it again after some time.

---

### Post by majnu on 2010-02-28
Do you know how I can delete what I did so when I type "Sudo apt-get update" that the error goes away? I will try installing Firefox instead.
 
How long do I have to wait, the problems has been like that since yesterday?
 
Thanks for your reply.

---

### Post by majnu on 2010-02-28
I managed to delete

deb [[COLOR=#22229c]http://ppa.launchpad.net/chromium-daily/ppa/ubuntu[/COLOR]]("http://ppa.launchpad.net/chromium-daily/ppa/ubuntu")  karmic main
deb-src [[COLOR=#22229c]http://ppa.launchpad.net/chromium-daily/ppa/ubuntu[/COLOR]]("http://ppa.launchpad.net/chromium-daily/ppa/ubuntu")  karmic main 

now when I try and install firefox using this guide:-

1. Get firefox.  Enter terminal mode with ctrl-alt F3
 sudo apt-get install firefox

I had to do** sudo apt-get install update** before I could download firefox

2. Make a shortcut directory that xbmc can see
sudo mkdir /home/(your username)/shortcuts
3. make a symlink to this directory for firefox that allows you to run  firefox from launcher
ln -s /usr/lib/firefox  /home/(your username)/shortcuts/firefox
4. Install launcher 
get it from here  [http://code.google.com/p/xbmc-launcher/downloads/list](http://code.google.com/p/xbmc-launcher/downloads/list)
use winscp to put in /home/(your username)/.xbmc/plugins/programs   
5. Reboot to xbmc and open programs, program plugins, launcher
6. Choose standalone (normal PC executable) and choose firefox from Home  folder/shortcuts
7. At application arguments you can hit done.  Set title of the launcher  as firefox. You can get a firefox thumbnail and add to favorites if you  desire. 
8.  When you open firefox, it may only open in half the screen.  You get  mouse and keyboard focus by hitting the \  key.  You can resize it by  dragging or hit f11 for fullscreen toggle.  Once you exit firefox you  will need to hit the \ key to once again see xbmc fullscreen.  
9. One other thing.  Installing firefox somehow will ruin your  suspend/awake from suspend control by your remote (if you have this  working).  There is a ticket for this.  Basically, under shut down  functions, if you see ?0? and ?1? for choices, then you have this issue.   For me the following solved it. 
sudo apt-get remove policykit-1
 sudo apt-get remove devicekit-power

Now when I type in the bolded sectionahown above I get the error:-

[B]Reading package lists...Done
Reading dependency tree
Reading state information...Done
E: Couldn't find package update
[/B]
When I try and do **sudo apt-get install firefox** I get the following error

[B]The following packages have unmet dependencies:
Firefox: Depends: firefox-3.5 but is not going to be installed
              Depends: firefox-3.5-branding but is not going to be installed
[/B]**E:Broken packages**

Also is there a way that I can find this error in the directory, it saves me typing it all out. I am using winscp as suggested in the guide above and I can connect to my revo which has xbmc live installed on it.

Thank You

---

### Post by majnu on 2010-02-28
Anyone Please?
 
I really don't want to do my 5th re-install because I can't get past another hurdle lol

---

### Post by majnu on 2010-02-28
bump

---

### Post by Soul-Sing on 2010-02-28
maybe you could try synaptic packagemanager, option: find broken packages.

---

### Post by majnu on 2010-02-28
> **leoquant said:**
> maybe you could try synaptic packagemanager, option: find broken packages.
 
I have XBMC Live and that is CLI driven, and from looking on the web package manager is a a GUI. I think I will have to just do my 5th re-install aggghhhhhh.

---

### Post by Wardje on 2010-02-28
> **majnu said:**
> When I try and do **sudo apt-get install firefox** I get the following error

[B]The following packages have unmet dependencies:
Firefox: Depends: firefox-3.5 but is not going to be installed
              Depends: firefox-3.5-branding but is not going to be installed
[/B]**E:Broken packages**

What if you use aptitude? It can be nicer when playing with broken dependencies.
```
sudo aptitude install firefox
```

---

### Post by majnu on 2010-02-28
Hi everyone.

Sorry I re-installed xbmc live before I saw aptitude. I re-installed xbmc and carryed out all the instructions, i even  created a thumbnai which looks cool, but it does not launch.

I go Program>Program Plugins>Launcher>Firefox and nothing  happens.

I have no idea why it works for some people and not for me. Is there any way to test? The only thing I may have done differently is that I wrote in the CLI

sudo apt-get install firefox-3.6 and not sudo apt-get install firefox. Do you think that caused the problem

Help

---

### Post by majnu on 2010-02-28
bump
 
this firefox is rattling my cage :popcorn:

---

