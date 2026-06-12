---
title: "How to instal Ndiswrapper without an internet connection"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by SheldonJ on 2011-04-12
Hi, I am totally new to Ubuntu. I just installed Ubuntu 10.10 onto Windows XP. Unfortunately My wireless USB adapter does not work in Ubuntu, so I do not have internet. I need to(I think.) install Ndiswrapper onto Ubuntu so that my USB adapter will work. Does anyone know how to istall Ndiswrapper without an internet connection? I do have a working USB flash drive which I can use to copy files, I just don't know how to do it.

Thanks.

---

### Post by TeoBigusGeekus on 2011-04-12
See this [link]("http://sourceforge.net/projects/ndiswrapper/files/stable/1.56/").
Read the text files for instructions on how to install it.

---

### Post by f1tz on 2011-04-12
TeoBigusGeekus's link should get you to the file you need to download. I'm assuming you might not know how to extract the tarball? If not...

You'll need to type:
tar -zxf ndiswrapper-1.56.tar.gz 

That will create a new directory, inside which is a text file called INSTALL,  which should have instructions on how to carry on from there.

---

### Post by SheldonJ on 2011-04-12
Thanks, but where do I type the command?

---

### Post by TeoBigusGeekus on 2011-04-12
Where did you put the downloaded archive?
It might be easier if you double clicked it, to avoid further confusion.

---

### Post by dcsoldschool53 on 2011-04-12
**Open up a terminal and type them there**.

---

### Post by dcsoldschool53 on 2011-04-12
[B]Ok if you are still having problems, click the link. 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Scroll down to the line "2.2. Installing Packages (With Internet access on another computer)" Read that section. Or, Scroll down to 2.3. Installing Packages (Without Internet access). Here it tells you how to install ndiswrapper using the CD[/B]

---

### Post by SheldonJ on 2011-04-12
Okay, I downloaded the files, but where do I put the files before extracting them?

---

### Post by dcsoldschool53 on 2011-04-12
**Desktop**

---

### Post by wep940 on 2011-04-12
PLEASE, don't bother with a downloaded copy of ndiswrapper.  Instead, just do the following:
 
[LIST]
[*]with Ubuntu up and running, put the LiveCD you installed from in the drive.  If a message comes up about a software source just cancel the message.
[*]using "Places", navigate to the /pool/main/n folder on the CD
[*]click on the ndiswrapper folder
[*]double-click on the ndiswrapper common file and wait for it to complete installing.  The password will be your normal password.
[*]double-click on the ndiswrapper utilities file and wait for it to complete installing.
[*]back up one level to the /pool/main/n folder again
[*]click on the ndisgtk folder
[*]double-click on the ndisgtk file and wait for it to complete.
[/LIST]This has installed ndiswrapper and it's gui'd front-end ndisgtk to your Ubuntu installation.  
 
