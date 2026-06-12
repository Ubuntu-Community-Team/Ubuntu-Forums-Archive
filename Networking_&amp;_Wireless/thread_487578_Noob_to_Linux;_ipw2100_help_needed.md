---
title: "Noob to Linux; ipw2100 help needed"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by jloo25 on 2007-06-29
Alright, so here's the deal:  I have Feisty with the kernel 2.6.20-16 and an Intel 2100 card in my laptop.  I've been able to (i think) install ndiswrapper as well as ndisgtk, and I also downloaded the necessary .zip driver file from intel's site.  I unzipped it, and tried adding the new driver via ndisgtk...but every time i "add" the .inf file, it doesn't show up as listed.

So could someone **pretty, pretty please** help a poor newbie out walk me through this.  I've tried other walkthrough's but i never seem to get it right, which is why I tried to go the gui route.

---

### Post by Ayuthia on 2007-06-29
Let's start with the basics by finding out what you have and how far along you are.  Can you post the following:
lspci -n (to verify the pci id of your card)
ndiswrapper -v (to find the version of ndiswrapper)
ndiswrapper -l (to see if anything is installed)
Which driver you are trying to install and where you got the drivers

Edit: I forgot a couple of items to include:
ifconfig
iwconfig

---

### Post by jloo25 on 2007-06-29
Alrighty, well here's the vitals:

jason@jason-laptop:~$ lspci -n
00:00.0 0600: 8086:3340 (rev 03)
00:01.0 0604: 8086:3341 (rev 03)
00:1d.0 0c03: 8086:24c2 (rev 01)
00:1d.1 0c03: 8086:24c4 (rev 01)
00:1d.2 0c03: 8086:24c7 (rev 01)
00:1d.7 0c03: 8086:24cd (rev 01)
00:1e.0 0604: 8086:2448 (rev 81)
00:1f.0 0601: 8086:24cc (rev 01)
00:1f.1 0101: 8086:24ca (rev 01)
00:1f.5 0401: 8086:24c5 (rev 01)
00:1f.6 0703: 8086:24c6 (rev 01)
01:00.0 0300: 1002:4c66 (rev 02)
02:00.0 0200: 14e4:165d (rev 01)
02:01.0 0607: 1217:7113 (rev 20)
02:01.1 0607: 1217:7113 (rev 20)
02:03.0 0280: 8086:1043 (rev 04)

jason@jason-laptop:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.38
vermagic:       2.6.20-16-generic SMP mod_unload 586 

jason@jason-laptop:~$ ndiswrapper -l
jason@jason-laptop:~$ 

As for the driver, its from Intel's site version 1.2.5.37  It is an XP driver, and I downloaded it for two reasons: 1. was because I could not find a ".inf" file in the downloads from iwp2100.sourceforge.net and 2. because I read on another forum that a person could just use it's ".inf" file and that everything would be golden.

jason@jason-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:56:E2:AE:8A  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:fee2:ae8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27864 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25868 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24103789 (22.9 MiB)  TX bytes:4916836 (4.6 MiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:0C:F1:44:81:EE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0x8000 Memory:fafef000-fafeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 b)  TX bytes:500 (500.0 b)

jason@jason-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by Ayuthia on 2007-06-29
Ok.  Your pciid appears to be 8086:1043.  The 2100 appears to have more than one version so I just wanted to be sure that we know which version you have.  

I would like to see one more thing:
iwlist scan (to list out what your wireless can see--possible that nothing shows)

After this, if we don't see anything with the scan, we will start with what you have and see if we can get anywhere.  If not, we will have to remove this installation of ndiswrapper and compile a newer version.

If we do see something, we will see if we can connect.

By the way, if you have a wireless network light, is it on?

---

### Post by jloo25 on 2007-06-29
jason@jason-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

And as for my light, it is........off. haha

---

### Post by Ayuthia on 2007-06-29
Ok.  Lets go ahead and try to install your driver.  Go to the directory where you have your driver and do the following:
sudo ndiswrapper -i driver.inf

replace driver.inf with your file.  Post the results and then if all looks ok, we shall need to do this:

ndiswrapper -l

---

### Post by jloo25 on 2007-06-29
jason@jason-laptop:~$ sudo ndiswrapper -i /home/jason/Desktop/WirelessConfig/w70n501.inf
driver w70n501 is already installed

that's interesting, because i've never seen it verified as "installed"

and on a side note, thanks a lot for helping me out

---

### Post by Ayuthia on 2007-06-29
Don't thank me yet, we don't have it running!  :p

Ok, we are going to try to remove it and see if we can install it again to see what information we pick up.  Lets now enter:
sudo ndiswrapper -e w70n501.inf (This will remove the driver)

