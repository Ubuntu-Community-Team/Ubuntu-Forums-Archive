---
title: "Help with Dazzle DVC100"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by charliechip95 on 2010-06-08
I've been trying to get Dazzle working on Ubuntu, but I haven't had any success yet. Bear with me, I'm an Ubuntu n00b lulz. :lolflag:

I found these instructions when googling and used them...

```
Here are the commands needed to install your device in a condensed version:
Open an Applications-->Accessories-->Terminal and type:

Code:
lsusb
with your device plugged in the result should look something like this:

Code:
Bus 005 Device 003: ID 2304:021 a Pinnacle Systems, Inc.
You will need to install a few programs to help compile the driver. In the same terminal type:

Code:
sudo apt-get install mercurial build-essential
You need to use mecurial you installed in the previous step to retrieve the source module:

First you deed to create a directory to download the module source to:

Code:
mkdir ~/src
This command creates a directory called src in you home directory. Next change directory to src:

Code:
cd ~/src
This next command:

Code:
hg clone http://linuxtv.org/hg/v4l-dvb
downloads the module source to the directory you just created, go get a cup of your favorite beverage as this step may take a while.

Code:
cd v4l-dvb
The above command changes directory to the directory that was created when the module source was retrieved
the next step is to compile the source:

Code:
make
You will see some errors, but it is safe ignore them
The final step is to install the modules:

Code:
sudo make install
once this step is done the driver for your device should load automagically when the device is plugged in.
```

Everything seemed to work as he said, except, after doing this, I plugged in the Dazzle and nothing happened. I can't find anything on the computer that shows it recognized the Dazzle was plugged in. Thinking perhaps I need to get software to see if it works, I tried installing TV Time. It seemed to install fine, but whenever I try to open TV Time (in the terminal), it gives me this error:

```
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/user/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/user/.tvtime/tvtime.xml: Permission denied.
videoinput: Cannot open capture device /dev/video0: No such file or directory
Found "DVC100 : USB Audio (hw:1,0)"
I/O error : Permission denied
I/O error : Permission denied
Segmentation fault
```

I'm not sure what this means, or how to fix it.  Help! :confused:

---

### Post by anewguy on 2010-06-08
You may want to look [here]("http://www.linuxquestions.org/questions/linux-hardware-18/dazzle-dvd-recorder-497596/"). 

Dave ;)

---

### Post by charliechip95 on 2010-06-08
UPDATE: I got TVTime working after updating the computer. TVTime doesn't record though, any suggestions on how to record the Dazzle?

Thanks for the link -- I looked in it but it's a bit advanced. I'm not sure how to use the info there.

---

### Post by charliechip95 on 2010-06-08
Any help? :P

---

### Post by baconman on 2010-06-09
There are several programs to capture and edit video. Kino is supposed to be one of the best.

---

### Post by charliechip95 on 2010-06-09
Thank for the replies so far. :) I don't think Kino accepts USB video.

I think maybe Cinelerra does though. I tried to install it and got this error:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libcinelerra
The following NEW packages will be installed:
  cinelerra libcinelerra
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 13.7MB of archives.
After this operation, 29.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ppa.launchpad.net/akirad/akirad/ubuntu/ lucid/main libcinelerra 2.1.1-git20100325~ppa5~lucid [2,441kB]
Get:2 http://ppa.launchpad.net/akirad/akirad/ubuntu/ lucid/main cinelerra 2.1.1-git20100325~ppa5~lucid [11.3MB]
Fetched 13.7MB in 1min 53s (121kB/s)                                           
Selecting previously deselected package libcinelerra.
(Reading database ... 159886 files and directories currently installed.)
Unpacking libcinelerra (from .../libcinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libcinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb (--unpack):
 trying to overwrite '/usr/lib/libmpeg3hv-1.5.0.so.1.0.0', which is also in package libmpeg3hv 1:2.1.0-2svn20070109
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package cinelerra.
Unpacking cinelerra (from .../cinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb) ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libcinelerra_2.1.1-git20100325~ppa5~lucid_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The package didn't install correctly. I tried to completely remove it in Synaptic Package Manager and got this...

```
(Reading database ... 159885 files and directories currently installed.)
Removing Cinelerra ...
Description:    Ubuntu 10.04 LTS
locale "en_US.ISO-8859-15" not in archive
locale "ru_KU.KOI8-R" not in archive
rm: cannot remove '/usr/bin/Cinelerra' No such file or directory
dpkg: error processing cinelerra (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 cinerella
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:


```

Is Cinelerra good for capturing USB video/audio? And how do I get this broken package fixed?

---

### Post by anewguy on 2010-06-09
Okay, I'm not familiar with it at all, but I've heard the package cheese lets people be sure their USB net cameras work.  It might be worth checking it to see if it can do anything like you are looking for.

Dave ;)

---

### Post by charliechip95 on 2010-06-09
I think it should work just fine if I can find the right software, because I can hear and see it on TVTime. If only TVTime had a 'Record' button. :(

Hopefully I haven't messed things up big time, but I can't install any programs now, because of the broken Cinelerra package. When trying to install a program, it says, "The package system is broken", and clicking "Details" it says "cinelerra". Trying to get my Dazzle to work has formed into a much bigger problem it seems. I really need some help; not just with the Dazzle but fixing this broken package so I can install things.

If I can install it, I'll tell you how Cheese works with the Dazzle later.

---

