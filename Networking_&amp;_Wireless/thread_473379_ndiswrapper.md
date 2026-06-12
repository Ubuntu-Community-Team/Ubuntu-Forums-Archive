---
title: "ndiswrapper"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by soad2237 on 2007-06-14
I am an absolute beginner with linux. My wireless card (usr5410) will not work so I attempted to read through the forums and figure out how to fix it. I tried the  ```
cd / lib/firmware/<kernal>/...
``` code and changed some stuff..Not a clue what it did but that didn't work. So then I tried to install ndiswrapper and thats where I'm stuck. Not a clue what I'm doing no matter how many tutorials I read on how to install. I keep getting errors including "Implicit declaration of function" errors and "... Undeclared" errors during the install. Also recieved a "cannot create directory: permission denied" error. Then I tried installing ndiswrapper from the Ubuntu cd and when I went to use it it said the command doesn't exist.

Please help. I can't get this card running correctly.
Thanks.

By the way I'm running Ubuntu Fiesty Fawn 7.04

---

### Post by kevdog on 2007-06-14
You are going to have to first tell me more about the wireless card.  Using command line (I hope you know how to do this), post results of:
lspci
lspci -n


Also if you have specific name of wireless card (linksys,belkin,etc) and model that would be great!

---

### Post by soad2237 on 2007-06-14
Right now the wireless card isn't the huge problem. I'm still trying to figure out how to install ndiswrapper and have been trying on and off for 2 days now. It looks like it has been installed but when I go to use it it doesn't seem to be there. Unless I'm using it wrong? Not a clue how to work this. There is no command called ndiswrapper when I try to type that. I'm so confused.

---

### Post by soad2237 on 2007-06-14
When I go to "make" ndiswrapper it runs so smoothly for a few seconds and then BOOM. error error error error error error warning warning warning warning undeclared inplicit declaration error 1 error 2. There were atleast 50 errors...no exaggeration. why...All I want to do is install the drivers for my card. Windows is so much easier. lol :(

---

### Post by kevdog on 2007-06-14
Ok you are not giving me much to work with.  You need to be more specific about what you did and the errors you are getting.

First Im going to guess that you downloaded ndiswrapper.tar.gz file from the sourceforge website.
It sounds like you were able to unzip/untar the file.  You than tried to compile the file with the make statement but got tons of errors.

Likey you do no have the build-essentials package installed -- this is a package you must have that allows you to compile other programs.  Without this you can not compile source files, and you will never get anything compiled and working.

ndiswrapper is not installed -- that is the reason why when you type ndiswrapper on the command line you dont get anything.

You can get the build-essentials package from the ubuntu cd (if you choose).  Place CD in drive.  
At command line:
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential

Once this package is installed you can then re-enter into the directory structure where you unzipped/untarred the ndiswrapper source files. Then at command prompt
make distclean
make

If you get no errors (hopefully you wont - now install the package):
sudo make install

Check if it was installed properly:
ndiswrapper -v

A version number should print.

That is how you install ndiswrapper (well actually compile and install from source files!)

If you need more help with driver installation after this step let me know -- As of yet we havent done anything with your wireless card drivers.  Ndiswrapper is a program that "wraps itself" around windows drivers making them appear like linux drivers to the operating system.  The next step is to find the correct version of the card drivers compatible with the card and ndiswrapper, then "wrap" the driver, install the "ndiswrapper-driver" combination, make a few configuration file changes, reboot computer, and then enjoy!!!

---

### Post by NfF on 2007-06-14
hey kev,

thx for the guide! ive been looking for it for days
well..i havent tried yet..but im not sure whether my ubuntu 7.04 has ndiswrapper.

---

### Post by kevdog on 2007-06-14
Unless you have installed ndiswrapper through package repositories -- synaptic, apt-get, aptitude, adept, etc. The default ubuntu installation does not come with ndiswrapper.  In fact ndiswrapper is not included on the Live/Alternate Ubuntu CD.  Its highly unlikely you have ndiswrapper on your installation unless you have established an internet connection somewhere.

Let me know if you need any more help.
Once you figure out the process for this whole thing, you could install your wireless connection in about 3-5 minutes.  The first time through however is very painful, since oftentimes the user has never compiled anything before, doesnt have the compiling tools even installed, doesnt know sequence how to install ndiswrapper into kernel as driver, and most likely doesnt have wireless driver for card (at least one that is compatible with both card and ndiswrapper).  Once you do everything, you'll say, OK I understand everything now!  I could do that again fairly easy.

---

### Post by Evan394 on 2007-06-15
Kev,

I'll second that thank you.  I'm pretty green at this stuff and it was difficult to locate a guide/how-to that included the syntax.

By the way... could you suggest any resources (in addition to this forum) where a noob could find some shell tutorial, I'm really struggling with the shell.  I get the concept, but I need some help with the syntax.

thanks!!

---

### Post by kevdog on 2007-06-15
Were you able to install ndiswrapper??

As far as a shell tutorial on basic commands Ive read many but do not remember any off the top of my head.  I just started using unix about 3 months ago, so the commands at one time were very foreign to me.  I really just found that the more jams I ran into the more I learned about different commands.  A lot of the commands listed above are not something you are going to learn in a tutorial.  You are just going to pick them up by doing.

You do need to know basic commands like:
cd, ls, mkdir, rm

Hang in there -- its very hard at first, but with about a month to month and a half under your belt, it will become very easy.

A lot of things we are doing to install ndiswrapper are advanced for beginner, call this your first big learning experience.

---

### Post by Evan394 on 2007-06-15
Hooray!

I WAS able to install ndiswrapper.  I see what you mean about the just doing to learn.  thanks again for your help.  I'm just going to be banging it out on this thing for a while to figure out what I can.

---

### Post by Griffiss on 2007-06-15
Hey kev

After trouble with wireless since upgrading to feisty, I've been following your walkthroughs on a couple of threads. I may have found a problem: 

ndiswrapper -v gives this output:
```
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 
```
which looks not good. 

the problems I've been having are wireless never being connected at startup and frequently dropping out after inactivity, then not connecting for a long time. If you have time to offer a solution that would be great.

griff

---

### Post by kevdog on 2007-06-15
That is correct there is a problem with ndiswrapper.  You probably need to start at the beginning of this thread.

Starting at the beginning of this thread just try the steps

It should get ndiswrapper installed so at least when you check the version statement, there should be nothing hinting of a problem or error.

Let me know if I can help you

---

### Post by Griffiss on 2007-06-15
Do I need to remove the ndiwrapper that I do have before following the insructions in this thread, like unload the module or something?

Thanks for helping kev

---

### Post by kevdog on 2007-06-15
simply compiling and reinstalling ndiswrapper will not change that.  If we can successfully compile and install ndiswrapper, we can then go about uninstalling the driver, etc.

Im just trying to get something up and running first
We will deal with the other garbage later.

---

### Post by Griffiss on 2007-06-15
ok, i've done that. now ndiswrapper -v gives following output
```
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net

```

I've had a look through that site and can't find instructions for how to remedy the situation.

---

### Post by kevdog on 2007-06-15
Ok, maybe you can not install over the older stuff.

Here are the instructions right from the ndiswrapper site:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,uninstall/)

