---
title: "Network manager not detecting connections"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by viveknz76 on 2006-08-16
HI,

I am using a Asus laptop.  The inbuilt wireless in it is PRO/Wireless 2200BG.  I have installed Network Manager and commented all the lines in /etc/network/interfaces except lo.  My network manager is not showing any connections.  I did an iwconfig and the result was as follows.

-----------------------------------------------------------------------
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"AGWL44"  Nickname:"AGWL44"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:95:CF:3C:EC
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=94/100  Signal level=-33 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:2  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
----------------------------------------------------------------------

What is it that i am doing wrong?  I have wpa_supplicant installed and I can get my wpa connection working through command line "-D wext -i eth1 -c /etc/wpa_suppllicant.conf -d -ww".

Please help.

Thanks

---

### Post by mjziegle on 2006-08-16
Maybe your keyring is messed up.  

Anyway, try using WEP with nm first then go to the WPA.

Sounds like you followed the deprecated WPA thread.  I'd undo all those changes and start with nm.

---

### Post by ComplexNumber on 2006-08-16
go into you  system menu and select Services. is your network manager started and enabled at boot time?

also, switch your wpa_supplicant service OFF, switch 'named' service ON.

---

### Post by viveknz76 on 2006-08-16
Thanks for your reply guys.

**mjziegle: **When I click on Network Manager it says, "No network devices have been found".

**ComplexNumber:** I went to System > Administration > Services.  All I see is samba, gdm, cupsys, ssh, etc... I cannot see Network Manager service listed.  Also, I do not know how to start the service on bootup and stop wpa_supplicant service.

Can you please redirect me to an appropriate thread that explains setting up Network Manager?

Thanks

---

### Post by viveknz76 on 2006-08-16
OK... I figured one thing out.. there is nm-applet --sm-disable listed under sessions with order 50 and style as settings.  The same is available under Startup Programs. So I guess the Network Manager is starting up.

One more thing when I run sudo /etc/init.d/dbus restart... I Network Manager does not start up

---

### Post by mjziegle on 2006-08-16
> **viveknz76 said:**
> OK... I figured one thing out.. there is nm-applet --sm-disable listed under sessions with order 50 and style as settings.  The same is available under Startup Programs. So I guess the Network Manager is starting up.

One more thing when I run sudo /etc/init.d/dbus restart... I Network Manager does not start up

Well duh (sorry ;) ) nm starts with gdm and depends on dbus.  If you kill dbus it goes away but won't come back until you restart gdm.  

What is the output of ifconfig?  

Anyway, double check your /etc/network/interfaces since that gets written to everytime you try and restart the network usind the old gui tool.

---

### Post by viveknz76 on 2006-08-16
I am a newbie to linux... so trying to learn.  Here is the dump from ifconfig

eth0      Link encap:Ethernet  HWaddr 00:11:2F:8D:B1:C8
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:4

eth1      Link encap:Ethernet  HWaddr 00:0E:35:5F:4F:EB
          inet addr:192.168.89.200  Bcast:192.168.89.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fe5f:4feb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160024 errors:2 dropped:2 overruns:0 frame:0
          TX packets:163798 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:83181644 (79.3 MiB)  TX bytes:26135285 (24.9 MiB)
          Interrupt:4 Base address:0x2000 Memory:ff9ee000-ff9eefff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)

---

### Post by ComplexNumber on 2006-08-17
**viveknz76**
if you haven't already, add the Notification Area to your panel by right clicking on the panel and selecting Add to Panel. then select Notification Area. this will show the network manager applet and will help you determine if you're connected or not when you finally manage to connect.

did you enable and disable the services that i asked you to above?

---

### Post by aslabbekoorn on 2006-08-17
Hi, I have acer with same card spending last 3 days on this stuff and used the most complex forum answers till I found this 7 step one and this worked immediately after reboot. Try it out..

[http://en.magenson.de/2006/06/11/ubuntu-dapper-drake-and-wpa-encrypted-wireless/](http://en.magenson.de/2006/06/11/ubuntu-dapper-drake-and-wpa-encrypted-wireless/)

---

### Post by viveknz76 on 2006-08-17
Firstly, I just want to thank all the people for being so helpful.

**ComplexNumber**:  I do not know how to turn off the **wpa** service off and **named** on. I'll find a resource that tells how to acheive above.

I can see the Network Manager in the sys tray.  It is showing as crossed out and when I click on it the pop up says, "No Network devices have been found".  I have already tried what's on the link but no luck.

---

### Post by ComplexNumber on 2006-08-17
> ComplexNumber: I do not know how to turn off the wpa service off and named on.
i got it wrong about switchng wpa_supplicant OFF. it needs to be ON.
go to services in the menu, go down the list until you see wpa_supplicant. if it has a click by the side of it, click it OFF so that it doesn't startup at boot time. then click the Start button to start the service if it isn't running.  then find the 'named' service and click it ON. then click the Start button to start the service if it isn't running. 
also, make sure that the network manager is enabled at boot and is also running. 
see screenshot below

---

### Post by viveknz76 on 2006-08-17
I am not quite sure what is happening... I went into System > Administration > Services.  What i see is attached.

---

### Post by ComplexNumber on 2006-08-18
i've just figured out why. that services application is particular to red hat systems. i'm using fedora core 5. i thought that it may have been a gnome application.

---

### Post by mjziegle on 2006-08-18
Looks like your ifconfig is ok.  Try and setup eth1 (your wireless) using network manager.  Then reboot.  

Remember with network manager you'll have to activate your wireless connection after you turn on your computer if you don't enter the keyring password quickly.

---

### Post by viveknz76 on 2006-08-19
I cannot access any connections using network manager hence cannot setup eth1 using it.

---

