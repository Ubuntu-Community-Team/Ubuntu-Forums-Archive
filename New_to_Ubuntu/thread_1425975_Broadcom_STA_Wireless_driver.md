---
title: "Broadcom STA Wireless driver"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by noixzx on 2010-03-09
After installing the .deb file directly and it's dependent, when I go into Hardware Drivers, Broadcam shows up, but when I try to activate it, it says "searching for available drivers" and when it's done it still says it's not activated.
Aghhhhhhhhh.
What do I do?
And what are "proprietary drivers", should this be one?

I have BCM4311, if it helps any. 
Also, I noticed there are older versions of bcmwl-kernel-source, the one that came with it being bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb.
That's the one I installed.

I've been trying to make my wireless work all day and all last night and I'm severely lacking sleep.

Someone, PLEASE, PLEASE give me an answer.
I can't revert to windows, or I would by now. This is irritating.

Any way I could get my wireless working would be IMMENSELY appreciated. I'm tearing my hair out over here.

---

### Post by hsartoris on 2010-03-09
I would look up fwcutter in google... I had the same problem initially, but I found a website (I believe it is a broadcom site) that told me how to use the tools it provided. sorry I can't give you a link

---

### Post by undecim on 2010-03-09
If you can connect to the internet with an ethernet cable (i.e. directly to your router or modem), you can use that to install the drivers via System -> Administration -> Hardware Drivers

---

### Post by sandyd on 2010-03-09
```

sudo modprobe wl
```?

---

### Post by lkraemer on 2010-03-10
noixzx,
You haven't given anyone any information to be able to offer help!

What is the Ubuntu Version?  8.04x, 8.10, 9.04, 9.10, 10.04, ????
32 bit or 64 Bit? .....Yes, it makes a difference!...Depending....
Laptop or Desktop?
USB Wifi Dongle or onboard Wifi?
What instructions were followed and what was the URL?
What were the results after install? ....other than it didn't work.

First we need to know what hardware your Laptop/Desktop has installed.

Just use "copy & paste" for the commands.
And, there is a difference in LSPCI and lspci.
```

uname -r
lspci
lspci -nn
lsusb
lshw -C network
lsmod
ndiswrapper -l
cat /etc/modprobe.d/blacklist.conf
iwconfig
ifconfig

```
Just copy & paste the commands in a Terminal window,
one at a time, and post the results.
(If you are using versions earlier than 9.10, or 9.04 use:
cat /etc/modprobe.d/blacklist)


I just booted Ubuntu 9.10 Livecd with my Wifi PCMCIA card (Broadcom) and got it working in a few minutes.

Pick one method and stick with it. Don't mix-n-match.

Your options that can be used:
1. Ndiswrapper and a Windows Driver....bcmwl5.inf & sys
2. bcm43xx module and some Firmware.... B43 & B43legacy *.fw
3. b43 and some Firmware that was downloaded/extracted when you
enabled the Driver.


