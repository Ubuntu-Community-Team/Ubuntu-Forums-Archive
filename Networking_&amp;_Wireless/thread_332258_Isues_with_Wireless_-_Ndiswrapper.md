---
title: "Isues with Wireless - Ndiswrapper"
date: 2007-01-05
forum: Networking &amp; Wireless
---

### Post by Nightknight83 on 2007-01-05
Greetings,

I have an issue setting up my Internet connection.

I shall describe what I've done so far:

I installed Ndiswrapper Utils 1.8 using the Ubuntu 6.10 CD.

Installed the drivers (*.inf)
$sudo ndiswrapper -i driver.inf

After I run $sudo ndiswrapper -l I get a successfull message
Driver Present, Hardware Present.

NOW the trouble comes:

When I run:
sudo modprobe ndiswrapper or
modprobe ndiswrapper

FATAL: Module not present.

Any thoughts? 

Thanks

---

### Post by Metaljaz on 2007-01-05
what wireless card are you using?
You may have to blacklist any previously installed drivers.

---

### Post by Nightknight83 on 2007-01-05
88w8335 [Libertas] 802.11b/g Wireless

I installed the proper driver (Came in the manufacturer CD)
Older drivers shouldn't be an Issue, since I just installed Ubuntu 6.10 like 4 hours ago. :-)

BTW, this is hard with Wireless

---

### Post by Metaljaz on 2007-01-05
run this command to see what driver is present.
ndiswrapper -l

What is the output?

---

### Post by Nightknight83 on 2007-01-05
As I said before, it's successful

MRV8000c driver.

Driver present, Hardware present.

---

### Post by Metaljaz on 2007-01-05
See if this helps:

Bring up the driver:

user@ubuntu:~$  sudo depmod -a
user@ubuntu:~$  sudo modprobe ndiswrapper

If you do not get any errors and your system does not immediately freeze the driver should now be loaded. It may take a few seconds (12 - 30) for the modprobe to return, please wait. Do not reboot until we have made some basic checks and installed the driver permanently.
Step 6 - Install the device and configure the network settings

Issuing an iwconfig command should reveal that your device is waiting to be configured, similar to this one:

user@ubuntu:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          RTS thr:2432 B   Fragment thr:2432 B   
          Power Management:off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


You should be able to put your data in through the System-->Administration-->Networking applet. You just need to end up with the record formats that I am showing in my example. I used gedit to put the required record into the /etc/network/interfaces file: (note that the Xs are your actual WEP key.)

user@ubuntu:~$  sudo gedit /etc/network/interfaces

Create a record that looks like this: (Note we are using 128bit WEP encryption in this example.)

iface wlan0 inet dhcp
wireless-essid My_Essid
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX
auto wlan0

Save the file.

Make the driver permanent using the ndiswrapper method:

user@ubuntu:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
couldn't add module alias:  at /usr/sbin/ndiswrapper line 717.
user@ubuntu:~$ 

Critical Notice: Check the file /etc/modprobe.d/ndiswrapper file and make sure that the ndiswrapper alias is wlan0 an not something else such as eth1.

Use cat to look at /etc/modprobe.d/ndiswrapper and ensure that it contains the line "alias wlan0 ndiswrapper" and nothing else:

user@ubuntu:~$ cat /etc/modprobe.d/ndiswrapper

Make sure that it contains only the wlan0 identifier and no other:

alias wlan0 ndiswrapper

If it contains anything else edit /etc/modprobe.d/ndiswrapper and ensure that it contains the line "alias wlan0 ndiswrapper" and nothing else:

user@ubuntu:~$ sudo gedit /etc/modprobe.d/ndiswrapper

Save the file.

Reboot your system in preparation for testing and validation of your work.
Step 7 - Testing the device

Now when we run iwconfig we should see that your ESSID and Access Point fields have been filled in with your access point's correct information and the Frequency field shows the correctly detected frequency:

user@ubuntu:~$  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"My_Essid"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:08:74:02:01:FC   
          Bit Rate:11 Mb/s   
          RTS thr:2432 B   Fragment thr:2432 B   
          Power Management:off
          Link Quality:95/100  Signal level:-35 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


The ESSID field should contain the name of your wireless network and the Access Point field should be filled in with the MAC identifier of your access point.

Run a "netstat -rn" command, and you should see that the correct routing is setup:

user@ubuntu:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan0
0.0.0.0         192.168.0.2     0.0.0.0         UG        0 0          0 wlan0
user@ubuntu:~$ 

In this case 192.168.0.2 is the gateway address to an Internet router.

If everthing looks good then all of your network data has been entered correctly.

---

