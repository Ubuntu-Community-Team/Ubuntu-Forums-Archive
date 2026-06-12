---
title: "Total Linux Newb having problems with IPN2220"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by TheOfficeFan on 2010-12-08
First of all I would like to say that I have searched and gone through all of the "how to's" that I have found on the subject.  But, I can not seem to get my wireless card working on my old Acer laptop.  Here are the details:

Acer 1414wlci
Just installed Ubuntu 10.10
IPN2220 Wireless card

Once I finished installing Ubuntu I started the PC and noticed there is no option to connect to a wireless network.  Upon searching (here and on google) I found that the wireless card is not supported by Ubuntu.  So, I downloaded ndiswrapper and the windows driver for the card.  I followed the steps listed here [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) and got through step 3.5 OK.  But, when I reboot there is still no options for a wireless network.  Did I miss something?  Is there something I can copy and paste here to offer better insight into what I may have missed?

---

### Post by cariboo on 2010-12-09
To lets us see if the wireless device has been detected and the proper driver loaded, could paste the output of:

```
sudo lshw -C network
```

in your next post.

If you type:

> sudo lshw -C network > network.txt

The above command will create a text file called network.txt, that may be easier to transfer to a system with a working internet connection.

---

### Post by TheOfficeFan on 2010-12-10
I believe that it is being picked up, but for some reason I am unable to get the driver to work.  Here is the results from the above command (I have the computer at work and am connected to the internet via a network cable.

  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:78:65:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.10.106.121 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:6 memory:e0204000-e0205fff memory:54000000-54003fff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: IPN 2220 802.11g
       vendor: InProComm Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
       resources: ioport:3800(size=32) memory:e020a000-e020a01f memory:e0209000-e02097ff

---

### Post by TheOfficeFan on 2010-12-10
If I am correct, this section refers to the wireless card, correct?

description: Ethernet controller
       product: IPN 2220 802.11g
       vendor: InProComm Inc.

---

### Post by anewguy on 2010-12-10
Yes.

Please do the following and post the results back here:

- open a terminal window (Applications/Accessories/Terminal)

- type:

sudo ndiswrapper -l <press return> Where that's a lower case "L" for list.  We need to see what ndiswrapper thinks it has loaded.  Please post the output back here.

There are some posts out there on using ndiswrapper that are out of date.  This is what I would suggest:

- edit the /etc/modules file and remove the line that says ndiswrapper.  Save the file and exit the editor.

- in a terminal window:

sudo ndiswrapper -l

for each device returned:

sudo ndiswrapper -e xxxxx Where xxxxx is the device name

repeat the 2 above commands until the ndiswrapper -l command returns nothing.


Now, with you system already booted in Ubuntu, put the LiveCD in the drive.  Cancel any message about a software package disk being found.

- open "Places"

- navigate the LiveCD to the following folder:
/pool/main/n/ndiswrapper

- double-click on the ndiswrapper common file to install it - wait for this to finish.  I don't know how you installed your ndiswrapper before, so I'd like to get this version loaded.

- double-click on the ndiswrapper utilities file to install it - wait for this to finish as well.

- navigate to the /pool/main/n/ndisgtk folder

- double-click on the ndisgtk file to install it - wait for this to finish.


Now, be sure you have the Windows XP drivers for your adapter.  They *must* be Windows XP drivers, and the type must match your ubuntu type - 32-bit or 64-bit.  Put the .inf and .sys files that make up your driver on your ubuntu desktop.

Start ndisgtk - System/Administration/Windows Wireless Drivers.  Select "new....", then point it to the .inf file in your ~/Desktop folder.

Ndisgtk is a graphical front-end to ndiswrapper and saves a lot of typing at the command line (and subsequent potential for errors).

Wait a few minutes, then right-click on the network manager icon and see if "Enable Wireless" shows and be sure it is enabled.

Wait a few minutes, then left-click on the network manager icon and see if you can see wireless networks now.

Remember:

- if you use MAC filtering on the router, and this adapter has never been used to connect to your router, you will need to add the MAC address to the routers MAC table.

- if you use encryption, the type and password/passphrase must match.  Be aware that some older adapters may not support WPA2 or even WPA.  If you seem to never be able to connect this may be the problem.

- if your router does not broadcast the ESSID (e.g., it's a "hidden" network), then you *must* left-click on the network manager icon and select "Connect To Hidden Network".

Dave ;)

---

### Post by TheOfficeFan on 2010-12-10
Here are the results from running sudo ndiswrapper -l:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
neti2220 : driver installed
    device (17FE:2220) present

I do not have the live CD as I installed Ubuntu from a usb drive.  Can I use that instead?  I will not proceed with your second sets of instructions until I get the answer to that question.  

Also, if it matters, I have connected to the same router with the same laptop using windows, so I know it works.

---

### Post by TheOfficeFan on 2010-12-10
Also, one of the how-to's that I read said to do that "blacklist" thing.  But, I don't know if that is causing problems or not.

---

### Post by Spyderkid on 2010-12-10
I'm afraid that the IPN2220 isn't supported

---

### Post by anewguy on 2010-12-10
Any blacklisting you may have done needs to be reversed.  However, it's possible the post you were reading is old enough not to be up to date on that either.

The old blacklist file was /etc/modprobe.d/blacklist, however that changed and has been:

/etc/modprobe.d/blacklist.conf  for quite a while.

Please let me know what you did blacklist.

Yes, you can run off the USB flash drive if you used it to install.

Dave ;)