By the way, in the directory where you have your .inf file, are there any other files?  With the Broadcom cards, they usually need some .sys files also.

---

### Post by jloo25 on 2007-06-29
Haha, that's true but I have faith. 

I tried it two ways, one without the specific location and one with the directory:

jason@jason-laptop:~$ sudo ndiswrapper -e w70n501.inf
couldn't delete /etc/ndiswrapper/w70n501.inf: No such file or directory

jason@jason-laptop:~$ sudo ndiswrapper -e /home/jason/Desktop/WirelessConfig/w70n501.inf
couldn't delete /etc/ndiswrapper//home/jason/Desktop/WirelessConfig/w70n501.inf: No such file or directory

As for the files, yea there's a couple ".sys" and an .exe plus a few others

---

### Post by Ayuthia on 2007-06-29
My mistake.  Lets try the command again without the .inf extension:
sudo ndiswrapper -e w70n501

If that doesn't work please list out what is in /etc/ndiswrapper:
ls -l /etc/ndiswrapper

Ok, when we do the install we will have to change to that directory so that ndiswrapper will find those .sys files.

---

### Post by jloo25 on 2007-06-29
Alright, well I believe that worked.  I entered the command, it dropped down to a new line.  So I entered it again just to be sure:

jason@jason-laptop:~$ sudo ndiswrapper -e w70n501
jason@jason-laptop:~$ sudo ndiswrapper -e w70n501
couldn't delete /etc/ndiswrapper/w70n501: No such file or directory

---

### Post by Ayuthia on 2007-06-29
Ok, the next thing we will do is change to the directory where the drivers live and try to install the driver:

cd /home/jason/Desktop/WirelessConfig/ (I am guessing that is where your .inf and .sys files are located--if they are not there, please change to that directory)

sudo ndiswrapper -i w70n501.inf

Post any messages that come from that and if it looks good, we will try:
ndsiwrapper -l

---

### Post by jloo25 on 2007-06-29
Well it looked pretty good, so i went ahead and did ndiswrapper -l:

jason@jason-laptop:~/Desktop/WirelessConfig$ sudo ndiswrapper -i w70n501.inf
installing w70n501 ...

jason@jason-laptop:~/Desktop/WirelessConfig$ ndiswrapper -l
w70n501 : driver installed
        device (8086:1043) present (alternate driver: ipw2200)

---

### Post by Ayuthia on 2007-06-29
Ok.  We will keep an eye on the alternate driver (ipw2200).  If we can't get connected, we will try to remove and blacklist it because it might be interfering with ndiswrapper.

Lets go ahead and see what happens when we do this:
sudo modprobe ndiswrapper

Wait for a little bit and see if the wireless lights up.  We can then do iwconfig and iwlist scanning next.

---

### Post by jloo25 on 2007-06-29
Welp, I didn't see the wireless light come on and i did the iwconfig and scanning, doesn't look good:

jason@jason-laptop:~/Desktop/WirelessConfig$ sudo modprobe ndiswrapper

jason@jason-laptop:~/Desktop/WirelessConfig$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jason@jason-laptop:~/Desktop/WirelessConfig$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

---

### Post by Ayuthia on 2007-06-29
Ok.Before we try to reinstall ndiswrapper, lets try to blacklist the alternate driver and see what it does.

echo 'blacklist ipw2200' | sudo tee -a /etc/modprobe.d/blacklist
sudo ndiswrapper -e w70n501

We will then need to reboot.  I think that if we don't want to do a reboot, we could just do:
sudo rmmod ipw2200

The only thing that I am not sure about is if the rmmod would permanently remove that driver or not.  I don't think that it does, but I don't want to chance it on someone else's computer.

By the way, are you wired to the network using ubuntu or are you on another computer?  If you are using this computer with a wired connection, we will have to disconnect when we reach the golden moment.

---

### Post by jloo25 on 2007-06-29
Well first, just for records sake:
jason@jason-laptop:~/Desktop/WirelessConfig$ echo 'blacklist ipw2200' | sudo tee -a /etc/modprobe.d/blacklist
Password:
blacklist ipw2200
jason@jason-laptop:~/Desktop/WirelessConfig$ sudo ndiswrapper -e w70n501
jason@jason-laptop:~/Desktop/WirelessConfig$ 

Yes, I am connected with this laptop via ethernet cable...so thats gonna be a little scary come the moment of truth..and its not that I don't trust you, but since you're not totally confident yourself, I'm just going to go ahead and reboot right now

---

### Post by jloo25 on 2007-06-29
back

---

### Post by Ayuthia on 2007-06-29
Let's try the install of the driver again since we blacklisted the alternate:

cd /home/jason/Desktop/WirelessConfig/ 

sudo ndiswrapper -i w70n501.inf

