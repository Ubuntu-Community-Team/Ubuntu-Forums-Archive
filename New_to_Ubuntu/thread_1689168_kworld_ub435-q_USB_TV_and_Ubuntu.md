---
title: "kworld ub435-q USB TV and Ubuntu"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by docshawnc on 2011-02-16
Good Day -
     I've looked around and only found a couple of obscure references to this digital TV dongle sold by Kworld and linux.  I picked this up on New Egg for a whopping $23 so if I can't get it working with Ubuntu I'm not going to jump out the window.
     That being said, it would be great if it would work.  Has anyone had success with this?  They do make windows and mac drivers, but no linux to date.  Thanks in advance to everyone!

---

### Post by PaulReaver on 2011-02-16
sorry my bad... my bro has the dvb-t version


there is some positive info [**_[COLOR="Red"]here[/COLOR]_** ]("http://www.linuxtv.org/wiki/index.php/KWorld_UB435-Q_USB_ATSC_TV_Stick")

---

### Post by docshawnc on 2011-02-16
Thanks for the suggestion - I saw that page during my searches.  I guess no one has developed a package for it yet.  It's not a bad little dongle either, works pretty well under windows 7 for over the air TV - too bad.

---

### Post by pepar on 2011-02-27
Hi there,

I got my Kworld UB435-Q **v1** USB adapter to work on Lucid (also works for Maverick) by compiling the _current_ V4L-DVB tree (original instructions here: [https://wiki.ubuntu.com/em28xx]("https://wiki.ubuntu.com/em28xx")). Don't fret, although the procedure may not be *"for the absolute beginner"*, it is not as hard as it seems ... just follow the steps below (if you are not too scared of the 'terminal').

Warning: as of today, only v1 is supported, NOT v2. So these instructions **only apply to v1**. See here: [www.gossamer-threads.com/lists/mythtv/users/472834]("www.gossamer-threads.com/lists/mythtv/users/472834")

Alternative solution: [www.gossamer-threads.com/lists/mythtv/users/457574]("www.gossamer-threads.com/lists/mythtv/users/457574")


If you have not yet compiled anything on your system, you may need to install a couple of packages (original instructions here: [https://help.ubuntu.com/community/CompilingEasyHowTo]("https://help.ubuntu.com/community/CompilingEasyHowTo"))
```
sudo apt-get install build-essential checkinstall
```

-----------------------------------
Here it goes.

!!!  **must** do as **regular** user (**NOT** root)  !!!

Requirements:
- Hg from [http://www.selenic.com/mercurial/]("http://www.selenic.com/mercurial/"). You can install Mercurial in Ubuntu with:
```

$ sudo apt-get install mercurial

```
- The linux kernel sources for your kernel. Install sources for you current kernel with this command:
```

$ sudo apt-get install linux-headers-`uname -r` linux-source

```
We need to get the source code (do not use the web frontend for downloading the repository)
```

$ hg clone http://linuxtv.org/hg/v4l-dvb

```

Now build from source (the following steps also need to be repeated if the kernel gets updated, ie. version change):
```

$ cd v4l-dvb
$ make
$ sudo make install

```
Before posting any error messages, reboot your machine here.
Now load the drivers:
```

$ sudo modprobe em28xx

```
To verify that your setup was correct you might compare your dmesg output with ones on following wiki site: [http://linuxtv.org/v4lwiki/index.php/Em2880/dmesg]("http://linuxtv.org/v4lwiki/index.php/Em2880/dmesg"). If your device isn't listed there please help to complete the list and add your device there too.

Scanning for channels, to use with xine media player, if you are in the USA (or replace us-ATSC-center-frequencies-8VSB with your region specific frequency file, if you have one)
```

$ dvbscan -n -o zap -p us-ATSC-center-frequencies-8VSB > ~/.xine/channels.conf

```

Both Me-TV and Kaffeine (needs some KDE dependencies) work well, and have built-in 'channel scanning'.


Hope it helps someone.
PEP

---

### Post by 05mav on 2011-05-22
Hi Guy's,
 
I bought a kworkd UB435-Q V2 USB and was searching the net for some information on it and came across this forum.
 
It was bit of an impluse buy, i said i'd get it and see how i get on. I have it installed and all seems to work without issue, but it was only later i was wondering will this work in Europe, i'm originally Irish and will be returning there in a year or so, so would like to have something that works there.
 
I mainly want to be able to record TV programs and put them on my media player. It seems that this is ATSC (8VSB), Ireland/Europe use DVB-T, but i was wondering if i could go in and change the drivers for use in Europe. Obviously i don't have a clue of what to change, but maybe somebody here might.
 
Thanks for any help, also is the only way to get a copy of the program recorded to burn it onto a CD, it be much easier if i could just copy to a USB

---

### Post by 05mav on 2011-05-22
Sorry Guy's another question,
 
Is the ATSC (8VSB) for aerials only, i connected my UB to the cable and it worked fine, i think that's QAM, so would that work in Europe, will QAM work for satellites

---

### Post by jamrbrts8 on 2012-01-26
:p With Xubuntu 11.10 "Ocelot", my Kworld ub435-q USB TV tuner works great in Kaffeine Media Player v. 1.2.2 and KDE v. 4.7.4 for "over the air broadcasts" without any modifications.

      A) Simply open up Kaffeine
      
      B)  choose "Digital TV" in the Start Menu

      C)  hit "Configure Television" option icon

      D) Click on "Device 1" tab

      E)  Choose "Source" which for me was "us-ATSC-center-frequencies-8VSB" for over-air broadcasts

      F) Close window, go back to Kaffeine TV window and click "Channels" option icon

      G)  In "Channels" window, make sure "Source" is set to "ATSC", then hit "Start Scan" button -- the scan took about 3 minutes and 17 channels were found -- I believe all that are in my area.

      H) Once the scan is complete, highlight all channels found in the right-hand box "Scan Results"  (or all that you would like to save)  then click "Add Selected" and those channels will then appear in the left-hand box called "Channels" 

      I) Hit "OKAY" to get out of "Channels" window and you will return to Kaffeine "Digital TV" window with your selected channels appearing in the left margin column.

      j) Double click on a channel to select  -- and now hopefully you are watching !