To install your driver:
[LIST]
[*]First, remember the Windows driver *MUST* be Windows XP *ONLY* and must match the architecture of your Ubuntu installation - 32 or 64 bit.
[*]Copy the .inf and .sys files for your driver to your Ubuntu Desktop
[*]Go to System/Administration/Windows Wireless Drivers - this will start up the gui'd front-end to ndiswrapper called ndisgtk.  It is FAR easier this way than trying to use ndiswrapper in the command line.
[*]Start with new device or what ever it says (I'm in Windows right now).
[*]Point it to the .inf file on your Ubuntu desktop and click the ok, install, or what ever it is (again, I'm in Windows right now).
[/LIST]This should have installed your driver.
 
Now a step some omit:  reboot your PC.  This will be sure that any modules that were loaded before that were incorrect are no longer loaded, and guarantee that the ndiswrapper loaded driver should work.
 
Go to the network manager icon on your desktop and right-click.  If "Enable Wireless" is not checked, be sure to check it.
 
Left-click on the network manager icon - do any networks show now?
 
Things to remember:  
[LIST]
[*]if the router is not broadcasting the network name, a so-called hidden network, you must left-click on the network manager icon and select "Connect To Hidden Network".
[*]if you have any encryption, etc., set on the router, you must match it and the password/passphrase when prompted.
[*]if you have MAC filtering active on the router, be sure this PC's MAC address in the list on the router.
[/LIST]

---

### Post by SheldonJ on 2011-04-12
Okay, I installed ndiswrapper and am going to try to find the inf file for my USB adapter. It is a Belkin N adapter. If anyone else know where I can find the inf file for it that would be great!

---

### Post by SheldonJ on 2011-04-12
To be exact it is a F7D2101 usb adapter. I found the folder that it was located, but there was no inf file there. Where can I find the inf file?

Thanks

---

### Post by wep940 on 2011-04-12
Do you dual-boot with Windows XP?  If so, you should be able to find the .inf and .sys files (you need both) in your Windows installation.  If not, we can try to get what you need.

---

### Post by wep940 on 2011-04-12
Unzip the attachment and place the files on your Ubuntu desktop, then go through the steps for ndisgtk to install the driver.

---

### Post by SheldonJ on 2011-04-13
Okay, I installed the driver amd it says that it found the hardware, but I still don't have internet. I set up the internet connection and gave all of my network information, but it still can't find a connection. Is there something that I am not doing right?

Thanks.

---

### Post by Razorback on 2011-04-13
Check you network connections by clicking System > Administration > Network Connections.  Make sure the wireless connection is enabled.

---

### Post by SheldonJ on 2011-04-13
I don't see it there. I see an Ethernet and a Loopback connection, but I don't see a wireless connection.

---

### Post by Onesimus on 2011-04-13
You may need to logout or even reboot your machine.

---

### Post by SheldonJ on 2011-04-13
I have done that a couple of times already. And it still does not work. Is my driver not supported by ndiswrapper?

---

### Post by SheldonJ on 2011-04-13
I just went to the ndiswrapper site and my driver is there. The person said that they did exactly the same thing that I did.
Here is what they said.
"Belkin F7D2101 'surf & share'
 chipset: rtl8192su 
 usbid: 050d:845a 
Info

Used the win XP driver net8192su.inf from the accompanying CD. Works fine"
Does anyone know why it does not work for me?

---

### Post by wep940 on 2011-04-13
Maybe we should go back and ask for the details of everything you did trying to get the driver installed and working, as it's quite possible, particularly if you downloaded ndiswrapper from the net and followed out-dated instructions, that you did something that is restricting or stepping on the driver now.

---

### Post by SheldonJ on 2011-04-13
I went to this link: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and installed the first three files. I just realized that they were for Ubuntu 10.04 and not Ubuntu 10.10 which is what I have installed. Is that the problem? If it is not the problem I can give you list of everything that I did.

---

### Post by SheldonJ on 2011-04-13
It also said to "3.1. Disable Free Drivers

Firstly, all releases since Ubuntu 6.06 have the open source bcm43xx driver, which was replaced in 8.04 by b43 and b43legacy, see WifiDocs/Driver/bcm43xx. If this driver doesn't work for you, then you should disable it, because it will conflict with ndiswrapper. To disable it, add blacklist bcm43xx lines for each driver to the modprobe blacklist. 
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist"

Is this something that I need to do?

---

### Post by wep940 on 2011-04-14
I think I would go in to Synaptic package manager and remove the existing installations of ndiswrapper common, ndiswrapper utilities and ndisgtk.   Once those are removed, go back and load from the LiveCD you used to install Ubuntu.  Then try loading your driver again.
 
As far as blacklisting is concerned, be aware that your adapter is NOT a Broadcom adapter, and therefore nothing related to Broadcom should be causing any problem.  That is also part of the beauty of using ndisgtk - if something needs blacklisting it normally handles all of that for you.  All of the things you would normally have to type in the command line, and therefore open for errors, when you use only ndiswrapper are handled by ndisgtk.  
 
So, if you followed any instructions that had you blacklist any drivers or had you make some changes to files, reverse all of those as well.  Then reboot.

---

### Post by SheldonJ on 2011-04-14
Well, I installed Ubuntu through the Windows Wubi installer. So I had to download the Ndiswrapper files to a flash drive and copy them over.

---

### Post by wep940 on 2011-04-14
> **SheldonJ said:**
> Well, I installed Ubuntu through the Windows Wubi installer. So I had to download the Ndiswrapper files to a flash drive and copy them over.
 
Wubi?  Normally only used to just try out ubuntu.  I don't know about making the wireless work in wubi.  Sorry.

---

### Post by stevenmelgar on 2011-11-10
Irrelevant comment. 
I just want to thank wep940.
I've spent the last three days trying to figure this out and almost returned my wireless adapter and gave up. I read your instructions and was done in under five minutes. Worked like a charm.

---

### Post by Ddamia on 2012-08-02
I know this is an old thread, but I'm facing what seems to be an identical problem and I'm at my wits' end. I have followed wep940's instructions religiously, but nothing doing. 

I've just bought a shiny new (well, matte new) Lenovo x121e without an operating system, because I just wanted to stick Ubuntu on it, like I have on all the other computers in the house. After a very smooth Lucid install (I just happen to like Lucid and want to hold on to it) however, unfortunately I get the "no network devices available" in the network manager.

$ sudo lshw -C network
gives me:
*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0200000-f0203fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f013ffff ioport:2000(size=128)


AFter following wep940's instructions Wireless Network Drivers manager shows hardware as present. But,

iwconfig gives me:
lo        no wireless extensions.

pan0      no wireless extensions.

What we should be seeing somewhere is a Realtek 802.11b/g/n WiFi Adapter... Where is it?

Any help would be massively appreciated!

---

