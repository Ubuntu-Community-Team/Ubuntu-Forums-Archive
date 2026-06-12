---
title: "Installing ndiswrapper"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by omnigate on 2007-05-03
I'm new to Ubuntu and was trying to get my wireless network card running on my Dell Latitude D505. My understanding is that I would need to d'l and install an ndiswrapper, then pull the XP driver (NETw4x32.INF) over and run something like "ndiswrapper -i <drivername>.inf". 

Sounds easy enough and most of the topics I've researched on the Internet for the past 5-6 hours don't really cover installing ndiswrapper as apparently I'm the only one having the problem with it. 

I'm hoping someone out there can explain to me why I'm not getting how to install ndiswrapper. 

Here's what I've done so far. 

1. Installed Ubuntu 7.04 Desktop Edition onto my Dell Latitude D505 (Dual-boot with XP).
2. Went to ndiswrapper.sourceforge.net and downloaded ndiswrapper release 1.43
3. Went to Places - Computer - File System and found the file under home/omnigate called ndiswrapper-1.43.tar.gz. I extracted to the same folder and it created the directory 'ndiswrapper-1.43'. 
4. I read the INSTALL file and it mentions the prerequisite is to run the following command:
        ls /lib/modules/`uname -r`/build
It states 'should have at least 'include' directory and '.config' file.' I see the include directory but don't see the 'config' file. More importantly I don't see how to remedy this if it doesn't show what it's supposed to. 
5. So, flying blind, I run the following command thinking this will appease the kernel-header files God:
       sudo apt-get install linux-headers-2.6.20
fingers crossed, ENTER.  Seemed to take it...
6. Next I run 'sudo make uninstall', then 'sudo make', followed by 'make install'. 
7. So I think I'm ready to install the XP Wifi driver now. So I run:
        ndiswrapper -i NETw4x32.INF
Suddenly, I get:
       The program 'ndiswrapper' is currently not installed.  You can install it by typing:
       sudo apt-get install ndiswrapper-common
       bash: ndiswrapper: command not found
8. Doh! Jumped and completely missed the trampoline, luckily I was only jumping from the second story. 
9. Ah, but I see salvation. It's tells me to run 'sudo apt-get install ndiswrapper-common' to install ndiswrapper. Sweet, slam dunk, homerun. Let's type it in and get r done. I get:
       Reading package lists... Done
       Building dependency tree       
       Reading state information... Done
       ndiswrapper-common is already the newest version.
       0 upgraded, 0 newly installed, 0 to remove and 0 not 
