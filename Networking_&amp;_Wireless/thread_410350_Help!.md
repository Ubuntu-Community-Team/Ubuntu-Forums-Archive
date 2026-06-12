---
title: "Help!"
date: 2007-04-15
forum: Networking &amp; Wireless
---

### Post by Mightyspider on 2007-04-15
hello i need help with installing my wireless driver please i have built in wireless. Its the PRO Wireless 3945ABG.

I tried installing well make and install the driver but i get errors all the time and its telling me permission denied,but im logged in as root so is there something im doing wrong maybe someone can help me with step by step instructions,because im ver new to ubuntu.

Thanks in adavance
Mightyspider

---

### Post by chili555 on 2007-04-16
The module ipw3945 is built in to Edgy, so I would not download and struggle with a source file. I assume that's what you meant by 'make and install.'

The built-in kernel module works very well; I am using it now. Make sure the switch is on on your laptop, then do:```
lsmod | grep ipw3945
``` If you get a few lines from this command, it means the module is loaded and your wireless is ready to rock-n-roll.

Check```
iwconfig
```and see if your wireless is ready. If so, you might see something like this:```
eth1      IEEE 802.11g  ESSID:"myrouter1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:13:19:62:8D:F7   
          Bit Rate:18 Mb/s   Tx-Power:14 dBm   
          etc.
```Then I would do```
sudo iwlist eth1 scan
```It might take a few tries. This will tell you the exact name of your ESSID. In my case, if I specified Myrouter1, I will never connect to myrouter1.

Then, it is as easy as:```
sudo iwconfig eth1 essid <your_router's_essid>
sudo dhclient eth1
```This assumes you do not have encryption in place: WEP, WPA, etc. If you do, post back what you have and we'll help.

---

### Post by Mightyspider on 2007-04-17
Hi Chili

i tried to do the iwconfig and its telling me that no wireless found is there something im doing wrong.

So the only thing i need to install is the ieee80211 then?

Thanks

---

### Post by chili555 on 2007-04-17
Please post the output of:```
lsmod | grep 3945
```Thanks.

---

### Post by Mightyspider on 2007-04-17
Hi there Chili

This is what i get if i promp the commands...

root@ubuntu-laptop:~# lsm|grep ipw3945
bash: lsm: command not found
root@ubuntu-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

root@ubuntu-laptop:~# sudo iwlist eth1 scan
eth1      Interface doesn't support scanning.

root@ubuntu-laptop:~# sudo iwconfig eth1
eth1      No such device

root@ubuntu-laptop:~# sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
root@ubuntu-laptop:~#

---

### Post by chili555 on 2007-04-17
I did not ask for lsm, I asked for:```
 **lsmod** | grep 3945
```

---

### Post by Mightyspider on 2007-04-17
oh sorry my bad ill try it and get back to u 

Thanks

---

### Post by Mightyspider on 2007-04-17
This is what i got check the attachment

---

### Post by chili555 on 2007-04-17
Let's do:```
sudo modprobe ipw3945
```Then:```
iwconfig
```and let's see if your wireless has made an appearance. If so, you should be able to configure and connect through System - Administration - Networking. Post back if you need more help.

---

### Post by Mightyspider on 2007-04-18
Ok i will try the commands but if i go to System - Administration - Networking all i get is wired connection, modem connection thats all no wireless connection but u also told me to make sure that my wireless is switch on if i press my wireless button it stays Off its not coming On is there any other way that i can switch it On maybe?

The only thing that is installed is my ieee80211 thats it and i cant install the ipw3945 but u said that its build in ubuntu right?

So what should i do ?

Thanks

---

### Post by chili555 on 2007-04-18
Well, ieee80211 is built in to the kernel as well. If you downloaded a source code file and installed it, I suggest doing a *make uninstall* so the outside version doesn't interfere with the built-in version and it's interaction with ipw3945. 

I wonder if the switch is turning the wireless radio on when you press the switch but the light is not coming on because the driver, ipw3945, is not loaded. You should see some activity in *sudo tail -f /var/log/messages* when the button is toggled. I just flipped my switch and saw this:```
kernel: [17182770.292000] Kill switch must be turned off for wireless networking to work.
``` Take a look.

---

### Post by Mightyspider on 2007-04-18
What sould i do now?

---

### Post by Mightyspider on 2007-04-18
i have done the make uninstall but i can get the other infomation u send me what should i do to get that infomation u send me the sudo tailf/var/messeges?

---

### Post by chili555 on 2007-04-18
Open up a terminal and type:```
sudo tail -f /var/log/messages 
```Watch the output from the terminal as you press the wireless switch. If you press the switch and it is turning the wireless radio OFF, the terminal will say something like:```
Kill switch must be turned off for wireless networking to work.
```If you are turning the wireless radio ON, it probably will say nothing. The fact that the light comes on or stays off only means the wireless is not yet recognized and trying to connect.

Then do:```
sudo modprobe ipw3945
iwconfig
```Did your wireless show up as eth1? If so, configure it under System -> Administration -> Networking. 

Post back if you need more help.

---

### Post by Mightyspider on 2007-04-18
ok but my wireless never worked yet im trying to make it work so no i have never picked up the wireless connection yet

---

### Post by Mightyspider on 2007-04-18
ok this is what i got 

The files is attached

---