(Options #1, and #2 are shown at:
[http://ubuntuforums.org/showthread.php?t=1314852&highlight=B43](http://ubuntuforums.org/showthread.php?t=1314852&highlight=B43))


#3 ONLY - (The following is for Ubuntu 9.10 as it uses b43.)
If you just need the Broadcom firmware for b43 it can be found on
the internet. ie. [www.omattos.com/broadcom](www.omattos.com/broadcom)
Extract the files, copy them to /lib/firmware and then enable
the Hardware Drivers.

If lsmod shows module b43xx, ndiswrapper, and others installed you
will need to remove them and blacklist them, since you are going to
be using b43. Be sure to insert a # at the beginning of the line if
any of the existing driver modules are blacklisted, and you will be
using them. You may have to remove the following depending on what lsmod
shows: (DON'T BLACKLIST SSB)
```

modprobe -r b44
modprobe -r b43legacy

```
You can use sudo gedit /etc/modprobe.d/blacklist.conf
and add the necessary modules to blacklist them.

If you don't like this method, you can use the results from
lshw -C network to search the Forum for a howto: on the specific model.
I know there is a good howto:, but I didn't find it in the search.
I've got it bookmarked on some computer around here.
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851)
[http://ubuntuforums.org/showthread.php?t=760568&highlight=bcm4311+broadcom](http://ubuntuforums.org/showthread.php?t=760568&highlight=bcm4311+broadcom)
[http://ubuntuforums.org/showthread.php?t=1390535&highlight=bcm4311+broadcom](http://ubuntuforums.org/showthread.php?t=1390535&highlight=bcm4311+broadcom)
[http://ubuntuforums.org/showthread.php?t=896713&highlight=bcm4311+broadcom](http://ubuntuforums.org/showthread.php?t=896713&highlight=bcm4311+broadcom)

Shouldn't take more than 10 minutes.

LK

---

### Post by noixzx on 2010-03-10
Ubuntu 9.10 32bit
Laptop, 
Onboard.
[U]
I'll attach the OpenOffice file of my terminal results[/U] since this computer won't let me open it and copy the contents.

Keep in mind I cannot access ANY form of internet on my Ubuntu PC... I'm using a seperate PC right now and move files back and forth via flashdrive.

Maybe an older version would be a good idea?
I just want to get my wireless working ASAP.
Terminal confuses me and I have no idea what I'm doing, and believe me, if I knew anyone who had Linux experience I'd just have them do this for me. I've never felt so... dumb in my life.

I'll keep working on it, but with every failed attempt I become closer and closer to smashing my PC that is now good for nothing but tetris.

---

### Post by sandyd on 2010-03-10
alright...
32 bit.
```

sudo modprobe -r wl
sudo modprobe -r b44
sudo modprobe -r b43legacy
sudo modprobe -r b43
sudo apt-get install build-essential 
mkdir bcm-wl
cd bcm-wl
wget -c http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5.60.48.36.tar.gz
tar xvfz hybrid-portsrc-x86_32-v5.60.48.36.tar.gz
make
sudo make install
sudo modprobe wl

```

---

### Post by achase79 on 2010-03-10
This is how to get it to work [here]("http://ubuntuforums.org/showpost.php?p=7970798&postcount=8").

---

### Post by lkraemer on 2010-03-10
Did you perhaps remove the b43 and ssb modules?  b43 & ssb are not listed by lsmod,
and it should be.

You can try opening a Terminal Window and typing:
```

sudo modprobe b43
sudo modprobe ssb

```
to see if it loads.
Everything else looks as I would expect.
Next would be to download the Firmware, and copy it to the Ubuntu machine,
and unzip it.  Then copy the two folders b43 and b43 Legacy to /lib/firmware
Then Go to the top menu and Enable Hardware Drivers.

That should make your Wifi functional.  (Your LED might not change colors,
or might not turn Blue, but just leave the Wifi Button alone)

Or maybe you want to try what Carlee or others suggest.

It concerns me that b43 & ssb wasn't loaded by Ubuntu 9.10, as I have it running
on my Compaq and it was installed.

lk

---

### Post by noixzx on 2010-03-10
sudo modprobe b43
sudo modprobe ssb

I did this and nothing happened, whatsoever.

Also I keep getting:
FATAL: Module wl not found.

And it won't let me copy anything to lib/firmware, I tried. Why is this?

---

### Post by sandyd on 2010-03-10
> **noixzx said:**
> sudo modprobe b43
sudo modprobe ssb

I did this and nothing happened, whatsoever.

Also I keep getting:
FATAL: Module wl not found.

And it won't let me copy anything to lib/firmware, I tried. Why is this?
[B]You need root privelages to do so since it is part of the OS.
```

gksudo natilus
```
[/B]
.

---

### Post by lkraemer on 2010-03-10
Because you are copying in the root area where system commands can be
dangerous, you must have root priviledges.  ie. the sudo command.

If you open a Terminal Window and do the following commands, assuming you
have them unzipped at /Desktop/folder/b43 and /Desktop/folder/b43legacy:
```

cd /
cd /lib/firmware
cd /b43

```
You should get an error since b43 wasn't created.
if so do the next two commands, otherwise skip the next two.
```

sudo mkdir b43
sudo mkdir b43legacy
cd b43
sudo cp -pr ~/Desktop/folder/b43/* .
ls -alt
cd ..
cd b43legacy
sudo cp -pr ~/Desktop/folder/b43legacy/* .
ls -alt
cd /

```
that should copy all the files to the proper folders,
and you should see a file listing via the ls -alt command.

Then just enable the Hardware drivers.

Also issue the lsmod command and post that since you should have
loaded the modules b43 & ssb.

If you ran the commands carlee suggested and didn't get the new wl module
created then it is missing because it has been removed with the modprobe -r command.
For now try modprobe wl and wait on her commands until you finish trying this first.
One thing at a time.

lk

---

### Post by noixzx on 2010-03-11
Oooooookay, well, it still says I don't have permission.

I tried sudo md...
And it says sudo: md: command not found.
So I still can't move the files.

I went to the lib folder and it says I am not the owner, so I cannot change these permissions.
But I am the owner; there are no other users.

---

### Post by lkraemer on 2010-03-11
Well, I must have been asleep.

use mkdir like it is supposed to be.....Sorry!

By using the sudo command you have root power for that command.
lk

---

### Post by noixzx on 2010-03-11
It works up until this point:

cp: Cannot stat `/Desktop/folder/b43/*': No such file or directory.
I also tried:
/Desktop/b43/* .

Should I take the star out?

---

### Post by lkraemer on 2010-03-11
Man, I sure messed up bad.  use:
sudo cp -pr ~/Desktop/folder/b43/* .

Just realize Desktop and folder can be any name you have given for the
downloaded files.  Just substitute the correct path where your b43 & b43legacy files
are located.  The path might be /Desktop/folder1/folder2/folder3/b43

lk

---

### Post by Naggobot on 2010-03-11
I bump in by one message. Please lkraemer keep helping noixzx. 

I installed about a two weeks ago a laptop with b43 compatible hardware. My friend had exact same model working fine but after installation I could not find wireless drivers even though I was told that everything works out of the box. 

I reinstalled from start but the second time I had network and b43 worked out of the box. 
Later I found "some" related bugs listed at the launchpad. 

I have spent the last hour searching for the most relevant one for you but there are just too many reports cumulated on this subject over the years.  

Evidently the problem is that the some broadcom driver is not working directly from cd. If you install from the live cd you end up with no working wireless and no wireless driver but wireless will start working after system has been updated. (System -> administration -> update manager)

Now do not deviate from the path you have chosen with Ikraemer but if things do not work out in the end I suggest that you find wired network and reinstall. Things should work out of the box by that way, at least they have for me.  (Please someone correct me if I am wrong)



Some reports that may be related 

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/291271](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/291271)
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/218922](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/218922)

---

### Post by noixzx on 2010-03-12
Okay, after figuring that out (I really should've thought about it, but oh well, the clarification was helpful)
I get: cp: target `/.../ucode5.fw' is not a directory.
And then I look in the folder and it has copied nothing.

Thanks for helping, by the way, I feel like I'm making SOME progress.

---

### Post by noixzx on 2010-03-12
[EDIT: It sent my reply twice. Can't figure out how to delete.]

---

### Post by lkraemer on 2010-03-12
OK, it works but I don't know what you are doing wrong.
Open a Terminal Window and type:
```

cd /
cd /lib/firmware
pwd
ls -d b43*

```
You should see something like this, but for both subdirectories:
drwxr-xr-x  2 root root    4096 2010-03-12 16:45 b43

If you don't see folders named b43 and b43legacy in the listing, do the following
Otherwise skip the next two commands: (I am assuming that if you created one you created the second!)
```

sudo mkdir b43
sudo mkdir b43legacy

```
Continue:
```

cd b43
pwd
sudo cp -pr ~/Desktop/folder/b43/* .
ls -alt
cd ..
cd b43legacy
pwd
sudo cp -pr ~/Desktop/folder/b43legacy/* .
ls -alt
cd /
pwd
exit

```
Copy and paste each command to keep from having errors.
(The last character in the copy command is a PERIOD as in "." so
don't skip it.)
The ls -alt command should list a lot of *.fw files in b43 and b43legacy.
The ls -d b43* should list the directories that conatin b43??????????


Subdirectory b43 should contain:
-rw-r--r--  1 larry larry    18 2008-04-18 19:27 a0g0bsinitvals4.fw
-rw-r--r--  1 larry larry   158 2008-04-18 19:27 a0g0bsinitvals5.fw
-rw-r--r--  1 larry larry  2680 2008-04-18 19:27 a0g0initvals4.fw
-rw-r--r--  1 larry larry  1858 2008-04-18 19:27 a0g0initvals5.fw
-rw-r--r--  1 larry larry   158 2008-04-18 19:27 a0g1bsinitvals13.fw
-rw-r--r--  1 larry larry   158 2008-04-18 19:27 a0g1bsinitvals5.fw
-rw-r--r--  1 larry larry  2056 2008-04-18 19:27 a0g1initvals13.fw
-rw-r--r--  1 larry larry  1858 2008-04-18 19:27 a0g1initvals5.fw
-rw-r--r--  1 larry larry   158 2008-04-18 19:27 b0g0bsinitvals13.fw
-rw-r--r--  1 larry larry    18 2008-04-18 19:27 b0g0bsinitvals4.fw
-rw-r--r--  1 larry larry   158 2008-04-18 19:27 b0g0bsinitvals5.fw
-rw-r--r--  1 larry larry  2056 2008-04-18 19:27 b0g0initvals13.fw
-rw-r--r--  1 larry larry  2680 2008-04-18 19:27 b0g0initvals4.fw
-rw-r--r--  1 larry larry  1858 2008-04-18 19:27 b0g0initvals5.fw
-rw-r--r--  1 larry larry   158 2008-04-18 19:27 lp0bsinitvals13.fw
-rw-r--r--  1 larry larry  2052 2008-04-18 19:27 lp0initvals13.fw
-rw-r--r--  1 larry larry  1320 2008-04-18 19:27 pcm4.fw
-rw-r--r--  1 larry larry  1320 2008-04-18 19:27 pcm5.fw
-rw-r--r--  1 larry larry 26600 2008-04-18 19:27 ucode11.fw
-rw-r--r--  1 larry larry 24424 2008-04-18 19:27 ucode13.fw
-rw-r--r--  1 larry larry 20080 2008-04-18 19:27 ucode4.fw
-rw-r--r--  1 larry larry 22088 2008-04-18 19:27 ucode5.fw


Subdirectory b43legacy should contain:
-rw-r--r--  1 larry larry    18 2008-04-18 19:08 a0g0bsinitvals2.fw
-rw-r--r--  1 larry larry   158 2008-04-18 19:08 a0g0bsinitvals5.fw
-rw-r--r--  1 larry larry  2520 2008-04-18 19:08 a0g0initvals2.fw
-rw-r--r--  1 larry larry  1818 2008-04-18 19:08 a0g0initvals5.fw
-rw-r--r--  1 larry larry   158 2008-04-18 19:08 a0g1bsinitvals5.fw
-rw-r--r--  1 larry larry  1818 2008-04-18 19:08 a0g1initvals5.fw
-rw-r--r--  1 larry larry    18 2008-04-18 19:08 b0g0bsinitvals2.fw
-rw-r--r--  1 larry larry   158 2008-04-18 19:08 b0g0bsinitvals5.fw
-rw-r--r--  1 larry larry  2520 2008-04-18 19:08 b0g0initvals2.fw
-rw-r--r--  1 larry larry  1818 2008-04-18 19:08 b0g0initvals5.fw
-rw-r--r--  1 larry larry  1320 2008-04-18 19:08 pcm4.fw
-rw-r--r--  1 larry larry  1320 2008-04-18 19:08 pcm5.fw
-rw-r--r--  1 larry larry 21680 2008-04-18 19:08 ucode11.fw
-rw-r--r--  1 larry larry 16360 2008-04-18 19:08 ucode2.fw
-rw-r--r--  1 larry larry 20096 2008-04-18 19:08 ucode4.fw
-rw-r--r--  1 larry larry 22280 2008-04-18 19:08 ucode5.fw

It works as I just verified it again.

lk

---

### Post by noixzx on 2010-03-14
I did it exactly as you said, and the files are in the folders, but wireless still does not work and still cannot be activated.

---

### Post by lkraemer on 2010-03-14
What does this command show:
```

lsmod

```
Is b43 installed?

lk

---

### Post by noixzx on 2010-03-14
No, it isn't. What did I do wrong?

---

### Post by achase79 on 2010-03-14
what do you get when you sudo modprobe b43

---

### Post by noixzx on 2010-03-14
Let me put it this way: I'm replying from my Ubuntu laptop.

Thank you SOOOOOOOO much everyone, especially lkraemer.
I was worried there for about a week.

---

### Post by mcoleman44 on 2010-03-14
Nevermind, You have it!

---

### Post by seenthelite on 2010-03-15
Try using Mandriva 2010 it has better support  for Broadcom cards.

---

