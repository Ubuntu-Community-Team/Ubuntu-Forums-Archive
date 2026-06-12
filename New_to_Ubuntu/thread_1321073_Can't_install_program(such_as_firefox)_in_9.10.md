---
title: "Can't install program(such as firefox) in 9.10"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by Dnajun_Tnuieh on 2009-11-09
Everytime I try to install a program, such as firefox, or flash player I get errors. Most commonly one saying that the package is already installed..

---

### Post by phillw on 2009-11-09
> **Dnajun_Tnuieh said:**
> Everytime I try to install a program, such as firefox, or flash player I get errors. Most commonly one saying that the package is already installed..

Hi,

Check  Applications -->> Internet

If Firefox is there, you already have it. Firefox is installed by default.

Regards,

Phill.

---

### Post by Dnajun_Tnuieh on 2009-11-09
> **phillw said:**
> Hi,

Check  Applications -->> Internet

If Firefox is there, you already have it. Firefox is installed by default.

Regards,

Phill.

It only shows the installer for me. "Mozilla Firefox Browser Installer" And when I try using that and install, it errors and says the package is already installed. And yet I don't see it. I also get this error for Amarok, it suggests updates to me everytime I open it, but I get the same error.


edit,
Also another thing, how do I get Amarok to play .mp3 files? I've trying and trying to get it to play files on my external disk, but it never even attempts to play it seems..

---

### Post by kansasnoob on 2009-11-09
One thing at a time.

If you click on the Firefox icon in the upper panel it does not launch Firefox?

---

### Post by Dnajun_Tnuieh on 2009-11-09
> **kansasnoob said:**
> One thing at a time.

If you click on the Firefox icon in the upper panel it does not launch Firefox?

What do you mean upper panel?

---

### Post by The Funkbomb on 2009-11-09
> **Dnajun_Tnuieh said:**
> What do you mean upper panel?

You should have a panel at the top of your screen that has the Ubuntu Logo, Applications, Places, System, and then by default, there's a Firefox quick launch, an Evolution launch and a help launch.

Click the Firefox one.  Tell us what happens.

---

### Post by Dnajun_Tnuieh on 2009-11-09
> **The Funkbomb said:**
> You should have a panel at the top of your screen that has the Ubuntu Logo, Applications, Places, System, and then by default, there's a Firefox quick launch, an Evolution launch and a help launch.

Click the Firefox one.  Tell us what happens.

Don't have a panel on top, I have one on bottom with a K on bottom left, that opens up like windows start menu.  then I go to Applications -> Internet then the only firefox relation I see is the installer I mentioned earlier.

---

### Post by The Funkbomb on 2009-11-09
Durr.  You're using Kubuntu.  Sorry.

What happens when you try to run Firefox from Konsole?

---

### Post by Dnajun_Tnuieh on 2009-11-09
> **The Funkbomb said:**
> Durr.  You're using Kubuntu.  Sorry.

What happens when you try to run Firefox from Konsole?

Whats the command to do that?

---

### Post by The Funkbomb on 2009-11-09
I believe it's firefox

---

### Post by Dnajun_Tnuieh on 2009-11-09
> **The Funkbomb said:**
> I believe it's firefox


dnajun@dnajun-pc:~$ firefox
The program 'firefox' can be found in the following packages:
 * firefox-3.5
 * firefox-3.0
Try: sudo apt-get install <selected package>
firefox: command not found
dnajun@dnajun-pc:~$

---

### Post by The Funkbomb on 2009-11-09
Try firefox-3.5

If that doesn't work, try to install it through Konsole with the command:

```
sudo apt-get install firefox-3.5
```

If that doesn't work, copy the output of what happened and paste it here.

---

### Post by Dnajun_Tnuieh on 2009-11-09
> **The Funkbomb said:**
> Try firefox-3.5

If that doesn't work, try to install it through Konsole with the command:

```
sudo apt-get install firefox-3.5
```

If that doesn't work, copy the output of what happened and paste it here.

dnajun@dnajun-pc:~$ sudo apt-get install firefox-3.5
[sudo] password for dnajun:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package firefox-3.5
dnajun@dnajun-pc:~$

