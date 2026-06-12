---
title: "Can some kind soul please help me get my wireless card working?"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by I Use Dial on 2008-11-22
I have a Linksys WPC55AG.  I haven't been able to get it to work since I 'upgraded' to 8.04.

---

### Post by Joe2Shoe on 2008-11-22
Go to System/Adminlstration/Hardware Drivers to see if your wifi card's drivers are listed there.
If so, click on the driver, then click the 'activate' button below.
Reboot.
Try connecting.

---

### Post by I Use Dial on 2008-11-22
Already done - Atheros Hardware Access Layer (HAL) and Support for Atheros 802.11 wireless LAN cards were both already enabled.

---

### Post by Joe2Shoe on 2008-11-22
I had the same problem, until I updated the repositories.

You must enable all the repositories to be able to download the needed drivers for your system:

Go to System/Administration/Synaptic Package Manager.
Enter password.
Click Settings/Repositories.
Under the "Ubuntu Software" tab, check the first 4 choices, and your region (United States).
Under the "Third-Party Software" tab, check both choices.
Under the "Updates" tab, under "Ubuntu updates", check the first 2 choices.
Under "Automatic Updates", check "Check for updates: daily".
Close.
File/Quit.
Reboot.
Your pc will check all repositories and download all the required updates for your system.

---

### Post by I Use Dial on 2008-11-22
I did all that, and it still isn't working.

In Network Settings the computer can see the network because the signal level is about right, but I can't get it to connect.  I enter the password using copy and paste from the exact same file that I use to copy and paste for Windows, so I know the password is correct.

---

### Post by Joe2Shoe on 2008-11-22
In the top-right of the screen, right-click the "Network Manager" icon (the signal strength bar).
Left-click on "Edit Connections".

Click the "Wireless" tab
Click your network's name, then click "Edit".

Connect automatically: is Checked
System setting: is not Checked

Under the "Wireless" tab
SSID: name of network
Mode: Infrastructure
BSSID: blank
MAC address: blank
MTU: automatic

Under the "Wireless Security tab"
Security: WPA & WPA2 Personal (or whatever type of encryption you used on your wireless router).
Password: xxxx

Under the "IPv4 Settings tab"
Method: Automatic (DHCP) or Automatic (DHCP Address only)

Save/Exit.
Try connecting again.

---

### Post by I Use Dial on 2008-11-22
I don't have a 'Network Manager' icon.

---

