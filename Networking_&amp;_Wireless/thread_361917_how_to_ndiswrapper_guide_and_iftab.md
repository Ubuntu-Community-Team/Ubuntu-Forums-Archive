---
title: "how to: ndiswrapper guide and iftab"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by sephirothsigep on 2007-02-14
ndiswrapper wireless how to:

[SIZE="3"]1) Install ndiswrapper[/SIZE]

ndiswrapper is a tool that allows users to use Windows XP Drivers for wireless cards. if you want more information on this tool after install look at the manual page by typing in the following command:
```
man ndiswrapper-1.9
```

	a) go to System>Administration>Synaptic Package Manager
	b) search ndiswrapper
	c) mark for install the following pakages 
		i)   ndiswrapper-common
		ii)  ndiswrapper-utils-1.8

[SIZE="3"]2) find your wireless cards make and model[/SIZE]

In order to set up ndiswrapper, it is necessary to obtain the Windows driver for your wireless card. Generally, the best way to do this is from the CD supplied with your wireless card. You should copy two files to the same place on your computer, one ending in .SYS and one ending in .INF. If you find any files which end in .BIN, also copy those. If you are not able to find the right files, and have alternative access to the Internet , you may be able to obtain help from the ndiswrapper website.

	IF YOU NEED TO OBTAIN DRIVERS FROM THE INTERNET USE THE FOLLOWING STEPS IN BLUE

[COLOR="Blue"]        a) open a terminal and type the following command. 
		```
lspci
```
	    this command will list all of the pci divices on your system.
	b) search throuhg the list till you find an entry that deals with your wireless card
	c) download your drivers from your wireless cards manufactures site or you may be able to 
             find driver for your card from The ndiswrapper webstie.
             [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")
[/COLOR]
[SIZE="3"]3) Install your wireless card drivers.[/SIZE]

	IF THERE ARE GENERIC DRIVERS THAT DO NOT WORK FOR YOUR WIRELESS CARD
      THAT COME STANDARD WITH UBUNUT YOU NEED TO BLACK LIST THE GENERIC DRIVERS. 
do the following items in red to blacklist the item.

[COLOR="Red"]
                 ```
sudo gedit /etc/modprobe.d/blacklist
```
and add the generic drive to the list. This is what i had to add. NOTE it will be different for every card. this is what i had to add for my wireless card. search the forum for information on what drivers to blacklist

		```
#module below does not work with Broadcom 4318, 4306 wireless cards
		blacklist bcm43xx
```
[/COLOR]

	a) do the following command
		```
sudo ndiswrapper -i /location/driverName.inf
```
	b) to check to see if driver is working correctly type
		```
ndiswrapper -l
```
	   if it is then continue else you may have to wrong drivers.
	c) now you need to assign the drivers to a given device. to do this you will need to do the following in the terminal
		i)   type the following command 
			    ```
lspci
```
		     find your wireless card and then note the numbers at the beginning example: 
			    ```
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g
                            Wireless LAN Controller (rev 03)
```	
   	              next type the following
			    ```
lspci -n
```
		ii)  now referance the noted number to the output. you need to find the number that is
                     in the form xxxx-xxxx example:
			    ```
02:02.0 0280: 14e4:4320 (rev 03)
```
		     in this example 14e4:4320 is the number that we want.
	   	     you will need the newly found number later
		iii) next you need to find the name of the driver that you will be using. type
			    ```
ndiswrapper -l
```
 	   	     from the output find the driver name
			    ```
{name of driver}  driver installed, hardware present
```
		iv)  now link the drivers by typing the following.
			    ```
ndiswrapper -d 14e4:4320 bcmwl5
```
	   	     bmwl5 = drivers name, 14e4:4320 = driver ID found number from step ii.

	 d) For ndiswrapper to function, you need to load a module. and then have it load
              at the boot each time. To do this, type:
		  ```
sudo depmod -a
```
		  ```
sudo modprobe ndiswrapper
```
		  ```
sudo ndiswrapper -m
```

[SIZE="3"]4) Restart your computer[/SIZE]
         press " ctrl + alt + backspace "


[SIZE="3"]5 Assign a name to the network interface[/SIZE] 

this will pin down an interface name based on mac address. so that on start up the the interface is given the same name each time. 

	a) type the following command into the terminal.
		 ```
sudo  gedit /etc/iftab
``` 
	b) change the interface name to wlan0 for the correct mac address in this case eth1
             will be changed to wlan0
```

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:12:3f:d8:6b:44 arp 1
eth1 mac 00:90:96:bb:34:2f arp 1

```

restart linux and if all is good it should work 
best of luck

---

### Post by bigbadmoshe on 2007-02-15
ok was fallowing but some thing got messed up  with drivers and this is what i get 
Installed drivers:
drivers invalid driver!
what can ido now

---

### Post by Floppyjoe on 2007-02-15
```
ndiswrapper -l
```
Lists drivers
```
sudo ndiswrapper -e drivernamegoeshere
```
deletes the driver.

---

### Post by bigbadmoshe on 2007-02-15
moshe@moshe-laptop:~$ sudo ndiswrapper -e w29n51
Password:
Driver w29n51 is not installed.Use -l to list installed drivers
moshe@moshe-laptop:~$ sudo ndiswrapper -e NETw39x5
Driver NETw39x5 is not installed.Use -l to list installed drivers
moshe@moshe-laptop:~$ ndiswrapper -l
Installed drivers:
drivers invalid driver! :mad:

---

### Post by sephirothsigep on 2007-02-15
> moshe@moshe-laptop:~$ sudo ndiswrapper -e w29n51
Password:
Driver w29n51 is not installed.Use -l to list installed drivers
moshe@moshe-laptop:~$ sudo ndiswrapper -e NETw39x5
Driver NETw39x5 is not installed.Use -l to list installed drivers
moshe@moshe-laptop:~$ ndiswrapper -l
Installed drivers:
drivers invalid driver! 


most likly what happened was you installed the wrong drivers for your wireless divice. I would look to see if you did get the right ones. in order to remove the drivers you need to do
 ```
sudo ndlswrapper -e drivers
``` the reason that you need to type drivers instead of w29n51 is that the name of the driver just so happens to be " drivers ". try this and let me know what you get. it may take me a little bit of time to get back

---

### Post by bigbadmoshe on 2007-02-15
ok got it to work the way u said but the problem i have is i cant even see any wirless in network manager there is not wireless option there

---

### Post by sephirothsigep on 2007-02-18
> **bigbadmoshe said:**
> ok got it to work the way u said but the problem i have is i cant even see any wirless in network manager there is not wireless option there
give me output for the following commands after giving the system a reboot
iwconfig
ifconfig
ndiswrapper -l
less /etc/iftab

---

