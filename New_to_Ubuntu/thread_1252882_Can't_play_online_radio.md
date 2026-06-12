---
title: "Can't play online radio"
date: 2009-08-29
forum: New to Ubuntu
---

### Post by rausuar on 2009-08-29
Using a fresh install of Ubuntu 9.04, with VLC 1.01 and ubuntu-restricted extras, and Firefox 3, latest updates, I cannot get it to play online live radio stations, which oftenly use WMV or Windows Media formats.  

Am I missing some package? 

Thanks...

---

### Post by arochester on 2009-08-29
It might have helped if you gave us example web addresses...

Look at "Comprehensive Multimedia & Video Howto" on [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by oldos2er on 2009-08-29
I can't remember if ubuntu-restricted-extras contains the package w32codecs (or w64codecs if you're running 64-bit Ubuntu), but you might want to check to see if it's installed.

 Do you see any error messages?

---

### Post by candtalan on 2009-08-29
> **rausuar said:**
> Using a fresh install of Ubuntu 9.04, with VLC 1.01 and ubuntu-restricted extras, and Firefox 3, latest updates, I cannot get it to play online live radio stations, which oftenly use WMV or Windows Media formats.  

Am I missing some package? 

Thanks...

I have a couple of pages which has tried to put some multimedia information together in one place:
=============================================

Multimedia and Ubuntu
How to get multimedia codecs the easy way!

Disclaimer:   Patent and copyright laws operate differently depending on which country you are in. Please obtain legal advice if you are unsure whether a particular patent or restriction applies to a media format you wish to use in your country. 

Note- most of this information is taken from the medibuntu pages, mentioned below.

For legal reasons Ubuntu (as first installed) lacks many of the codecs which are needed to play some of the many possible audio or video formats available. This is because of global, geographical, variations in legislation regarding intellectual property, security and other issues.

Before following any of the procedures offered in here, please note that immediately after installation it is recommended to first download any security updates which are available to date. If you do not see a pop up offer for this then use    System>Administration>UpdateManager
and accept the updates (this is not the same as an upgrade to a later version of Ubuntu, which you should avoid doing unless you deliberately want that).

1) Multimedia – Linux native codecs
To get pretty well all of the multimedia codecs the easy way, ensure the machine is connected to the internet and use the facility
Add/Remove applications 
If the list is out of date, accept a refresh, and more recent information will be downloaded. Then use
Applications>Add/Remove

Ensure that 'All' is selected, and Click the choices to select 'All Available Applications' from the list.

Then into the 'Search' space type
gstreamer

After a short time, the search results will display a number of gstreamer entries and in addition the item 'Ubuntu restricted extras'.

For each of these in turn, including the 'Ubuntu restricted extras', click the check box so that a tick is shown. As you do this you will also be asked to confirm what you want and that you do not live in a country where such codecs are not allowed (such as USA).

Note that in some versions of Ubuntu, for example, 9.04, the [gstreamer fluendo MPEG2 demuxing plugin] is not required and will conflict with other installed software. If so, you will see an error warning message, so in this case, there is no need for this item.

When your choices are all checked and accepted, click the 'Apply' button and they will be downloaded and installed. You will now have installed most of the multimedia codecs. 

2) Further actions:
Playing Encrypted DVDs
The several actions above will be capable of installing most multimedia codecs. However, to play encrypted DVDs (some commercial DVDs), the libdvdcss2 package is also an essential requirement. libdvdcss2 is a simple library designed for accessing DVDs like a block device without having to use decryption. This can be installed easily after the medibuntu repository has been enabled for your machine, please see below.

3) Playing some non-native formats
Some media formats do not have native Linux facilities. In such cases it is possible to make use of binary Windows and other codecs through a 'wrapper', bundled as the 'w32codecs', for playback of these media formats. This can be installed easily after the medibuntu repository has been enabled for your machine, please see below.
There are various ways of installing these additional packages, although the exact details depend upon which type of computer you have and which version of Ubuntu you use (Note 1). 
4) The medibuntu repository
If your computer is configured to make use of the special software repository for Multimedia, Entertainment & Distractions In Ubuntu (medibuntu), then subsequent actions, including security updates, can be handled conveniently. Unfortunately for the beginner, the configuration to include a new software repository can seem a bit demanding at first.
The following actions are closely based on information at
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

An overview of actions is:
- Get the sources list and keyring
- Then get specific information for your Ubuntu version
- Then, add the GPG Key (to help ensure you only use the repository you are expecting).

The detailed actions for these three stages are best followed by using the medibuntu link
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
(please note the leading upper case in the word Medibuntu here)
On that page please see:
'Adding the Repositories' 
This technique makes use of a Terminal, and copy and paste.
If it seems complicated at first, have a look again at the overview of actions listed above, to help see what is being done.

How to get a 'Terminal'?
Applications>Accessories>Terminal
It is a powerful way of doing things fast. It is certainly much more powerful than it first appears, so do not rush with any typing or commands. Take your time.

For example, the first action is to get the sources list and keyring, appropriate for 'Any Ubuntu Release and keyring'. Carefully highlight the appropriate block of text in the medibuntu page,   
edit>copy, then into the Terminal, use 
edit>paste into the terminal. 
When you hit the Return key your password will be needed, and actions begin. 
Wait until all downloads are completed and you see a normal prompt again.

Complete the subsequent two actions listed in the overview above, specific information for your Ubuntu version, and then the GPG key, in a similar way. Please refer to the medibuntu page for more detailed information.

When these actions are completed, medibuntu repository is available in your Ubuntu. 
Well Done!

You can verify your success by looking at
System>Administration>Software Sources 
and the tab
Third Party Software
and you should see medibuntu packages free and non free as being entered and ticked (enabled).

Installing the packages: 
libdvdcss2    and    w32codecs
As will be seen in the Medibuntu page referenced above,  to play encrypted DVDs it is necessary to use libdvdcss2. Because in the preceding actions in this information sheet, the entire Medibuntu repository has already been made available, then it is now only necessary to call for the particular package to be installed, so, we follow the Medibuntu page's information to install libdvdcss2. Use a terminal and carefully enter
sudo apt-get install libdvdcss2
For non native formats for i386 (32 bit) machines, the w32codecs is needed. To install  this, use a terminal and carefully enter
sudo apt-get install w32codecs

For amd64 (64 bit) and PPC machines please use the appropriate package names as detailed in the Medibuntu pages.

Note 1:   Q: Which version of Ubuntu am I using? A: See System>Administration>System Monitor     and choose the tab:   System

=============================================

---

### Post by rausuar on 2009-08-29
> **arochester said:**
> It might have helped if you gave us example web addresses...

Look at "Comprehensive Multimedia & Video Howto" on [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Hi, thanks for the response!... I have already installed medibuntu and w32codecs and it is still the same.  I have attached a txt file where i put the debug of when I start Firefox via the console and enter the website.  Inside the file is also the website I tried to enter and listen.

I hope it helps...

---

