---
title: "can't get Brother MFC-240 working U 10.4"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by technmom on 2010-06-03
I did download some file from the Brother site but didn't know how to install it. I went back to Windows and did an upgrade on the firmware. The install menu for printers does not include this printer. Oh and a side note. I'm starting to feel like........I know someone will die at this one.........but I need to know commands like I did when I was a software engineer using Dos to use Ubuntu Where can I learn these and if this is the case I'm not sure I could recommend it to too many people.

---

### Post by anewguy on 2010-06-03
Not being familiar with your printer, I did a little searching online via a Yahoo search with ubuntu 10.04 brother mfc-240 and got several hits.  Some of them mention a driver from Brother, and also mention some files that can be installed from Synaptic Package Manager:

- open Synaptic Package Manager

- put brother in the search string

- I think the packages I would install are:

brother-lpr-drivers-common
brother-cups-wrapper-common
brother-lpr-drivers-extra
brother-cups-wrapper-extra


I would install those and see how things go.  Please post back with the results, any errors, etc..

Dave ;)

---

### Post by pricetech on 2010-06-03
Does Ubuntu detect the printer ??  If so, it should recommend a driver.  It may not be what you'd expect, but should work anyway.

You said you downloaded a file from Brother but did not know how to use it.  What kind of file was it ??

I'm not familiar with that model of Brother printer, so I can't tell you anything specific to it, but Brother seems to work well under Ubuntu as a rule.

---

### Post by anewguy on 2010-06-03
> **technmom said:**
> Oh and a side note. I'm starting to feel like........I know someone will die at this one.........but I need to know commands like I did when I was a software engineer using Dos to use Ubuntu Where can I learn these and if this is the case I'm not sure I could recommend it to too many people.

I wanted to answer this separately so as not to confuse it with the printer info.  As an ex systems programmer and system administrator I can say the real power of Linux lies in mastering the command line.  However, with that being said, the average Joe/Julie user just wanting an OS different from others can normally run Ubuntu with very little, if any, need for the command line.  Things that might require the command line could be posted here and someone can walk them through it easy enough.

Linux and it's distributions have come a long way.  There are still distributions geared more towards "the old days" of digging, dumps and low-level fun.  However, most modern distributions, and just my 2-cents worth, Ubuntu, have made Linux pretty easy.

Hope you have fun!

Dave ;)

---

### Post by technmom on 2010-06-03
I am really really new to this, so how do I open Synaptic Package Manager??? Thanks for your other post.


> **anewguy said:**
> Not being familiar with your printer, I did a little searching online via a Yahoo search with ubuntu 10.04 brother mfc-240 and got several hits.  Some of them mention a driver from Brother, and also mention some files that can be installed from Synaptic Package Manager:

- open Synaptic Package Manager

- put brother in the search string

- I think the packages I would install are:

brother-lpr-drivers-common
brother-cups-wrapper-common
brother-lpr-drivers-extra
brother-cups-wrapper-extra


I would install those and see how things go.  Please post back with the results, any errors, etc..

Dave ;)

---

### Post by technmom on 2010-06-03
I found the files I downloaded yesterday. I extracted them. When I open they are code in text. Looks like a C program.

---

### Post by migs73 on 2010-06-03
Look here; [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) 
and follow the instructions BEFORE downloading any drivers.
Basically all you have to do before hand is make a couple of directories (to put the drivers in), check you have other required software installed and then download the drivers ( I found if you just click on them for download and use the default GDebi package installer that pops up, it installs them into the correct directories anyway, instead of the long winded' right click and download to desktop cd to correct directory...' etc but this may be needed if trying to force them onto 64bit architecture). Then follow the instructions to make sure they are in the right place, and then configure the Cups printing system (again as per the instructions on the website).
It sounds worse than it is, I'm a newbie and managed to follow it (on my second attempt though:)).

