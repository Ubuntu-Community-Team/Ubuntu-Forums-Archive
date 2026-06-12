---
title: "Starting from square one"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by OldGoat58 on 2009-11-28
I apologize if I offended anyone on the forum boards.  People have asked me "Just what is your problem".  My problem is, and has always been, the fact that when I open the Synaptic application manager it fades to black and does not respond.  It doesn't matter if i access the application from the "System" menu or I open from the terminal.  I do not get any error messages except on closing the application in which I get the popup window attached.  

I'm sorry if my problem doesn't fit the correct criteria for resolution but it is all I can give you.  I have exhausted the Ubuntu help application included with my distribution and I have not found anything that explains why the Synaptic application fades to black.

Once again I do humbly apologize if I in any way offended anyone, violated any TOS of the Ubuntu Forums, or if my comments have been rude or otherwise deemed inappropriate.

Frustrated in Fairless Hills, PA
Mike

---

### Post by Zzl1xndd on 2009-11-28
First I wouldn't worry too much, even the best of us have been frustrated, particularly with computers. 

When you first got set up had you been able to access the Ubuntu Software Center or Synaptic at all? And it might sound a little Windowsy but have you attempted just a simple restart of the system?

---

### Post by sandyd on 2009-11-28
> **OldGoat58 said:**
> I apologize if I offended anyone on the forum boards.  People have asked me "Just what is your problem".  My problem is, and has always been, the fact that when I open the Synaptic application manager it fades to black and does not respond.  It doesn't matter if i access the application from the "System" menu or I open from the terminal.  I do not get any error messages except on closing the application in which I get the popup window attached.  

I'm sorry if my problem doesn't fit the correct criteria for resolution but it is all I can give you.  I have exhausted the Ubuntu help application included with my distribution and I have not found anything that explains why the Synaptic application fades to black.

Once again I do humbly apologize if I in any way offended anyone, violated any TOS of the Ubuntu Forums, or if my comments have been rude or otherwise deemed inappropriate.

Frustrated in Fairless Hills, PA
Mike
try running
```

sudo apt-get update

```
in the terminal
copy and paste any errors.

---

### Post by OldGoat58 on 2009-11-28
> **carlee said:**
> try running
```

sudo apt-get update

```in the terminal
copy and paste any errors.


Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Reading package lists... Done

I have no clue if there are any errors there or not but it is everything I got doing what you told me to do.

---

### Post by jrrader on 2009-11-28
Synaptic is mearly the graphical frontend for apt-get.  Applications fade to black when they system finds them unresponsive.  Something is obviously wrong with synaptic and it's possible that it did not install correctly.  Have you tried completely removing synaptic and then reinstalling it?  It will only take a moment.

From the command line:

```
sudo apt-get -y purge synaptic
sudo apt-get -y install synaptic
```
(I tested this on my computer before telling you to do it)

---

### Post by OldGoat58 on 2009-11-28
> **tweakedenigma said:**
> First I wouldn't worry too much, even the best of us have been frustrated, particularly with computers. 

When you first got set up had you been able to access the Ubuntu Software Center or Synaptic at all? And it might sound a little Windowsy but have you attempted just a simple restart of the system?


I have always been able to access Ubuntu Software Center.  Synaptics only once, and as soon as I tried to go to a different tab it faded to black.  I can still see everything, just can't do anything.  I have rebooted more with Ubuntu than I ever did with Windows.  Sorry, that was a crappy thing to say.  Yes I have rebooted.  I have forced the application to close, forced the system to reboot.  Maybe I need to just do what one person suggested and reinstall the whole damn thing.

---

### Post by Cuco3 on 2009-11-28
> **OldGoat58 said:**
> I apologize if I offended anyone on the forum boards.  People have asked me "Just what is your problem".  My problem is, and has always been, the fact that when I open the Synaptic application manager it fades to black and does not respond.  It doesn't matter if i access the application from the "System" menu or I open from the terminal.  I do not get any error messages except on closing the application in which I get the popup window attached.  

I'm sorry if my problem doesn't fit the correct criteria for resolution but it is all I can give you.  I have exhausted the Ubuntu help application included with my distribution and I have not found anything that explains why the Synaptic application fades to black.

Once again I do humbly apologize if I in any way offended anyone, violated any TOS of the Ubuntu Forums, or if my comments have been rude or otherwise deemed inappropriate.

Frustrated in Fairless Hills, PA
MikeI see you're running the absolute latest version of Ubuntu (9.10), which I would never recommend for new users (you are new, no?). I made that mistake on an older PC, circa 2003. Wasn't able to get much out of it because it had an Intel video card (which suck with Ubuntu 9+ up). For reference, the first Ubuntu (6.04) was released in April, 2006 (6.04 denotes Year.Month it was released).

If none of the above has worked for you:

