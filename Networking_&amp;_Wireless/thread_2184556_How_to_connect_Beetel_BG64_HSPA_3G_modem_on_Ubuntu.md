---
title: "How to connect Beetel BG64 HSPA 3G modem on Ubuntu 12.04"
date: 2013-10-29
forum: Networking &amp; Wireless
---

### Post by pushpendumajumdar on 2013-10-29
Hello;
Recently I bought Beetel BG64 HSPA 3G modem and faced connection issue on Ubuntu 12.04 LTS. The modem was not detected at all. Network Manager could not detect any device. In terminal *lsusb* output detects the device as following:

[TABLE="class: outer_border, width: 500, align: left"]
[TR]
[TD]$ [COLOR=#800000]lsusb[/COLOR]
Bus 001 Device 004: ID 2020:0002[/TD]
[/TR]
[/TABLE]

So,
VendorID = 2020
ProductID = 0002

But, on Windows OS I got the device ID when "switched", as follows.

VendorID = 2020
ProductID = 2000

**If you are facing the same issue, here is the solution:**

_**Step-1:**_

Disconnect your Modem from USB Port.

_**Step-2:**_

Install current version of **usb-modeswitch** and **usb-modeswitch-data** from Synaptic Package Manager.
For other installation options and help about usb-modeswitch visit [http://www.draisberghof.de/usb_modeswitch](http://www.draisberghof.de/usb_modeswitch) [You may download it and other necessary packages from here to another machine, especially helpful if you currently have no internet connection on desttination machine.]

[The current version of usb-modeswitch-data  contains mode-switching option for 2020:0002. Which is for MediaTek MT6229 chipset. But this settings for 2020:0002 is not going to work. Your device is still undetected]

[In older version of usb-modeswitch-data, the mode-switching for 2020:0002 is simply not present.]

Whatever the case may be, if your modem is still not detected go to step 2.

[B][U]Step-3:
[/U][/B]
Now you have to edit the file "**40-usb_modeswitch.rules**" with root privilege. To do this, open ***Terminal.***
[B]
In Terminal, you have to input commands identified by only [COLOR=#800000]Maroon Color.
[/COLOR]
[/B][TABLE="class: outer_border, width: 500, align: left"]
[TR]
[TD]xxxx@yyyy:~$ [COLOR=#800000]sudo gedit /lib/udev/rules.d/40-usb_modeswitch.rules
[/COLOR][sudo] password for xxxx: [COLOR=#800000]****[/COLOR][/TD]
[/TR]
[/TABLE]

where "gedit" is the text editor. You may open another text editor of your choice. And enter your administrative (sudo) password, when prompted.

Text Editor will open the file in sudo mode.

Now, find the exact attributes matching the following:
**ATTRS{idVendor}=="2020", ATTRS{idProduct}=="0002"**

If you find an exact match, leave the file and close.

If no exact match found, copy/paste the following text

[TABLE="class: outer_border, width: 800, align: left"]
[TR]
[TD]# Beetel 3G HSPA USB Modem - BG64 (made by MediaTek MT6229)
ATTRS{idVendor}=="2020", ATTRS{idProduct}=="0002", RUN+="usb_modeswitch '%b/%k'"[/TD]
[/TR]
[/TABLE]

before the last line of the file.
[U][B]
Step-4:
[/B][/U]
1. Now create a blank file on Desktop and rename it as [B]2020:0002
[/B]
2. Open **2020:0002** and copy/paste the following text:

[TABLE="class: outer_border, width: 800, align: left"]
[TR]
[TD]# BeetelBG64
#
# Contributor: Pushpendu Majumdar


DefaultVendor= 0x2020
DefaultProduct=0x0002


TargetVendor=  0x2020
TargetProduct= 0x2000


MessageContent="55534243106ccf810000000000000600000000000000000000000000000000"
MessageContent2="555342430820298900000000000003f0010100000000000000000000000000"


NeedResponse=1[/TD]
[/TR]
[/TABLE]

3. Save and close the file.

_**Step-5:**_

Now, in Terminal, write the following command

[TABLE="class: outer_border, width: 800, align: left"]
[TR]
[TD]xxxx@yyyy:~$ [COLOR=#800000]sudo thunar [/COLOR][COLOR=#800000]/etc/usb_modeswitch.d[/COLOR][COLOR=#800000]
[/COLOR][sudo] password for xxxx: [COLOR=#800000]****[/COLOR][/TD]
[/TR]
[/TABLE]

where "thunar" is the File Manager. You may open another File Manager of your choice. And enter your administrative (sudo) password, when prompted.

_**Step-6:**_


1. Now copy the newly created file 2020:0002 from Desktop and paste the file in the directory named **modeswitch.d**


2. Close the File Manager.


_**Step-7:**_


You are almost done. 


1. Now close Terminal and any other open application.


2. Insert 2G/3G active SIM Card and a Micro-SD Card into your Beetel BG64 HSPA 3G USB Modem. (Micro-SD Card will help you to detect whether your device is mounted automatically ore not.)

3. Now connect your Beetel BG64 HSPA 3G USB Modem to the USB Port.


If everything was right, your Micro-SD Card should be detected and mounted automatically. You should get your files and directories open on Desktop, in the File Manager.


4. If your Micro-SD card is mounted, go to next step. 
Otherwise, there might be still some issue. Reply your situation to resolve.


_**Step-8:**_


1. Now find the Network Manager Icon near the clock [Bottom-right corner of your Desktop.]


2. Right-Click Network Manager to select "Enable Networking".


3. Again, Right-Click Network Manager to select "Enable Mobile Broadband".


4. Wait a few seconds.


5. You will get a notification massage, that you are connected to GSM Network.


_**Step-9:**_


1. Right-Click Network Manager again to select "Edit Connections".
    A pop-up window called "Network-Connections" will open.


2. In the pop-up window, select the Tab named "Mobile Broadband".


3. Select "Add" button.
    A new pop-up window called "New Mobile Broadband Connection" will open.


4. Here, select the device called "Network Connect MT6229". [So, your Modem is correctly detected at last]


5. Click "Continue" button.


6. On next screen, select your "Country or region".


7. Click "Continue" button.


8. On next screen, select your "Provider".


9. Click "Continue" button.


10. On next screen, select your "Plan".[Here, check that APN is selected correctly] 


11. Click "Continue" button.


12. On next screen, review the connection summary and modify any detail if needed.


13. Click "Apply" button.
A new pop-up window called "Editing xxxx 1" will open. [Here, xxxx is your SIM Service Provider Plan name]


14. Edit the "Connection name" as you desire.


15. Select the Check-box "Connect automatically".


16. Fill in the required fields with data provided by your SIM service provider under the Tab "Mobile Broadband".


17. Select Advanced > Type: "Any"


18. Select the Check-box "Allow roaming if home network is not available"


19. Now, select the Tab "PPP Settings"


20. Click "Configure Methods..." under Authentication and De-Select ALL Check-boxes.
[Do it first time to check your device connect to internet. You may change the options one by one later as you desire. And test your connection]


21. Keep all other fields to their defaults.


22. Click "Save..." button.


23. Click "Close" button on Network Connections.


_**Step-10:**_
1. Wait a while, to establish a successful Network Connection.


[If not connected automatically, click on "Network Manager" icon.
Select your connection from "Available" list.]


You have done it.


2. Open any browser to test.


**For any query or feed-back about this process, please post your message.**

---

### Post by appugupta007 on 2014-02-06
I have tried to adopt this method, and partly became successful. I had a success to connected my dongle in ubuntu only once. In the STEP 7 /(4) My 16 GB micro sd memory card is simply not detected. Finally no device appears in the network manager device select option. I already posted in askubuntu.com, here is the link 
 [http://askubuntu.com/questions/414963/setting-up-beetel-bg64-3g-usb-modem-in-ubuntu-13-10-how-to](http://askubuntu.com/questions/414963/setting-up-beetel-bg64-3g-usb-modem-in-ubuntu-13-10-how-to)   
Please help.

---

