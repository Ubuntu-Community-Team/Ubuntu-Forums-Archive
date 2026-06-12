---
title: "Netgear WG111(v1) Success Story on Ubuntu 7.10"
date: 2008-03-30
forum: Networking &amp; Wireless
---

### Post by willnut on 2008-03-30
I just got my Netgear wg111(v1) wireless USB adapter working with very very little effort so I thought I'd post instructions on what I did. It may work for other Netgear adapters also. 

Some points to note
[LIST]
[*]I did this from a clean install of Ubuntu 7.10
[*]No complex command line/config file operations are needed
[*]I did not have a wired ethernet connection on my Linux box
[*]I had my netgear adapter plugged in from the beginning of the install
[*]I am using WPA encryption,
[*]I have a Netgear router (DG834G)
[*]I used a windows PC to download 2 files onto a USB stick. I then copied these onto my Linux box
[/LIST]

**1. Install Ubuntu 7.10, Wired ethernet connection not needed.**

**2. Install NDIS wrapper and utilities**

With your Ubuntu CD inserted access the Synaptic package manager (System->Administration->Synaptic Package Manager).

In the search box type "ndis" and select the 

ndiswrapper-common
ndiswrapper-utils-1.9

packages for installation.

Click "Apply" to install these packages.

**3. Get required files from the Internet **

Download these two files and put them on your Linux PC (e.g. using a USB stick). You can put these files on your Linux desktop or home folder, anywhere really.

NDIS GTK
File name : ndisgtk_0.7.2-1ubuntu1_i386.deb
URL : [http://packages.ubuntu.com/gutsy/i386/ndisgtk/download](http://packages.ubuntu.com/gutsy/i386/ndisgtk/download)

WG111 driver
File name : wg111_2_1.zip
URL : [http://kbserver.netgear.com/release_notes/d102869.asp](http://kbserver.netgear.com/release_notes/d102869.asp)

**4.Install NDIS Gtk**

NDIS GTK is a GUI interface for NDIS wrapper so you don't need to mess around with command line entry and config files.

Double click on the "ndisgtk_0.7.2-1ubuntu1_i386.deb" file you copied onto your Linux PC. This will automatically install NDIS GTK.

A system restart may be required here but I didn't need one.

**5. Extract Netgear driver files**

Right click on the "wg111_2_1.zip" file and select "Extract here" to unzip the driver files into a directory called "WG111_SW1.2Beta13".

**6. Add your wireless device to list of available network interfaces**

Select [System->Administration->Network]

As I'm going from memory (sorry) at this point you should be prompted to provide the location of your driver INF file. Just select the "WG111_SW1.2Beta13" directory.

**7. Enable your wireless adapter**

Click the Wireless "tick" box.
Click on properties.
De-select "Enable Roaming".
On the "Network Name" drop-down list select your router from the list. You should see a list of all available routers your adapter can pick up.
Select password type, in my case "WPA Personal".
Enter your router password.
Click "OK" and then "Close".

**8. That's it !**

Barring the install of Ubuntu this process takes about 15 minutes to complete max. It's not complicated and just worked.

I do wish Ubuntu came with NDIS wrapper and NDIS GTK pre-installed as this would have found my adapter automatically. I know the reasons against doing this but it's just a shame. Wireless not working is one of Linux/Ubuntu's biggest failings and puts many people off Linux. I know it put me off the last time I had a go at Ubuntu.

One point to mention, my connection does drop on very rare occasions but not enough to bother me ..... yet ! :)

Hope this helps at least one person!

---

### Post by Miles111 on 2008-03-30
THANK YOU! I can now switch over my last machine to ubuntu with your guide! And I agree, if only linux had wireless support at the level of windows, it would certainly increase in popularity.
EDIT: Oh well, have to scrap the switch, sadly the PC has only 128MB of ram, not enough. Still, I'm sure the guide will help others.

---

### Post by freshtimes on 2008-03-30
Hi, I believe I did everything you mapped out (thank you by the way) and I get to the last step. I verified that I have drivers installed and it recognizes my hardware. But when I go to the "drop down list" to see a list of networks nothing shows up. Is there a way to refresh this or something? 

Also, it finds all the networks in my building when romaing is enabled and I can connect to my network but it only lasts about 3 web pages before it kinda "shuts off" and cant see any network there after.

thanks

---