My advice is either to do a fresh install of 8.04, for the sake of troubleshooting the problem and making sure it's just 9.10 and not all of Ubuntu on your computer. You can also try running 9.04 (or upgrading to it after you install an older version), which is stable for me on a circa 2005 computer.

Good luck.

---

### Post by jrrader on 2009-11-28
> **OldGoat58 said:**
>  Maybe I need to just do what one person suggested and reinstall the whole damn thing.

That was me, but try my suggestion above before you do that.

---

### Post by OldGoat58 on 2009-11-28
> **jrrader said:**
> Synaptic is mearly the graphical frontend for apt-get.  Applications fade to black when they system finds them unresponsive.  Something is obviously wrong with synaptic and it's possible that it did not install correctly.  Have you tried completely removing synaptic and then reinstalling it?  It will only take a moment.

From the command line:

```
sudo apt-get -y purge synaptic
sudo apt-get -y install synaptic
```(I tested this on my computer before telling you to do it)


I hope this is what it was supposed to look like!

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Reading package lists... Done

---

### Post by sandyd on 2009-11-28
> **OldGoat58 said:**
> I have always been able to access Ubuntu Software Center.  Synaptics only once, and as soon as I tried to go to a different tab it faded to black.  I can still see everything, just can't do anything.  I have rebooted more with Ubuntu than I ever did with Windows.  Sorry, that was a crappy thing to say.  Yes I have rebooted.  I have forced the application to close, forced the system to reboot.  Maybe I need to just do what one person suggested and reinstall the whole damn thing.
did you try disabling compiz?/desktop effects? some users have reported having problems when using some apps w/ compiz/desktop effects.

---

### Post by OldGoat58 on 2009-11-28
sudo apt-get -y install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenal1 libqtscript4-network libsvga1 libqtscript4-gui mplayer-nogui
  libtag-extras1 libqtscript4-sql libqtscript4-xml mplayer-skins amarok-utils
  amarok-common liblzo2-2 kdemultimedia-kio-plugins libqtscript4-uitools
  liblastfm0 libqtscript4-core
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  software-properties-gtk
Suggested packages:
  dwww menu deborphan
