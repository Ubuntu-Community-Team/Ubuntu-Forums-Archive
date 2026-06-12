---
title: "Run script application before DHCP Discover"
date: 2016-01-17
forum: Networking &amp; Wireless
---

### Post by Mark_Gabriel on 2016-01-17
[COLOR=#111111][FONT=Ubuntu]I have a program that reads in the code plug external pins to determine the desired IP address of a particular device. This program will then update the /etc/dhcp/dhclient.conf file with the correct dhcp-client-identifier with respect to the code plug read. I need this program to run before the DHCP DISCOVER/REQUEST is sent out by the device so that it can read the correct /etc/dhcp/dhclient.conf Where is the best place to run this program?[/FONT][/COLOR]

Regards,
Mark

---

### Post by ian-weisser on 2016-01-17
It depends upon the release of Ubuntu that you are running: 12.04, 14.04, or 15.10?
Are you familiar with Upstart jobs or systemd targets?

---

### Post by matt_symes on 2016-01-17
Hi

This may be helpful for you if you are using dhclient.

```
man 8 dhclient-script
```

> 
This script is not meant to be customized by the end user.  If local customizations are needed, they should be possible using the enter and exit hooks provided (see HOOKS for details).   These hooks will allow the user  to  override the default behaviour of the client in creating a /etc/resolv.conf file. 

> 
After defining the make_resolv_conf  function,  the  client  script  checks  for  the  presence  of  an  executable /etc/dhcp/dhclient-enter-hooks  script,  and  if  present, it invokes the script inline, using the Bourne shell ´.´ command.   It also invokes all executable scripts in /etc/dhcp/dhclient-enter-hooks.d/*  in  the  same  way. 

You may find that useful.

**EDIT:**

Actually after re-reading your first post again, I'm not so sure if this will be useful for you but I'll leave is here just in case, as i have no idea what changes you want to make to dhclient.conf or what the program you want to run actually does.

Kind regards

---

### Post by Mark_Gabriel on 2016-01-18
> **ian-weisser said:**
> It depends upon the release of Ubuntu that you are running: 12.04, 14.04, or 15.10?
Are you familiar with Upstart jobs or systemd targets?

Hi thanks for your reply. I'm using 14.04. The sequence I would like to follow is:
1.) System initializes all drivers including I2C drivers for reading GPIO etc...
2.) Run our application which reads the code from the GPIO pins (/home/abc/readGPIOApp).
Our program modifies the /etc/dhcp/dhclient.conf and puts the correct dhcp-client-identifier based on the read GPIO pins.
3.) Dhclient sends out discover/request with corresponding dhcp-client-identifier based on the modified /etc/dhcp/dhclient.conf.
(dhcp-client-identifier is important when dhclient requests IPaddress. DHCP server will know what IP Address to give based on the dhcp-client-identifier sent out by DHClient)

#1 and #3 are out of my control(I think) so I would like to know where is the best place to do #2.

I'm not sure of upstart jobs/systemd targets.  What I'm experimenting now is just add the line to run my application in one of the scripts of the /etc/init/  just doing trial and error where it can read the code first before dhcp client starts sending requests to the dhcp server.  Right now the more stable place to put it is in the /etc/init/network-interface.conf. However there are times where the dhclient still send the previous dhcp-client-identifier, or doesn't even have dhcp-client-identifier (which means my application was run later than desired).

Regards,
Mark

---

### Post by Mark_Gabriel on 2016-01-18
I also don't know when or where this DHCP Discover/Request is started in ubuntu 14.04. If I know which script this is started maybe I can put my program execution line inside.  Does anybody know where this is started?

Regards,
Mark

---

### Post by matt_symes on 2016-01-18
Hi

Why do you need to edit the file /etc/dhcp/dhclient.conf ?

Can't you just change the mac address on the interface you are trying to assign and IP address to, based on the "code plug read" before the DHCP discover/request ?

I think you may be trying to tackle this the wrong way if your goal is to the edit dhclient.conf file before receiving an address.

Kind regards

---

### Post by Mark_Gabriel on 2016-01-18
> **matt_symes said:**
> Hi

Why do you need to edit the file /etc/dhcp/dhclient.conf ?

Can't you just change the mac address on the interface you are trying to assign and IP address to, based on the "code plug read" before the DHCP discover/request ?

I think you may be trying to tackle this the wrong way if your goal is to the edit dhclient.conf file before receiving an address.

Kind regards

I'm not sure what you mean to change the mac address?
We have 20 devices.
1.) All devices read their own code plug. These codes can change depending on what code the user uses.  So it is important during startup to read this code first.
2.) Based on the code read, our application will modifiy the /etc/dhcp/dhclient.conf with the correct [COLOR=#000000] dhcp-client-identifier (i.e. led1, led2, lcd1,lcd2, etc...).
The dhcp server needs this [/COLOR][COLOR=#000000] dhcp-client-identifier to know what IP address it will give.

Where and how do I change the mac address for this purpose?

Regards,
Mark[/COLOR]

---

