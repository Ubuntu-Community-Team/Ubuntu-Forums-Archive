---
title: "Prob with AirLink AWLL3028 on Ubuntu and Xubuntu"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by Dark Aspect on 2008-01-24
I have a Airlink 101 AWLL3026 and it works well with Ubuntu however I was wanting to connect another computer to my network with Xubuntu.I thought the easiest solution would be to buy another card just like what I have but I made a mistake and brought the easily confused Airlink 101 AWLL3028.At first I did not noticed the difference on the item number and since the card looks identical to my other card I though the AWLL3028 was bad.Both Ubuntu and Xubuntu fails to noticed the cards been plugged in at all,but a window system detects the hardware so I think its a Linux incompatibility,what can do to fix the problem or am I SOL.

I don't think I can return it and windows is useless to me so if I can't get it too work then I just burned $20........anybody want a wifi?

---

### Post by jeffus_il on 2008-01-24
It seems like the adaptor has a Realtek chip and needs a module rtl8187.ko

In a terminal do ```
sudo modprobe rtl8187
```

and see if it works.

---

### Post by Dark Aspect on 2008-01-24
> **jeffus_il said:**
> It seems like the adaptor has a Realtek chip and needs a module rtl8187.ko

In a terminal do ```
sudo modprobe rtl8187
```

and see if it works.
Um no still doesn't detect it,I tired it twice on both Ubuntu and Xubuntu and even reset both computers........

Thanks for the very fast reply though.

---

### Post by Dark Aspect on 2008-01-25
Bump

Is there any ideas,maybe with the nswrapper driver??????

---

### Post by Pointswest on 2008-01-25
I have this same adapter Airlink AWLL3028 with a realtek 8187b chipset.  I was able to use this adapter by installing ndiswrapper and using the Win 98 drivers from the Airlink CD.  The two files needed from the Airlink CD are labeled rtl8187b.inf and rtl8187b.sys.  After following the instructions posted by forum user Kevdog about setting up ndiswrapper and troubleshooting you wireless connection I have been running this adapter for several days with no problems.

Pointswest

---

### Post by Dark Aspect on 2008-01-25
> **Pointswest said:**
> I have this same adapter Airlink AWLL3028 with a realtek 8187b chipset.  I was able to use this adapter by installing ndiswrapper and using the Win 98 drivers from the Airlink CD.  The two files needed from the Airlink CD are labeled rtl8187b.inf and rtl8187b.sys.  After following the instructions posted by forum user Kevdog about setting up ndiswrapper and troubleshooting you wireless connection I have been running this adapter for several days with no problems.

Pointswest
Thank you very much,I have not tried it but it look promising.I have the CD with the two files but I am little bit of a noob with ndiswrapper.I don't mind looking it up but you wouldn't happen to have a Link to Kevdog's instructions would you? 

Thanks for your help.Does ndiswrapper work with Xubuntu?If not I can just trade wireless cards between my two computers.

Edit:For future reference here are the links,works great:

[http://ubuntuforums.org/showthread.php?t=574501&highlight=Kevdog]("http://ubuntuforums.org/showthread.php?t=574501&highlight=Kevdog")

[http://ubuntuforums.org/showthread.php?t=571188&highlight=Kevdog]("http://ubuntuforums.org/showthread.php?t=571188&highlight=Kevdog")

---

### Post by Pointswest on 2008-01-25
I am new at this forum posting and to Ubuntu/Linux so I don't know how to add links to this post so I will give you the title of the tutorials below:

1.  How to:  install ndiswrapper (source,svn) -with included problem solving suggestions.

 2.  Troubleshoot your wireless network connection-connect manually using the command line.


If you can't find from the title just enter the name Kevdog into the browser window and you will see a llist of all his posts.

These instructions are for connecting at the command line, not using the Network Manager.  I have read many posts for using the  Net Manager but have never been able to get connected using any of these methods.  Follow these instructions closely and make sure when you enter a command you have copied it correctly.  A lot of my problems were keyboard errors, ie: "o" instead of "0" (zero) , or 1(one) instead of 
 l (L)  or an extra space in the command.  If a message appears saying   "permission denied" try entering the same command again using  the prefix "sudo".

I used the method of installing ndiswrapper from the installation disk from Ubuntu 7.10.  I am sure the commands for installing via the internet will also work as well if you can get a wired connection.

This should work for Xubuntu as well as Ubuntu.  I will try to set up Xubuntu with this method this weekend, but first I have to fix the terminal screen from reverting to the log in page before I can issue any commands.

I have solved my terminal problems and have now installed this adapter on an older dell 400 mz/ Xubuntu 7.10 using these instructions above for installing ndiswrapper and connecting with the command line.  I will state again this is accomplished with command line execution, not anything to do with the network manager.  The monitor icon will be on the tool bar and the available  networks shown if you use Network Manager. but you don't need to click on anything to make this method work.  Upon completion of the start up commands and saving to the etc/rc.local file you will connect automatically at boot.  I think this works better if NM is uninstalled so you don't go mousing around up there and cause it to disconnect.  This NM has never worked with this chipset.  To see a list of connections without NM installed just type "iwlist scan" in the  terminal to see the available signals.

 I will remind again that the driver that works for this chipset (rtl8187b) was the Win 98 driver.  I tried using the WinXP driver but always got an invalid driver error.

Pointswest

---

### Post by Almumin on 2008-05-29
> **Dark Aspect said:**
> Bump

Is there any ideas,maybe with the nswrapper driver??????

Ok. Had the same problem with the install. This worked on Ubuntu Hardy 8.04.

1. Open terminal and sudo apt-get install ndsiwrapper-common and then go to Add/Remove programs and install the graphical ndiswrapper GUI.

2.  Go to the Airlink 101 website:
[http://www.airlink101.com/support/index.php?cmd=files&id=106](http://www.airlink101.com/support/index.php?cmd=files&id=106)

3. Download the driver for 5/21/2008. to your desktop.

4. Rt. Click and Extract the AWLL3028_051908.zip. 

5. cd into AWLL3028_051908/RTL8187B/Win98

6. Now this is completely optional. You can mkdir /home/wireless and cp * the files from the Win98 directory. sudo chown username.username * and this will allow the files to be used from your user account. 

OR!

 You can just move the folder itself that was extracted. 
7. System => Administration => Windows Wireless Drivers

8. Install New Driver. Select the driver location.

9. Wait a few minutes. Click on your nm-applet icon and select your wireless network!:popcorn:

---

### Post by otterstrom on 2008-06-22
I have the same card and I desire to get it working for wireless internet. 

I tried to install ndsiwrapper-common using the command prompt and the message i get is; "E: Couldn't find package ndsiwrapper-common"

Any suggestions? Could it be a repository problem?

Edit: My problem was that the above post had a typo, it should be "ndISwrapper-common"

But now when I get to the last steps, I install the driver and the wireless network driver says "Hardware Present: No"

Does this mean that the system does not recognize the wireless card?

---

### Post by pmulgaonkar on 2008-07-17
In that folder, the two files I see are called "net8187b.inf" and "rtl8187b.sys". Should both of them have the same name (i.e, rtl8187b.inf and sys)? Should I manually rename/copy the net8187b.inf --> rtl8187b.inf?

I can get all the drivers loaded, but it does not connect with the AP.

--prasanna

---

### Post by Almumin on 2008-07-17
> **pmulgaonkar said:**
> In that folder, the two files I see are called "net8187b.inf" and "rtl8187b.sys". Should both of them have the same name (i.e, rtl8187b.inf and sys)? Should I manually rename/copy the net8187b.inf --> rtl8187b.inf?

I can get all the drivers loaded, but it does not connect with the AP.

--prasanna

Prasannal,

Use the .inf file. Don't worry about the .sys file.

---

### Post by alfonsomigliore on 2008-07-17
I bought an Airlink AWLL3028 wireless USB adapter and could not get the internet on my Ubuntu Feisty Fawn (7.04? I believe). I followed the instructions for installing ndiswrapper, but still I could not get my two browsers, Epiphany and Firefox, to open web pages. I had been trying with 'roaming enabled', so I decided to disable roaming and then I went (on a windows machine) to my router management page (for my netgear router the page is: [www.routerlogin.com](www.routerlogin.com)). Then I copied the IP Address and Subnet Mask numbers. I also disabled the WEP security and chose 'none' for security.

Then I went back to my Ubuntu box and unchecked 'enable roaming' and manually configured it putting in the numbers I copied from the router page for IP Address and Subnet Mask.

It works.

---

### Post by pmulgaonkar on 2008-07-17
I too can get up to the point where the Airlink trys to associate with the access point (mine is a DLink). It does not connect (no association or DHCP access). Has anyone else had this trouble? Is manually adding the IP etc the only solution? Or has anyone else got the DHCP to work right.

Thanks for the help.

--prasanna

---

### Post by fung on 2008-07-23
> **alfonsomigliore said:**
> I bought an Airlink AWLL3028 wireless USB adapter and could not get the internet on my Ubuntu Feisty Fawn (7.04? I believe). I followed the instructions for installing ndiswrapper, but still I could not get my two browsers, Epiphany and Firefox, to open web pages. I had been trying with 'roaming enabled', so I decided to disable roaming and then I went (on a windows machine) to my router management page (for my netgear router the page is: [www.routerlogin.com](www.routerlogin.com)). Then I copied the IP Address and Subnet Mask numbers. I also disabled the WEP security and chose 'none' for security.

Then I went back to my Ubuntu box and unchecked 'enable roaming' and manually configured it putting in the numbers I copied from the router page for IP Address and Subnet Mask.

It works.

Well I don't know about you but it doesn't "work" until it can connect using WPA. I've tried about everything I can think of, messing around with WPA to connect but no cigar unfortunately.

---

