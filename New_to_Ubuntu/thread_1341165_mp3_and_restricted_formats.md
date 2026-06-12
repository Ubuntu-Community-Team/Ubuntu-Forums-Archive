---
title: "mp3 and restricted formats"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by lunyx on 2009-11-29
hello everyone. 
I installed ubuntu yesterday and already I am frustrated.
It works faster but all this codec stuff gives me nightmares.
So i try download restricted file package by going to 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and than clicking on "click here to install the ubuntu-restricted-extras package and than i get a message saying.
"could not find ubunutu restricted package"
if i got under apllications and ubuntu software center and try do it there it says that its not available in current data!

it annoys me since i want flash player and especially MP3 and so on.
PLEASE HELP since i am an absolute noob.
thank you!

---

### Post by manny43 on 2009-11-29
system
administration
synaptic package manager
type restricted extras in quick search window
choose ubuntu restricted extras
that should do it

---

### Post by Magical Tiger on 2009-11-29
what manny43 said should work, but also if you try to play one of those formats in something like Rhythmbox then it should prompt you to install codecs.

---

### Post by jrrader on 2009-11-29
You shouldn't have to go to websites to install things.  

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by lunyx on 2009-11-29
> **jrrader said:**
> You shouldn't have to go to websites to install things.  

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

but when i go to do same thing this website explains it doesnt work.
looking at the fourth picture, it doesnt offer me install option.
all it says is that canonical does not offer updates for ubuntu!
what does that mean ?

---

### Post by lunyx on 2009-11-29
bump. help please :(

---

### Post by GepettoBR on 2009-11-29
What version of Ubuntu are you using? If Canonical doesn't offer updates, that means you're using a very old version.

---

### Post by howefield on 2009-11-29
> **lunyx said:**
> bump. help please :(

Do you feel up to installing via the terminal ? Very easy.

Go to Applications > Accessories > Terminal

Type in the terminal window

```
sudo apt-get update
```

Enter your password when prompted, you won't see it typed, just press enter when you've typed it in.

Then type 

```
sudo apt-get install ubuntu-restricted-extras
```

And follow the instructions.

---

### Post by Major_Tom on 2009-11-29
I had this same problem when I just installed Ubuntu. After a few minutes use, Ubuntu prompted me to download a whole load of system updates. When this was done, all of the packages were available to load. So my advice is to wait, or maybe someone here can tell you how to search for updates.

---

### Post by lunyx on 2009-11-29
hmmmm. 
i went to terminal before and it didn't work.
but i didn't do update stuff.
now i tried but it tells me the same thing.
it says "failed to fetch" ... "could not resolve archive.ubuntu.com"

---

### Post by philinux on 2009-11-29
> **lunyx said:**
> hello everyone. 
I installed ubuntu yesterday and already I am frustrated.
It works faster but all this codec stuff gives me nightmares.
So i try download restricted file package by going to 
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
and than clicking on "click here to install the ubuntu-restricted-extras package and than i get a message saying.
"could not find ubunutu restricted package"
if i got under apllications and ubuntu software center and try do it there it says that its not available in current data!

it annoys me since i want flash player and especially MP3 and so on.
PLEASE HELP since i am an absolute noob.
thank you!

Which version of ubuntu are you running.

---

### Post by SPazzo on 2009-11-29
What version of Ubuntu are you running?  Go to System > About Ubuntu and it'll tell you there.

---

### Post by lunyx on 2009-11-29
i'm using 9.10 Karmic Koala
its so weird i don't know why is it doing this.
i tried getting restricted package off internet.
i tried thru terminal.
i tried thru synaptic package manager.
i tried thru ubuntu software center.

nothing seems to work. 
internet is fine b/c i can go on websites and IM software.
anybody can help ?

---

### Post by NoaHall on 2009-11-29
Can you post the output of 
```
 cat /etc/apt/sources.list
```?
Also, once you've done that, go to System -> Admin -> Software Sources -> Select Best Server.

---

### Post by Major_Tom on 2009-11-29
> **lunyx said:**
> i'm using 9.10 Karmic Koala
its so weird i don't know why is it doing this.
i tried getting restricted package off internet.
i tried thru terminal.
i tried thru synaptic package manager.
i tried thru ubuntu software center.

nothing seems to work. 
internet is fine b/c i can go on websites and IM software.
anybody can help ?

Have you tried System-Administration-Update Manager. 

See if there are any updates.

If not then your problem is different to mine.

---

### Post by t0p on 2009-11-29
Go to **System > Administration > Software Sources**.  Check boxes to get everything (Universe, Multiverse, whatever else is there). Close the window.  Open a terminal and type:

```
sudo apt-get update
```

then

```
sudo apt-get install ubuntu-restricted-extras
```

If that doesn't do the job, report back with all error messages.

---

### Post by Tiberion on 2009-11-29
> **t0p said:**
> Go to **System > Administration > Software Sources**.  Check boxes to get everything (Universe, Multiverse, whatever else is there). Close the window.  Open a terminal and type:

```
sudo apt-get update
```then

```
sudo apt-get install ubuntu-restricted-extras
```If that doesn't do the job, report back with all error messages.


You may have to go to system/administration/software sources and make sure that under other software all the boxes are checked!

---

### Post by lunyx on 2009-11-29
ok right now i am doing what i have been suggested and downloading updates.
it should take 30 minutes and than i will report what is happening.
thank you so much guys for all the help :D

---

### Post by candtalan on 2009-11-29
I have some notes which may be useful:
==========================================

Multimedia and Ubuntu

How to get multimedia codecs the easy way!

Disclaimer:   Patent and copyright laws operate differently depending on which country you are in. Please obtain legal advice if you are unsure whether a particular patent or restriction applies to a media format you wish to use in your country. 
For legal reasons Ubuntu (as first installed) lacks many of the codecs which are needed to play some of the many possible audio or video formats available. This is because of global, geographical, variations in legislation regarding the legal situation, security and other issues.

Before following any of the procedures offered in here, please note that immediately after installation it is recommended to first download any security updates which are available to date. 

If you do not see a pop up offer for this then use    System>Administration>UpdateManager
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
=================================================================================================================================

Background Information:
In the GNU/Linux community there is an important difference between Free and non Free software. The difference is an ethical difference relating to the freedom and respect that Free Software bestows on the user. This is enshrined in the 'Four Freedoms' of software user rights. Non free software, which is typically proprietary software, whether gratis or paid for, is secretive from the user and restrictive of the user. The Free Software Foundation is the conscience of the Free Software Movement and strives to encourage the world to greater use of Free Software, to gain benefits to society and creativity that result. 
Non free software has become a fact of life for many computer users, and although it may offer conveniences, the lack of user Freedoms is regarded as a heavy price by freedom aware people, and is treated with reluctance or under some protest. The Free software movement works hard to provide Free software alternatives. Please see [www.fsf.org](www.fsf.org) for more information.

---

