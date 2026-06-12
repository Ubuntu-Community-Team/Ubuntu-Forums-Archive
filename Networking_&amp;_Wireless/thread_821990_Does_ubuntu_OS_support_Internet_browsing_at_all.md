---
title: "Does ubuntu OS support Internet browsing at all?"
date: 2008-06-07
forum: Networking &amp; Wireless
---

### Post by pmokgweetsi on 2008-06-07
Just a small question to u guys but i'm curiuos as to whether this operating system **does or does not** support the internet at all? Because it seems to me like everyone of us here has the same problem of not being able to connect to the internet thru wired, wireless or phone connection.So i wonder if during the design of the operating system may be something major that enables users to connect to the internet was omitted. I mean what else could it be? I use wireless internet connection myself and trying to connect to the internet thru ubuntu has been nothing but a nightmare ever since i downloaded it to my computer a few days ago but i know there is nothing wrong with my connection 'cause other operating systems that i have in my laptop can identify the wireless networks around my vicinity so i wonder whats wrong with this one.

---

### Post by lisati on 2008-06-07
A short and sweet answer: Yes it does support Internet browsing, and worked "out of the box" for me.

---

### Post by lemuriaX on 2008-06-07
Yep it's awesome for networking/internet.

There are some known issues with wireless cards, there is a ton of info in the forums on that subject, and you will find plenty of people here can help you through that if you post the info they ask you to. 

I have never had an install not detect the internet right way through my ethernet card. 

Dialup I think just have to do a little more research to find the right application since it's not used so much anymore.

---

### Post by issih on 2008-06-07
Your problem, from having a little look at your other post, is simply that you do not have a driver loaded for your wireless card.

Sadly wireless is one of those areas that driver support is a bit flaky, because there are just so many variants of the hardware out there, and the manufacturers are very bad at providing drivers for linux themselves. In fact, Ubuntu comes with a lot of drivers built in (unlike that 'other' os where you always have to install them from cd) but there is just too much hardware in the world to be able to support everything perfectly out of the box. Bear in mind that the installer you used was only a cd....one cd , 750mb total.

You see nothing in network manager about your wireless card because the os has no idea how to talk to it without a valid driver.

In order to get any further you need to tell us what the make and model of the wireless card is (the wireless card not the laptop) and from there we can look at what options you have available.

at the very least post the output of running the command lspci in a terminal.

---

### Post by chili555 on 2008-06-07
> it seems to me like everyone of us here has the same problem of not being able to connect to the internet thru wired, wireless or phone connectionNot correct. I think there are far more answers here than questions. Did you think we who have posted help 500, 1000, 10,000 times are doing so through Vista? Lots of people with problems connect wired to read and post questions until they get their wireless tuned up.

If you install Vista or Mac OS from scratch, your wireless will not work without a driver. Ubuntu is only different in that drivers for many wireless cards 2-3 years old and older _are_ preinstalled in Ubuntu. I doubt that's true of your OS.

If you want to ask how to get a driver installed and tell us what kind of wireless card you have:```
sudo lshw -C network
```Then many of us will be very happy to help.

---

### Post by pmokgweetsi on 2008-06-07
Ok i've used the command that u've given me Chilli555 and this is what i got...i'm not so sure if its enuf information or more is missing but this is what i got anyway...

*-network 
  description: Ethernet interface  
  product: 88E8039 PCI-E Fast Ethernet Controller  
  vendor: Marvell Technology Group Ltd. 
  physical id: 0  
  bus info: pci@0000:02:00.0  
  logical name: eth0 
  version: 15  
  serial: 00:1a:80:27:be:60  
  capacity: 100MB/s  
  width: 64 bits  
  clock: 33MHz  
  capabilities: pm vpd msi pciexpress bus_master cap_list    
  ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 
  autonegotiation 
  configuration: autonegotiation=on broadcast=yes driver=sky2 
  driverversion=1.20 firmware=N/A latency=0 link=no module=sky2   multicast=yes port=twisted pair
 *-network UNCLAIMED 
  description: Ethernet controller 
  product: AR242x 802.11abg Wireless PCI Express Adapter 
  vendor: Atheros Communications Inc. 
  physical id: 0  
  bus info: pci@0000:06:00.0  
  version: 01 
  width: 64 bits 
  clock: 33MHz 
  capabilities: pm msi pciexpress msix cap_list 
  configuration: latency=0

Seems to me like the wireless network driver has no "logical name" but looks like it was manufactured by Atheros...Can you help me out as to the next step i should take to identify my network driver?