The following NEW packages will be installed:
  software-properties-gtk synaptic
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 862kB of archives.
After this operation, 6,861kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main synaptic 0.62.7ubuntu6 [823kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main software-properties-gtk 0.75.4 [39.0kB]
Fetched 862kB in 1s (592kB/s)                 
Selecting previously deselected package synaptic.
(Reading database ... 154274 files and directories currently installed.)
Unpacking synaptic (from .../synaptic_0.62.7ubuntu6_amd64.deb) ...
Selecting previously deselected package software-properties-gtk.
Unpacking software-properties-gtk (from .../software-properties-gtk_0.75.4_all.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Setting up synaptic (0.62.7ubuntu6) ...

Setting up software-properties-gtk (0.75.4) ..

I hope this is what it was supposed to look like.

---

### Post by jrrader on 2009-11-28
Yeah, looks about right.  But does it work now or has nothing changed?

---

### Post by OldGoat58 on 2009-11-28
> **carlee said:**
> did you try disabling compiz?/desktop effects? some users have reported having problems when using some apps w/ compiz/desktop effects.


I went to "System, Preferences, Appearance" and turned off the desktop graphics.  I do not know how to disable compiz!

---

### Post by Zzl1xndd on 2009-11-28
> **OldGoat58 said:**
> I went to "System, Preferences, Appearance" and turned off the desktop graphics.  I do not know how to disable compiz!

If the desktop effects are set to none then Compiz is disabled the easiest way to do it is to right click on your desktop go to Change Desktop Background then select Visual effects and set to None.

---

### Post by halitech on 2009-11-28
the desktop effects and compiz are mostly the same thing. Basically compiz is a window manager (what draws the graphics for you) and having the special effects can cause issues, especially if your video card is just barely up to the task. Setting the special effects to none should be good enough for now.

Now try to open Synaptic and see what happens.

---

### Post by OldGoat58 on 2009-11-28
Then the answer would be yes I have disabled compiz.  I did the uninstall and reinstall as suggested and I can now open Synaptic and it doesn't fade to black!  Now it doesn't do anything.  No errors.  No action.  Can't select anything.  I can minimize it.  I can alt+tab and go to a different window.  Now I just did a alt+tab, went back to Synaptic and the page is black.  The only thing displayed are the minimize, maximize, close options in the upper right corner, and the word *"Synaptic" *in the center of the page.

I'm tired.  I give up for tonight.  I am going to play some solitaire and put some CDs in my sons stereo so I can listen to music and relax.

Thank you all so much for your help!
Mike

ps:  When do I mark the thread solved?  I'm ready for people to give up!

---

### Post by Cuco3 on 2009-11-28
Don't waste your time going through a million fixes when simply downgrading will help you isolate the problem down to Ubuntu 9.10 or just your computer not getting along with Ubuntu at all. You won't be able to make any progress until you have an idea of what is causing the problem.

The easiest thing would be to downgrade to Hardy 8.04. If that works, you can then upgrade to Jaunty 9.04 (but I'd stop there since Karmic 9.10 was obviously giving you problems with Synaptic).

For future reference, any new version of Ubuntu is only recommended for users who are already comfortable in Ubuntu and have already tested the new version via virtualization or a test computer.

Good luck and hang in there.

---

### Post by kansasnoob on 2009-11-28
> When do I mark the thread solved? I'm ready for people to give up!

Not until your problem is actually solved!

I was trying to read through your old posts but there are simply too many. So when you are rested (that goes for me too, I'm pooped) please post the output from terminal of:

```
sudo apt-get -f install
```

And:

```
sudo dpkg --configure -a
```

Maybe that will give me a brilliant idea.

---

### Post by jrrader on 2009-11-28
> **Cuco3 said:**
> Don't waste your time going through a million fixes when simply downgrading will help you isolate the problem down to Ubuntu 9.10 or just your computer not getting along with Ubuntu at all. You won't be able to make any progress until you have an idea of what is causing the problem.

Laptops are extra finicky.  My wife's 1 year old laptop worked terribly with 9.04, but works perfectly with 9.10 (clean install).  My dad's 2 year old laptop worked with 9.04 but for some reason he upgraded to 9.10 and it was barely usable.  Last week my brother-in-law dropped his 7 year old laptop and XP would no longer boot.  I installed 9.04 on a USB thumb drive for him to use until he can get Windows working again.  He was shocked to learn how fast his slow old laptop could go.  He upgraded to 9.10 and it still worked great.  It doesn't really make much sense why an older computer (that just barely survived a drop from a raised chevy silverado onto wet concrete) works better than a newer computer using a newer operating system - but that's the way it goes.

OP - you shouldn't mark things as solved until they are actually solved, even if you give up.

---

### Post by woodnymph on 2009-11-28
i have an official release disc of hardy 8.04, and still running it on an hp dv5000.  if you have a wired connection to do an update right away, i can't see why it wouldn't work for you .. let me know your address i can mail you the cd as needed.

---

### Post by candtalan on 2009-11-29
> **woodnymph said:**
> i have an official release disc of hardy 8.04, and still running it on an hp dv5000.  if you have a wired connection to do an update right away, i can't see why it wouldn't work for you .. let me know your address i can mail you the cd as needed.

Please keep in mind that 8.04 has already passed through several re incarnations, and the best one to use is
8.04.3
which will contain the newer kernel and driver additions etc.

So, using the original Shipit pack may work ok on hardware of the same vintage, but on principle it would be better to use the latest iso image available.

---

### Post by candtalan on 2009-11-29
> **OldGoat58 said:**
> I went to "System, Preferences, Appearance" and turned off the desktop graphics.  I do not know how to disable compiz!

1) The way to do this is
System>Preferences>Appearance>Visual Effects [choose None]
The problems you seem to have are easily interpreted as coming because the Visual Effects giving is trouble in your machine.

2) it would be useful to confirm that the CD used for the install was perfectly seen by your CD drive. This can be checked at any stage by booting from the CD and choosing 
'Check disc for defects' when using the target machine.
This is useful because even if the CD itself is good, the possibility of a sticky cd drive is also checked with this method.

3) Take it gently! Keep in mind that your machine was probably made with Windows in mind, and occasionally despite the best efforts of the GNU/Linux community some initial experiences can cause frustration. Be assured that solutions are usually found, though.

hth

---

### Post by Bartender on 2009-11-29
If Old Goat were to drop back from 9.10, wouldn't 9.04 be a better choice than all the way back to 8.04??

OG, I'm of the opinion to just wipe and reinstall instead of fighting it anymore.  Your install CD may have been corrupted, or maybe the rig doesn't like something about 9.10, but the best way to find out is to try something completely different and see if the same problems crop up.

I have a few different PC's to experiment with, and several versions of Ubuntu on CD.  I've found the quickest way to the bottom of some problem is to swap parts or OS'es and compare the results.
  
Just the other day a new install of Karmic wouldn't recognize the optical drive with a Steely Dan CD in the tray.  That was weird; optical drives usually just work.  I swapped that drive for another and it's working now.  Without the ability to move parts around, I would have had no idea what to do.

---

### Post by ed-koala on 2009-11-29
I agree, I think it's time to try a different version and see what happens. Either 8.04.3 or 9.04 would be fine I think, though I still recommend 8.04 for new users especially ones with really old hardware.

Save yourself the frustration and headaches, and also get answers. Installing a different version will do both at the same time.

---