Post any messages that come from that and if it looks good, we will try:
ndsiwrapper -l

You can also do the iwconfig and iwlist scan

If you don't hear back from me for a few minutes, it is because I am writing up the instructions for downloading ndiswrapper and installing it (in case this step does not work).

---

### Post by jloo25 on 2007-06-29
Haha, ok, i'll just be waiting because I don't think it worked.  And the alternate driver is still listed:

jason@jason-laptop:~/Desktop/WirelessConfig$ sudo ndiswrapper -i w70n501.inf
Password:
installing w70n501 ...

jason@jason-laptop:~/Desktop/WirelessConfig$ ndiswrapper -l
w70n501 : driver installed
        device (8086:1043) present (alternate driver: ipw2200)

jason@jason-laptop:~/Desktop/WirelessConfig$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jason@jason-laptop:~/Desktop/WirelessConfig$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

---

### Post by t4thfavor on 2007-06-29
Did I miss something or did you already try the open source drivers for that card? I would assume they would be better than the ndiswrapper alternative.

---

### Post by Ayuthia on 2007-06-29
I forgot two more steps:
sudo depmod -a
sudo modprobe ndiswrapper

If that does not work, here are the instructions for the install of ndiswrapper.  If these steps do not work, we will have to search for other drivers.

Step 1:
Remove any prior installations:
sudo rmmod ndiswrapper
sudo ndiswrapper -e w70n501
sudo apt-get remove ndiswrapper-utils

Step 2:
Grab the necessary packages for installing ndiswrapper:
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`  (the ` is a backquote not the single quote)

Step 3:
Download ndiswrapper:
[http://sourceforge.net/project/showfiles.php?group_id=93482](http://sourceforge.net/project/showfiles.php?group_id=93482)

Step 4:
Change to the directory where you downloaded ndiswrapper and extract the file:
tar -xzvf ndiswrapper-1.47.tar.gz

Step 5:
Change to the extracted directory and prepare for isntall:
cd ndiswrapper-1.47
sudo make uninstall

Step 6:
Make the installation:
sudo make
sudo make install

Step 7:
Change to the driver directory and load the driver:
cd /home/jason/Desktop/WirelessConfig/
sudo ndiswrapper -i w70n501.inf

Step 8:
Check to see if the driver is loaded:
ndiswrapper -l

Step 9:
Load the module:
sudo depmod -a
sudo modprobe ndiswrapper

Step 10:
See if it all worked:
iwconfig
iwlist scan

---

### Post by Ayuthia on 2007-06-29
I guess I assumed that it was done already.  If you have not tried, we should do that first.  There are some cases where the open source set works out of the box.  

If you have not tried it yet, do the following to remove the drivers:
sudo rmmod ndiswrapper
sudo ndiswrapper -e w70n501

You will also have to go into /etc/modprobe.d/blacklist and remove the line 'blacklist ipw2200':
gksu gedit /etc/modprobe.d/blacklist

reboot and check by doing the iwconfig and iwlist scan 

If those steps work, I am very sorry that I dragged you through all this.

---

### Post by t4thfavor on 2007-06-29
I use the ipw2200 drivers on an ipw2200B/G card, I am sure its not much different than a 2100B card.

---

### Post by jloo25 on 2007-06-29
well i didn't know of any open source drivers..but i do know that i just rebooted and did iwconfig/list scan and it doesn't work...so I'm guessing I should do the ndiswrapper procedure you laid out?:

jason@jason-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jason@jason-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

---

### Post by Ayuthia on 2007-06-29
t4thflavor, do you know your pciid?  I would like to know for future reference?  If you don't mind posting your lspci and lspci -n info for your card, that would be helpful for me so that I can keep track of what works and what doesn't.

jloo25, it looks like that we will need to go through the steps unless someone knows the answer to why eth1 comes up as unassociated.

---

### Post by t4thfavor on 2007-06-29
eth1 unassociated ESSIDff/any Nickname:"ipw2100"
Mode:Managed Channel=0 Access Point: Not-Associated
Bit Rate=0 kb/s Tx-Powerff
Retry limit:7 RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Thats it right there. Its working, its just off. Type sudo iwconfig eth1 power on and try pushing the hardware wireless switch if there is one. if the drivers put it there I can bet it will work just fine. Ths above command might not be the correct one, but thats what it is. alternatively you could try to config it with iwconfig commands to the tune of this.
#!/bin/bash
sudo iwconfig eth1 essid "Something" key D265AE2C7B6B3
sudo iwconfig eth1 channel your channel
sudo dhclient eth1


As for  my lspci -n
02:04.0 0280: 8086:4220 (rev 05)
lspci
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

### Post by Ayuthia on 2007-06-29
Are you able to scan for wireless sites via iwlist scan or by any other means?

---

### Post by jloo25 on 2007-06-29
Well I don't think it worked, here are the iwconfig/list scan, i'm pretty sure the rest of the commands went through properly as I did not get any denials, or invalids...I then tried t4thfavor's way and that is the final couple of commands:

jason@jason-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jason@jason-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
*******
jason@jason-laptop:~$ cd /home/jason/Desktop/WirelessConfig/
jason@jason-laptop:~/Desktop/WirelessConfig$ sudo iwconfig eth1 power on
jason@jason-laptop:~/Desktop/WirelessConfig$ #!/bin/bash
jason@jason-laptop:~/Desktop/WirelessConfig$ sudo eth1 essid "______" key D265AE2C7B6B3
jason@jason-laptop:~/Desktop/WirelessConfig$ sudo iwconfig eth1 channel 11

Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Operation not supported.
jason@jason-laptop:~/Desktop/WirelessConfig$ sudo dhclient eth1

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:0c:f1:44:81:ee
Sending on   LPF/eth1/00:0c:f1:44:81:ee
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by Ayuthia on 2007-06-29
If you want to try it his way, you will need to disable the ndiswrapper module first.
sudo rmmod ndiswrapper
sudo ndiswrapper -e w70n501

You can then try his method.  Also, before you test the wireless, you will need to disconnect from the wired world first (if you are connected directly to the router).

---

### Post by jloo25 on 2007-06-29
thanks, but yea that didn't work either...i still got the channel error too...i don't know whats going on..i've been at this for over 14 hours now

---

### Post by Ayuthia on 2007-06-29
The only thing that I can think of is to try other drivers.  Some other recommended ones are listed here:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_g-l/)
Just search for the ones that match your card and your pciid (8086:1043).  What you will need to do is remove the current driver and install the new one:
sudo rmmod ndiswrapper
sudo ndiswrapper -e <current.inf>
cd <location of new driver>
sudo ndiswrapper -i <new.inf>
sudo depmod -a
sudo modprobe ndiswrapper

