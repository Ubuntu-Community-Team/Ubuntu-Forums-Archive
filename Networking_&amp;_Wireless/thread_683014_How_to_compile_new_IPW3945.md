---
title: "How to compile new IPW3945"
date: 2008-01-30
forum: Networking &amp; Wireless
---

### Post by duxi on 2008-01-30
hey,

i'm a really noob, in linux, so i've got a question to you. i want to compile my IPW3945 driver to a never self-compiled version...

in the original driver, there is the monitor mode disabled. so a deleted the "#" in the makefile. like this:

```
# If you are not interested in using monitor mode, simply comment out:
#
# NOTE:  If you have problems compiling due to IW_MODE_MONITOR not being
#        defined then you need to update the wireless extension version
#	 installed in your kernel, or comment this line out.
CONFIG_IPW3945_MONITOR=y

# If you are interested in using radiotap headers in monitor mode,
# simply uncomment:
#
# NOTE:  To use RADIOTAP you must also enable MONITOR above.
CONFIG_IEEE80211_RADIOTAP=y

# The above monitor mode provides standard monitor mode.  The following
# will create a new interface (named raw%d) which will be sent all
# 802.11 frames received on the interface
#
# NOTE:  To use PROMISCUOUS you must also enable MONITOR above.
CONFIG_IPW3945_PROMISCUOUS=y

# The following, if enabled, will add a sysfs entry 'rx' that raw
# 802.11 radiotap formatted packets can be written to.  Those packets
# will be passed to the driver as if they were received from over the
# air.  This is useful in debugging features not supported by your AP.
CONFIG_IPW3945_SIM_RX=y
```

so this file i would like to instal...but how can i do this?

i tried it a few days ago, and killed my ieee80211 driver...but already working...

so could someone out there help me?

nice greez

ps: in attachment i uploaded the whole folder.

---

### Post by Pandemic187 on 2008-01-30
For what reason are you trying to compile this? My wireless adapter uses ipw3945 and I never have to compile anything to get it working...so are you trying to compile it just for the sake of compiling?

---

### Post by chili555 on 2008-01-30
What does the INSTALL file say you should do?

---

### Post by duxi on 2008-01-31
i want to turn on the monitor mode, which is disabled in the original driver...

the card it-self works...got no problems...but i want to turn on with:```
 iwconfig eth1 mode monitor
``` this mode...

when i say ```
./load
```

it says: "synatx error or not expected error on line 5"

what do you mean?, what does the install file say`?

---

### Post by chili555 on 2008-01-31
> i would like to instal...but how can i do this?The INSTALL file, created when you extracted the tar.gz, says, in part:> 2. QUICK INSTALL STEPS
-----------------------------------------------

The following provides steps that can be used to manually install and 
load the driver.  

Lines beginning with % can be run as any user.  Lines beginning with # 
must be run as root.

First, we build and install the ieee80211 subsystem.  You can obtain 
the latest ieee80211 subsystem from [http://ieee80211.sf.net](http://ieee80211.sf.net).  We 
recommend version 1.1.12 or newer:

	% tar xzvf ieee80211-1.2.16.tgz
	% cd ieee80211-1.2.16
	% make 
	# make install   <--- You may need to be root
	% cd ..

If you encounter problems with the above, you may need to install the 
ieee80211 sources into your kernel and then build it as part of your 
kernel image.  See the INSTALL and README.ieee80211 files provided in 
the ieee80211 subsystem package for more information.My point is that a README or INSTALL file is usually included to tell you how to install software from a tar.gz.

By the way, my ipw3945 *does* go into monitor mode. This is a very complex install you are undertaking. Are you sure you want and need to do so?

---

### Post by navaburo on 2008-03-20
Ok, so I almost have this working. I will try more tomorrow sometime. Here is a PRELIMINARY howto for enabling promiscuous mode on the ipw3945. I am working on an hp nw8440 laptop.

Progress:
1) I can connect to access points in managed mode and use the card normally (except that the driver doesnt autoload (yet))
2) I can capture packets in managed mode, but only ones addressed to me or broadcast ;(. Note that this is with Wireshark and the "Capture Packets in Promiscuous Mode" box is checked.
3) I can enable monitor mode with iwconfig iface mode monitor, but then Wireshark won't capture, giving the error "EN10MB is not one of the DLTs supported by this device).

So, if anyone knows how to fix this HELP! And we can get quite a few people online promiscuously.





PRELIMINARY howto:

To enable ipw3945 promiscuous mode on Ubuntu Gutsy (and probably others), do the following:

```


#get to a temporary directory
cd
mkdir tmp-ipwstuff
cd tmp-ipwstuff

#download and untar the sourcecode for the dependancy
wget http://prdownloads.sourceforge.net/ieee80211/ieee80211-1.2.18.tgz?download
tar -xzvf ieee80211-1.2.18.tgz
cd ieee80211-1.2.18

#NOTE: the following command may prompt you, if so
# hit enter for the default options in all cases.
sudo make SHELL=/bin/bash
sudo make install
cd ..

#download and untar a recent version of the driver source code
wget http://prdownloads.sourceforge.net/ipw3945/ipw3945-1.2.2.tgz
tar -xzvf ipw3945-1.2.2.tgz 
cd ipw3945-1.2.2/

#use an editor to make some changes to the Makefile
gedit Makefile


```

Now uncomment four lines which appear near the beginning of the file. That is, remove the # from the beginning of the line.
These four lines are:

CONFIG_IPW3945_MONITOR=y

CONFIG_IPW3945_RADIOTAP=y

CONFIG_IPW3945_PROMISCUOUS=y

CONFIG_IPW3945_SIM_RX=y

Then, somewhere amoung the lines add the following:

IEEE80211_IGNORE_DUPLICATE=y

Save and exit from the editor.

```


#build the driver
make SHELL=/bin/bash

#now we need to get/install the new device firmware:
wget http://bughost.org/ipw3945/ucode/ipw3945-ucode-1.14.2.tgz .
tar -xzvf ipw3945-ucode-1.14.2.tgz
cd ipw3945-ucode-1.14.2.tgz
cp ipw3945.ucode /lib/firmware/
cd ..

#now get the regulatory daemon:
wget http://bughost.org/ipw3945/daemon/ipw3945d-1.7.22.tgz
tar -xzvf ipw3945d-1.7.22.tgz
cd ipw3945d-1.7.22

#on 32-bit systems do this:
sudo cp x86/ipw3945d /sbin
#on 64-bit systems do this:
sudo cp x86_64/ipw3945d /sbin

#ok, now we can try it out
cd..


```

edit the first line of both the "load" and "unload" files to read:

#!/bin/bash

instead of

#!/bin/sh

for some reason the script authors used the full bash grammer but specified sh :(

```


#NOTE: you should now be in the ipw3945-1.2.2 directory

#test out the driver
sudo ./load debug=0

#some non-error stuff should come up

#now, test to see if it worked:
iwconfig

#if iwconfig says "unassociated" at all then it worked!


```

---

### Post by duxi on 2008-03-22
thx dude, very well explained ;)

works :-)

---