### Post by Joe2Shoe on 2008-11-22
Try this.

Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper.  This allows you to use a Windows wireless device driver under Ubuntu.

   1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2. Install ndisgtk (System/Administration/Synaptic Package Manager).
   3. Open ndisgtk (System/Administration/Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
   6. Click OK.


[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

Even though the driver seems to be activated and 'working fine', it isn't.  That was my case, also.

Copy the .inf Window's driver file for your wifi's card to a flash drive or cd, then copy it to your desktop in Ubuntu.
After installing NDISwrapper per the above link, locate the driver file and install it.
Then go to System/Administration/Hardware Drivers, and the driver should be listed, activate it, reboot if necessary (most often is), and check wifi connection.

---

### Post by Joe2Shoe on 2008-11-22
> **I Use Dial said:**
> I don't have a 'Network Manager' icon.

You can go to System/Preferences/Network Configuration to edit the configuration of your wifi card.
If configured correctly, it will put the "network Manager' icon back up in the top-right corner by the clock (time).

---

### Post by Joe2Shoe on 2008-11-22
Using Windows Wireless Drivers

Ubuntu supports a system known as NDISWrapper.  This allows you to use a Windows wireless device driver under Ubuntu.

   1. Obtain the Windows Driver for your system and locate the file that ends with .inf.
   2. Install ndisgtk (System/Administration/Synaptic Package Manager).
   3. Open ndisgtk (System/Administration/Windows Wireless Drivers).
   4. Select Install new driver.
   5. Choose the location of your Windows .inf file and click Install.
   6. Click OK.


[https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.10/internet/C/ndiswrapper.html)
Install NDISwrapper so you can install the Windows driver for your wifi card.

Even though the driver seems to be activated and 'working fine', it isn't.  You may have a great signal strength, but no connection.  That was my case, also.

Copy the .inf Window's driver file for your wifi's card to a flash drive or cd, then copy it to your desktop in Ubuntu.
After installing NDISwrapper per the above link, locate the driver file and install it.
Then go to System/Administration/Hardware Drivers, and the driver should be listed, activate it, reboot if necessary (most often is), and check wifi connection.

---

### Post by I Use Dial on 2008-11-22
The driver is not listed in the hardware drivers.  The old wireless drivers are not in use.

I have rebooted and it still will not connect to the router.

---

### Post by Olivier2371 on 2008-11-22
I Use Dial,

Tell me is your wireless adapter is the pcmcia Linksys WPC55AG, or an Atheros wireless adapter.

Forget I asked.

---

### Post by I Use Dial on 2008-11-22
It is a Linksys WPC55AG, which I understand to be have an Atheros chip in it.

---

### Post by Olivier2371 on 2008-11-22
Yes  I googled it. Which is why I wrote "forget I asked".

I do have a pcmcia card from linksys but can find it as yet.

I'll keep you posted.

---

### Post by Olivier2371 on 2008-11-23
You could also try on of these links.

[http://linuxwireless.org/en/users/Drivers/ath5k]("http://linuxwireless.org/en/users/Drivers/ath5k")

[http://linuxwireless.org/en/users/Drivers/ath9k]("http://linuxwireless.org/en/users/Drivers/ath9k")

---

### Post by I Use Dial on 2008-11-23
Okay, I looked at those pages.  The MadWiFi driver is already installed on my computer.

---

### Post by Olivier2371 on 2008-11-23
When you click left on the network icon do you see any wireless network there.(post screenshot of it if you can)

---

### Post by I Use Dial on 2008-11-23
When I click left on the networking icon I get the following message:

Please contact your system administrat to resolve the following problem:

SIOCGIFFLAGS error: No such device

---

### Post by Olivier2371 on 2008-11-23
Did you remove NDISWrapper?

---

### Post by I Use Dial on 2008-11-23
I have removed NDISWrapper and I still have the error.

---

### Post by Olivier2371 on 2008-11-23
Did you do a full update after upgrading to unbuntu 8.04? before enabling the restricted drivers.

---

### Post by I Use Dial on 2008-11-23
I did a fresh install.

---

### Post by Olivier2371 on 2008-11-23
yes me too I did a full install, but I changed some of the settings in Software Sources, to get the update. For my laptop I had 304 updates.

Then after the updates I restarted the machine and then unabled the restricted drivers, then restated again.

---

### Post by I Use Dial on 2008-11-23
I have no available updates and all stable repositories are checked.

Do you have a WPC55AG?

---

### Post by Olivier2371 on 2008-11-23
I had one not long ago but I have changed all my systems to a more unbuntu friendly sytem.

Please find below screenshots of my Software Sources, and compare it to yours.

[ATTACH]93886[/ATTACH]

[ATTACH]93887[/ATTACH]

[ATTACH]93888[/ATTACH]

---

### Post by I Use Dial on 2008-11-23
I don't use proposed (my Software Sources calls it 'Pre-released') updates, everything else is pretty much the same.

---

### Post by Olivier2371 on 2008-11-24
I have check the spare wireless pc card I have, but it is an older model

which support only WEP encryption.

WPC11 version3.

Funny enough I just tried it under Ubuntu 8.04 and found no trouble connecting to the internet. I wasn't even asked to install a restricted driver. Sometimes I just love my laptop. I was connecting using WEP of course I changed the encrytpion settings in the router to reflect the wep settings.

---

### Post by I Use Dial on 2008-11-26
Still not working.

---

### Post by I Use Dial on 2008-12-04
Bump.

---

### Post by I Use Dial on 2008-12-06
Bump.

---

### Post by I Use Dial on 2008-12-10
Bump.

---

