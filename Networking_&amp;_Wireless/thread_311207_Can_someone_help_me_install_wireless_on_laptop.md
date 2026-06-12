---
title: "Can someone help me install wireless on laptop?"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by chapmc on 2006-12-02
I have trying to install my wireless connection for quite a while.  Read lots of threads, docs, etc, but I still don't have it done.  If you can help me with this I would much appreciate it.  I am pretty new at ubuntu.

Dell B130 laptop with Dell 1370 miniPCI card (internal Broadcom).
Ubuntu Dapper just installed and updates applied.

This is where I stand.

/etc/modprobe.d/blacklist contains
blacklist bcm43xx

installed ndiswrapper-utils 1.8

chap@dell:~$ sudo ndiswrapper -i /home/chap/bcmwl5.inf
Password:
Installing bcmwl5
chap@dell:~$ sudo ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!
chap@dell:~$

This is the latest driver from Dell and it is the one being used by windows xp and working correctly on this machine.
I have tried other drivers I have downloaded and get the same result.

Please tell me what to try next.  I will much appreciate it.  I have been pulling my hair out with this and am about ready to give up.

---

### Post by FrodoB on 2006-12-02
What is the output of:

lspci

---

### Post by FrodoB on 2006-12-02
Also, it would appear from my web search that this post is the one you need to look at. Use the driver that he posts at the end of the first message in the thread.

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

If this is the same device.

---

### Post by chapmc on 2006-12-02
chap@dell:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express P rocessor to DRAM Controller (rev 03)
0000:00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GM L Express Graphics Controller (rev 03)
0000:00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Expre ss Graphics Controller (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High De finition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 1 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) P CI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil y) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge  (rev 03)
0000:00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family ) IDE Controller (rev 03)
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (re v 02)
0000:02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]  802.11g Wireless LAN Controller (rev 02)

And thanks for helping.

---

### Post by FrodoB on 2006-12-02
That looks right, go to the forum message that I pointed out in my previous post, the driver that he is proposing and attached should work for you per his instructions.

---

### Post by FrodoB on 2006-12-02
And this post as well:

[http://ubuntuforums.org/showthread.php?t=285809](http://ubuntuforums.org/showthread.php?t=285809)

---

### Post by chapmc on 2006-12-02
the last thread you mentioned is the one have have tried a couple of times without success.  Should I go ahead and the script in the first thread since I have already installed ndiswrapper, etc?

---

### Post by FrodoB on 2006-12-02
Yes, if he is using the version of ndiswrapper that comes with Ubuntu, the  same one you have anyway.

---

### Post by chapmc on 2006-12-02
OK, I ran it and the system networking box says eth1 is active but I can't connect using it.  It tried pinging my router and that fails. 

chap@dell:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

chap@dell:~$ ping 192.168.0.1
connect: Network is unreachable
chap@dell:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
chap@dell:~$


I'm tired right now and am going to quit for a while.  If you can tell me what to try next that would be great.  And thanks for all the help.

---

### Post by FrodoB on 2006-12-02
So your device is called eth1.

From a terminal prompt you should be able to see your access point if it is turned on using:

sudo iwlist eth1 scanning

If you device supports it.

Now you need to try to configure the interface using the Networking tool in the menu:

System -> Administration -> Networking

Set you WEP key and activate it.

You should end up with a record in the /etc/network/interfaces file that looks like:

iface eth1 inet dhcp
wireless-essid Your_ESSID
wireless-key XXXXXXXXXXXXXXXXXXXXXXX
auto eth1

If you just want to put in in manually you can edit the file from a terminal using gedit like this:

sudo gedit /etc/network/interfaces

---

### Post by chapmc on 2006-12-02
We're getting close.  It is probably something real simple.
When I do the scan I can see the network and I can see other networks.  Also the file has amy network and wep key in it. But I still can't do a ping of my router and I don't connect with firefox.  I disabled eth0 and enabled eth1.

---

### Post by FrodoB on 2006-12-02
Take a look at /etc/iftab and see if something else is tied to the wlan0 device, if so remove that line from the file and reboot and report the outputs of:

iwconfig

and the contents of:

/etc/network/interfaces

---

### Post by chapmc on 2006-12-02
/etc/iftab only contains eth0 mac and eth1 mac

---

### Post by FrodoB on 2006-12-02
I would delete the line that says eth1 (or change it to wlan0) and reboot, that will probably change the interface to wlan0 which is the default. That sometimes helps for some reason.

Then publish the requested outputs.

---

### Post by chapmc on 2006-12-02
I quitting for the night.  Many thanks.  Try again tomorrow perhaps.  I did delete the eth1 and reboot and eth1 was back again and wouldn't connect.

---

### Post by FrodoB on 2006-12-02
> **chapmc said:**
> I quitting for the night.  Many thanks.  Try again tomorrow perhaps.  I did delete the eth1 and reboot and eth1 was back again and wouldn't connect.

Then try changing it from eth1 to wlan0 in /etc/iftab if it is still there. Also look in /etc/modprobe.d/ndiswrapper and change it from eth1 to wlan0 if it says eth1 still.

---

