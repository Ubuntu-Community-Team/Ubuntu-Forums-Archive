---
title: "Putting flash in it's place ..."
date: 2010-03-21
forum: New to Ubuntu
---

### Post by Langstracht on 2010-03-21
Flash stopped working for me and I have other issues with it that I am unable to resolve.

According to both about:plugins and Tools>Add-ons>Plugins I have TWO versions of flash 10 on my machine (r22 and r45).

I have been playing around - pretending I knew what I was doing - with a variety of sudo apt-get remove commands which has not changed the above situation.  Indeed I get errors saying flash is not installed and so cannot be removed - and yet when I "sudo apt-get install" I am told I already have the latest version and so it won't install it.

Because of having a legacy video card what I think I need to do is to get rid of version 10 and install version 8.

Any help much appreciated.

---

### Post by sandyd on 2010-03-21
> **Langstracht said:**
> Flash stopped working for me and I have other issues with it that I am unable to resolve.

According to both about:plugins and Tools>Add-ons>Plugins I have TWO versions of flash 10 on my machine (r22 and r45).

I have been playing around - pretending I knew what I was doing - with a variety of sudo apt-get remove commands which has not changed the above situation.  Indeed I get errors saying flash is not installed and so cannot be removed - and yet when I "sudo apt-get install" I am told I already have the latest version and so it won't install it.

Because of having a legacy video card what I think I need to do is to get rid of version 10 and install version 8.

Any help much appreciated.
see sig.
press remove.

I already know where the flash plugins are located if you want to remove them manually.

one is located at /usr/lib/firefox-*/plugins/

one is located at /usr/lib/mozilla/plugins/

---

### Post by roccivic on 2010-03-21
with version 8, almost all modern websites will refuse to work. that includes youtube and friends.

try:

```
sudo dpkg-reconfigure abode-flashplugin
```

---

### Post by Langstracht on 2010-03-21
Sorry, what does 

see sig.
press remove.

mean?

---

### Post by sandyd on 2010-03-21
> **Langstracht said:**
> Sorry, what does 

see sig.
press remove.

mean?
[Universal Adobe Flash Installer/Uninstaller (with GUI)]("http://ubuntuforums.org/showthread.php?t=1414595")

---

### Post by Langstracht on 2010-03-21
Alas:

sudo dpkg-reconfigure abode-flashplugin
[sudo] password for joe: 
Package `abode-flashplugin' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: abode-flashplugin is not installed

...

---

### Post by lidex on 2010-03-21
> **Langstracht said:**
> Alas:

sudo dpkg-reconfigure abode-flashplugin
[sudo] password for joe: 
Package `abode-flashplugin' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: abode-flashplugin is not installed

...

No soup for you!!
Please follow the link in carlee's post - it works ;)

---

### Post by Langstracht on 2010-03-22
Sorry, I REALLY don't want to ask for advice and then, when I get some, ignore it.

However I'm a bit spooked by this whole thing (2 versions twice reported as installed, but no removal because it isn't there and no installation because it is) and I notice that carlee's post specifically refers to 64 bit.  I do not have 64.

But ... I should use the utility anyway??

---

### Post by wojox on 2010-03-22
See this [Removing Conflicting Plugins]("http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2")

---

### Post by Langstracht on 2010-03-22
Got nowhere with the remove/install commands referenced so decided to give carlee's code a try.

Unzipping gave me an 18.9 Kb executable file dated Feb 28, 2010 that I cannot get to execute.

Anybody any idea what I am missing THIS time.

Tx.

---

