---
title: "Trouble downloading all of Realtime files"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by mikodo on 2010-04-18
Hello everyone,

I never wanted to use Realplayer again; but I am following a quit smoking site (whyquit.com) that in some of the videos offered, seem to need it.

So off to synaptic and I reluctantly thought I would try to down load. I checked for installation for realplayer, then hit reload and when Downloading Package information, only 52 of 54 files were able to be downloaded and stalled at that point eventually giving the error:  

```
W: Failed to fetch http://packages.medibuntu.org/dists/karmic/Release.gpg  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2  Unable to connect to packages.medibuntu.org http:

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2  Unable to connect to packages.medibuntu.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```Bellow are screenshots of my Software sources and Authentication. (4 shots)

Maybe I need to add in my software sources **medibuntu .org**, I dunno?

If there is an easy fix for me to use Realtime, with all downloadable files, please explain. If not, like I said above, I really don't want to have to use Realplayer, and I'll be happy keeping it out of computer. It is not that big of a deal for me to watch those particular videos tied with Realplayer and I can do without them quite readily. This is not something I want to go to a lot of trouble fixing or finding alternative open source players for.

Thank you.

EDIT:    I'm off to bed. Again, if anyone has an easy fix, please post. If not, I"ll do without Realplayer quite happily. Thanks again!

---

### Post by candtalan on 2010-04-18
multimedia: I think these notes are up to date, and if you follow them I think you wil be able to play most things.

Multimedia and Ubuntu

Disclaimer:   Patent and copyright laws operate differently depending on which country you are in. Please obtain legal advice if you are unsure whether a particular patent or restriction applies to a media format you wish to use in your country. 
For legal reasons Ubuntu (as first installed) lacks many of the codecs which are needed to play some of the many possible audio or video formats available. This is because of global, geographical, variations in legislation regarding the legal situation, security and other issues.

Before following any of the procedures offered in here, please note that immediately after installation it is recommended to first download any security updates which are available to date. If you do not see a pop up offer for this then use    
System>Administration>UpdateManager
and accept the updates (this is not the same as an 'Version' upgrade, to a later version of Ubuntu, which you should avoid doing unless you want that).

1) Multimedia – GNU/Linux native codecs
To get pretty well all of the multimedia codecs the easy way, ensure the machine is connected to the internet and use the facility (note - for Ubuntu 9.10 or later, use Ubuntu Software Centre, not Add/Remove)
Add/Remove applications 
If the list is out of date, accept a refresh invitation, and more recent information will be downloaded. Then use
Applications>Add/Remove

Ensure that 'All' is selected, and Click the choices to select 'All Available Applications' from the list  (for Ubuntu 9.10 or later, Get Free Software).

Then into the 'Search' space type
gstreamer

After a short time, the search results will display a number of gstreamer entries, 

Note that the search results may also include some items related to gstreamer, but are not directly gstreamer items, for example Subtitle Editor, OpenOffice full Suite, Bluemindo. these are not necessary in this current activity.

For each gstreamer item in turn, click the check box so that a tick is shown. It is possible you will be asked to confirm what you want and that you do not live in a country where such codecs are not allowed (such as USA).

Note that in some versions of Ubuntu, for example, 9.04, the [gstreamer fluendo MPEG2 demuxing plugin] is not required and will conflict with other installed software. If so, you will see an error warning message, so in this case, there is no need for this item.

When your choices are all checked and accepted, click the 'Apply' button and they will be downloaded and installed. You will now have installed most of the multimedia codecs. (Note that for Ubuntu 9.10 or later, the items might need to be installed one at a time) 

Then, into the 'Search' space type
Ubuntu restricted extras
and install it. In some versions of Ubuntu it may have been possible to install this item at an earlier stage.

2) Further actions:
Playing Encrypted DVDs
The several actions above will be capable of installing most multimedia codecs. However, to play encrypted DVDs (some commercial DVDs), the package libdvdcss2 is also an essential requirement. libdvdcss2 is a simple library designed for accessing DVDs like a block device without having to use decryption. This can be installed easily after the medibuntu repository has been enabled for your machine, please see below.

3) Playing some non-native formats
Some media formats do not have native GNU/Linux facilities. In such cases it is possible to make use of binary Windows and other codecs through a 'wrapper', bundled as the 'w32codecs', for playback of these media formats. This can be installed easily after the medibuntu repository has been enabled for your machine, please see below.

4) The Medibuntu repository
If your computer is configured to make use of the special software repository for Multimedia, Entertainment & Distractions In Ubuntu (medibuntu), then subsequent actions, including security updates, can be handled conveniently. Unfortunately for the beginner, the configuration to include a new software repository can seem a bit demanding at first.
The following actions are closely based on information at

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

(please note the leading upper case in the word Medibuntu here)

An overview of actions is:
- Add the Repository. A Repository is a private library of relevant software packages, administered by a known group of people.
On the Medibuntu web page mentioned above please see: 'Adding the Repository' 
This technique makes use of a Terminal, and copy and paste.
If it seems complicated at first, please don't be concerned, it uses Edit>copy, and Edit>paste.

How to get a 'Terminal'?
Applications>Accessories>Terminal
It is a powerful way of doing things fast. It is certainly much more powerful than it first appears, so do not rush with any typing or commands. Take your time.

Adding the Repository
Carefully first highlight the entire block of command text in the Medibuntu page,   
edit>copy, then into the terminal, use 
edit>paste into the terminal. 
When you hit the Return key your password will be needed, and actions begin. 
Wait until all downloads are completed and you see a normal prompt again.

Please refer to the Medibuntu page for more detailed information.

When these actions are completed, Medibuntu repository is available in your Ubuntu. 
Well Done!

You can verify your success by looking at
System>Administration>Software Sources 
and the tab
Third Party Software  (or 'Other Software')
and you should see Medibuntu packages free and non free as being entered and ticked (enabled).

Installing other packages: 
libdvdcss2    and    w32codecs

As will be seen in the Medibuntu page referenced above,  to play encrypted DVDs it is necessary to use libdvdcss2. Because in the preceding actions in this information sheet, the entire Medibuntu repository has already been made available, then it is now only necessary to call for the particular package to be installed, so, we follow the Medibuntu page's information to install libdvdcss2. Use a terminal and carefully enter (or copy and paste from the Medibuntu page)
     sudo apt-get install libdvdcss2

For playing non native formats for i386 (32 bit) machines, the w32codecs is needed. To install  this, use a terminal and carefully enter (or copy and paste from the Medibuntu page)
      sudo apt-get install w32codecs

For amd64 (64 bit) and PPC machines please use the appropriate package names as detailed in the Medibuntu pages.


hth

---

### Post by wojox on 2010-04-18
I think the servers are down. I'd try again when you wake up.

---

### Post by mikodo on 2010-04-18
In this thread  [http://ubuntuforums.org/showthread.php?t=1457340](http://ubuntuforums.org/showthread.php?t=1457340) Howefield explains that the servers for Medibuntu are up; but anything to do with the packages are down, and to keep trying, for when they are up (my paraphrase).

Thanks.

---

