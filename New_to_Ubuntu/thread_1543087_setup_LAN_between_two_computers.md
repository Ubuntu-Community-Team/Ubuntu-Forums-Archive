---
title: "setup LAN between two computers"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by deb_untu on 2010-07-31
I have two computers and both have Ethernet card.
Have installed Linux on both of them (one of them has windos as well as linux).
Want to know how to connect those so that I can share the files between them.

I don't have router/hub. Is it still possible ?

Seek your help. Or guide me to any easy to understand tutorial that you know.

Thanks,

---

### Post by jerenept on 2010-07-31
oh yes, I believe it is possible.

simply plug the computers into each other.

Do not use DHCP. 
What you can do, is right click the NetworkManager applet, and click "edit connections", then click "add" on the window that comes up. Click the "IPv4 settings" tab and change the option  "Automatic (DHCP)" to "Manual".
Click "Add". A text entry field will be shown in the table next to the "Add" button.
put in: "192.168.1.2" and then press enter.
Click the area under "Netmask" and enter "255.255.255.0"
[http://windows.microsoft.com/en-US/windows-vista/Change-TCP-IP-settings]("http://windows.microsoft.com/en-US/windows-vista/Change-TCP-IP-settings")
That should help for Windows. Set the IP Address to "192.168.1.3" and the subnet Mask to "255.255.255.0"

---

### Post by davidmohammed on 2010-07-31
... I'm sure you'll need a cross-over cable for direct computer to computer stuff.  You can't use a regular RJ45 cable.

---

### Post by AlphaLexman on 2010-07-31
> **jerenept said:**
> oh yes, I believe it is possible.

simply plug the computers into each other.
I believe a 'crossover' cable is required for this to work without a hub or router.

---

### Post by skatinjj on 2010-07-31
Also, to connect two computers directly like that, you have to use a cross-over cable (still a ethernet cable)
[URL="http://www.lanshack.com/make-cat5E.aspx"]
http://www.lanshack.com/make-cat5E.aspx[/URL]

---

### Post by mapes12 on 2010-07-31
> I don't have router/hub. Is it still possible ?Connect the ethernet cards together with a crossover ethernet cable.

**For Linux networking:-**

It goes like this for me:

I guess what you want is file sharing between two linux boxes.

1.) Make sure the openssh-server and openssh-client are installed on both machines.

```
sudo apt-get install ssh
```Is a meta package and will install both applications. Or you can search for it in Synpatic and install it from there.

2.) Go to the machine you want to connect to. You need to find the machines IP address, so in Terminal:

```
ifconfig
```

This should give you an output just like this one

> eth0 Link encap:Ethernet HWaddr 00:50:da:e0:67:74
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:9 Base address:0xc000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:27 errors:0 dropped:0 overruns:0 frame:0
TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1732 (1.7 KB) TX bytes:1732 (1.7 KB)

wlan0 Link encap:Ethernet HWaddr 00:11:50:dd:a9:16
inet addr:**192.168.1.68** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::211:50ff:fedd:a916/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
TX packets:1639 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1661090 (1.6 MB) TX bytes:342426 (342.4 KB)

wmaster0 Link encap:UNSPEC HWaddr 00-11-50-DD-A9-16-39-31-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter).

So, in my case the address would be 192.168.1.68

3.) Access the computer
Now, when you want to access a computer from the other, go to places>connect to server.
- Choose SSH as the "service type" from the drop down list
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This is the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click OK

You may get a message about keys on first time connection. Just OK it

You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

**For Linux / Windoze Networking:-**

Go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

If your router is providing DHCP services then you shouldn't need to worry about IP addresses. The MS Sharing configuration will sort that out.

---

### Post by Old_Grey_Wolf on 2010-07-31
If your computers have wireless adapters that support it you can do it with wireless. See [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc).
I have 10.04 installed. Where the instructions say "click on the tray icon", it means the network icon usually located on the top panel, unless you have changed the panel.

---

### Post by deb_untu on 2010-07-31
Thanks for you replies.

I have an ADSL broadband which I use to connect to internet & has 4 Ethernet jacks behind it. I don't know whether it is a hub or router.

In either case How I can connect both the computers to share files (access) between them ?

After connecting what I should check whether they are connected ?

I know that I am asking about networking stuff. I read some tutorials on the net but couldn't get anything.
 
Thanks.

---

### Post by Raymond2201 on 2010-07-31
hi deb_untu,

If you have ethernet cables on your adsl broadband then it has an inbuilt router.

to test the connectivity between your machines you can use the ping command from both windows cmd.exe or bash in Linux. you will need either the IP address or the hostname of your PC's to test it.

eg:
ping IP address or hostname here



