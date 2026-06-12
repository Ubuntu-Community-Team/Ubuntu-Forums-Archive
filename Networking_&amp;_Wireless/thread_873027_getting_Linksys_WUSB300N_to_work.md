---
title: "getting Linksys WUSB300N to work"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by Bisochim on 2008-07-28
I am a total noob at linux so please bear with me. I just installed ubuntu. Have no access to my wireless at all. I did find a thread to get it running. this what i was told to do

Download the drivers:
[http://www.atvnation.com/WUSB300N.tar](http://www.atvnation.com/WUSB300N.tar)
Extract them to /opt/ndis/:
# mkdir /opt/ndis
# tar xvf WUSB300N.tar C
/opt/ndis/
# cd /opt/ndis/Drivers
Install the Driver using NDISWrapper
# sudo ndiswrapper i
netmw245.inf
installing netmw245 ...
# sudo ndiswrapper l
netmw245 : driver installed
# sudo modprobe ndiswrapper
... go ahead and plug in the adapter ...
# sudo dmesg | grep ndis
"[ 9273.652000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[ 9273.712000] usbcore: registered new interface driver ndiswrapper
[ 9340.364000] ndiswrapper: driver netmw245 (Linksys, A Division of Cisco Systems, Inc.,12/07/2006,1.0.5.1) loaded"
You should now be able to go to your Network Applet Icon and see wireless network in the list.
... or the command iwconfig should return an entry for wlan0, mine looks like this:
wlan0 IEEE 802.11FH ESSID:off/any
Mode:Managed Channel:0 Access Point: Not Associated
Bit Rate=1 Mb/s Sensitivity=200
dBm
RTS thr=2346 B Fragment thr=2346 B
Encryption key:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
If you have an unprotected wireless hub, then issue this command to connect:
# sudo dhcpclient wlan0

First prob was that I am unable to create the dir in the OPT dir that is is saying to do I am given that I have no permission to do this. when i try to extract the files somewhere else i have errors telling me that i still cant do this. I am a long time windows user and web designer. i am trying to get into linux because i am growing to dislike windows and want more control over things if you need more info let me know again i have no idea of what i am doing here. only on page 75 of the linux bible :)
also tred to use the help files in  Linux the part where it said to click on system-hardware i do not have this option

Also tried to install ndisgtk but the program i do not have this file to install and do not know how to install something that i don't have

---

### Post by eram on 2008-07-28
alright, those instructions are just fine for someone who understands them. I don't, but [here's]("http://ubuntuforums.org/showthread.php?t=872078") a good way to get the WUSB adapter working, if you understand that way but you have trouble with it, you could try posting in that thread.
Hope you get your internet!

---

### Post by caljohnsmith on 2008-07-28
Welcome to the Ubuntu Community! :)