---

### Post by The Funkbomb on 2009-11-09
Weird...

I'm going to step out and let someone with more experience and more kubuntu experience help you.

---

### Post by Dnajun_Tnuieh on 2009-11-09
> **The Funkbomb said:**
> Weird...

I'm going to step out and let someone with more experience and more kubuntu experience help you.

alright then. thanks for your attempt.

---

### Post by Paqman on 2009-11-09
Can you try running:
```
firefox-3.5
```
in the console and post what you get?

Firefox is part of the default install, you should just be able to launch it from the menu.

---

### Post by nerdy_kid on 2009-11-09
firefox is not installed by default in Kubuntu.

maybe refresh software lists???

```
sudo apt-get update
```


then try

```
sudo apt-get install firefox
```


sorry i cant help anymore

---

### Post by sandyd on 2009-11-09
> **Dnajun_Tnuieh said:**
> alright then. thanks for your attempt.

open up a terminal and run
```

cat /etc/apt/sources.list >> ~/Desktop/sources.list

```
then attach the sources.list (on your desktop) to the post.

---

### Post by Dnajun_Tnuieh on 2009-11-10
> **nerdy_kid said:**
> firefox is not installed by default in Kubuntu.

maybe refresh software lists???

```
sudo apt-get update
```


then try

```
sudo apt-get install firefox
```


sorry i cant help anymore

Thanks that worked.

> **carlee said:**
> open up a terminal and run
```

cat /etc/apt/sources.list >> ~/Desktop/sources.list

```
then attach the sources.list (on your desktop) to the post.

it says invalid file when I try to attach to post.

Also got flash player to install thanks to nerdy_kids suggestion, still need assistance on why Amarok isn't playing mp3 files.



And now another thing, I'm not getting any sound. Everything is turned up. nothing is muted.. was playing the logoff and login sounds before.

---

### Post by aaycumi on 2009-11-10
One thing to try is opening up a terminal and typing "firefox", if it loads its installed, if not it is not installed.
If it is installed and not working type "sudo apt-get remove firefox" and then sudo apt-get install firefox", that should solve it. If not the installation CD was probably burned incorrectly and you should try burning another at the slowest possible speed and reinstalling the OS.

---

### Post by SunnyRabbiera on 2009-11-10
Kubuntu has always been troublesome, you might actually want to swap it out for regular ol Ubuntu.
Granted Gnome might not look as pretty as KDE but Ubuntu's gnome is pretty solid.

---

### Post by Dnajun_Tnuieh on 2009-11-10
> **SunnyRabbiera said:**
> Kubuntu has always been troublesome, you might actually want to swap it out for regular ol Ubuntu.
Granted Gnome might not look as pretty as KDE but Ubuntu's gnome is pretty solid.

Can you provide a good download link?

Also how do I burn .iso files with linux?

Found out problem with audio, slider was all the way down inside the mixer...

---

### Post by kansasnoob on 2009-11-10
Sorry I was thinking Ubuntu earlier.

I seldom use Kubuntu but first go to Synaptic and click on Settings > Repositories. Under the (K)Ubuntu tab make sure Main, Universe, Restricted, and Multiverse are all checked. Under the Other Software tab be sure the Partner Repo is checked and under the updates tab make sure both Security and Recommended are checked. 

Then click on reload and Mark all upgrades and apply. Then see if package installation improves.

As far as trying Ubuntu or Xubuntu, no need to reinstall, look here:

> Playing Around
KDE/Gnome Comparison
Install KDE
Install XFCE
Install IceWM
Pure Gnome
Pure KDE
Pure XFCE
Make your own Ubuntu remix 

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by Dnajun_Tnuieh on 2009-11-10
> **kansasnoob said:**
> Sorry I was thinking Ubuntu earlier.

I seldom use Kubuntu but first go to Synaptic and click on Settings > Repositories. Under the (K)Ubuntu tab make sure Main, Universe, Restricted, and Multiverse are all checked. Under the Other Software tab be sure the Partner Repo is checked and under the updates tab make sure both Security and Recommended are checked. 

Then click on reload and Mark all upgrades and apply. Then see if package installation improves.

