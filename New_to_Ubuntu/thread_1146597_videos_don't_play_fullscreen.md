---
title: "videos don't play fullscreen"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by phantomjoker on 2009-05-02
In Firefox if i click the full screen button on the iplayer or similar websites the video appears full screen for a second, flashes and then the full screen image closes. 

This didn't happen before i updated to JJ 9.04

Any ideas?

---

### Post by phantomjoker on 2009-05-03
oh come on... this forums getting rubbish, my 5th question and not 1 reply.... what happened to the community?

no one has any idea?

---

### Post by phantomjoker on 2009-05-04
anyone....

---

### Post by phantomjoker on 2009-05-08
anyone in the world?

---

### Post by kansasnoob on 2009-05-08
OK, want to be sure, you just upgraded to Jaunty?

Only if this is Jaunty go to synaptic and click on Search (not quick search) and type "flash".

The only packages you should see installed are adobe-flashplugin and ubuntu-restricted-extras!

Everything else (especially swfdec* and gnash) should be marked for complete removal.

Then restart Firefox!

---

### Post by pro003 on 2009-05-08
> **kansasnoob said:**
> OK, want to be sure, you just upgraded to Jaunty?

Only if this is Jaunty go to synaptic and click on Search (not quick search) and type "flash".

The only packages you should see installed are adobe-flashplugin and ubuntu-restricted-extras!

Everything else (especially swfdec* and gnash) should be marked for complete removal.

Then restart Firefox!

I bumped in to this thread and saw this reply, nice tip. Earlier I used to have similar problems but not now, and I can see why.

---

### Post by phantomjoker on 2009-05-09
I have Jaunty

and when i look at my synaptic i dont have the package 'adobe-flashplugin' in the list at all....

I already have 'ubuntu-restricted-extras'


But two others i have installed are
flashplugin-installer
flashplugin-nonfree


how do i get 
adobe-flashplugin
in my synaptic list?

cheers

---

### Post by pro003 on 2009-05-09
> **phantomjoker said:**
> I have Jaunty

and when i look at my synaptic i dont have the package 'adobe-flashplugin' in the list at all....

I already have 'ubuntu-restricted-extras'


But two others i have installed are
flashplugin-installer
flashplugin-nonfree


how do i get 
adobe-flashplugin
in my synaptic list?

cheers

you should remove those two by typing in terminal:

```
sudo apt-get remove flashplugin-nonfree flashplugin-installer
```

and 
```

sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install -f
sudo apt-get clean
```

after that you'll should have adobe flashplugin in your list...

---