Thanks Ubuntu and Kaffeine for programming for this tuner.

JR

---

### Post by robrobinette on 2012-06-27
I tried this with Ubuntu 12.4 and my Kworld UB435-Q V2 and I don't have a "Device" tab in "Configure Television." lsusb does show the dongle is recognized by Ubuntu.


> **jamrbrts8 said:**
> :p With Xubuntu 11.10 "Ocelot", my Kworld ub435-q USB TV tuner works great in Kaffeine Media Player v. 1.2.2 and KDE v. 4.7.4 for "over the air broadcasts" without any modifications.

      A) Simply open up Kaffeine
      
      B)  choose "Digital TV" in the Start Menu

      C)  hit "Configure Television" option icon

      D) Click on "Device 1" tab

      E)  Choose "Source" which for me was "us-ATSC-center-frequencies-8VSB" for over-air broadcasts

      F) Close window, go back to Kaffeine TV window and click "Channels" option icon

      G)  In "Channels" window, make sure "Source" is set to "ATSC", then hit "Start Scan" button -- the scan took about 3 minutes and 17 channels were found -- I believe all that are in my area.

      H) Once the scan is complete, highlight all channels found in the right-hand box "Scan Results"  (or all that you would like to save)  then click "Add Selected" and those channels will then appear in the left-hand box called "Channels" 

      I) Hit "OKAY" to get out of "Channels" window and you will return to Kaffeine "Digital TV" window with your selected channels appearing in the left margin column.

      j) Double click on a channel to select  -- and now hopefully you are watching !

Thanks Ubuntu and Kaffeine for programming for this tuner.

JR

---

