---
title: "Sea Monkey closes?"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by rosswmcgee on 2011-05-10
I installed Sea Monkey from the synaptic manager. When I click on compose 

message Sea Monkey closes. How to fix?

After trying the hints in this thread to no avail I stumbled on notes like this in the software center reviews:

2.0.13 works fine with ubuntu 10.10  If you upgrade or install  11.04 seamonkey will crash.  You Must MANUALLY upgrade to seamonkey 2.0.14  There are instructions in the README file in the tar ball.  Hint: use tar xjvf sea*.tar.bz2 to extract.  I did not experience any loss of mailbox, address book or bookmarks, but be safe and back them up. Hope this will save U

Now if I can figure out how to do this, I have never been successful in opening tar files and the ubuntu soft ware tool won't recognize it.

I was successful in following the read me instructions Seamonkey 2.0.14 now works with our crashing.

---

### Post by TeoBigusGeekus on 2011-05-10
Any error messages appearing when you run it from terminal?

---

### Post by rosswmcgee on 2011-05-10
Whether I run it from terminal or the regular way it still happens. No error message from terminal, but this upon re-opening.

Would you like to restore your session?

      


      
      


        
        

          

Your previous SeaMonkey session closed unexpectedly. We sincerely apologize for the inconvenience. You can restore the tabs and windows from your previous session, or start a new session if they are no longer needed.

        


        
        

          

If SeaMonkey closes repeatedly: 
*             Try disabling any recently added extensions in the Add-ons Manager.
*             Try restoring your session without any Web pages you suspect might           be        causing the problem:


I added no extensions., and had no web page open. Tried re install same thing.

---

### Post by rosswmcgee on 2011-05-10
I decided to re-install Seamonkey from terminal, this is the read out:

ross@ross-ET1161-05:~$ sudo apt-get install seamonkey-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-renderpm libqt4-test python-reportlab-accel libqt4-help python-qt4
  python-sip libqtassistantclient4 python-qt4-dbus libgwibber1 libqt3-mt
  libqt4-scripttools python-reportlab
Use 'apt-get autoremove' to remove them.
Suggested packages:
  latex-xft-fonts seamonkey-mailnews seamonkey-dom-inspector
The following NEW packages will be installed:
  seamonkey-browser
0 upgraded, 1 newly installed, 0 to remove and 23 not upgraded.
Need to get 0 B/11.7 MB of archives.
After this operation, 33.0 MB of additional disk space will be used.
Selecting previously deselected package seamonkey-browser.
(Reading database ... 159120 files and directories currently installed.)
Unpacking seamonkey-browser (from .../seamonkey-browser_2.0.13+nobinonly-0ubuntu1_i386.deb) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up seamonkey-browser (2.0.13+nobinonly-0ubuntu1) ...
update-alternatives: using /usr/bin/seamonkey to provide /usr/bin/mozilla (mozilla) in auto mode.
update-alternatives: warning: skip creation of /usr/share/man/man1/mozilla.1.gz because associated file /usr/share/man/man1/seamonkey.1.gz (of link group mozilla) doesn't exist.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
ross@ross-ET1161-05:~$

---

### Post by TeoBigusGeekus on 2011-05-10
The only thing I can think of, and therefore suggest, is to clean seamonkey's cache folder, either by seamonkey itself (I've never used it, but it should have something like clean cache, delete history or whatever).
You could even install bleachbit - if you haven't already - and attempt to clean up seamonkey's folders.

---

### Post by rosswmcgee on 2011-05-10
I did clean using Sea Monkey and also used bleachbit, however bleachbit does not show Seamonkey. 
So here is what I think. I think Natty has some bugs and I do think they erred in not
providing Seamonkey as an Internet Suite. As it was listed in ubuntu 10, same goes for Opera it has one small bug that I cannot fix in Natty but works fine in Mint 10.
both browsers are excellent for those of us that like a browser with mail built in.
It will be interesting to see when the new Mint is released if it is a ditto of Natty. It seems to me for all the progress made some very good packages were not upgraded properly. But what do I know I am not a real techie but I do know when things work and when they don't. My Mint 10 computer has no problem with Seamonkey or Opera. So I may just leave my Mint 10 alone, and then when the new mint comes out
replace natty with it and see if the problems go away. I do enjoy ubuntu but if does not run my browsers who needs it?

---

### Post by jtarin on 2011-05-10
I was going to ask as its not clear to me.......How did you install....as a suite w/comoser/mail/IRC or separate without mail client? I initially installed the browser which comes with composer and IRC but no meail client. I installed afterwards and it integrated with the browser. I have no problems with mail client as you state. I'm running it on 10.10

---

### Post by jtarin on 2011-05-10
> **rosswmcgee said:**
> 
It will be interesting to see when the new Mint is released if it is a ditto of Natty. It seems to me for all the progress made some very good packages were not upgraded properly. But what do I know I am not a real techie but I do know when things work and when they don't.Yea kinda like all those XP applications I had,that no longer run under Win7. Don't ya just hate that when you try to upgrade to the latest and greatest, even though it's a beta, and some favorite things don't work. Who wants to wait around until the bugs get ironed out....there'll be another new version come along about the time that happens...Sheesh! 

> **rosswmcgee said:**
> I do enjoy ubuntu but if does not run my browsers who needs it?That's the spirit!! I run Arachne browser in DOS.....it never let's me down. Does anyone know when the next DOS upgrade is? I want to make sure all my applications are up to date.:P

---

### Post by rosswmcgee on 2011-05-10
First the Seamonkey Internet Suite 2.011 and then the mail newsgroups and address book, which is working fine in Mint 10 Julia. So my other computer is Ubuntu Natty,

Seamonkey is listed as: Sea Monkey Internet Navigator ( Internet Browser )and Composer

2.013

Then the Mail and Newsgroup and address book. 
So I am using an older Seamonkey in Mint and the newer one in Natty.

My Natty is an upgrade, does anyone see a difference in the clean install?

---

### Post by Kenneth D. Gladden on 2011-05-12
Thanks - Worked for men with xubuntu 11.04
Kenneth D. Gladden

---

### Post by rosswmcgee on 2011-05-12
Which version of Seamonkey is in the xbuntu repository? Did you install from there?

Or did you download seamonkey from their website 2.0.14, and install the tar file?

Our you using the mail and newsgroups if so if you click on compose msg. form there does it crash?

---