### Post by phantomjoker on 2009-05-09
> mckenzie@mckenzie-home:~$ sudo apt-get update
[sudo] password for mckenzie: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB [52.6kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB [4640B]
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB [35.2kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB [47.5kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources
Fetched 140kB in 0s (144kB/s)
Reading package lists... Done
mckenzie@mckenzie-home:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libtorrent-rasterbar0 ca-installer
  libboost-filesystem1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mckenzie@mckenzie-home:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libtorrent-rasterbar0 ca-installer
  libboost-filesystem1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
mckenzie@mckenzie-home:~$ sudo apt-get clean
mckenzie@mckenzie-home:~$ 


And at the end i did not have the adobe flashplugin in my synaptic.

I have removed the 2 other packages though.

Any ideas?

---

### Post by pro003 on 2009-05-09
you can go to adobe.com and download linux version of flash player and they have a deb package which is good cause you can just open it right away with gdebi and install it...

good luck

---

### Post by moleculeman on 2009-05-10
I'm now having this problem too, and none of the suggestions above are working.

Any other ideas?

---

### Post by phantomjoker on 2009-05-10
could you explain how to install a deb package?

cheers

---

### Post by moleculeman on 2009-05-10
This link [http://www.pendrivelinux.com/how-to-install-deb-packages/]("http://www.pendrivelinux.com/how-to-install-deb-packages/") explains how to install .deb packages.

---

### Post by phantomjoker on 2009-05-10
thanks!
will try it and report back!

---

### Post by phantomjoker on 2009-05-10
well i installed it, and thus installed adobeplugin, but the same think happens, even after a full restart.

---

### Post by 45acp on 2009-05-10
I had the same problem in intrepid. I found that if you right click on the video and disable hardware acceleration I could then play videos full screen.

---

### Post by phantomjoker on 2009-05-10
unfortuantly that doesnt help either... sorry!

cheers for the help though!

---

### Post by birddog165 on 2009-05-10
> **45acp said:**
> I had the same problem in intrepid. I found that if you right click on the video and disable hardware acceleration I could then play videos full screen.

I took your advice. It works, most of the time. Sometimes I can get fullscreen and other times not. Not sure why, but thanks.

---

### Post by Bölvaður on 2009-05-10
lol :) many people are getting help from this thread... but not the OP :D

Here is my guess.

Do you have 64 bit ubuntu? (if not, ignore this)
Google 64 bit adobe flash and download it from the adobe website. It is still in beta but it is quite good. If you will get a tar.gz or tar.bz2 with .so file in it, then place that file into the firefox plugin directory (you need to be root to do that)

firefox needs it in /usr/lib/firefox/plugins
so you can place the plugin where ever you want and just create a link in that location to point to the .so file.

If you need help with that just ask.

This should get you far (specially if you downloaded the stuff to your desktop)

alt+f2
type: gksu nautilus ~/Desktop

---

### Post by phantomjoker on 2009-05-11
yes i know... all this advice and nothing works!

And in reply - no, i'm not using 64 bit. Sorry!

---

### Post by phantomjoker on 2009-05-13
bump'edy bump

---

### Post by phantomjoker on 2009-05-21
bump'edy bump bump bump!

---

### Post by sena-sena on 2009-05-21
Are you running compiz?
Cos I'm on intrepid, and I find that with some video compiz completely messes it up. So if running, turn it off. If you're not sure how to do it, in package manager search for compiz switch and install. It'll be in accessories.
Hope that helps

---

### Post by phantomjoker on 2009-05-24
i dont have 'compiz switch' in my synaptic. 

Any other suggestions?

---

### Post by clhsharky on 2009-05-24
If Jaunty doesn't work right with you hardware, and Ibex does use what works. Many of us use 8.04.1 for this, and 9.04 for that, and XP for something else. I have never found a perfect computer, or operating system. But sometimes we find a combination that does what we need. And next year every thing is different in this fast world of computing.

---

### Post by zobcat on 2009-05-24
Here is the compiz switch deb. Good luck!

[CompizSwitch]("http://blogage.de/files/3611/download?compiz-switch_0.4.3%7Eubuntu-1_all.deb")

---

### Post by phantomjoker on 2009-05-25
Oh my gosh! it WORKS! Thank you so much!

So can i ask - what is compiz and why have it switched on?
sorry for the nieve question.

---

### Post by zobcat on 2009-05-25
Compiz gives you 3d effects like the desktop cube, and zoom capabilities, also alot of more basic effects. If you don't even use it, you could uninstall compiz and replace it with the lighter metacity. But, if everything is working now, then go with that.

---

### Post by moleculeman on 2009-05-26
Thank you. Fixed.

I feel awful silly now.

---

### Post by zobcat on 2009-05-26
@phantomjoker

Please mark this thread as solved.

Thanks

---

### Post by okayneil on 2009-05-26
> **zobcat said:**
> @phantomjoker

Please mark this thread as solved.

Thanks

What worked for me was in compiz settings manager -> options -> deselect "unredirect fullscreen windows"

---

### Post by phantomjoker on 2009-05-28
you see i would mark this as solved... but i cant, i dont get the option, its gone :|

I have like 5 threads all solved, but i cant mark them?? Kind of annoying

---