Follow whatever they recommend to the letter -- Ive messed up once uninstalling because I skipped a few things they said (by accident).

---

### Post by Griffiss on 2007-06-15
I've had a look at that page. puzzled by this:

'uninstall programs and modules installed with make uninstall in ndiswrapper directory'

which do you reckon is the ndiswrapper directory? 

I've done locate ndiswrapper and there's ndiswrapper all over the place! Am I supposed to delete *everything* just by going to that directory and doing rm command?

---

### Post by kevdog on 2007-06-15
When using the locate command, ignore the crap in the source directory where you compiled all the files.

Here's the most important steps:

      Make sure you unload your current ndiswrapper module with ‘ sudo modprobe -r ndiswrapper’ 

    *
      You need to remove the user space tools ndiswrapper (in

/usr/sbin) and loadndisdriver (in /sbin), and kernel module ndiswrapper (in /lib/modules/`uname -r`/misc)

remember to remove these files its sudo rm filename.

Once these files are removed, go back into where your sourcefiles are located
make distclean
make
sudo make install

Then check the ndiswrapper -v command.

So basically you need to remove three files.
uname -r is your kernel number
Type uname -r on command line and it will give you the number.
Or simple just do the following:
sudo rm /usr/sbin/ndiswrapper
sudo rm /sbin/loadndisdriver
sudo rm /lib/modules/`uname -r`/misc/ndiswrapper.ko  

Check on the last statement.  Im not in front of my computer.  It might be called something different than ndiswrapper.ko

---

### Post by Griffiss on 2007-06-16
I reinstalled ndiswrapper and that seems fine now, but the network keeps cutting out, so I guess it wasn't the whole problem :(

seems to be a bit better though. cheers for your help

---

### Post by kevdog on 2007-06-16
Few things to try if it keeps cutting out

#1. Make sure you have right driver installed (just double check -- sometimes on ndiswrapper site they list two drivers for a single card -- may want to try other driver if there is one)

#2. Setup /etc/network/interfaces file manually -- Ive found at least in may case that if I set a static IP address (I know this is possible at home but not with a public router), that my connection is far more reliable than depending on dhcp.  

