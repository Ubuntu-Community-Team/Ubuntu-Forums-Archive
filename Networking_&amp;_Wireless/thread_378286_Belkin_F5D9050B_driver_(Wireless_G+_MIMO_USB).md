---
title: "Belkin F5D9050B driver (Wireless G+ MIMO USB)"
date: 2007-03-07
forum: Networking &amp; Wireless
---

### Post by GeertPoels on 2007-03-07
Hello,

I just got a Belkin Wireless G+ MIMO USB controller, part F5D9050.
Though Belkin doesn't support Linux, I found out that this controller features a Ralink chip 2501/2601.
Ralink appears to have a driver. 
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

Has somebody already compiled and tried this driver ?
Or a similar very new Belkin USB model ?

Thanks,

Geert

[http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com) you can find drivers for older versions

---

### Post by bhutz on 2007-03-20
I have managed to download the driver ([http://prdownloads.sourceforge.net/rt2400/rt2570-1.1.0-b2.tar.gz?download]("http://prdownloads.sourceforge.net/rt2400/rt2570-1.1.0-b2.tar.gz?download")), compile it and install it using the instructions in the README file.

	a. $tar -xvzf rt2570-x.x.x.tar.gz
	go to "./rt2570-x.x.x/Module" directory.

	b. $make # compile driver source code

	c. $make install # installs kernel module driver

	d. $modprobe rt2570

I type 'lsmod | grep rt and get...

usbcore 134912    4    rt2570, ndiswrapper, ohci_hcd

Which I guess my driver is availble but doesn't look like it communicating because I plug the USB adapter in and nothing.

I am using this page as a guide and I'm on "3.2.4. Check driver", the driver seems to be there but iwconfig doesn't display the interface....using a previous adapter I saw wlan0 but can't remember how I added that interface, if I even did, lol

Any ideas how to move forward with this one guys/gals?

---

### Post by bhutz on 2007-03-20
Hey GeertPoels...managed to get my USB F5D9050 working, and so far it's seems to be working well!

The key for me was to make and install this version [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) (without errors), then use 

sudo modprobe rt73

One of the commands (I think it was install, added an alias to /etc/modprobe.conf) which if worked correctly should be shown when you do 'iwconfig'

Then all I had to do was go to 'system > admin > networking' and then configure and enable my device!

I'll give you a hand tomorrow (it's been a long evening) if I can but new to Ubuntu and Linux, so you might have to bare with me :) I found your post on the rt2x00 forum so it's the least I can do :)

---

### Post by GeertPoels on 2007-03-21
Hello bhutz,

I'm very happy everything works !!
I'm as eager as you to get this baby up and running.

There seems to be something wrong with my kernel sources folder.

