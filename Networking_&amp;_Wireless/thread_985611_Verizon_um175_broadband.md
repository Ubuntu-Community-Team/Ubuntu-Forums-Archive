---
title: "Verizon um175 broadband"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by Doodlemepink on 2008-11-17
Hello all,

I'm trying to get my USB broadband card to work in Linux. I am running Ibex 8.10 with the hope that it would be supported but to no avail. I have tried the basic set up through network manager but, the broadband network doesn't show up in my networks. So after that I tried to use gnome-ppp to set it up but it will not detect the modem. I can't find a driver/all of the threads here or anywhere haven't helped me get this going. 

I'm a ubuntu N00B so I will need mostly a walk-through on this.

Thanks for your help!

---

### Post by jprogers5181 on 2009-09-30
I searched for several days trying to find help with this same problem and finally found a solution. However, I did not save the solution URL (sorry). Essentially, I had to initialize the Verizon account using a Windows operating system. I installed the VZAccess Manager software on the Windows machine and followed all the prompts. Once the UM175 was communicating as advertised, I plugged it into my Ubuntu 9.04 machine (freshly updated!!!) and the modem was recognized and I connected immediately. On previous install attempts I did enter all the required information requested in the NetworkManager|Mobile Broadband tab. That may have been why it seemed like a seemless solution. After I got the Ubuntu machine communicating with the Internet I uninstalled the VZAccess Manager from the Windows machine and all is well. By the way, I tried installing the VZAccess Manager in a Windows VirtualBox, but could not get access to the USB port. I've read other forums that corraborate this problem so don't bother trying that route. Use a pure Windows machine or a Windows partition and it will hopefully get you connected quickly.

---

### Post by DLinn on 2009-10-07
Hi-
I have been using the Pantech UM175 cellular modem from Verizon for about a year now and I have no comlpaints. Of course I can't remember if I had some... In any case all's well now.  :)

I'm running Ubuntu 8.10, Intrepid Ibex.

I use WvDial: Internet dialer version 1.60.

Make a backup copy of etc/wvdial.conf (e.g. wvdial.conf.orig)

Edit the etc/wvdial.conf file using gedit as below-

  [Dialer Defaults]
  Init1 = ATZ
  Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
  Stupid Mode = 1
  Modem Type = USB Modem
  ISDN = 0
  Phone = #777
  Modem = /dev/ttyACM0
  Username = your modem phone [email]number@vzw3g.com[/email]
  Auto Reconnect = on
  Password = vzw
  Baud = 460800

Save the file.

Then, using terminal enter-
  sudo wvdial

Then you should see something like this-
  account name@account name@account name-desktop:~$ sudo wvdial

Terminal will ask for your password...
  [sudo] password for account name:

Then you will see a series of messages...
  --> WvDial: Internet dialer version 1.60
  --> Cannot get information for serial port.
  --> Initializing modem.
  --> Sending: ATZ
  ATZ
  OK
  --> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
  ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
  OK
  --> Modem initialized.
  --> Sending: ATDT#777
  --> Waiting for carrier.
  ATDT#777
  CONNECT
  --> Carrier detected.  Starting PPP immediately.
  --> Starting pppd at Wed Oct  7 11:53:06 2009
  --> Pid of pppd: 11401
  --> Using interface ppp0
  --> local  IP address 70.217.169.115
  --> remote IP address 66.174.160.64
  --> primary   DNS address 66.174.95.44
  --> secondary DNS address 66.174.92.14

You should now be connected.

If this doesn't do the trick search the Forums using 'wvdial'

Best Wishes
DL

---