#3. Sorry dont have any more thoughts

---

### Post by Griffiss on 2007-06-16
1. The driver is off the cd that came with the card. worked fine with edgy - might it be out-dated?

2. How do I set a static IP? just replace 'dhcp' with the IP? and how do I know which IP to set it to?

---

### Post by kevdog on 2007-06-16
Im not associated with Ubuntu in any means, but Im getting the sense there are problems with wireless with Feisty in comparison to Edgy.  Just a suspicion based on the massive number of problems people are reporting.

Anyway, I would try to install drivers referenced from the ndiswrapper website.  Possibly they are the same.  I downloaded the zip archive for your card and the inf,sys files are dated -- April and February 2005 -- so they are not that new.  If your drivers creation date is the same then I would say that is a waste.

Here is an example of how to set a static IP up in the /etc/network/interfaces file.  This is just an example:

auto wlan0
iface wlan0 inet static
address 192.168.1.5
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 68.87.85.98 68.87.69.146 192.168.1.1

If messing wtih your interfaces file, make sure to make a copy of the working version for if some reason something screws up, you can just restore the old one!

#4. Last suggestion.  By default Ubuntu uses network-manager to manage its network controllers.  You could experiment with wicd or wi-fi radar -- two different packages.  Ive tried wicd in feisty but couldnt make it work.  Possibly some other posts could help you.  Just a suggestion.

---

### Post by abrand888 on 2007-06-17
Hi,

I followed your instructions up to untarring ndiswrapper but I copied the ndiswrapper to my desktop and I need to know how to navigate to the desktop where I copied the file. I entered cd ~/desktop and got nowehere.

Maybe I should copy ndiswrapper to another location and then try installing it.

I will appreciate help in getting this to work if possible.
Arthue

---

### Post by abrand888 on 2007-06-17
Hi,

In addition to having ndiswrapper on my desktop, I have the Atheros files and inf files also on my desktop. I am not using a router. I live right next to a public hotspot and in Windows, my antenna is connected to the lan driver and I pick up a great signal. I would like to get ndiswrapper working so it will use the Windows driver and work the same way.

Will Ubuntu allow one to detect automatically a IP address like Windows.

Thanks.

Arthur

---

### Post by kevdog on 2007-06-17
Its cd ~/Desktop

---

### Post by abrand888 on 2007-06-17
If I type cd ~/desktop which I believe I did, I can't see ndiswrapper which is on my desktop.

I typed ls and it sees ndiswrapper but when I type tar-zxvf ndiswrapper-1.45.tar.gz it states cannot open : no such file or directory.
error is not recoverable exiting
child returned status 2
error exit delayed from previous errors

---

### Post by kevdog on 2007-06-17
Desktop not desktop

---

### Post by Erky on 2007-06-20
Hello,
   I'm using a Linksys WUSB54G Ver. 1, and I download the new driver and added it to ndiswrapper's list of drivers, but it tells me it's invlaid. Can you tell me what I did wrong?

---

### Post by kevdog on 2007-06-21
Erky 

Please post 
lsusb


