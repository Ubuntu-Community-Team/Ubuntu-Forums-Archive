---
title: "GUI Update Manager fails silently"
date: 2011-08-13
forum: New to Ubuntu
---

### Post by Dorie on 2011-08-13
Hey,

could someone help me with this problem?  (Also, I hope the thread title is useful...^__^)

I'm on Ubuntu 10.04, and the Update Manager was recently interrupted a day or two ago when my internet connection was lost for a few moments/minutes.  The manager had already downloaded the updates, and was in the process of implementing them.  This was an update that required a reboot afterward- but I only know this since the power icon in the corner turned red.  I never got to the point where the manager asks if you'd like to reboot, because it froze once the internet connection was lost.

Anywho, the updater froze around maybe 57% completion of some task (don't know what, but I had the details window expanded, and it showed a percentage -1%, 2% etc on each line, along with other info- and had stalled at around 57%.)  I couldn't get it to unfreeze, so logged out and logged back in.  (I've also properly rebooted since then- though I was afraid to do so initially.)

Now, when I attempt to open the update manager, it looks as though it's checking for updates for a moment, then immediately closes again.  Also, on Firefox I noticed that flash videos don't play any more (no youtube,etc.).

I was in another thread here, and tried that fix:
[http://ubuntuforums.org/showthread.php?t=1532208](http://ubuntuforums.org/showthread.php?t=1532208)

I did the update and upgrade thing a few times, and the output was as follows:

////////////////////////////

```
                     p { margin-bottom: 0.08in; }  dorie@dorie-laptop:~$ sudo apt-get update 
 [sudo] password for dorie:  
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg 
 Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US   
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid Release.gpg                   
 Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US 
 Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US 
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                    
 Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US        
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                       
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US 
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US 
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                     
 Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US 
 Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates Release.gpg            
 Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US 
 Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US 
 Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US 
 Ign [http://mx.archive.ubuntu.com/ubuntu/](http://mx.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid Release                        
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                        
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US 
 Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates Release                          
 Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                               
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                         
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/main Packages                  
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/restricted Packages 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/main Sources 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/restricted Sources 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/universe Packages 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/universe Sources 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/multiverse Packages 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid/multiverse Sources 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/main Packages 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/restricted Packages 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/main Sources 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/restricted Sources 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/universe Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/universe Sources 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/multiverse Packages 
 Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) lucid-updates/multiverse Sources 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources 
 Reading package lists... Done 
 dorie@dorie-laptop:~$ sudo apt-get upgrade 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 dorie@dorie-laptop:~$  
```
 
/////////////////////////


I also tried this command, and got the error message I posted in this thread's title:

/////////////////////////

```
dorie@dorie-laptop:~$ sudo mv /var/lib/dpkg/updates /root/
[sudo] password for dorie: 
mv: cannot stat `/var/lib/dpkg/updates': No such file or directory
dorie@dorie-laptop:~$ 
```

///////////////////////////


Arg, I wish I could remember everything I did in the exact order, but the truth is I can't.  I may have done something else in between when the Update Manager was interrupted and now, but can't think what.  In any case, if anyone has an idea about how to fix my Update Manager, as well as the flash player, that would be great.  (About the flash player, I did go to the flash website and attempted to download it for ubuntu there- it obviously didn't work right...>_<;)


Apparently I've deleted an important file somehow, or something's been corrupted about the Update Manager, thus the "no such file or directory" answer?  I think?

Thanks for reading!  And sorry for not pasting in the code right, I'm not sure how to do so. :)

---

### Post by robsoles on 2011-08-13
The 'no such file or directory' error from the 'mv' command is irrelevant to the problem your system has, trust me - unless you accidentally moved or removed that specific folder before executing the 'mv' command on it this was never anything to do with your updating problem.


Please confirm that you have executed;```
sudo apt-get upgrade
```as well. The output from that command (if error(s) indicated as I suspect) will be much more help.

Re: [noparse]```
[/noparse] tags - please review [http://ubuntuforums.org/showthread.php?t=581745](http://ubuntuforums.org/showthread.php?t=581745) (Bapoumba is talking about the advanced editor and  not the 'quick reply' one)


If the 'apt-get upgrade' command produces errors (as I expect it should) then you can try[code]sudo apt-get -f upgrade
```before posting the previous response, it might actually fix it but may just respond with something even more helpful to know; Remember to post back anything that looks handy to know (no matter how depressing) to the thread :)

If you don't get any error messages from 'sudo apt-get upgrade' then your system is supposedly up to date and the problem is in the GUI updater/wrapper; We'll probably turn to your /var/logs pretty quickly if this is the case. Plenty else I could turn to though, first quick dirty fix I see and I'll say so! (I gave that 'mv' command to the other user as a quick and dirty fix I spotted between their error and the state of my system after a successful update.)


(soz pal, thread title isn't super relevant to problem, possible better title might have been: "GUI Update Manager fails silently" or the most obvious problem/error in output from a related terminal command,  like "apt-get: too many broken packages ..... aborting")

---

### Post by Dorie on 2011-08-13
Hi again!

I executed the update command and the upgrade command, which didn't have any problems, followed by the upgrade f command.  Here's what it looks like in the terminal:

//////////////////////

```
dorie@dorie-laptop:~$ sudo apt-get upgrade
[sudo] password for dorie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dorie@dorie-laptop:~$ sudo apt-get -f upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dorie@dorie-laptop:~$

```
////////////////////////

It didn't fix the update manager, as you guessed. :P  About any detail that might be important, I do remember getting the following message from the Update Manager before it stopped being accessible (meaning now I open it, and the window goes away almost immediately):

////////////////////////////

    ```
Dpkg: cannot scan update directory '/var/lib/dpkg/updates/': No such file or directory
 

 E: Sub-process /usr/bin/dpkg returned an error code (2)
 A package failed to install.  Trying to recover:  
 dpkg: cannot scan update diretory '/var/lib/dpkg/updates/': No such file or directory
```
 
/////////////////////////////

This message seems pretty important...

---

### Post by Dorie on 2011-08-13
Meh, I tried changing the thread title, but apparently I merely added a title to my previous post!  Woops!

---

### Post by Dorie on 2011-08-13
Hi again!  Firefox prompted me to "install missing plugins" just now, so I tried it again.  This time, it showed three things, all adobe Flash related (as I mentioned before, no flash videos play now)...

I clicked "install", using the Firefox GUI (I think?), and it paused, then told me they were "already installed".  Still no flash, so that's obviously not the case, lol

Anywho, just thought this might also be useful information.

Thanks,
Dorie

edit: this probably isn't useful, but here's a screenshot of the update page.  When I clicked next, it gave me the "already installed" message.

---

### Post by robsoles on 2011-08-13
Terminal```
sudo mkdir /var/lib/dpkg/updates
```in terminal and try to open the update manager in your GUI - is that fixed?

It is odd to me that jaconat didn't mention a problem with his GUI updater after following my advice, seems yours won't go without that folder and as I check my system more thoroughly today, mine won't either! :lol:

Soz I didn't spot that sooner, what's it been, three days? Sure did help, seeing the 'Dpkg: cannot scan....' error though!



Re: Getting the thread title changed :)

I am going to press the 'Report abuse' button on my post here and tap in a request to change the title of this thread**; **My submission will be reviewed by a moderator, they'll probably review the thread that I am choosing a sensible title, they'll change the title and they will probably post a brief message :p

---

### Post by Dorie on 2011-08-14
Haha, clever way to get the thread title changed, lol!

Again, thanks for helping me out, no problem about delay- I've only been checking about once a day myself.  This isn't a hugely painful problem, after all...

So I used that command, and the update manager comes up now, no problem!  That said...I tried going to youtbe and videos still don't play.  I tried the update via firefox again, and got the same problem "already updated" or whatever.  

So...I guess that's my main problem now, assuming the Update Manager is properly working and isn't simply loading up without fully functioning in some other way, lol...

Just occurred to me to go through Synaptic for the flash plugin, guess I'll try that...?  lol,   Ah, the excitement of using Ubuntu with way to little knowledge about how computers really work...

---

### Post by Dorie on 2011-08-14
lol...meep, I just fixed the Flash problem via Synaptic. That said, it was weird because it had the Adobe Flash Installer installed and in order to click the Adobe Flash player 10 FOR installation, it wanted me to uninstall the installer.

So I clicked them both a few times, and convinced it to try and install both...don't ask me, I don't know what really changed other than that both the intaller and Flash version 10 had a green check next to them, whereas initially the installer would automatically flip to having a red X once I checked Flash 10 for installation.

Weirdness!  So I got them both successfully checked for installation, they installed (I did noticed that it uninstalled then reinstalled the installer), and now flash works again inside Firefox.  Yay!

Anywho.  I...guess everything's fixed now!  I'll believe it completely when another update comes up via the Update Manager.  

I do have one more question, though.  My fear is that during that last interrupted update that files being updated got corrupted.  Is there a way (or have I already done it via one of the afore mentioned fixes) to check for corrupted files stemming from that update?  I'm concerned that if the Flash player seemingly got garbled up temporarily that whatever else was being updated might be suspect too?

That said, perhaps further updates overwrite previous versions, and thus delete any glitched code at that time?  Sorry, asking a lot of questions here.  I guess I just want to make sure other files/programs haven't been corrupted in a way that doesn't require that I discover the problem through happenstance...

Thanks, sorry for the ramble!  I'd just hate for the computer to die on me suddenly, particularly if one of those "security" updates failed and is currently causing a bug to get worse and worse as I speak...O___O  lol...I don't trust computers much. ^_^

Thanks again for the help. :)

---

### Post by LowSky on 2011-08-14
I use the firefox add-on called flash-aid. it give you a more up to date version of flash then what may be available form Ubuntu's repos.

---

### Post by robsoles on 2011-08-14
> **Dorie said:**
> I do have one more question, though.  My fear is  that during that last interrupted update that files being updated got  corrupted.  Is there a way (or have I already done it via one of the  afore mentioned fixes) to check for corrupted files stemming from that  update?  I'm concerned that if the Flash player seemingly got garbled up  temporarily that whatever else was being updated might be suspect too?

That said, perhaps further updates overwrite previous versions, and thus  delete any glitched code at that time?  Sorry, asking a lot of  questions here.  I guess I just want to make sure other files/programs  haven't been corrupted in a way that doesn't require that I discover the  problem through happenstance...


No, something else may crash as soon as you open it (though perhaps not) and all you have to do is find out what it's package name is and reinstall that package and it will (usually) be fixed.
```
sudo aptitude -f reinstall [COLOR=Blue]broken-package-name-goes-here[/COLOR]
```
There are circumstances where this won't work but those are all new threads ;)

> **LowSky said:**
> I use the firefox add-on called flash-aid. it give you a more up to date version of flash then what may be available form Ubuntu's repos.

+1

Once that update manager problem was out of the way I was going to suggest you grab flash-aid for firefox and stop having hassles with flash - mmmh, yah, think about it I probably should have told you the first you mentioned flash troubles :roll-eyes:

Happy computing to you Dorie.

---

### Post by robsoles on 2011-08-14
Oh, I just reviewed that other thread and I see in post #4 I fixed the problem with not having the directory present - I gotta review threads people revive better from now on!!

---

### Post by Dorie on 2011-08-14
Thank you robsoles for walking through this!  Woo, everything seems to be fixed for now, and if I've got a problem in the future the first thing I'll try is the fix you suggested. :)


Thank you LowSky (and robsoles again) for the alternate Flash installer for Firefox.  I'll have to give it a try. :)

Happy computing to you guys too!

Dorie

---

