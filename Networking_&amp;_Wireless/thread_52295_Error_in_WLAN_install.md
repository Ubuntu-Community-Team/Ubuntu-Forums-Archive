---
title: "Error in WLAN install"
date: 2005-07-27
forum: Networking &amp; Wireless
---

### Post by tohen on 2005-07-27
I followed the guide on [https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo) -and everything worked fine til i was goign to try it, if i type "sudo ifup ra0" I get the following error: "Ignoring unknown interface ra0=ra0".
I tried doing everything on the site, one more time, But I still get the same error.
Any ideas?
I'm useing Kubuntu HH 5.04

Also, by useing the "sudo insmod rt2500.ko" i get the following error: "insmod: error inserting 'rt2500.ko': -1 File exists"

"5. Under System -> Administration you will find networking. Your Ralink card will be listed there. Activate it."
I can't find the Administration menu, and when I go there from the Control Center I can't get into Administration mode.

---

### Post by SpaulS on 2005-07-28
I followed the same instructions on the wiki, and my rt2500 is working.

Do you have a file /etc/modprobe.d/rt2500, and does it contain:

alias ra0 rt2500 

When you run the "insmod" command, the error may be because the file and module is already installed. Try running the following command from a terminal:

modinfo rt2500

and see if it is installed.

On KDE/Kubuntu, the "Networking" function is directly under the "System" menu on the KDE launch pad. If you cannot find it there, try running the following command from a terminal:

sudo network-admin

Run ifconfig and iwconfig and see if the output says anything about ra0.

See if these help.

---

### Post by tohen on 2005-07-28
> Do you have a file /etc/modprobe.d/rt2500, and does it contain:
alias ra0 rt2500
/etc/modprobe.d/rt2500 exists, but it's empty..


> modinfo rt2500
returns some lines with text:p so I think it's installed, cause i get:
Filename: /lib/modules/2.6.10-5-386/kernel/drivers/web/wireless/rt2500.ko


"sudo network-admin" Does not work

"ifconfig and iwconfig" Gives info about ra0.

However, last night I tried the folowing:

*ifconfig eth0 down* 
*ifconfig ra0 up* 
*dhclient* 

And it connected to the, but I had to disable crypting, When I use WPA and WEP it does not work.

Any Ideas how I can get crypting to work??

---

### Post by SpaulS on 2005-07-29
Definitely add the data to the /etc/modprobe.d/rt2500 file. This will ensure the alias for the interface and the driver for the interface are known.

As far as network-admin not working, that is kind of weird. Is the binary present in /usr/bin?

As far as encryption, I used the RaConfig utility listed on the HowTo web page. I use WPA-PSK encryption, and the RaConfig allowed me to put in the key value. Build and run RaConfig and see if you can get encryption set up. Good luck.

---

### Post by tohen on 2005-07-29
I added the data to the rt2500 file ;)

[QUOTE=SpaulS]As far as network-admin not working, that is kind of weird. Is the binary present in /usr/bin?[/QUOTE]
huh?:-\


[QUOTE=SpaulS]As far as encryption, I used the RaConfig utility listed on the HowTo web page. I use WPA-PSK encryption, and the RaConfig allowed me to put in the key value. Build and run RaConfig and see if you can get encryption set up.[/QUOTE]
I also used the RaConfig, but that did'nt help, so I had to go for the dhclient, I set up everything that had to be set up in the RaConfig, but still it doesent work. I don't get an new IP with the RaConfig, any more ideas?

[QUOTE=SpaulS]Good luck.[/QUOTE]
Thanks! I really need it! ;)

---

### Post by SpaulS on 2005-07-30
Is the binary (executable) program for network-admin locate in /usr/bin, or in other words, does your system have the program installed and available? (it should)

From a terminal, type:
which network-admin

You should get a response:
/usr/bin/network-admin

And if you wish, type:
file /usr/bin/network-admin

You should get a response like:
/usr/bin/network-admin: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), stripped

As far as RaConfig, the RaConfig does not get your IP address, it allows you to set up your wireless connection including encryption. Run the RaConfig program, and go to the "profile" tab. You should be able to create a new profile for your wireless router, including your encryption (second tab when you create a new profile).