Can you let me know what type of laptop you have and also post the information for:
lspci      (it will list the name of your network card)
iwconfig    (I would like to see what it is saying after you tried to connect)

If you need to rest, go for it.  I am going to continue to search and see if I can find anything.

---

### Post by t4thfavor on 2007-06-29
The module is working, there is just something else going on. I would recomment uninstalling ndiswrapper via synaptic. Is there a wireless switch on that machine (one you push to turn the wireless card off)? If so I would recommend pushing it and seeing if anything happens to your iwconfig output. 

If the driver wasn't working you wouldnt get eth1 in the list it would just not show up. That part is half the battle. Is there anyway you can install wicd or something like it (perhaps wifi-radar) those are supposed to work a bit better on the wireless nics than the gnome-network-manager.

Sorry I couldnt get your stuff working for ya, I just thought you should try the native linux drivers before the ndis ones since they are actually made for linux, and not windows.

If you have anymore problems feel free to contact me.

---

### Post by jloo25 on 2007-06-29
Yea, i am definitely going to go rest.  Thanks for the help, it sucks we didn't get anywhere..i have a dell latitude D600 and t4thfavor, there isn't a wireless button..i'll check back later tonight, thanks again..here is lspci:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
***
iwconfig
jason@jason-laptop:~/Desktop/WirelessConfig$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"loomis"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate=0 kb/s   Tx-Power:off   
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by t4thfavor on 2007-06-29
I think the wireless button on that is fn+F2 I got one around here somewhere I will look for it.


EDIT: Confirmed the wireless kill switch on the Dell is fn+F2 it toggles the hardware kill switch.

---

### Post by jloo25 on 2007-06-29
Awesome, thanks t4thfavor and Ayuthia, it is working beautifully now, after toggling the F2 and some other finagling with iwconfig and such...thanks again

---

### Post by louiech21 on 2007-07-17
Hey guys I am in a similar situation, I have an HP Pavillion ze2000 and I believe I also have an ipw2100 wireless card.  I've been going through as much of these threads as possible and I am willing to try anything to get my wireless working in Ubuntu 7.04  

Do you have any suggestions?  I have the Wireless Network Drivers program, I can't find any .inf files at all.:(

---

### Post by louiech21 on 2007-07-19
I used this site to set my wireless up and it's been good ever since, maybe this will help you I would suggest trying it at least to see if it will work for you.  I was practically dancing in the streets once I saw my wireless LED finally turn on!!!!

I know this link says it's for Broadcom but it worked for me and I also have the same card and I'm online with it.  I hope this will be of some help to you.

[http://ubuntuforums.org/showthread.php?t=434946&highlight=bcm4310]("http://ubuntuforums.org/showthread.php?t=434946&highlight=bcm4310")

---

