---
title: "Belkin N1"
date: 2008-04-13
forum: Networking &amp; Wireless
---

### Post by Jack to Jill on 2008-04-13
So, I have a belkin n1 wireless adapter, and I have no idea what to do. I just pluged it into my usb port, and I dont even now where to start after that

---

### Post by chili555 on 2008-04-14
Usually, when a card is not recognized, it's because a driver can't be found or loaded. Sometimes, there is a driver and we need to identify it and load it up. Sometimes, in new cards, no Linux driver exists yet, and we must use a wrapper and the Windows driver. First, let's find out what we have. Please plug in the device, open up a terminal and do:
```
lsusb
lshw -C network
```

Post the data that relates to your Belkin and we'll go from there.

---

### Post by Jack to Jill on 2008-04-14
jill@jill-jill:~$ lsusb
Bus 004 Device 003: ID 050d:815c Belkin Components 
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
jill@jill-jill:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:ca:91:f9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.18 firmware=N/A ip=68.37.232.10 latency=0 module=sky2 multicast=yes
  *-network
       description: Wireless interface
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wifi0
       version: 01
       serial: 00:19:7e:70:d8:74
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

### Post by Jack to Jill on 2008-04-14
O, and I have a bilt-in wireless, but I wanted to get a better one/one with a visible antenea

---

### Post by chili555 on 2008-04-14
Looks to me as if it's all set and ready to go. However, your ethernet is connected and has an IP address: NetworkManager will not activate the wireless as long as wired is in place. Please see [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) especially:> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has has been managed for themSo, please detach the cable, then go to System -->Administration-->Network and un-check Wired and check Wireless. Select Properties and fill in your ESSID and any encryption details and it should connect.

Post back if you need more help.

---

### Post by Jack to Jill on 2008-04-14
I have roaming mode on, I can just see the available networks in the connections window, and connect. I guess I now want to know how to switch between the usb wireless and the built in, and how to tell wich one is on.

---

### Post by chili555 on 2008-04-15
Well, there is good news and not-so-good news. I was researching the chipset  in your Belkin N1 USB and compared it to your *lshw.* According to my research, the Belkin uses a Marvell chipset for which there is no Linux driver yet. To get this device working, you will have to use the Windows driver with ndiswrapper. kevdog has a great tutorial here: [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

You connected using your built-in. As you can see from the *lshw* the logical name of the built-in is wifi0. If you install ndiswrapper, the logical name will be wlan0.

The only way I know of to be *sure* you are using the Belkin is to disable the built-in with the switch or key combination on your laptop or in the BIOS. You probably could also do it from a terminal:```
sudo ifconfig wifi0 down
sudo ifconfig wlan0 up
```Are to trying to get "N" capabilities specifically? ndiswrapper and disabling the built-in seems like a pain when you have a wonderfully, perfectly working wireless card in place right now.

---

### Post by Jack to Jill on 2008-04-15
Well, first of all, you are being very helpfull, so thanks. Looking at this, it seems that the bilt in is as good as the belkin? But, my whole goal in all of this is to use that belkin so I can boost the range, with a dish or something,  because I dont know were the built in is physicaly located.

---

### Post by chili555 on 2008-04-16
Usually, in a laptop, the wireless card is deep within the mechanism, often, under the keyboard. They require an antenna to operate well, and the antenna is typically a wire around the display. It's more of an antenna than a USB dongle, and sits higher, but doesn't really lend itself to hacks, mods or experimentation.

Let's see if we can get the Belkin USB going. First, please figure out how to disable your built-in. There may be a switch on your laptop, or a key combination, Fn+F5, perhaps or you may need to go into the BIOS as the machine is booting up and find a place that you can enable/disable wireless.

Next, plug that ethernet cable back in and go to System ->Administration -> Synaptic and install ndisgtk, ndiswrapper-common, ndiswrapper-utils-1.9, cabextract, unshield, unrar and unzip. There will be some dependencies and you might as well Mark All Upgrades, hit Apply and sit back and let everything install.

Now, get the install CD that came with your Belkin and load it in your CD drive. It should pop up an icon on your desktop. Right click it and Browse Folder. The biggest file you will find will be an .exe file. The next step is to open a terminal and use cabextract, unshield, unrar or unzip to pop open the .exe. You will be looking for a Windows XP folder where you will see Mrvw245.sys
and netmw245.inf. Drag-n-drop these into Places -> Home Folder. If we are very lucky, the .inf and .sys may be in their own file and not need surgical extraction!

Then start *sudo ndisgtk* in the terminal and Install New Driver. Point it to the .sys and .Inf files and you should be up and running.

Needless to say, post back if you get stuck.

---

### Post by chili555 on 2008-04-16
Is yours a version 2000 or version 3000? They use different chipsets! Also, I downloaded the version 2 driver from Belkin's website, and, so far, I have only been able to get the .inf and .sys files with Wine (a nice Pinot Noir, actually.) Please let me know your progress.

---

### Post by Jack to Jill on 2008-04-16
The reason I got the belkin cheap, was that the disk was stolen from the box.  And what about 2000, 3000

---

### Post by chili555 on 2008-04-16
Look all over it, at everything written, embossed or branded into the plastic or otherwise and see if anything says a version number. It will probably say 2000, 3000, 2 or 3. We need that information because one driver will not work with the other.

---

### Post by Jack to Jill on 2008-04-16
v3 :)

