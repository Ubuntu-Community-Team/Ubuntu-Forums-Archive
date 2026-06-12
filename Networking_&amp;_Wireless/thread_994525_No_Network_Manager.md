---
title: "No Network Manager"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by norman_069 on 2008-11-26
Hello,

Somehow i managed to uninstall my network manager.  It was working good then all of a sudden it was gone.  i have seen many forums but nothing is helping me.  I have a lenovo x61 tablet with ubuntu 8.10 on it.  I cant connect to the internet to download the network manager again so i don't know what to do.  here is what my ifconfig says if it helps.

eth0     	 Link encap:Ethernet  HWaddr 00:16:d3:3e:c6:95 
             	UP BROADCAST MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
	Memory:fe000000-fe020000 

lo               Link encap:Local Loopback
	inet addr:127.0.0.1  Mask:255.0.0.0
	inet6 addr: ::1/128 Scope:Host
	UP LOOPBACK RUNNING  MTU:16436  Metric:1
	RX packets:302 errors:0 dropped:0 overruns:0 frame:0
	TX packets:302 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0 
	RX bytes:19560 (19.5 KB)  TX bytes:19560 (19.5 KB)

wlan0        Link encap:Ethernet  HWaddr 00:1b:77:a2:a4:0c 
	UP BROADCAST MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 	collisions:0 txqueuelen:1000
	RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0   Link encap:UNSPEC  HWaddr 00-1B-77-A2-A4-0C-00-00-00-00-00-00-00-00-00-00  
	UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
	RX packets:0 errors:0 dropped:0 overruns:0 frame:0
	TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000 
	RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Thanks

---

### Post by lswb on 2008-11-26
If you can plug your system into a wired ethernet network with internet access, as on a router, it is pretty simple, usually just open a terminal and type:

sudo dhclient eth0

should do it.

If not post back with the connection types you have available (wired ,wifi, modem, etc) and if you know, does the connection use dhcp, (most common for wired or wifi) and if wireless, what encryption type. (WEP, WPA)

---

### Post by norman_069 on 2008-11-27
Thanks a lot.  That got me connected back to the internet.

What did dhclient eth0 due when i typed it in.

Thanks Again

---

### Post by lswb on 2008-11-27
> **norman_069 said:**
> Thanks a lot.  That got me connected back to the internet.

What did dhclient eth0 due when i typed it in.

Thanks Again

dhclient is the program that connects to a dhcp server on a network and asks for an ip address to be assigned to your computer. It is nowadays probably the most common method for assigning ip addresses on a lan. The acronym stands for Dynamic Host Control Protocal.

---

### Post by norman_069 on 2008-11-27
ok, Thanks a lot.

Now i reinstalled network manager but how do i get the icon back into the top right toolbar.  The one that shows the green bars and the strength of the network.

---

### Post by rlzyoner on 2008-11-27
Short term - Open a terminal and type nm-applet
Long term - System => Preferences => Sessions

Look under the Startup Programs tab. If "Network Manager" is not already there, click Add, if needs be, put nm-applet in as the command.

---

### Post by norman_069 on 2008-11-27
Ok, that seems to work but it doesn't put the bars in the right top toolbar.  i do however have wireless now, but the problem is when i want to get on another network i don't know how to switch it without that icon up there.

---

### Post by lswb on 2008-11-27
First try logging out and back in again, if that doesn't do it, you may also need to reinstall the nm-applet. Start synaptic and search for "network-manager-gnome" and make sure it is installed, then if necessary add to your sessions menu as rizyoner described.

---

### Post by norman_069 on 2008-11-27
I appreciate the advice but I have tried everything here and it wont show up.  Since the problem i have is when i take my computer school i cant see the network and i use to use that icon to click on it and change networks. But,  will that dhclient thing work on wireless networks.

thanks

---

### Post by lswb on 2008-11-28
I'm wondering if perhaps you deleted the notification area from the panel? IIRC Network Manager puts it's icon there rather than just any old place in the panel. Try right clicking on the panel, select and add the notification area, then if the nm-applet icon doesn't show up immediately, try opening a terminal and running the command "nm-applet"

You can use the cli to connect to wireles networks but it a little more complicated than a wired connection. A gui like NM or wicd is certainly more conveneient. (if it is running!)

Assuming no WEP or WPA key is required, your wireless interface is wlan0, and the essid (wireless network name) at your school is "school" the basic sequence is normally something like this:

```

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode managed essid "school"
sudo ifconfig wlan0 up
sudo dhclient wlan0

```

This will usually connect to the most common wireless network configuration. If the network uses WEP or WPA and the key is ABCDE add

key ABCDE 

to the end of the line that begins with "sudo iwconfig ...."

---

### Post by norman_069 on 2008-11-28
If i did delete the one that was up there is there a way to get it back.  When i try and run nm-applet from terminal i get a warning saying that is could not acquire the NetworkManagerUserSettings as it is already taken.  then it returns 3 and says it failed.

---

### Post by lswb on 2008-11-28
Not sure what is going on with your system. Start synaptic and search for "network manager" and "network-manager-gnome" and make sure they are both installed. Close synaptic. Make sure you have a notification area installed on the top panel. This is where your battery/power status icon is, where the update-available icon shows up, and where nm-applet will appear when it is running properly. Without any icons visible, the notification area itself is difficult to see; It looks like 2 columns of small dots. If you don't have one, then install it as described above: right click on panel, select "add to panel" then select "notification area" from the list. After that select Main Menu/System/Preferences/Sessions and make sure Network Manager is checked. After all that cross your fingers and reboot.

---

### Post by norman_069 on 2008-11-29
I got it working.  I think the problem was the notification area wasn't either installed or not on.  I reinstalled the network manager and network-manager-gnome and now everything works great.  Thanks for all the help!

---

### Post by hemantbabu on 2008-11-30
I have been following this conversation since I was also facing the same problem.

I have reinstalled nm applet. the synaptic shows it installed. but when tried launching it from terminal i got following. Please help.

** (nm-applet:6825): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6825): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

---

### Post by lswb on 2008-11-30
> **hemantbabu said:**
> I have been following this conversation since I was also facing the same problem.

I have reinstalled nm applet. the synaptic shows it installed. but when tried launching it from terminal i got following. Please help.

** (nm-applet:6825): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6825): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

I don't know enough about dbus to understand the 1st error message. I believe the 2nd message has to do with gtk or gnome and displaying the desktop. Perhaps logging out & back in, or rebooting your system may help.

---

### Post by norman_069 on 2008-11-30
> **hemantbabu said:**
> I have been following this conversation since I was also facing the same problem.

I have reinstalled nm applet. the synaptic shows it installed. but when tried launching it from terminal i got following. Please help.

** (nm-applet:6825): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6825): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

That's exactly what I had going on. I got the same error.  I went to the synaptic package manager and reinstalled network manager and network-manager-gnome.  I then went to the top panel right click and add to panel and i added notification area.  Now everything works like a charm.

---

### Post by ttoolin on 2008-12-01
I was having the same problem, with the suddenly-disppearing signal strength icon.  It happened to me while I was adding applets to the task-bar, like the weather report, etc.

I turned on the notification area, as lswb suggested, and it worked great!

Thanks, all, for the very educational thread!

terry

---