Also, I am not a fan of command line either, it is annoying you cannot create the two directories required using the GUI (I tried but there is no option in a hidden[root??] folder to create a new folder.). There should be the facility to do so, but with all the warning bells and whistles along with sudo password so you know you can be doing harm. By the way, apart from the sudo password there are NO warnings what you are doing could be dangerous to your system in terminal (ominous name don't you think!!).

---

### Post by wojox on 2010-06-03
[HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies!]("http://www.uluga.ubuntuforums.org/showthread.php?t=590793")

---

### Post by migs73 on 2010-06-03
Wojox;

That is the howto that got me stuck the first time I tried (was trying to follow it and the brother website it directs you too). It is really just what is on the brother website but in a different order. It is also from 2007, probably doesn't make much difference but the brother website states it is for 9.10.

If I get the time I might try my own Howto.

---

### Post by roger_1960 on 2010-06-03
Hi

As suggested, look at [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-240C](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-240C) and follow all the instructions.

---

### Post by plucky on 2010-06-03
> **technmom said:**
> I am really really new to this, so how do I open Synaptic Package Manager??? Thanks for your other post.

**System > Administration > Synaptic Package Manager** and search for **mfc-240c** and it will find ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
``` if you have the multiverse repository enabled.

Select both and install.

Then go to **System > Administration > Printing** and install the printer.

Good Luck

---

### Post by technmom on 2010-06-03
> **roger_1960 said:**
> Hi

As suggested, look at [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-240C](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-240C) and follow all the instructions.


I did this and went to the folder.  as it says in the instructions posted below step 4 I have to say I'm not sure which folder :

  	 	 	 	 	 	  tep 3. Download a driver.  
 Download LPR driver.  	 	[Printer 	Driver download page]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html")  	 	Step 4. Install the driver  	 	4-1. Turn on the printer and connect the usb, network or parallel 	cable.  	 	4-2. Go to the directory where the driver is.  	 	4-3. Install LPR driver  	 		Command (for 		dpkg)  :  dpkg  -i  --force-all  (lpr-drivername) 				 		Command (for rpm)  :  rpm  -ihv  --nodeps  (lpr-drivername) 				 		[Example(for 		dpkg)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#dpkg1") | [Example(for 		rpm)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#rpm1")  		 	4-5. Check if the LPR driver is installed  	 		Command (for 		dpkg)  :  dpkg  -l  |  grep  Brother 				 		Command (for rpm)  :  rpm  -qa  |  grep  -e  (lpr-drivername) 				 		[Example(for 		dpkg)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#dpkg3") | [Example(for 		rpm)]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html#rpm3")I am stuck on step 4-3 I assume I am supposed to know the driver name and don't ???  still Greek to me or Ubuntu. at this point I might know more Greek than Ubunu since some English words are derived from Greek roots

---

### Post by technmom on 2010-06-03
> **plucky said:**
> **System > Administration > Synaptic Package Manager** and search for **mfc-240c** and it will find ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
``` if you have the multiverse repository enabled.

Select both and install.

Then go to **System > Administration > Printing** and install the printer.

Good Luck

Okay I'm getting closer. After trying the brother site and commands and installations that I don't know if I did right I did what you say here and did a test print. That worked but when I tried to print a page of a document (the Ubuntu pocket guide) it says receiving data but never prints and nothing is left in the queue.

---

### Post by plucky on 2010-06-04
> Okay I'm getting closer. After trying the brother site and commands and installations that I don't know if I did right I did what you say here and did a test print. That worked but when I tried to print a page of a document (the Ubuntu pocket guide) it says receiving data but never prints and nothing is left in the queue.



Open a terminal ```
Applications > Accessories > Terminal
```]
and input this command ```
dpkg -l | grep brother
```.

You can copy and paste it directly into the terminal window.This command will tell you whether the drivers are installed.

Did you select the correct driver when you added the new printer?

Check you have the correct paper size selected for your printer.

Another troubleshooting tool is the CUPS interface which is accessed by putting ```
 http://127.0.0.1:631/
``` into the Firefox address bar.

Good Luck

---

### Post by anewguy on 2010-06-04
The drivers that are downloaded from the Brother site are probably outdated or in some other way not correct.  The files that are in the link that was posted by migs73 are all replaced by the files in that I mentioned in my post about using Synaptic Package Manager.  It's a little late now, since everyone pointed you down the other path instead of telling you how to access the package manager, but let's give this a try anyway:

Click on system/administration/synaptic package manager

Enter in the search string I suggested

For each of the 4 packages I mentioned, click on the little box at the front and then on mark for installation.

Once all 4 packages are marked, click on Apply and wait for it to finish.  When it all finishes, close the package manager and try printing again.

Dave ;)

---

### Post by migs73 on 2010-06-04
Anewguy;

If all that was required was for me to download those packages I'll be extremely disheartened. All the How-to's give some sort of version of what is on the Brother website.
I have looked at those packages you mention, and the 'extra' ones mention a group of printers supported and neither the MFC-240C or the MFC-255CW (my printer) are listed.
There is no listing for what printer drivers are bundled in the common files.
If these packages are downloaded, will they automatically create/populate the correct folders?
The Brother website lists the drivers that are required for each printer, and appears to be updated (new printers getting added), so I would think the drivers will be correct (won't they be the drivers in the packages anyway??).

---

### Post by wojox on 2010-06-04
Okay try this HowTo. I have a Brother Printer also.

Step 1
-------

```
sudo mkdir /var/spool/lpd
```

Step 2
-------

You need to install the lpr driver here so type in the name of you lpr driver.

```
sudo dpkg -i --force-all mfc240cwlpr.deb
```

Step 3
-------

```
sudo mkdir /usr/share/cups/model
```
 
Step 4 
-------

Install cupswrapper here and make sure you use the name of yours.

```
sudo dpkf -i --forece-all mfc240cwcupswrapper.deb
```

Step 5
-------

Open System > Administration > Printing and configure your new printer in there.

---

### Post by technmom on 2010-06-04
you have me totally confused. I am going away for a few hours...business and will be back to try these things when I can read them and digest them.........thanks for trying.......now I'm needing to install some type of plugin for MP4 
I can see where it would have an advantage to use Ubuntu. We did some bill paying with Windows last night that took forever, but we needed the printer. I tried some of the things that took a while there last night on Ubuntu and it worked really fast. Without the printer though.........hmmm
Okay I'll get this fixed and learn in the process.
it took me four days to figure out how to get some videos from a repository my teacher set up and by the time I was done I'm not sure what I did..........so goes the life of a newbie Ubuntu user

---

### Post by technmom on 2010-06-04
> **anewguy said:**
> The drivers that are downloaded from the Brother site are probably outdated or in some other way not correct.  The files that are in the link that was posted by migs73 are all replaced by the files in that I mentioned in my post about using Synaptic Package Manager.  It's a little late now, since everyone pointed you down the other path instead of telling you how to access the package manager, but let's give this a try anyway:

Click on system/administration/synaptic package manager

Enter in the search string I suggested

For each of the 4 packages I mentioned, click on the little box at the front and then on mark for installation.

Once all 4 packages are marked, click on Apply and wait for it to finish.  When it all finishes, close the package manager and try printing again.

Dave ;)

Thank you, Dave! It worked! I should have tried that first, but got a bit confused. I'm learning.  Now to see if I can scan..........brb

---

### Post by technmom on 2010-06-04
I did not try the scanner, but only need it when doing one function at a banking site and they don't allow anything but Outlook.....darn.
Thanks for all the help, now onto opening those MP4's

---

### Post by anewguy on 2010-06-04
> **technmom said:**
> I did not try the scanner, but only need it when doing one function at a banking site and they don't allow anything but Outlook.....darn.
Thanks for all the help, now onto opening those MP4's

You may want to open another post if you have problems with MP4's.  I think there are some additional codecs to install for those, but I'd have to check first (I just do somethings automatically now when I install - like when I saved my stuff, deleted 9.10 and then installed 10.04).

Glad the information got your printer working.  From what I had read on the net (it can be your best friend - try putting ubuntu 10.04 brother mfc-240 driver in a yahoo search string), it was supposedly all that needed to be done with 10.04.

Best of luck, hope you enjoy Ubuntu!  Like any OS, it has its quirks and silly little aggravating things, but I enjoy it!

Dave ;)

---