### Post by lidex on 2010-03-22
Download this file; extract, and simply double-click on it.
[http://ubuntuforums.org/attachment.php?attachmentid=148549&d=1267376842]("http://ubuntuforums.org/attachment.php?attachmentid=148549&d=1267376842")

---

### Post by Langstracht on 2010-03-23
Sorry to have to report that doubling clicking on the extracted file did nothing,  Neither did right clicking and "Open"ing.

---

### Post by lidex on 2010-03-23
The filename should be "adobe_flash_installer"
Open a terminal and from your desktop or nautilus drag that file into the terminal window and press enter.

---

### Post by Langstracht on 2010-03-23
Alas no ...

error message reads:

bash: /home/Downloads/adobe_flash_installer: cannot execute binary file

---

### Post by philinux on 2010-03-23
Open a terminal, Applications>accessories>terminal

Copy and then use paste the following code into the terminal and press enter. Enter your login password when prompted.

```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash adobe-flashplugin
```

after that then copy this in.

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by QIII on 2010-03-23
Just as a bit of explanation for philinux' post...

swfdec and gnash conflict with flash, so what he is doing there is  making sure they are uninstalled.

---

### Post by Langstracht on 2010-03-23
The results of so doing are:

sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash adobe-flashplugin
[sudo] password for #*&@!: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package swfdec-mozilla is not installed, so not removed
Package mozilla-plugin-gnash is not installed, so not removed
Package adobe-flashplugin is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I previously used these commands (as I think I said) with the same results - not removed because it isn't there.  And not installed because it is.

And meanwhile about:config and Add On>Plugins both insist that 2 versions exist (r2 and r45).

---

### Post by lidex on 2010-03-23
Run this command in a terminal:
```
locate libflashplayer.so
```
Delete all instances of libflashplayer.so brought up there. Restart firefox and check your plugin status.

---

### Post by Langstracht on 2010-03-24
O.k. there were 2 instances of libflashplayer.so (one of which seems to have been associated with Adobe AIR) and I deleted both.  I wonder if perhaps I should NOT have deleted the AIR one ... but in any event.

Returning to a re-booted Firefox about:plugins and Add On - surprising to me - both show 1 version of flash.  r 45 has disappeared, r22 remains.

But flash (still) doesn't work.

Alas I have no idea what this means ... or what to do about it.

---

### Post by lidex on 2010-03-24
Make sure firefox is closed. Run this command:
```
sudo updatedb
```

Then run this command again:
```
locate libflashplayer.so
```

Your goal is to remove them all. Start firefox and check plugins.

---

### Post by Langstracht on 2010-03-25
I have no idea how things might have gotten so out of kilter but I have to report that following your advice unearthed FOUR more copies of libflashplayer.so.  Which have now been summarily dismissed.

And, indeed, about:plugins and Add Ons>Plugins both now report zero instances of flash.

But ... given a dated/legacy video card ... and, now, no flash "for real", what to do?

---

### Post by lidex on 2010-03-25
Go here:
[http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1]("http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1")

---

### Post by philinux on 2010-03-25
I would suggest if they've all gone then just install this.

```
sudo apt-get install flashplugin-nonfree
```

Restart firefox.

---

### Post by Langstracht on 2010-03-25
O.K. then, if I understand correctly it basically boils down to:

sudo apt-get install flashplugin-nonfree.

Which I think will get me flash 10 - and which may, or may not, have issues with my video card.

I am, at least until the end of next month, still using Hardy Heron LTS - so no Jaunty issues.  And all the other commands have been run ad nauseum.

Can you please confirm that is the case.  Or point out some other issue I may be missing.

Thanks so much.

---

### Post by Langstracht on 2010-03-25
Sorry - the foregoing was in reply to lidex.

philinux seems to endorse my conclusion ...

---

### Post by lidex on 2010-03-25
> **Langstracht said:**
> Sorry - the foregoing was in reply to lidex.

philinux seems to endorse my conclusion ...

...as do I...it's basically what the linked page would tell you but, man, everything that should have been simple for you has been nothing but complicated. ;)

Go for it.

---

### Post by Langstracht on 2010-03-26
Before taking the plunge, one last kick at the cat if you'll permit me.

What is the difference between:

    running:  sudo apt-get install flashplugin-nonfree

    clicking on "install missing plug ins" on a complaining Firefox page

    using Firefox's "Tools>Add-ons>Get Add-ons"?

Or, is there a difference?

---

### Post by philinux on 2010-03-26
> **Langstracht said:**
> Before taking the plunge, one last kick at the cat if you'll permit me.

What is the difference between:

    running:  sudo apt-get install flashplugin-nonfree

    clicking on "install missing plug ins" on a complaining Firefox page

    using Firefox's "Tools>Add-ons>Get Add-ons"?

Or, is there a difference?

As always there is more than one way to skin a cat. Now just kick it. Any method should work. Here's another. Click this. [cat-kicked]("apt:flashplugin-nonfree")

---

### Post by Langstracht on 2010-03-26
Well, I went with the apt-get ... and guess what ...

sudo apt-get install flashplugin-nonfree
[sudo] password for #*&@!: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Unreal.

Oh me miserum ...

---

### Post by philinux on 2010-03-26
> **Langstracht said:**
> Well, I went with the apt-get ... and guess what ...

sudo apt-get install flashplugin-nonfree
[sudo] password for #*&@!: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Unreal.

Oh me miserum ...

Ok so what does ```
about:plugins
``` show in firefox.

And again run this.

```
sudo updatedb

then

locate libflashplayer.so


```

---

### Post by Langstracht on 2010-03-26
about:plugins has no entry for flash.

updatedb locate finds no libflashplayer.so.

---

### Post by philinux on 2010-03-26
> **Langstracht said:**
> about:plugins has no entry for flash.

updatedb locate finds no libflashplayer.so.

Something odd happened to your install then. Could be an apt problem.

What does this give.

```
apt-cache policy flashplugin-nonfree
```

---

### Post by Langstracht on 2010-03-26
apt-cache policy flashplugin-nonfree
flashplugin-nonfree:
  Installed: 10.0.1.218+really9.0.262.0ubuntu1
  Candidate: 10.0.1.218+really9.0.262.0ubuntu1
  Version table:
 *** 10.0.1.218+really9.0.262.0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
        100 /var/lib/dpkg/status
     10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
     9.0.124.0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages

As you will have surmised ... all Greek to me.

---

### Post by philinux on 2010-03-26
Ok do these commands one at a time. Use copy and paste them into terminal.

```
sudo apt-get update && sudo apt-get upgrade

then

sudo apt-get purge flashplugin-nonfree
```

Post back the terminal output.

---

### Post by Langstracht on 2010-03-26
I guess you were serious ... so here you are:

 sudo apt-get update && sudo apt-get upgrade
[sudo] password for #*&@!: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US       
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg [189B]             
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release [51.2kB]               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Packages                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages                
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages [119kB]          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages              
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages [14B]      
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages [115kB]      
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages [14.6kB]   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages                              
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Release.gpg                                   
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Translation-en_US                             
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Release                                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg                            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US       
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US   
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Packages      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release [27.6kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Fetched 300kB in 5s (52.2kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

AND

sudo apt-get purge flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 168kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 220457 files and directories currently installed.)
Removing flashplugin-nonfree ...
Purging configuration files for flashplugin-nonfree ...

---

### Post by philinux on 2010-03-26
Ok thats good no errors. Lets make sure it's gone.

```
apt-cache policy flashplugin-nonfree
```

---

### Post by Langstracht on 2010-03-26
apt-cache policy flashplugin-nonfree
flashplugin-nonfree:
  Installed: (none)
  Candidate: 10.0.1.218+really9.0.262.0ubuntu1
  Version table:
     10.0.1.218+really9.0.262.0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
     10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
     9.0.124.0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages

---

### Post by philinux on 2010-03-26
Ok close firefox. 

```
sudo apt-get install flashplugin-nonfree
```

Start firefox and look in ```
about:plugins
```

See if flash is picked up.

---

### Post by Langstracht on 2010-03-26
O.k.  Done.

And about:plugins assures me that I am the proud owner of Shockwave Flash 9.0 r262.  Although not the 10 that I had expected.  But not necessarily wanted.

So I am hoping I am good to go.

Although as I said pages ago, with a dated card ...

All of that said, first of all huge thank you's to philinux both for your knowledge AND especially perhaps your patience.

I wonder if there would be any utility to summarizing all of this both in terms of, I suppose necessarily, guessing how it may have come about in the first place.  And then a list of steps of the fix ... and what those steps were doing.

Whatever you decided I sure hope not to put myself or anyone else through this again.

And thanks so much again.

---

### Post by philinux on 2010-03-26
Nice one enjoy the flash. I would not worry about the version. I think thats a hardy LTS thing. You can check the versionw with that apt-cache policy command.

---

### Post by Langstracht on 2010-03-26
I did check and am surprised at the result:

apt-cache policy flashplugin-nonfree
flashplugin-nonfree:
  Installed: 10.0.1.218+really9.0.262.0ubuntu1
  Candidate: 10.0.1.218+really9.0.262.0ubuntu1
  Version table:
 *** 10.0.1.218+really9.0.262.0ubuntu1 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
        100 /var/lib/dpkg/status
     10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
     9.0.124.0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages

I see an awful lot of 10's there ... and yet I have 9.  Am I now set for more trouble?

---

### Post by philinux on 2010-03-26
No you really got 10 it's just a Hardy LTS version thing. Enjoy.

Try some flash sites like youtube.

---