---

### Post by chili555 on 2008-04-17
Excellent! Glad you found it!

This is a Ralink rt2870 chipset, Ralink actually has a driver which we might try first: [http://www.ralinktech.com.tw/data/drivers/2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2) I suggest this, because the .inf and .sys files are a real pain to get and I would like to try the easier method before we try the harder.

Open a terminal and do:```
sudo apt-get build-essential
wget http://www.ralinktech.com.tw/data/drivers/2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2
tar -xvzf 2007_1220 <press_Tab_it_will_fill_in> 
cd 2007_1220 <Press_Tab>
sudo make
sudo make install
sudo cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
sudo modprobe rt2870sta
```You should now see your N1 light up and when you do *iwconfig* you should have a new wireless interface *ra0.*If you have your built-in disabled, you should now be able to do:```
sudo iwconfig ra0 essid <your_essid>
sudo dhclient ra0
```Are you connected?

---

### Post by Jack to Jill on 2008-04-17
jill@jill-jill:~$ sudo apt-get build-essential
E: Invalid operation build-essential
jill@jill-jill:~$ wget [http://www.ralinktech.com.tw/data/drivers/2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2)
--22:22:55--  [http://www.ralinktech.com.tw/data/drivers/2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2)
           => `2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2'
Resolving [www.ralinktech.com.tw](www.ralinktech.com.tw)... 192.72.83.242
Connecting to www.ralinktech.com.tw|192.72.83.242|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 464,504 (454K) [application/octet-stream]

100%[====================================>] 464,504       65.32K/s    ETA 00:00

22:23:03 (63.04 KB/s) - `2007_1220_RT2870_Linux_STA_v1.2.1.0.tar.bz2' saved [464504/464504]

jill@jill-jill:~$ tar -xvzf 2007_1220 <press_Tab_it_will_fill_in> 
bash: syntax error near unexpected token `newline'
jill@jill-jill:~$ cd 2007_1220 <Press_Tab>
bash: syntax error near unexpected token `newline'
jill@jill-jill:~$ sudo make
make: *** No targets specified and no makefile found.  Stop.
jill@jill-jill:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
jill@jill-jill:~$ sudo cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
cp: cannot stat `RT2870STA.dat': No such file or directory
jill@jill-jill:~$ sudo modprobe rt2870sta
FATAL: Module rt2870sta not found.
jill@jill-jill:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:788052  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jill@jill-jill:~$ 






that is not good, right?

---

### Post by chili555 on 2008-04-18
Oops! I meant to say:```
sudo apt-get **install** build-essential
```

Next, did you actually type or copy and paste *<press_Tab_it_will_fill_in> *? I meant for you to actually press the TAB key and watch the terminal fill in *_RT2870_Linux_STA_v1.2.1.0.tar.bz2* for you, so you wouldn't have to type it and risk a mistake. Then press Enter to execute the command.

Once you see an error:```
bash: syntax error near unexpected token `newline'
``` there is no need to go on to the next error and the next. Each step depends on the successful completion of the last.

We are learning about Linux!

Try again and we'll crack this nut if it kills me.

---