As far as trying Ubuntu or Xubuntu, no need to reinstall, look here:



[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

sooooo, what do I do to get regular Ubuntu??

---

### Post by kansasnoob on 2009-11-10
First of all check your repos like I suggested, then the rest is right in that link. More specifically I'd start here:

[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

You can then decide whether to boot the Kubuntu or Ubuntu desktops from the login window:

[http://www.psychocats.net/ubuntu/images/addgnomejaunty11.png](http://www.psychocats.net/ubuntu/images/addgnomejaunty11.png)

And if you decide you want pure Gnome (Ubuntu):

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Linux users have to be willing to read a little!

---

### Post by Dnajun_Tnuieh on 2009-11-10
> **kansasnoob said:**
> First of all check your repos like I suggested, then the rest is right in that link. More specifically I'd start here:

[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

You can then decide whether to boot the Kubuntu or Ubuntu desktops from the login window:

[http://www.psychocats.net/ubuntu/images/addgnomejaunty11.png](http://www.psychocats.net/ubuntu/images/addgnomejaunty11.png)

And if you decide you want pure Gnome (Ubuntu):

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Linux users have to be willing to read a little!

sorry I've been googling a lot lol, starting to get lazy for the time being.

thanks.

---

### Post by The Funkbomb on 2009-11-10
Still following this thread because it puzzles me.

How is he going to install GNOME if he can't install packages?

---

### Post by Dnajun_Tnuieh on 2009-11-10
> **The Funkbomb said:**
> Still following this thread because it puzzles me.

How is he going to install GNOME if he can't install packages?

I got fixed thanks to info on page 2.


error trying to install gnome

```
dnajun@dnajun-pc:~$ sudo apt-get update && sudo apt-get install ubuntu-desktop                   
Hit http://security.ubuntu.com karmic-security Release.gpg                                       
Ign http://security.ubuntu.com karmic-security/main Translation-en_US                            
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US                      
Hit http://us.archive.ubuntu.com karmic Release.gpg                                              
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                                   
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US                             
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US                        
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US                      
Hit http://security.ubuntu.com karmic-security Release                                           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US                               
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US                             
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                                      
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US                           
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US                     
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US                       
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US                     
Hit http://us.archive.ubuntu.com karmic Release                                                  
Hit http://security.ubuntu.com karmic-security/main Packages                                     
Hit http://us.archive.ubuntu.com karmic-updates Release                                          
Hit http://security.ubuntu.com karmic-security/restricted Packages                               
Hit http://security.ubuntu.com karmic-security/main Sources                                      
Hit http://security.ubuntu.com karmic-security/restricted Sources                                
Hit http://security.ubuntu.com karmic-security/universe Packages                                 
Hit http://us.archive.ubuntu.com karmic/main Packages                                            
Hit http://us.archive.ubuntu.com karmic/restricted Packages                                      
Hit http://us.archive.ubuntu.com karmic/main Sources                                             
Hit http://us.archive.ubuntu.com karmic/restricted Sources                                       
Hit http://us.archive.ubuntu.com karmic/universe Packages                                        
Hit http://us.archive.ubuntu.com karmic/universe Sources                                         
Hit http://security.ubuntu.com karmic-security/universe Sources                                  
Hit http://security.ubuntu.com karmic-security/multiverse Packages                               
Hit http://security.ubuntu.com karmic-security/multiverse Sources                                
Hit http://us.archive.ubuntu.com karmic/multiverse Packages                                      
Hit http://us.archive.ubuntu.com karmic/multiverse Sources                                       
Hit http://us.archive.ubuntu.com karmic-updates/main Packages                                    
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages                              
Hit http://us.archive.ubuntu.com karmic-updates/main Sources                                     
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources                               
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages                                
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources                                 
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages                              
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources                               
Reading package lists... Done                                                                    
Reading package lists... Done                                                                    
Building dependency tree                                                                         
Reading state information... Done                                                                
You might want to run `apt-get -f install' to correct these:                                     
The following packages have unmet dependencies:                                                  
  libgraphviz4: Depends: libgd2-noxpm (>= 2.0.36~rc1~dfsg) but it is not going to be installed or
                         libgd2-xpm (>= 2.0.36~rc1~dfsg) but it is not going to be installed     
  ubuntu-desktop: Depends: dcraw but it is not going to be installed                             
                  Depends: gnome-media but it is not going to be installed                       
                  Depends: gnome-nettool but it is not going to be installed                     
                  Depends: gnome-power-manager but it is not going to be installed               
                  Depends: gnome-session but it is not going to be installed                     
                  Depends: gnome-session-canberra but it is not going to be installed            
                  Depends: gnome-system-monitor but it is not going to be installed              
                  Depends: gnome-system-tools but it is not going to be installed                
                  Depends: gnome-terminal but it is not going to be installed                    
                  Depends: gnome-themes-selected but it is not going to be installed             
                  Depends: gnome-themes-ubuntu but it is not going to be installed               
                  Depends: gnome-utils but it is not going to be installed                       
                  Depends: gstreamer0.10-alsa but it is not going to be installed                
                  Depends: gstreamer0.10-plugins-base-apps but it is not going to be installed   
                  Depends: gstreamer0.10-pulseaudio but it is not going to be installed          
                  Depends: gtk2-engines-pixbuf but it is not going to be installed               
                  Depends: gucharmap but it is not going to be installed                         
                  Depends: indicator-applet-session but it is not going to be installed          
                  Depends: language-selector but it is not going to be installed                 
                  Depends: launchpad-integration but it is not going to be installed             
                  Depends: libgd2-xpm but it is not going to be installed                        
                  Depends: libgnome2-perl but it is not going to be installed                    
                  Depends: metacity but it is not going to be installed                          
                  Depends: nautilus but it is not going to be installed                          
                  Depends: nautilus-sendto but it is not going to be installed                   
                  Depends: notify-osd but it is not going to be installed                        
                  Depends: pulseaudio but it is not going to be installed                        
                  Depends: pulseaudio-esound-compat but it is not going to be installed          
                  Depends: screensaver-default-images but it is not going to be installed        
                  Depends: seahorse but it is not going to be installed                          
                  Depends: software-center but it is not going to be installed                   
                  Depends: software-properties-gtk but it is not going to be installed           
                  Depends: ssh-askpass-gnome but it is not going to be installed                 
                  Depends: system-config-printer-gnome but it is not going to be installed       
                  Depends: ubuntu-artwork but it is not going to be installed                    
                  Depends: ubuntu-sounds but it is not going to be installed                     
                  Depends: update-manager but it is not going to be installed                    
                  Depends: update-notifier but it is not going to be installed                   
                  Depends: xdg-user-dirs-gtk but it is not going to be installed                 
                  Depends: xscreensaver-data but it is not going to be installed                 
                  Depends: xscreensaver-gl but it is not going to be installed                   
                  Depends: xsplash but it is not going to be installed                           
                  Depends: zenity but it is not going to be installed                            
                  Recommends: brltty-x11 but it is not going to be installed                     
                  Recommends: evolution-indicator but it is not going to be installed
                  Recommends: gnome-games but it is not going to be installed
                  Recommends: gnome-mag but it is not going to be installed
                  Recommends: gnome-orca but it is not going to be installed
                  Recommends: gnome-screensaver but it is not going to be installed
                  Recommends: gvfs-fuse but it is not going to be installed
                  Recommends: ibus but it is not going to be installed
                  Recommends: ibus-gtk but it is not going to be installed
                  Recommends: ibus-m17n but it is not going to be installed
                  Recommends: ibus-table but it is not going to be installed
                  Recommends: indicator-messages but it is not going to be installed
                  Recommends: jockey-gtk but it is not going to be installed
                  Recommends: libpam-gnome-keyring but it is not going to be installed
                  Recommends: libwmf0.2-7-gtk but it is not going to be installed
                  Recommends: mousetweaks but it is not going to be installed
                  Recommends: nautilus-share but it is not going to be installed
                  Recommends: network-manager-gnome but it is not going to be installed
                  Recommends: onboard but it is not going to be installed
                  Recommends: openoffice.org-gnome but it is not going to be installed
                  Recommends: openoffice.org-help-en-us but it is not going to be installed
                  Recommends: openoffice.org-style-human but it is not going to be installed
                  Recommends: pulseaudio-module-bluetooth but it is not going to be installed
                  Recommends: pulseaudio-module-gconf but it is not going to be installed
                  Recommends: pulseaudio-module-x11 but it is not going to be installed
                  Recommends: rhythmbox but it is not going to be installed
                  Recommends: speech-dispatcher but it is not going to be installed
                  Recommends: telepathy-idle but it is not going to be installed
                  Recommends: tomboy
                  Recommends: totem but it is not going to be installed
                  Recommends: totem-mozilla but it is not going to be installed
                  Recommends: transmission-gtk but it is not going to be installed
                  Recommends: tsclient but it is not going to be installed
                  Recommends: ubuntuone-client-gnome but it is not going to be installed
                  Recommends: usb-creator-gtk but it is not going to be installed
                  Recommends: vinagre but it is not going to be installed
                  Recommends: vino but it is not going to be installed
                  Recommends: xsane but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dnajun@dnajun-pc:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
dnajun@dnajun-pc:~$

```

---

### Post by nerdy_kid on 2009-11-10
i think you might have broken packages on your system.  I dont know how to fix this with kpackagekit (i am assuming that synaptic isnt installed), so id run the command it says.


i use Kubuntu all the time, i switched from ubuntu.  If you have a laptop i would stick with KDE, if not then your prefence i guess -- like simple fast and pretty and modern go with GNOME, like cutting edge highly configureable modern desktop go with KDE :D    or both....

```

sudo apt-get -f install

```

---

### Post by Dnajun_Tnuieh on 2009-11-10
> **nerdy_kid said:**
> i think you might have broken packages on your system.  I dont know how to fix this with kpackagekit (i am assuming that synaptic isnt installed), so id run the command it says.


i use Kubuntu all the time, i switched from ubuntu.  If you have a laptop i would stick with KDE, if not then your prefence i guess -- like simple fast and pretty and modern go with GNOME, like cutting edge highly configureable modern desktop go with KDE :D    or both....

```

sudo apt-get -f install

```


check the bottom, I did try that command. and yeah I'm using a laptop.

---

### Post by nerdy_kid on 2009-11-10
> **Dnajun_Tnuieh said:**
> check the bottom, I did try that command. and yeah I'm using a laptop.
  no you didnt :D you didnt do the sudo :D

---

### Post by Dnajun_Tnuieh on 2009-11-10
> **nerdy_kid said:**
> no you didnt :D you didnt do the sudo :D

oops =P
```

dnajun@dnajun-pc:~$ sudo apt-get -f install
[sudo] password for dnajun:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gnome-sudoku libgd2-noxpm
Suggested packages:
  libgd-tools
The following NEW packages will be installed:
  libgd2-noxpm
The following packages will be upgraded:
  gnome-sudoku
1 upgraded, 1 newly installed, 0 to remove and 34 not upgraded.
1 not fully installed or removed.
Need to get 209kB/2,427kB of archives.
After this operation, 4,534kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic-updates/main libgd2-noxpm 2.0.36~rc1~dfsg-3ubuntu1.9.10.1 [209kB]
Fetched 209kB in 2s (79.5kB/s)
(Reading database ... 30%
dpkg: warning: files list file for package `gnome-sudoku' missing, assuming package has no files currently installed.
(Reading database ... 118603 files and directories currently installed.)
Preparing to replace gnome-sudoku 1:2.28.0-0ubuntu1 (using .../gnome-sudoku_1%3a2.28.0-0ubuntu1_i386.deb) ...
Unpacking replacement gnome-sudoku ...
E: Sub-process /usr/bin/dpkg exited unexpectedly
dnajun@dnajun-pc:~$
```

---

### Post by nerdy_kid on 2009-11-10
i dont know :(

id do a reinstallof Kubuntu  if i were you, and make sure to check the disc before, just select it after you select the language.

---

### Post by Dnajun_Tnuieh on 2009-11-10
Alright so I switched to Ubuntu, everything so far is working fine, no bugs yet =)

thanks for the help everyone. will be back if i ever run into complications in ubuntu.

---