t73-cvs-2007031913/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-11-generic'
make[1]: *** No rule to make target `Mimo'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-11-generic'
rt73.ko failed to build!
make: *** [module] Error 1

I've already downloaded a bunch of tools, compilers, kernel sources, kernel dev kit, etc. .
Maybe some link is missing.
It puzzles me :confused: 

Geert

---

### Post by GeertPoels on 2007-03-21
That's exactly the version I've been trying as well.

---

### Post by bhutz on 2007-03-21
I will try and find the post that I followed which suggested how to upgrade compiler and a bunch of other things I'm not yet to sure what they mean...but basically means compiling gets to the end.

Is there a way to see a history of the things I have installed via apt-get just in case I can't find this post for a while? That way I can tell you what I installed so my compiler works.

---

### Post by GeertPoels on 2007-03-21
Would this help ?
[http://ubuntuforums.org/showthread.php?t=36719](http://ubuntuforums.org/showthread.php?t=36719)

---

### Post by bhutz on 2007-03-21
I checked my history in firefox and I found this site... ...unfortunately I can't confirm if it's the correct one yet because site is down and for some reason so is the cached version in google???

Anyway, these are the commands that I executed that meant I was able to compile things a lot better. 

I'm sure these are fine to run but bare in mind I've just picked up Linux so if your machine has got important stuff on it ya might want to double check with someone more experienced.

[B]sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install gcc
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev[/B]

Then try and compile that rt73 driver see if it works this time round.

---

### Post by bhutz on 2007-03-21
Cool, I will double check that too

---

### Post by GeertPoels on 2007-03-21
All of those, I had.
I re-installed most of them :) 
Error remains the same... :confused: 

What do you have in /usr/src ?

I have :

drwxr-xr-x 19 root   root        4096 2007-03-06 22:35 linux-headers-2.6.17-11
drwxr-xr-x  4 root   root        4096 2007-03-14 22:16 linux-headers-2.6.17-11-generic
drwxr-xr-x 22 root   root        4096 2007-02-01 20:56 linux-source-2.6.17
-rw-r--r--  1 root   root   264990720 2007-02-01 20:57 linux-source-2.6.17.tar
-rw-r--r--  1 root   root    45963086 2007-02-01 20:57 linux-source-2.6.17.tar.bz2

---

### Post by bhutz on 2007-03-21
I checked my terminal history...
[B]
sudo gedit /home/carlton/.bash_history[/B]

and found some other commands that I tried around the same time...

**sudo apt-get remove wpasupplican**t 
and
**sudo apt-get install wireless-tools**

I also found these commands
[B]sudo apt-get install build-essential 
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-headers-`uname -r` /lib/modules/`uname -r`/build[/B]

in that directory I have...

[B]drwxr-xr-x 19 root root 4096 2007-03-17 23:03 linux-headers-2.6.17-10
drwxr-xr-x  4 root root 4096 2007-03-17 23:04 linux-headers-2.6.17-10-generic
drwxr-xr-x 19 root root 4096 2007-03-17 23:04 linux-headers-2.6.17-11
drwxr-xr-x  4 root root 4096 2007-03-17 23:35 linux-headers-2.6.17-11-generic[/B]

---

### Post by GeertPoels on 2007-03-21
In 
  /lib/modules/2.6.17-11-generic
 I've indeed got a link to
lrwxrwxrwx  1 root root     40 2007-03-06 22:35 build -> /usr/src/linux-headers-2.6.17-11-generic


That's often mentioned on the rt2x00 site as well.

---

### Post by bhutz on 2007-03-21
I have no idea why it might not compile then...I just assumed that upgrading gcc and things related to the compilation step would have sorted it out...is that the part you are still stuck on?

Hopefully some body else here might be able to help you out with that one...but I can say this USB definitely works and works so much better than the F5D7050 that I tried before.

---

### Post by GeertPoels on 2007-03-21
Me too...

Thanks for checking things out.
Glad to hear it works on your machine.
As soon as can compile, I know beauty is ahead of me ;-)

---

### Post by GeertPoels on 2007-03-22
You'll never believe it.
I got it compiled...

Wanna know the trick ?
Remove the space from the folder name of where I had put the driver...
(read this trick somewhere)

How did you enable the device ?
You can add rt73 to /etc/modules

And 
auto wlan0
iface wlan0 inet dhcp

in /etc/network/interfaces

But there's also a line added to modprobe.conf ?

Did you check ?
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT73?highlight=%28WifiDocs%2FDriver%29)

---

### Post by bhutz on 2007-03-23
Good news!

In modprobe.conf I have

[B]alias raus0 rt2570
alias ra0 rt73[/B]

I don't think I need the first line because that relates to old USB I was using.
Although when I do 'iwconfig' I can see rausb0 connected to my network but no mention of ra0? Confusing :(

Oh and something simple, I went to 

System > Admin > Networking, and jus configured and enabled my device....wish it had all been that easy from the start, lol

---

### Post by somumala on 2007-10-21
i need this driver 
you'll have?
thanks
kisses 
from alba

---

### Post by Dr. Computer on 2007-11-16
Has anyone gotten this wifi card to work?

---

### Post by GeertPoels on 2007-11-17
Yes, it works on my machine, Ubuntu 7.10.
Get the latest sources here :
[http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)

Follow the readme (sometimes you need you use 'sudo' in front).
For very technical questions, contact this [forum]("http://rt2x00.serialmonkey.com/phpBB2/viewforum.php?f=8").

A topic which you might want to read :
[http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4121](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=4121)

---