The network-admin utility is a GUI to the network commands, but 'ifup ra0' or 'ifconfig ra0 up' accomplish the same thing. This is where you get your IP address and dhcp configuration. If your /etc/network/interfaces file is correct, you should not have to run dhclient manually.

Try the items listed above, and could you also post your /etc/network/interfaces file in your reply?

Best-
Paul

---

### Post by tohen on 2005-08-02
> which network-admin
Nothing happends.. (new line)
:
> file /usr/bin/network-admin
/usr/local/bin/network-admin: ERROR: cannot open `/usr/local/bin/network-admin' (No such file or directory)

and the /etc/network/interfaces file:

[I]# The loopback network interface
auto lo
iface lo inet loopback
iface ra0 inet static
	address 0.0.0.0
	netmask 255.255.255.255[/I]

thanks for the help soo far :-)

regards,
Henning

---

### Post by SpaulS on 2005-08-04
Aha! Ok, replace these lines in /etc/network/interfaces:

iface ra0 inet static
address 0.0.0.0
netmask 255.255.255.255

with:

#####
iface ra0 inet dhcp
wireless-essid <your wireless SSID>

auto ra0

#####

That should correct your DHCP and startup issues.

As far as the network-admin: it's a tool from gnome, not kde. I started off with gnome and then upgraded to kde. That is why you do not have the program. I have not found the kde equivalent yet.

Try the change to /etc/network/interfaces and see if that helps.

Paul

---

### Post by tohen on 2005-08-07
[QUOTE=SpaulS]
iface ra0 inet dhcp
wireless-essid <your wireless SSID>

auto ra0
[/QUOTE]
This one actually makes the wlan connect automaticly, But it still doesent work with the encryption.. Is it possible to add the WPA-PSK to the /etc/network/interfaces ??
Or do you have any ideas how I can make it work??

Henning

---

### Post by SpaulS on 2005-08-10
This is where things get weird.

I originally installed Ubuntu with Gnome, which is where I got the network-admin utility. I then built and installed the RT2500 and RaConfig utilities. As I mentioned above, I used RaConfig to get the WPA-PSK set up and running. The RaConfig utility definitely does NOT put the WPA-PSK key in the /etc/network/interfaces. I do not know where it stores the value, but it keeps it somewhere.

Here is the problem I am having. If the ra0 interface shows up as "auto" or "up" in the /etc/network/interfaces file, the Gnome desktop will NOT start after the next shutdown/reboot. The X-server starts up and shows the login screen, but the desktop can take up to 15 minutes to start after logging in. If the ra0 interface shows up as "down" in /etc/network/interfaces, then the Gnome desktop starts up normally after login. If the startup gets stuck, I use CTL-ALT-F1 to get to a command prompt, execute a 'sudo ifconfig ra0 down' command which stops ra0, then execute a 'sudo pkill -HUP X' command which restarts the X server, and then I can log in back through the Gnome GUI and get a desktop. Then, I use network-admin to bring ra0 up, and then everything works, including the WPA-PSK encryption.

The Kubuntu KDE does NOT have this problem, and I suspect that is because RaConfig was built for KDE. Since you started off with Kubuntu/KDE, you should be able to set up the WPA-PSK with RaConfig.

When you launch RaConfig, do you have the tabs to add the security information?

---

### Post by tohen on 2005-08-11
[QUOTE=SpaulS]When you launch RaConfig, do you have the tabs to add the security information?[/QUOTE]
Yes, I get the information tab, And then I add the WPA-PSK, But It refuses to connect still, I have checked that the key mach, (wich it does:p). So I don't understand why it doesent work :\
I'm going to try WEP today, and see if that works.

Could the problem be in the router or in the laptop?

-Henning

A little update:
I tried the conenction with WEP, and it seems to work. So Actually the thing that does'nt work it the WPA krypting, any ideas how to get the WPA to work??

---

### Post by SpaulS on 2005-08-13
So you can connect with no encryption, you can connect with WEP encryption, but you cannot connect with WPA encryption, correct?

When you set up the WPA key and save the session in RaConfig, do you see a line showing the connection on the main RaConfig status page? I did not have any problems once I could see that.

Two ideas come to mind:
Can you see the security logs from your router? They might have some information regarding who is trying to connect.

Did you compile the driver with the "debug" flag as suggested in the wiki for the rt2500 driver?

---