Im trying to verify if this is your card:
   1.
      Card: Linksys WUSB54Gv1, 802.11b/g, USB 2.0

    *
      Chipset: Prism54
    *
      usbid: 5041:2234
    *
      Driver: Linksys Windows XP driver [http://www.linksys.com/download/default.asp](http://www.linksys.com/download/default.asp)
    *
      Other: Works smoothly, of course ;) - this is the device the USB extension was originally developed for. WEP is running, WPA is supported using wpa_supplicant 0.2.5. No problems with both 1.1 and 2.0 host controllers. As with many other USB devices, no success with 2.4 kernels so far. Try to use 2.6.7 or better. There is a native driver for Prism54 that is working on USB support. View its status at Prism54.org
    *
      Other: Works with latest Windows Driver from linksys.com. No success with 2.4 kernels (even with 8k stack). Works with kernel 2.6.11 and 2.6.12. Works smoothly with 2.6.12 and ndiswrapper 1.14.
    *
      Other: Driver from Linksys is old. Alternate driver for Sitecom WL-125 driver at [http://www.sitecom.com/showdownload.php?id=1998](http://www.sitecom.com/showdownload.php?id=1998) is newer version. With this, the card doesn’t disconnect. Tested with card with usbid 1915:2234.

---

### Post by Erky on 2007-06-21
It comes up as Bus 004 Device 002:ID 5041:2234 Linksys (?) WUSB54G 802.11g Adapter.

---

### Post by kevdog on 2007-06-21
Ok great, now lets check your installation of ndiswrapper

Please post output of following:
ndiswrapper -v 
ndiswrapper -l
sudo modprobe -l ndiswrapper

---

### Post by Erky on 2007-06-21
ndiswrapper -v:
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:         /lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko
version:          1.47
vermagic:        2.6.20-15 generic SMP mod_unload 586

ndiswrapper -l:
wlanuig:      invalid driver!
wusb54g:   invalid driver!

sudo modprobe -l ndiswrapper:
/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko

---

### Post by abrand888 on 2007-06-21
Erky,

I have a unusual setup. I am in a hot spot and am using a Engenius EUB-362 EXT wireless usb lan driver module that is connected to a yagi antenna. In Windows, the output of the EUB-362 EXT goes to my usb port and I am picking up three good signals. I got the driver loaded in terminal mode but that is all. The Engenius module is using a Atheros 5523 chip and I have all the files in a folder on my desktop. I have the inf and sys files in the DriverFolder and I would like to use Ubuntu to use the same signal as I use in Windows.

Please list me the steps I need to see it working. I already compiled the build-essentials and I into three weeks having failuse.

Thanks

Arthur

---

### Post by kevdog on 2007-06-22
Ok -- 

ndiswrapper seems to be compiled and installed appropriately.  Its true that you dont seem to have the correct driver for your card.  

First lets remove both of the bad drivers you have installed
Go into /etc/ndiswrapper, then type
rm -R *

That should remove all the drivers.   If you do a
ndiswrapper after this, nothing should be listed.

The second issue to to find a correct driver for you.  Try this link
[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&packedargs=sku%3D1115416827517&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377527517B03&displaypage=download#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1166859843775&packedargs=sku%3D1115416827517&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=4377527517B03&displaypage=download#versiondetail)

The file is a self extracting winzip executable.  You might have to extract this on a windows machine.  You basically want the XP drivers.  They are called
WUSB54G.inf
WUSB20XP.sys

Try installing these drivers.  Place both files in the same folder on Ubuntu and then try
sudo ndiswrapper -i WUSB54G.inf

Hopefully when you do a 
ndiswrapper -l
It will not say driver is incorrect.

---

### Post by abrand888 on 2007-06-22
Kevdog,

I am not sure where ndiswrapper is. I originally copied the ndiswrapper to my desktop and also the drivers for my engenius lan USB device to the desktop. Should they be removed from the desktop ? I was able to navigate in terminal mode and get to the desktop by typing cd  ~/Desktop.

I di compile Ndiswrapper so it is current. I am using 1.45 version.  I see different versions for Linksys. Ver 4 and ver 2. Which one should I try using ?

Perhaps I should start from the beginning and will appreciate the steps I should do so I can send you the details as I record them in terminal mode.

Thanks for getting back to me 

Arthur

---

### Post by kevdog on 2007-06-22
You do not need to reinstall ndiswrapper.  It is correctly installed from the information you gave me.

You do however need to find the appropriate driver.  You may have the correct driver on your desktop, you may not.  The link I posted above was simply the driver directly from the linksys website for version 1 of your usb device.

Lets do the following right now.  Lets totally uninstall the drivers from ndiswrapper.
cd /etc/ndiswrapper
sudo rm -R *

Next lets make a directory for drivers.
cd ~
mkdir wireless_drivers

Next go to the linksys website link I posted in my last post, download the driver file and place it in
~/wireless_drivers

Tell me what you have at this point.  Its very possible that the file you are downloading you already have, but I really dont know the name of the driver files you have at this point so in effect we are kind of starting from scratch at this step.

---

### Post by abrand888 on 2007-06-22
Hi,

I am not at my computer now. It is in my house. When I get back, I will try it.  Would you like for me to upload the drivers I have for the EUB-362 EXT unit or stay with just the Linksys drivers. I downloaded version 2 and 4. Should I download verion 1 and use just version 1 ?

Fyi, our EUB-362 EXT is using Atheros AR5005UG chipset (RoC AR2112 / Baseband AR5523). I got this information from EngeniusTech.com Hope this might be of interest to you. There are four files in the Driveerfiles directory on my desktop.

Arthur

---

### Post by kevdog on 2007-06-22
abrand

Sorry I was messing up your post with Erkys.  I guess it helps actually to read the name of the poster :)


Can you post the results of:
lsusb

Thanks.

---

### Post by Erky on 2007-06-22
Kevdog,

I did everything you said. I got rid of all the invlaid drivers, and I placed the two correct drivers in the same folder. But, when I did sudo ndiswrapper -i WUSB54G.inf, this came up:

installing wusb54g...
couldn't open WUSB54G.inf: No such file or directory at /usr/sbin/ndiswrapper line 217

---

### Post by kevdog on 2007-06-22
abrand888

Your device, EUB-362 EXT, requires the madwifi driver rather than ndiswrapper.  Here is the documentation: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

Ive never setup the madwifi driver, however in many respects it is very similar to ndiswrapper.

Let me know if I can help you.

---

### Post by kevdog on 2007-06-22
Erky

Ive seen this dang error before, and when I try to install the exact same driver on my computer, I dont get this error.  

You compiled ndiswrapper from source, so I dont see why yours would be different than mine.  

Do the following:
cd /etc/ndiswrapper
ls

And post the output.  I think it will be one directory name.
Then 
cd *****  <-substitute directory name here

And then post the following
ls

I just want to see something.

---

### Post by abrand888 on 2007-06-22
Kevdog,

I will try and follow their instructions. Should I remove completely all references to EUB-362 and ndiswrapper or might it be easier to reinstall Ubuntu and start from square one.

Do I type sudo bash to get into root ?

Do I have to make a Madwifi directory ?  How do I go about making a madwifi directory ? Should I unpack the downloaded file in the new Madwifi directory ?

Where it states in the instructions "Loading the MadWifi Module "  modprobe  ath_pci should I substitute modprobe ath_usb ?

What does this mean "If your svn snapshot is more recent than the 23rd of January 2006 " mean ?

If I am lucky and get to Scanning Access Points what do I do since I am in a dead center point of public hotspots ?

I guess if I am lucky in all the steps, then MadWifi will work automatically like it did in Windows obtaining automatically a access point and a DNS Server ?

When I am in terminal mode, and root moder, and get everything working properly, will all this information be written to my hard drive so I won't have to go thru all these steps when I boot up Ubuntu next time ?

Thanks

Arthur

---

### Post by kevdog on 2007-06-22
abrand

First you do not need to reinstall Ubuntu -- unless you want to go through all that pain (and like it!)

In fact if you want, you can leave ndiswrapper installed as long as its not inserted into the kernel.
If you do a 
sudo modprobe -l | grep ndiswrapper

And nothing comes back then it is not installed in the kernel and it should cause problems.
If it is installed just type
sudo modprobe -r ndiswrapper

If you want to go further (and remove more), just tell me how you installed ndiswrapper, from synaptic or did you compile from source.

Next issue
To run any command as root (you dont need a root terminal), just preface the command with sudo.
So whatever command they say needs to run in root terminal, just preface the command with sudo.

If you need to make a madwifi directory just type:
mkdir ~/madwifi

This directory is simply for storing all the installation files.  They recommend you make it, so they can reference this exact directory in their instructions.

OK big problem that I just found, officially from the madwifi site:
At this time MadWifi does not support any USB devices. It's unlikely that MadWifi itself will be extended for USB support, as the USB devices have a largely different architecture. Background information on that can be found in ticket #33.

At this time - here is my suggestion.  You are simply piggybacking onto the tail end of this thread.  Start a new thread and list your card, the results of usb, and ask what drivers you need to proceed.  Ive not worked with atheros cards so Im kinda out of the loop.  I fairly confident though a solution can be found -- although it doesnt look like it will be with madwifi.

---

### Post by kevdog on 2007-06-22
In addition - call this number about your product:
Technical Support is available from EnGenius Technologies at 888-735-7888

Tell them you need a linux driver, and although their website site stated the linux drivers were available -- madwifi -- tell them it is your understanding that madwifi only support pc/pcmcia and not usb devices.

Let me know what they say!

---

### Post by abrand888 on 2007-06-22
Hi,

I just got back a email from tech support stating they don't have any linux drivers and they expect open development to make them, so I think we are back to using the EUB-362 drivers and ndiswrapper.

What steps should I try and from your answer I will start a new thread.

Arthur

---

### Post by kevdog on 2007-06-22
Rant ***

Their answer although it might be true -- is complete BS.  Expecting open development to make them.  So let me get this straight.  I'll make a product, but wont make any compatible drivers.  I will release the product to the public, and when I get a phone call from someone stating it doesnt work, I will just say -- "Hey its not my problem, I expected someone else to make the drivers for the product.  Go bother someone else!"

Total CRAP!

---

### Post by Erky on 2007-06-22
Kevdog, 
The directory in that file is titled wusb54g, but when I change to it and do ls, nothing comes up.

---

### Post by kevdog on 2007-06-22
Erky -

What do you get when you type
sudo ndiswrapper -l

Anything???

---

### Post by kevdog on 2007-06-22
D***it Arthur

I appreciate you wanting a solution, but when I googled your problem I found posts from you all over google and on multiple boards.  Why didnt you tell me you had the EUB drivers in the first place????

---

### Post by Erky on 2007-06-22
Kevdog,

when I do sudo ndiswrapper -l, it comes up as wusb54g: invalid driver!

---

### Post by kevdog on 2007-06-22
Hmm

Do this:
cd /etc/ndiswrapper
sudo rm -R *

When you do a ls, make sure no directory is shown.

Then try
ndiswrapper -l

If you get the same thing what you just posted, try
sudo ndiswrapper -r wusb54g

Then try 
ndiswrapper -l

Tell me what happens.

---

### Post by Erky on 2007-06-22
Okay,

I did all that, and there is nothing there anymore.

---

### Post by kevdog on 2007-06-22
Great, try downloading the driver from the linksys website that I referenced earlier.  Make sure you have the version 1 drivers -- and specifically you want the XP drivers for version 1 of the card.

After extracting the drivers (may need windows machine to help you do this), place the .sys and .inf and .cat files in ~/wireless_driver directory.

---

### Post by abrand888 on 2007-06-22
Kevdog,

Kevdog,

They  provide drivers to Windows but I don't think they are ready or know how to make a Linux driver.  So we have to try and get their Windows driver working in Ubuntu.

So please start me off using either the EUB-362 EXT Windows driver or Linksys driver.

Thanks

Arthur

---

### Post by Erky on 2007-06-22
Kevdog,

I got everything installed, and when I run ndiswrapper -l, this comes up:
wusb54g : driver installed
               device (5041:2234) present (alternate driver: prism54usb)

But, it still shows that I have no internet connection.

---

### Post by kevdog on 2007-06-22
Ok great you are on the right path.

Now you have to insert the ndiswrapper/driver combination into the linux kernel.
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

One last step is to possibly modify you /etc/network/interfaces file and /etc/iftab file.  If you could post these it would be great.

Also if you are using a router, for right now if you could turn off any encryption - no WEP or WPA for right now, and no MAC filtering.

Thanks

---

### Post by Erky on 2007-06-22
After I did sudo ndiswrapper -m, it said adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

File /etc/network/interfaces says:
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet dhcp
auto eth2
iface eth2 inet dhcp
auto ath0
iface ath0 inet dhcp
auto wlan0
iface wlan0 inet dhcp

then file /etc/iftab says:
eth0 mac 00:11:11:31:16:0c arp 1

---

### Post by kevdog on 2007-06-22
Sorry and one more thing:
lshw -C network

I assume you only have a wireless networking card, and no wired ethernet???

---

### Post by Erky on 2007-06-22
right, only wireless card.

lshw -C network returns:

*-network
description: Ethernet interface
product: 82562EZ 10/100 Ethernet Controller
vendor: Intel Corporation
physical id: 8
businfo: pci@01:08.0
logical name: eth0
version: 02
serial: 00:11:11:31:16:0c
width: 32 bits
clock: 33MHz
cababilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI firmare=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes
resources: iomemory:fe9df000-fe9dffff ioport:ddc0-ddff irg:20

---

### Post by kevdog on 2007-06-22
First make a backup of your interfaces file:
sudo cp /etc/network/interfaces /etc/network/interfaces.bak

Ok, edit your /etc/network/interfaces file
gksu gedit /etc/network/interfaces

Change it to the following :

auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp

Next edit your /etc/iftab file
gksu gedit /etc/iftab

If there is any listing (such as eth0), change it to wlan0
If there is nothing in the file, then do not add anything.

Reboot computer, and cross your fingers.  Hopefully everything will work.

---

### Post by Erky on 2007-06-22
okay, that didn't work. when changing the interfaces file, did you mean wlan0 or just wlan? neither of them worked.

---

### Post by kevdog on 2007-06-22
wlan0.

When you mean it didnt work, I get what your saying but what did you try???

Please type 
dmesg

If you could post any section of the above that deals with the network driver it would be great.
Also post:
modprobe -l | grep ndiswrapper

Please also post the following
iwlist wlan0 scanning

---

### Post by Erky on 2007-06-23
At first I tried wlan in the interfaces file, then I tried wlan0.

For the dmesg, I'm not sure if this is what you were looking for, but it's the only thing that looked familiar:
e100: Intel(R) Pro/100 NEtwork Driver 3.5.17-k2-NAPI
e100: Intel (c) 1999-2006 Intel Corporation
e100: eth0: e100_probe: addr 0xfe9df000, irq 20, MAC addr 00:11:11:31:16:0c
prism54usb: eeprom read failed
prism54usb: probe of 4-3:1.0 failed with error -22

modprobe -l | grep ndiswrapper returned:
/lib/modules/2.6.20-15-generic/misc/ndiswrapper.ko

and iwlist wlan0 scanning returned:
wlan0 Interface doesn't support scanning.

---

### Post by Justin125 on 2007-06-23
When I type ndiswrapper -v after sudo make install I get:

```
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
(alot to type out- do you need it?)

```

also I'm not sure if the 0 is a 0 or an 8.

---

### Post by kevdog on 2007-06-23
Erky

Ok couple of things:

Please post /etc/network/interfaces
/etc/iftab
/etc/modprobe.d/blacklist

I think something needs to be added to the blacklist file

Lastly are you testing this wlan0 or wireless connection with the wired connection off?? Wireless and wired can not run at same time.

---

### Post by Erky on 2007-06-23
Okay, /etc/network/interfaces reads:
auto lo
iface lo inet loopback


iface wlan0 inet dhcp

and /etc/iftab reads:
wlan0 mac 00:11:11:31:16:0c arp 1

and /etc/modprobe.d/blacklist, excluding notes, reads:
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist i2c_i801
blacklist r818x
blacklist r8187
blacklist rt2570

and lastly, I haven't been, because I didn't realise that, but now I will.

---

### Post by kevdog on 2007-06-23
Erky

Your /etc/network/interfaces file needs to be:

auto lo
iface lo inet loopback

auto wlan
iface wlan0 inet dhcp

Try with this modification.  After making this change, type:
sudo /etc/init.d/networking restart

Then try to see what it says when you type
iwlist wlan0 scanning

If it doesnt work, reboot, and you then look in dmesg.  If get something that talks about prism54usb, you may then need to add (using gksu gedit) the following to /etc/modprobe.d/blacklist:

blacklist prism54usb


Id try rebooting after this, and then see if it works (sorry about the number of reboots -- its a pain).  There are some ways to bypass the reboots, however I know from helping a lot of people, the reboot is always the safest way particularly when you are trying to troubleshoot multiple problems.

---

### Post by abrand888 on 2007-06-23
Kevdog,

I am not sure how to start a new thread so please excuse me in answering you in this thread.

I see that I have in the etc/ndiswrapper sub directory and it states that the folder is net5523. This the folder for the EUB-362 EXT wireless device that is connected to my AMD computer. I ran the following stuff in terminal mode but it doesn't see my wireless connection like it sees in Windows. What you see is a recommendation of a friend to try. On my desktop I do have a folder called DriverFiles and it has all the files-drivers for my wireless device. I looked into Network and all it sees is the modem. I didn't yet tried to use the Linksys driver because that driver is for a pci_wireless card and I am not using any card.

server1@server1:~$ ndiswrapper  -l
net5523 : driver installed
server1@server1:~$ sudo bash
Password:
root@server1:~# lsusb
Bus 005 Device 004: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
Bus 005 Device 003: ID 0cf3:0002 Atheros Communications, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
root@server1:~# ndiswrapper  -a 0cf3:0002 net5523
WARNING: Driver 'net5523' will be used for '0CF3:0002'
This is safe _only_ if driver net5523 is meant for chip in device 0CF3:0002
root@server1:~# ndiswrapper  -l
net5523 : driver installed
        device (0CF3:0002) present
root@server1:~# ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
root@server1:~# 
root@server1:~# 

Something else is needed that will recognikze that I am accessing the driver properly to get a internet connection. I would appreciate your help in getting my device to work.

Arthur

---

### Post by Erky on 2007-06-24
when I ran uso /etc/init.d/networking restart, I got an odd message: Ignoring unknown interface wlan=wlan
and when I ran iwlist wlan0 scanning, I got wlan0 Interface doesn't support scanning.

---

### Post by kevdog on 2007-06-24
Sorry I keep typing the wrong junk

Make your interfaces file the following:

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

---

### Post by Erky on 2007-06-24
Now it says no DHCPOFFERS recieved.

---

### Post by a1unix529 on 2007-06-24
I hate to barge in like this but... this is exactly where I'm stuck too!

You can try:
```
sudo dhclient wlan0
```to try getting an IP address from your access point. It doesn't work for me though.

---

### Post by kevdog on 2007-06-24
Ok

What is the result of 
iwlist wlan0 scanning

If something doesnt work preface above command with sudo

Tell me about your router.  Is WEP and WPA off??

---

### Post by Erky on 2007-06-24
iwlist wlan0 scanning returns wlan0 Interface doesn't support scanning. Both WEP and WPA are off on my router.

---

### Post by kevdog on 2007-06-24
Im running out of ideas,

need to post
ifconfig
ndiswrapper -l
/etc/network/interfaces
/etc/iftab

Reboot computer if you havent done already.  Do the lights on the wireless card turn on??? Make sure wireless card is in the slot when rebooting??  Do you have to turn your wireless card on if there are no lights?

---

### Post by Erky on 2007-06-24
ifconfig:
lo:  
Link encap:Local Loopback
inetaddr:127.0.0.1 Mask:255.0.0.0
inet6 addr:   ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU: 16436 Metric:1
RX Packets: 4 errors:0 dropped:0 overruns:0 fram:0
TX packets: 4 errors:0 dropped:0 overruns:0 carrier:0
collisions: 0 txqueuelen:0
RX bytes : 200 (200.0 b) TX bytes: 200 (200.0 b)

wlan0:
Link encap: Ethernet HWaddr: 00:11:11:31:16:0C
UP BROADCAST MULTICAST MTU:1500 Metric: 1
RX Packets: 4 errors:0 dropped:0 overruns:0 fram:0
TX packets: 4 errors:0 dropped:0 overruns:0 carrier:0
collisions: 0  txqueuelen: 1000
RX bytes: 0 (0.0 b) TX bytes: 0 (0.0 b)

wlan0:ava:
Link encap: Ethernet HWaddr: 00:11:11:31:16:0C
inetaddr: 169.254.1.91 Bcast: 169.254.255.255 Mask: 255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric: 1

ndiswrapper -l:
wusb54g : driver installed
device (5041:2234) present (alternate driver: prism54usb)

/etc/network/interfaces reads:
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp

/etc/iftab reads:
wlan0 mac 00:11:11:31:16:0c arp 1

The lights on my wireless card are on, except for the one that shows that I'm connected to my network.

---

### Post by kevdog on 2007-06-24
Do you blacklist the prism driver???


Question -- you have a wired ethernet card on this computer???

Please also post 
sudo lshw

I just want to make sure the MAC addresses are OK and wlan is not associated with the MAC address of the wired ethernet card
Again just want to reiterate that the wired and wireless connections can not be working at same time.

Also (you may need to upload as a text file), the output of 
dmesg

---

### Post by Erky on 2007-06-28
okay here are both results. both are txt files (in a .tar.gz file), they're both pretty big, and I didn't know what you wanted out of them. sorry for the really late reply, been away from a computer for awhile.

---

### Post by kevdog on 2007-06-28
Erky  --- I thought you had died.

From my understandning (its been awhile since we've spoken) you have a wired ethernet connection and a wireless USB device.  The wired ethernet works, but the wireless usb device does not??

I see that wlan0 is now associated with the wired ethernet connection, but not the wireless connection.  What a pain.

So lets do the following:
Make your /etc/network/interfaces look like the following

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

eth0 represents the wired ethernet. wlan0 for the usb wireless device.

Change the /etc/iftab file back to eth0
eth0 mac 00:11:11:31:16:0c arp 1

The reason we are doing this is that the MAC address listed in iftab is the MAC address of the wired card, not the wireless.

Reboot!

Next I want to make sure that the ndiswrapper module is loaded in the kernel:
modprobe - l | grep ndiswrapper

Make sure the output is something like this:
/lib/modules/2.6.20-16-generic/misc/ndiswrapper.ko

Next I want to see if the prism modules are contained within your kernel (these are the alternate drivers for the USB device
modprobe -l | grep prism

Please post the output.

And finally please relist (Im lazy OK??):
ndiswrapper -l

I think the default prism drivers that are contained in your kernel already are conflicting with the ndiswrapper drivers.  We are going to have to unload the prism drivers so they dont cause a conflict.  Hopefully at that point it will work

Kind of seems like we are chasing our tail a bit!

---

### Post by Erky on 2007-06-28
I only have a wireless usb device. my computer is in a different room than my router.

modprobe-l | grep prism returns:
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/p54/prism54usb.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/p54/prism54common.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/p54/prism54pci.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/prism2/p80211/p80211.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/prism2/prism2_usb.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/prism2/prism2_plx.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/prism2/prism2_pci.ko

and ndiswrapper -l returns:
wusb54g: device installed
device (5041:2234) present (alternate driver: prism54usb)

---

### Post by Erky on 2007-06-28
Nevermind! I'm typing this on my own computer, which means my wireless is running perfectly! Thank you for all your help Kevdog!

---

### Post by kevdog on 2007-06-28
Just to fulfill my curiosity, are you going to leave me hanging, or actually tell me what you did to make it work :)

---

### Post by Erky on 2007-06-29
Sorry! All I did was change everything to what you told me to change it to, and it all of a sudden showed up in the network!

---

### Post by kevdog on 2007-06-29
Well great --- I was predicting there was going to be more problems, but sometimes I guess I fool myself.

Enjoy!

---

### Post by Erky on 2007-06-29
Thanks again for your help! I never could have done it without you!

---

### Post by kevdog on 2007-06-29
The only thing I ask is that once you get up and running with ubuntu, check back in the forums and help someone else out with a problem.  That's how to keep the Ubuntu community great!

---

### Post by Erky on 2007-06-29
will do!

---