You don't need to put that tar file in /opt/ndis. Just put that WUSB300N.tar file in your home directory somewhere, say in Public. Then at the command line, navigate to your public folder and untar the file:
```
cd ~/Public
tar xvf WUSB300N.tar
```
Un-tarring that file will create a "Drivers" directory in the Public folder with your Windows drivers. You need to make sure you have both the ndiswrapper-common and the ndiswrapper-utils-1.9 installed to use ndiswrapper:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```
After that, just install the Windows driver:
```
cd ~/Public/Drivers
sudo ndiswrapper -i netmw245.inf
sudo modprobe ndiswrapper
```
After that, open up your network manager and see if you can find any networks, and try connecting to them. Let me know if you have any problems with the directions above.

---

### Post by nakah1 on 2008-09-10
The guide is very usefull, but when I reboot my computer the wireless connection is gone. I must enter this commands everytime
# sudo modprobe ndiswrapper

Do you have a solution for my problem.

---

### Post by caljohnsmith on 2008-09-10
> **nakah1 said:**
> The guide is very usefull, but when I reboot my computer the wireless connection is gone. I must enter this commands everytime
# sudo modprobe ndiswrapper

Do you have a solution for my problem.
Sure, just do the following command and I think it will fix your problem:
```
sudo bash -c "echo ndiswrapper >> /etc/modules" 
```
Let me know how it goes or if you still have problems.

---

### Post by ALainONE on 2008-09-10
Hey, there!  You might want to try this...

Using the Driver CD that came with the device and with ndiswrapper.

- Make sure that you have the "Windows Wireless Drivers" for NDISWRAPPER installed on your system.  

If not, you can install them via menu bar... 
Click Applications - Add/Remove.  
On the search bar, type "Windows Wireless" (without the quotes).  
Select it then "Apply Changes"

- With that one sorted out... 
Go to System - Administration - Windows Wireless Drivers.  
Enter your root password.  
Click "Install New Driver"
Browse for the "netmw245.inf" on the Driver CD that came with your device
Click "Install" then "Close"

- You should now be able to see a wireless device on the network icon at the right side of your Applications Menu.

- Configure your wireless device and that's it!!!

NOTE:  If by chance the wireless is not listed on your networks, try restarting your machine.

I hope this helps!
I have the same device and mine is working perfect!

---

### Post by carljmoss on 2008-09-17
I just want to second what ALainONE said. I did exactly the same as he suggested and it works perfectly. Using the gui makes life a lot simpler than playing with ndiswrapper and modprobe.

However, I tried last night using the .tar downloaded from atvnation. That one **didn't** work, so possibly the driver has been revised and newer cards need the new version.

---

### Post by Old_Grey_Wolf on 2008-10-18
Thank you ALainONE, that was way to easy.

---

### Post by TTGRULES on 2010-08-10
I have the exact same card... however, it would not act like it was there, even though the GUI windows wrapper said it was there... Turns out, there was a newer version of the driver.. found it on my windows installer cd.. works fine now.... its called netmw246.inf and its under the xp folder on the install cd... just added that one and it works fine...

---

### Post by aviator1 on 2010-10-16
I would like to get my wusb300n working, but am new to Ubuntu.
 
I don't understand how to install, or modify the files mentioned.
 
I have downloaded ndiswrapper, and wusb300n.tar.
 
Would I use "terminal" or someplace else?
 
Is there an "out of the box" adapter that may save a lot of headahces?
 
Thanks for any response.
 
Dave

---

### Post by Kagemusha on 2010-11-26
> **aviator1 said:**
> I would like to get my wusb300n working, but am new to Ubuntu.
 
I don't understand how to install, or modify the files mentioned.
 
I have downloaded ndiswrapper, and wusb300n.tar.
 
Would I use "terminal" or someplace else?
 
Is there an "out of the box" adapter that may save a lot of headahces?
 
Thanks for any response.
 
Dave

Yes you use terminal to do the commands. You don't have to put the # symbols in your commands but everything after that in the instructions. I am new to Linux and followed these instructions and my adapter is working now so I speak from personal 5 minute ago experience when I say this works.

As far as OOB goes I don't think there is an adapter made to work with Linux specifically. If you can use a cable from your modem/router to your computer that really is the best option. No headache because its just plug and go

---

### Post by Old_Grey_Wolf on 2010-11-26
> **aviator1 said:**
> I would like to get my wusb300n working, but am new to Ubuntu.
 
I don't understand how to install, or modify the files mentioned.
 
I have downloaded ndiswrapper, and wusb300n.tar.
 
Would I use "terminal" or someplace else?
 
Is there an "out of the box" adapter that may save a lot of headahces?
 
Thanks for any response.
 
Dave

You can get the "Windows Wireless" tool from the Ubuntu Software Center. Then use the advice ALainONE provided in the post #6 above dated September 10th, 2008. You may need to select a newer version of the driver on the CD than the "netmw245.inf". It could be netmw246.inf, netmw247.inf, or something else by now.

---

### Post by jlfarfan on 2010-12-19
Hi I'm new at Ubuntu and the whole Linux stuff. I have a big problem with my WUSB300N adapter. I had installed the Windows Wireless ndiswrapper  application from Ubuntu, then I had installed successfully the netmw245 file and the system activated my card and recognize my wireless network and others around....BUT! when I enter my wep code the system asked me for my login keyring password and that was it! everything freeze! I have not a chance to put my full password or hit enter. I have waited a half an hour to see if this change and nothing happens, the whole system is frozen. I have try several times and nothing. I had to force the shutdown and restart the system and many times not even restart I just get a gibberish letters I don't understand. I have reinstalled Ubuntu and gone through the whole process twice with the same result. I don't want to go back to windows. Anyone can help?
Ubuntu 10.10 (Maverick)
GNOME 2.32.0
RAM: 1Gb
Processor Intel Pentium 4 1.80 GHz

---

### Post by bincue on 2011-04-05
I've the same Linksys WUSB300N Wifi Adapter using netmw245.inf, when I get to the keyring and type in the password, then retype.... complete system FREEZE. This is the only thing holding me up from completely moving to only Linux with this one particular desktop.

I too could use a workaround that keyring.  I'm only trying to make a wireless connection.. sheesh.
OS: Debian 'squeeze' stable
Desktop Environment: XFCE4
Ram: 1.5Gb
Processor: AMD 2200+

---

### Post by bincue on 2011-04-05
Just tried same adapter on UBUNTU STUDIO 10.04 Lucid Lynx... keyring lockup.

---

### Post by fluteflute on 2012-07-16
This is simply not working for me in 12.04

"Windows Wireless Drivers" happily loads netmw245.inf and tells me the hardware is present. But Network Manager isn't displaying a list of networks.

---