for file sharing you should only need to install samba on your linux machine to allow your windows machine to "see" the shares you have setup and vise-versa.

---

### Post by deb_untu on 2010-07-31
> to test the connectivity between your machines you can use the ping command 

It tried, It says 'Unknown host'

Any tweaking required to modem to add another computer ?

---

### Post by Raymond2201 on 2010-07-31
> **deb_untu said:**
> It tried, It says 'Unknown host'

Any tweaking required to modem to add another computer ?

were you using the hostname or the IP address?

also you can check your routers configuration page to see which computers are connected.

---

### Post by deb_untu on 2010-07-31
> were you using the hostname or the IP address?

Was using hostname. 

To check router config, isn't it [http://192.168.1.1](http://192.168.1.1) ? (in browser)

After that what to do next ?
Thanks.

---

### Post by Old_Grey_Wolf on 2010-07-31
> **deb_untu said:**
> Was using hostname. 

To check router config, isn't it [http://192.168.1.1](http://192.168.1.1) ? (in browser)

After that what to do next ?
Thanks.

Different brand modems, routers, and switches use different IP addresses. I have a modem that uses 192.168.100.1, a wireless G switch that uses 192.168.1.1, and a wireless N switch that uses 192.168.1.245. You need to Google the brand of modem/router/switch to find out what to use.

The status and configuration pages are different for each modem/router/switch. You have to read the manual or provide specifics about your modem/router/switch so people can Google for the manual in order to help you.

---

### Post by Elmer Fudd on 2010-07-31
Right click on your network manager icon in your taskbar. Select Connection Information. The ip address for the Default route is likely your router.
Go to that address in your browser and you should be able to find out most info about your network and what is connected.
Google the router model/number to find out the default password (then don't forget to change it).

---

### Post by deb_untu on 2010-08-01
> **mapes12 said:**
> Connect the ethernet cards together with a crossover ethernet cable.

**For Linux networking:-**

It goes like this for me:

I guess what you want is file sharing between two linux boxes.

1.) Make sure the openssh-server and openssh-client are installed on both machines.

```
sudo apt-get install ssh
```Is a meta package and will install both applications. Or you can search for it in Synpatic and install it from there.

2.) Go to the machine you want to connect to. You need to find the machines IP address, so in Terminal:

```
ifconfig
```

This should give you an output just like this one


Your output can differ quite a bit, but the important information is just the bold bit. These four numbers are the address of the machine (do not use the 127.0.0.1 address - this the internal address of your network adapter).

So, in my case the address would be 192.168.1.68

3.) Access the computer
Now, when you want to access a computer from the other, go to places>connect to server.
- Choose SSH as the "service type" from the drop down list
- the server is the IP of the other computer (the one you want to access)
- the port can be left blank (this means it assumes port 22)
- the folder you should put in is /home - but you can leave it blank in which case you will access the other machine at "/" level and then navigate to /home/username
- the username *must* be specified. This is the user you use to log into the other computer.
- also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser

Click OK

You may get a message about keys on first time connection. Just OK it

You will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine.

From this folder you will be able to browse the other machine and transfer files back and forth.

**For Linux / Windoze Networking:-**

Go into Control panel in XP and enable "File and print sharing". Then go to the folder you want to share. Right click and enable "sharing". If the user account where the share is located in XP is a Limited account then you may have problems. The account needs to be given Administrator permission. Bad security but that's not my fault.

Next, on the Ubu machine go into Synaptic and install pyNeighborhood. Once installed it will be an application you can select from Applications. Click it. First some tweaks:

PyNeighborhood - Edit>Preferences
- Mount folder change to /home/username (this saves root having to do everything).
- Then "Remove mount point after unmount" = tick
- Then "File Manager" tab - add Nautilus

Then in the left hand pain right click the globe and select "Scan"

This should find your shared windoze folders. Double click the one you want in the right hand pain. This mounts it. Then right click it and select Nautilus as the file browser. You can then transfer stuff between the 2 machines.

If you have followed the above and still have problems then in my experience the problem is always with the XP machine, not Ubu. XP can sometimes lead you into thinking folders are being shared when in fact they are not. Hence my comment about Limited windoze accounts. It took me 3 days to figure that one out.

If your router is providing DHCP services then you shouldn't need to worry about IP addresses. The MS Sharing configuration will sort that out.

I did as you directed. Now I can see ping working, saying 6 pk received 6 pk sent.

Regarding ssh, I entered ip address (of vec 192.168.1.8), user name, in "connect to server". I can see icon in nautilus. But on opening it, it says "couldn't display ssh://vec@192.168.1.8/home/vec/" 
"Aceess was denied"

????????

How to use use cmdline to do the same in terminal.

Thanks.

---