---

### Post by TheOfficeFan on 2010-12-10
I just did a clean install of Ubuntu and am going start over with a clean slate.  I did a bunch of different things from a bunch of different posts.  So, who knows how badly I have FUBAR'd this thing.  So, I will start back at square one with the sudo lshw -C network command and post the results.  Then I can start from square one.

---

### Post by TheOfficeFan on 2010-12-10
Here are the results of the sudo lshw -C network

PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 01
       serial: 00:c0:9f:78:65:a7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.10.106.121 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:6 memory:e0204000-e0205fff memory:54000000-54003fff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: IPN 2220 802.11g
       vendor: InProComm Inc.
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=32 mingnt=32
       resources: ioport:3800(size=32) memory:e020a000-e020a01f memory:e0209000-e02097ff


It looks like the card is still recognized.

---

### Post by TheOfficeFan on 2010-12-10
Here are the results from running sudo ndiswrapper -l:

sudo: ndiswrapper: command not found

What now?  I am going to try to do everything step by step as you tell me to, so I don't screw anything up.

---

### Post by TheOfficeFan on 2010-12-13
I went through the process of installing ndiswrapper and ngtdisk like you said in the above post.  I also downloaded what should be the correct driver.  But, when I try to install it using ngtdisk it says invalid driver.  What do I do next?

---

### Post by TheOfficeFan on 2010-12-13
I downloaded the driver from another place and ngtdisk allowed me to install it.  But, I am back to where I started with the first post.  It still does not does not show a wireless connection under the "Network Connections" screen.

---

### Post by TheOfficeFan on 2010-12-13
OK, I feel like I am getting very close.  Basically, I restarted a couple times and noticed that the "enable wireless" option has appeared when you right click on the network icon at the top of the screen.  Also, I left click the icon It shows "Wireless Networks" under the "available" heading.  But, it is greyed out and I can't click on it or anything.  So, now I need to know how to make it be able to see the wireless networks that are available.  I tried clicking "Connect to Hidden Wireless Network" but that didn't work.  Is there a setting that I need to change or something to make it look for available networks?

---

### Post by TheOfficeFan on 2010-12-14
Success, I fiddled around with it a little more and all my networks popped up and I am up and running.  Thank you all for your help.

---

### Post by wep940 on 2010-12-14
anewguy is a friend of mine, and he quit the forum and ubuntu over philosophical differences, and I know he was sorry to leave you hanging on this post.  I'm glad to see you got it going anyway.

---

### Post by TheOfficeFan on 2010-12-14
OK, so being a person that can never leave well enough alone, I have gotten myself back into the same predicament as before.  Once I got the wireless working I re-installed Ubuntu as the only OS on the PC (which is what I planned to do all along once I got the wireless working)  and now I can't connect wirelessly.  I went through all the same steps as before, and the driver is installed.  But, I think the wireless card is somehow disabled, and I can't figure out how to turn it on.  The button on the front has no effect at all.  I did an "sudo iwlist scan"  and for "wlan0" it says "no scan results"  I ran another command that I found somewhere else (I can't remember what it was) that basically said the wireless is disabled.  So, how can I turn it on?

---