(this is prob not the original message I got, but it's what I get now). So, back to step 7:
7b. I type in 'ndiswrapper -i NETw4x32.INF' and I still get the same error about ndiswrapper not being installed. 

I'm mystified. Not sure what to do. I tried uninstalling and reinstalling. No go, same messages, same dead ends. Can someone help me? Thanks. 

Sorry if it's a simple fix, I'm a vaccuum cleaner, I know.

---

### Post by Sloddy Shipper on 2007-05-03
Hi, i just had a similar problem getting a belkin card with rt2500 chipset to work on a default feisty fawn desktop installation. Here is how i got ndiswrapper installed and running.

It seems that the kernel module and sources are installed by default but not the user binaries. Hence your 'ndiswrapper is not installed' message. 

To solve this i manually uninstalled ndiswrapper following instruction found here[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/")

first find all the files using one or more of the following

~$ which ndiswrapper
~$ locate ndiswrapper
~$ find /lib/modules/$(uname -r) -name “ndiswrapper*” -print

Remove all the files found. For me this was the kernel module and sources only.

I downloaded the file ndiwrapper-1.42.tar.gz and followed the instructions here [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/")
to install.

where it says to ensure gcc and and associated packages are installed i read somewhere else to run, (probably sudo this actually)

 ~$ apt-get install build-essential

this should install a bunch of libraries and stuff from the installation CD, provided it is a registered package source,(which mine was not first time i tried for some reason?)

extract the ndiswrapper archive and install as follows

~$ tar -zxvf ndiswrapper-version.tar.gz
~$ cd ndiswrapper-version/driver/
~$ make distclean
~$ make
~$ cd ndiswrapper_version/
~$ sudo make install

that should do it. 

~$ ndiswrapper -l

should give some message other than 'ndiswrapper is not installed'

install your windows driver

~$ ndiswrapper -i filename.inf

i think you need a .inf .sys and .cat file in the same directory here.

~$ ndiswrapper -l

should tell you you have a driver installed and hardware present. if an alternate driver is indicated it means a native linux driver may be loaded. You must switch this off before loading ndiswrapper.

~$ sudo ifconfig ra0 down
~$ sudo modprobe -r drivername
 
assuming your wireless card is ra0 and the indicated alternate driver is drivername.
now

~$ sudo modprobe -i ndiswrapper
~$ dmesg | grep ndiswrapper

this last command should indicate whether or not the module had loaded properly.
or check using

~$ ndiswrapper -l
 or 
~$ lsmod | grep ndiswrapper

ok now try
~$ sudo iwconfig ra0 mode managed
~$ sudo ifconfig ra0 up
~$ sudo dhclient ra0


with luck your card will light up and connect to your accesspoint. If it lights up in a funny manner or just won't connect try disabling WEpor WPA on your acces point see if you can connect without encryption. Ummm i hopefully didn't forget anything crucial or get anything badly wrong. Hoe this helps you out.

---

### Post by DooZ on 2007-05-04
**I have exactly the same problem and I tried many solutions but they all failed with me. Sloddy Shipper's instruction didn't work 4 me. I think the problem is with this version of Ubuntu**

---

### Post by ronocdh on 2007-05-04
> **DooZ said:**
> **I have exactly the same problem and I tried many solutions but they all failed with me. Sloddy Shipper's instruction didn't work 4 me. I think the problem is with this version of Ubuntu**
I disagree. Looking at the variables, it's an infinitesimally small statistical chance that it's Feisty at fault; I mean, consider how many people are using Feisty (practically all of us) and how many are having this isolated problem (you). Not trying to be a jerk, just encouraging you not to give up!

Post more info and perhaps we can all help troubleshoot.

---

### Post by macabro22 on 2007-05-04
> Looking at the variables, it's an infinitesimally small statistical chance that it's Feisty at fault

Well, since since the wireless connection used to work fine in Edgy and he hasn't changed anything( *e.g.* ndiswrapper or windows drivers), then the Feisty variable is isolated. 

Actually, wireless malfunctioning in Feisty IS commonplace. Skepticism is a virtue. Check the topics yourself. You will be amazed.

---

### Post by Sloddy Shipper on 2007-05-05
yup don't give up Dooz, it was a battle but i now have my card working very well with WPA encryption. My AP is quite far away and my connection is now more reliable than it was in XP. Here are some more things which might help you.

I'll assume you have some sort of access point/router. In your routers wireless configuration turn off WEP and WPA, (you can get encryption to work later - first things first). Make sure it is set to broadcast the SSID. ( for me this is to uncheck the option marked 'hide SSID') Check that your routers DHCP server is enabled.

I took the advice of others to uninstall network manager. I used synaptic - search for network-manager and mark all the results for removal.

How far did you get with my previous post. Did ndiswrapper compile/install properly? Did you get ndiswrapper to load the driver - did you get the kernel module to load? An important step I forgot is this - 

Before the command

~$ sudo modprobe ndiswrapper

use this command

~$ sudo depmod -a

~$ dmesg | grep ndiswrapper

any errors? good the kernel module is loaded - to make sure

~$ lsmod | grep ndiswrapper

Now some other stuff i forgot which should help. Once you have the ndiswrapper module loaded run the following - 

~$ sudo ifconfig ra0 down
~$ sudo iwconfig ra0 ap <your access points' MAC address>
~$ sudo iwconfig ra0 channel <your wireless networks channel>
~$ sudo iwconfig ra0 essid <your ESSID>
~$ sudo iwconfig ra0 mode managed
~$ sudo ifconfig ra0 up
~$ sudo dhclient ra0

you should be able to find your ap MAC address and channel using -

~$ iwlist scan

or by checking the routers' configuration pages.

and check your card is on the right channel using - 
 
~$ iwlist chan

Does your card light up here, does the dhclient command go to sleep or assign your wireless card an IP address. Still no joy? Try this

~$ sudo /etc/init.d/networking restart
  
hopefully you can ping your router now and see webpages etc.

Good luck, post your /etc/networking/interfaces file if you still can't get this going.
Also check the ndiswrapper compatibility list to make sure you have the correct drivers for your exact card. My Belkin card had about six different versions of the same model number - drivers which worked in windows did not work in ndiswrapper.

---

### Post by bicball on 2007-05-11
after instaling ndiswrapper i was having the same problems as the other people when trying to get it to work with my driver's inf file: "command not found." i ended up doing something retarded and just formatted and reinstalled to start from scratch. this time i followed the instructions here. once i installed ndiswrapper and did "ndiswrapper -l" i got a "ls: /etc/ndiswrapper: No such file or directory"

what to do? (I'm running a brand new installation of kubuntu feisty)

this is exactly what i did in order:

sudo apt-get install build-essential
cd Desktop
tar -zxvf ndiswrapper-1.43.tar.gz
cd ndiswrapper-1.43/driver
make distclean
make
cd ..
make install
ndiswrapper -l
**ls: /etc/ndiswrapper: No such file or directory**

---

### Post by bicball on 2007-05-12
please?

---

### Post by Sloddy Shipper on 2007-05-12
hi, is that exactly what you entered, afraid i don't know much about the use of make , but that last step at least should be - 

~$ sudo make install

As for the change of directory before this step, see my post in this thread [http://http://ubuntuforums.org/showthread.php?t=433128]("http://http://ubuntuforums.org/showthread.php?t=433128")

Failing that you could try manually uninstalling ndiswrapper as described above and then reinstalling using the package manager.

Also if you get the message 'no such file or directory' instead of 'command not found' when running ndiswapper -l, that suggests you have installed the binary. Ndiswrapper stores its installed drivers in /etc/ndiswrapper. I don't know but perhaps the directory doesn't get created until you install a driver, did you try to install the driver?

~$ ndiswrapper -i filename.inf

be sure the .sys and .cat are in the same directory as the .inf. Hope this helps

---

### Post by bicball on 2007-05-14
i just tried "sudo make install" in both the ndiswrapper and ndiswrapper/driver directories and  i'm still getting the no such file or directory response

---

### Post by Tethtibis on 2007-06-27
search add/remove or synaptic, after enabling all repositories, for ndis, there is a gui frontend for ndis wrapper that works great.

---