Thanks.

---

### Post by pmokgweetsi on 2008-06-08
Looks like all those of us who are using the **AR242x 802.11abg Wireless PCI Express Adapter** are doomed. So far i haven't read any post about anyone being successful connecting to the internet thru this adapter. What a shame!!!!

---

### Post by chili555 on 2008-06-08
It looks like your wired connection is all ready to go! Is this a laptop you can walk over to the router, connect with an ethernet cable and do:```
sudo ifconfig eth0 up
sudo dhclient eth0
```Did you get an IP address?

If so, let's attack your wireless. The most hopeful process I've seen is here in post #7 : [http://ubuntuforums.org/showthread.php?t=766529&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=766529&highlight=AR242x) Notice, throughout this thread, that the AR5007 is the same as your AR242x. 

Post back if you get stuck.

---

### Post by issih on 2008-06-08
This thread tells you exactly how to fix your problem (hopefully :))

[http://ubuntuforums.org/showthread.php?t=766529&highlight=atheros+5007](http://ubuntuforums.org/showthread.php?t=766529&highlight=atheros+5007)

IF you read it carefully you will see that it is likely that part of the problem is that 8.04 is detecting the card incorrectly.

Anyway, as suggested above, go jack into the router with a nice simple wire in order to get an internet connection, then follow the steps in that thread to try and get your wireless up and running

---

### Post by pmokgweetsi on 2008-06-08
Okay so I've been able to connect to the internet through the wired connection? So now how do i go about setting up the wireless one?

Thanks.

---

### Post by chili555 on 2008-06-08
Go here and follow post #7 exactly. You can even copy and paste the commands right into the terminal. [http://ubuntuforums.org/showthread.php?t=766529&highlight=AR242x](http://ubuntuforums.org/showthread.php?t=766529&highlight=AR242x)

---

### Post by pmokgweetsi on 2008-06-08
Chilli555 bear with me for seemingly troubling you but i went as far as detecting my systems' network interface card which ubuntu detected as **06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01.** (whether it is right or wrong im not so sure)and then i disabled HAL (whatever that is) but i ran into trouble while trying to create a directory that i can use to download the two links under step 2. Where did i go wrong? The first link did not even work when i used windows internet explorer or firefox...how do i resolve this one? Again how do i extract tar.gz file from where ever i saved it? I tried typing the name that i gave to the file between "tar -xvf <<filename>>" but that didn't work...  

Many thanks.

---

### Post by pmokgweetsi on 2008-06-08
Hi...can anyone help me with **step 2** of the following excerpt...i can't seem to download any of the two attached links in a usable way. Also how do i extract the files that I've downloaded to the terminal? I'm having a hard time to trying to figure out how i can execute this seemingly important steps but i can't seem to make any headway. 

Thanks.  

[I]Re: wifi help for acer 5315 laptop
Firstly, confirm which Wireless Network card(NIC) your laptop is using(as i have not heard of this particular sub model of the 5315)

You can do this by typing:

Code:

lspci | grep "Ethernet"

If no hardware issues are occuring, you should be presented with something similar to:

Code:

db@dblaptop:~$ lspci | grep "Ethernet"
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
06:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
db@dblaptop:~$

If your NIC is an Atheros AR5006EG(It's really an AR5007eg) then you should have two choices - madwifi(a project designed for atheros network interface controllers) or ndiswrapper(which uses windows coded drivers)

Once you have conirmed its an atheros network interface controller you should update ubuntu to the latest software versions.

Madwifi is the better option, and appears to be stable as of the current version.

however if it presents issues, then you should try the slightly lengthier process of ndiswrapper.

Firstly, a few pages for reference:

[http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
[http://forum.ubuntu.pl/showthread.ph...ghlight=5007eg](http://forum.ubuntu.pl/showthread.ph...ghlight=5007eg)

Follow these steps:

1. Disable the restricted driver for the network card in restricted drivers

2. make a directory in your home folder(eg madwifi) and download:

[http://snapshots.madwifi.org/madwifi...0071018.tar.gz](http://snapshots.madwifi.org/madwifi...0071018.tar.gz)

Plus

[http://madwifi.org/attachment/ticket...tch?format=raw](http://madwifi.org/attachment/ticket...tch?format=raw)

The second link cannot be downloaded using wget(use firefox to download it)

3. extract the tar.gz file by typing "tar -xvf <<filenamehere>>

[/I]

---

### Post by issih on 2008-06-08
The thread chilli and I posted contains several different guides about how to get your card up and running, you've managed to pick one for which the file they used has been deleted from the server. Just pick another post and try what they say. In essence it looks like you need to build and install madwifi (although it looks like it may be a specially patched source tree) or use ndiswrapper (which allows you to use the windows drivers for the wireless card.

If I were you I'd start with the first guide (post 7ish of the link we've given you, and follow that, I checked, the file they mention is there.

If that doesn't work let us know, and you can try again, to be honest though, you'll jsut have to try the various methods listed in that thread, you can work through the list far more easily than we can, as you can tell whether anything is working.

---

### Post by chili555 on 2008-06-08
> **pmokgweetsi said:**
> Chilli555 bear with me for seemingly troubling you but i went as far as detecting my systems' network interface card which ubuntu detected as **06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01.** (whether it is right or wrong im not so sure)and then i disabled HAL (whatever that is) but i ran into trouble while trying to create a directory that i can use to download the two links under step 2. Where did i go wrong? The first link did not even work when i used windows internet explorer or firefox...how do i resolve this one? Again how do i extract tar.gz file from where ever i saved it? I tried typing the name that i gave to the file between "tar -xvf <<filename>>" but that didn't work...  

Many thanks.Open a terminal and do:```
mkdir Atheros
cd Atheros
```That, as you may guess, means 'make a directory named Atheros' and 'change directory to Atheros.' Now do:```
wget  http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz
tar -xvf madwifi-ng-r2756+ar5007.tar.gz
```A new directory will be created called madwifi-ng-r2756+ar5007. Do:```
cd madwifi-ng-r2756+ar5007

```Proceed with the other steps as listed.

---

### Post by pmokgweetsi on 2008-06-09
Alright at long last I've managed to get my system to detect my wireless interface card as well as the networks that are available to me...but now i can't seem to connect to the internet...does anyone know why this is? How do i get my internet up and running now that my computer has detected my network interface card and the networks around? 

As for the steps that managed to get me where i am its the ones in the thread below after i uninstalled my ubuntu and installed it afresh.  

[I]Oh man this made me sooo happy when I found this!I just have to share 

I can't take any credit for this how to but I have tried it out and it works great...no more ndiswrapper for this puppy 
You can see all the details regarding the lack of support for Atheros on 64bit linux here [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)

Currently this method uses an patched HAL from which I haven't noticed any problems.

Lets give it a go.
Of course you will need an internet connection so get wired up if need be.

1: First off be sure the build-essential package is installed
Code:
sudo apt-get install build-essential
2: Also install subversion
Code:
sudo apt-get install subversion
NOTE:If you have been using ndiswrapper like I was you need to disable/remove it
Code:
sudo ndiswrapper -e net5211
sudo modprobe -r ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils ndisgtk
I recommend doing what I did and run the first two commands in the next section before removing ndiswrapper that way you can avoid hooking up to a wired network if your wireless is functional using ndiswrapper

3: Follow these steps
Code:
svn co [http://svn.madwifi.org/madwifi/trunk](http://svn.madwifi.org/madwifi/trunk) madwifi
wget [http://people.freebsd.org/~sam/ath_hal-20080528.tgz](http://people.freebsd.org/~sam/ath_hal-20080528.tgz)
cd madwifi
mv hal hal.old
tar xvf ../ath_hal-20080528.tgz
mv ath_hal-20080528 hal
sudo make install BINDIR=/usr/bin MANDIR=/usr/share/man
sudo depmod -ae
sudo modprobe ath_pci
echo ath_hal | sudo tee -a /etc/modules
echo ath_pci | sudo tee -a /etc/modules
4: Finally go to System ->Administration ->Hardware Drivers and make sure Atheros drivers are enabled and reboot the system.

Hopefully this makes your day like it did mine![/I]

And many thanks to all those of you who have helped me get to this point especially the guy who posted this thread above.

Cheers

---

### Post by steveneddy on 2008-06-09
> **lisati said:**
> a Short And Sweet Answer: Yes It Does Support Internet Browsing, And Worked "out Of The Box" For Me.

+1

---

### Post by issih on 2008-06-09
I'm not sure what you mean by isn't connecting, what exactly do you do to try and connect?, how do you know the card is detected and is seeing networks?...more info please :)

When you go to the networking applet in the top right, does it offer an "enable wireless" checkbox if you right click.

Do you have a list of detected networks if you left click on the icon?

If you do, then simply click on the network you want to join, and enter the information it asks for about any encryption. N.B. you would be well advised to start by turning off all encryption in the router so you can confirm that the wireless hardware is at least working.

If the driver doesn't integrate with the network manager, then you will have to either configure the interface manually or look at installing wicd (search for it in synaptic) which is an alternative network manager that often works better for some wireless drivers.

---

### Post by Mgiacchetti on 2008-06-09
> **steveneddy said:**
> +1
+2

---

### Post by pmokgweetsi on 2008-06-09
> **issih said:**
> I'm not sure what you mean by isn't connecting, what exactly do you do to try and connect?, how do you know the card is detected and is seeing networks?...more info please :)

Well for starters im not even sure the way i tried doing it is the right way really...but what i did was when i realised the option for wireless networks is there in the network manager...i clicked on it and it opened sum kind of a dialogue box and in the space bar there, there were names of networks available, BT, Neatgear, Wineslus, Belkin etc and then i clicked the one that i know im using and tried to enter the information that was required. But after i completed doing this i tried the internet but there was none...

i dunno about the other method that u suggested but i'll try and follow it just after this.

Thanks

---

### Post by issih on 2008-06-09
If you are at the stage where you are seeing wireless networks in network manager, then do the following:

1) Log into the router and disable ALL encryption on the wireless network.

2) Try and connect with no encryption, this lets us know if the hardware is actually working at all, if it can't do this then there is another underlying problem,

3) once you can connect let us know what type of encryption you are going to use on the network, if you are using wep it will probably just work, bu if you are using wpa you might well need to do some more work.

Please check with encryption off, we need to know if the system is functional before we can go any further.

---

### Post by pmokgweetsi on 2008-06-09
> **issih said:**
> (1) Log into the router and disable ALL encryption on the wireless network.


Hi again guys...how do i logon to the router? I have no idea how that is done!!!How and where do i start? Do i have to turn it off altogether and then what after that? I'm so f*****g in the dark...

Cheers

---

### Post by issih on 2008-06-09
We can't really tell you that, it depends on the make and model, and also on what password if any was set when it was installed. I'm assuming here that it is your own home router. If that is the case tell us what make and model it is, and ideally go dig out the manual. if its not your own router (e.g. you are at an institution and logging into their network), then we will have to leave this step and just try and get the system running with encryption straight away.

The basic procedure though is going to be to log into the router via a web browser.

You need to type the ip address of the router into the address bar:

Common ones are:
192.168.1.1
192.168.0.1
192.168.100.1
10.0.0.1

but it will depend on the make. The browser will then ask you for a login name and password, which will be whatever they were set to when you installed the router. If you never changed them, then they will probably be something like "admin" for both username and password, or "admin" as username and leave the password field blank.

In the end though, it will depend on the router's make and model, Assuming it is your router go look at it to fins out, and fish out the manual, failing that find a copy of the manual online.

---

### Post by inportb on 2008-06-09
Does your router have an instruction manual? Perhaps you can find the address there.

Or you can tell us what kind of router you have, and we can Google it out together.

> **Mgiacchetti said:**
> [QUOTE=steveneddy;5149443][QUOTE=lisati;5138002]A short and sweet answer: Yes it does support Internet browsing, and worked "out of the box" for me.+1[/QUOTE]+2[/QUOTE]

+3, and using the same wireless chipset, with injection and all.

---

### Post by vincentvee on 2008-06-09
> **pmokgweetsi said:**
> Okay so I've been able to connect to the internet through the wired connection? So now how do i go about setting up the wireless one?

Thanks.

i set up the same card through restricted drivers manager, you might want to give it a try

system>administration>hardware drivers
but there are other methods of course, check through the [http://help.ubuntu.com](http://help.ubuntu.com) pages or the community help pages at [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
i sometimes find the info there better than what i can find here

---

### Post by pmokgweetsi on 2008-06-09
Gosh this operating system is kak...Now it has crashed!!!Can u believe this!!!After all that i've been thru...Every time i try to boot my computer up comes windows vista and says that the program that i've chosen could not be started as it is damaged or has been corrupted after my last re-installation...Gosh what a waste!!!!

Anyway...im not gonna give up, up until this thing starts running again...

Bye

---

### Post by pmokgweetsi on 2008-06-10
Finally I've been able to connect to the internet wirelessly ha :lolflag but only at school not at home...Wow how good can this feel!!!! Thanks to all of you guys who helped me...ohh i feel so good.

Cheers

---

