---
title: "Wireless Static IP not working"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by ryboto on 2007-05-05
I'm using the 64bit version of Feisty and I'm attempting to set a static IP using the network utility.  I enter everything, ESSID, IP address, subnet mask, gateway, everything same as the windows config.  the DNS servers are already listed if I go to the DNS tab.  If I set the manual connection using the static IP, and click the green check button, nothing happens.  I have to disable networking by right clicking the icon in the task bar, and then I have to enable networking.  when I do this, the icon goes from being two computers with an orange x to just two computers, similar to what a dial up network icon looked like in windows.  When I set it to static, sometimes I get a connection, sometimes I don't.  There's no way for me to know I'm connected unless I open a browser, or try to connect to gaim.  When I set ot to "enable roaming mode" which I assume means a dynamic IP, instead of the two computers icon in the taskbar, I get a wireless signal strength icon, and i'll get popups when I'm connected to the network.  So, my question is, how am i supposed to set a static IP address with wireless networking?

---

### Post by ryboto on 2007-05-06
anyone else have a similar issue?

---

### Post by macabro22 on 2007-05-06
I do. Systematicaly when modifying network settings. 
When I go to work, I have to setup the lab static ip, when I go home I setup my home static IP. The annoyance is the freakin system seems to not acknolewdge I changed the ip settings until I reboot one hell lot of times. Eventually it does, but I can´t see a pattern.

Yesterday I was navigating alright and in the morning Feisty decided not to surf anymore.

I don´t have a clue what makes it connect properly when it does. I just keep rebooting. Sometimes one time is enough, sometimes a couple.

If I just logout and relogin to access network manager, it displays a blank screen and I am forced to total reboot.

It is pissing me off. 

Also, I can connect to my wireless network but can´t browse the web. So I wire up the pc. When I wire up the PC at home I have to change the IP and everything is messed up because of that problem. I wish I had my wi-fi card working. 

Ubuntu doesn´t even accept my workarounds.. crap!

---

### Post by VolvoPunch on 2007-05-06
I am also having this problem.

My thread
[http://ubuntuforums.org/showthread.php?t=435274](http://ubuntuforums.org/showthread.php?t=435274)

It's very annoying especially when you don't have a monitor and keyboard plugged into the box. Some input on our problems would be nice.

---

### Post by VolvoPunch on 2007-05-07
bump, Does anyone know the solution to this problem?  ](*,)

---

### Post by VolvoPunch on 2007-05-07
I am going to keep bumping until i can get some feed back on this problem.

---

### Post by ryboto on 2007-05-07
I'll be doing the same

---

### Post by agurk on 2007-05-08
Heh, I use a little workaround, I first disable roaming mode, select static IP and in the terminal, I: "sudo ifconfig eth1 192.168.xxx.xxx" 
In addition, I use Conky (available from the repos) to display the assigned IP addresses for eth0 and eth1 on my desktop. That, in combination with the network manager applet, tells me what I need to know.

Let me know if you want the Conky script or if you have any other questions.

---

### Post by ryboto on 2007-05-08
well, I tried the ifconfig command,
sudo ifconfig ath0 192.168.0.10, and all it does is make the connection unusable.  I give the command, and I lose my connection, even though the network icon in the task bar is still there, and says I'm connected.  So, I right clicked it, disabled it, right clicked it, enabled it, and it must have reset back to dynamic ip, because now it's back to an IP of 192.168.0.124.

---

### Post by stchman on 2007-05-08
> **ryboto said:**
> I'm using the 64bit version of Feisty and I'm attempting to set a static IP using the network utility.  I enter everything, ESSID, IP address, subnet mask, gateway, everything same as the windows config.  the DNS servers are already listed if I go to the DNS tab.  If I set the manual connection using the static IP, and click the green check button, nothing happens.  I have to disable networking by right clicking the icon in the task bar, and then I have to enable networking.  when I do this, the icon goes from being two computers with an orange x to just two computers, similar to what a dial up network icon looked like in windows.  When I set it to static, sometimes I get a connection, sometimes I don't.  There's no way for me to know I'm connected unless I open a browser, or try to connect to gaim.  When I set ot to "enable roaming mode" which I assume means a dynamic IP, instead of the two computers icon in the taskbar, I get a wireless signal strength icon, and i'll get popups when I'm connected to the network.  So, my question is, how am i supposed to set a static IP address with wireless networking?

The Network-Manager under Feisty or Edgy does not support static IPs.  You will have to go into the Administration--->Network and check the enable connection on the device you want to assign the static IP to.  Also Network-manager will not support static IPs when using any type of wireless encryption.

Frankly I don't see a need to use Network-Manager if you are using a wired connection.

---

### Post by ryboto on 2007-05-08
> **stchman said:**
> The Network-Manager under Feisty or Edgy does not support static IPs.  You will have to go into the Administration--->Network and check the enable connection on the device you want to assign the static IP to.  Also Network-manager will not support static IPs when using any type of wireless encryption.

Frankly I don't see a need to use Network-Manager if you are using a wired connection.

going to Adminstration-> Network just gives me the same utility that I get if I right click on the networking icon in the task manager.  So, I'm not sure how to get to the settings you mention.

edit: it looks like to get to the "network" settings, I have to install xubuntu-system-tools.  Installing it will removed gnome-system-tools and ubuntu-desktop.  Should I proceed?

---

### Post by stchman on 2007-05-09
> **ryboto said:**
> going to Adminstration-> Network just gives me the same utility that I get if I right click on the networking icon in the task manager.  So, I'm not sure how to get to the settings you mention.

edit: it looks like to get to the "network" settings, I have to install xubuntu-system-tools.  Installing it will removed gnome-system-tools and ubuntu-desktop.  Should I proceed?

No, just place a check mark by the device you want to have a static IP for.  When you place a check mark you can then sepcify an IP address.  When you leave all unchecked then Network-Manager will take over these duties.

---

### Post by ryboto on 2007-05-09
> **stchman said:**
> No, just place a check mark by the device you want to have a static IP for.  When you place a check mark you can then sepcify an IP address.  When you leave all unchecked then Network-Manager will take over these duties.

I don't understand what you're referring to.  if I right click the icon in the task bar, i get a window that shows my wireless connection, and a modem connection.  The wireless connection can either be set to roaming mode, or static.  if i set it to static, i do see a "check" mark next to it, if i set it to roaming, there's just a dash.  Strangely, it only works in roaming mode.  I'm not sure how exactly to do what you're talking about.

---

### Post by stchman on 2007-05-09
> **ryboto said:**
> I don't understand what you're referring to.  if I right click the icon in the task bar, i get a window that shows my wireless connection, and a modem connection.  The wireless connection can either be set to roaming mode, or static.  if i set it to static, i do see a "check" mark next to it, if i set it to roaming, there's just a dash.  Strangely, it only works in roaming mode.  I'm not sure how exactly to do what you're talking about.

Go to Administration--->Networking

When network-manager is active none of the devices (Wireless, Wired, Modem) have a check mark next to them as network-manager is taking care of those.

If you want to make your wired ethernet static then highlight the device and hit properties.  This will bring up a window and the Enable box is not checked.  Check that box.  You can then either select static or DHCP.  Forget the icon in the notification area.

You can enter your IP, Gateway, etc in that box.

This is the way I know how to do it.

Since you are wanting to do wireless, you do know that you will not be able to do encryption (WEP, WPA, WPA2) and static IP through Ubuntu.  If your router supports it you can bind a certain IP to a certain MAC address.

---

### Post by ryboto on 2007-05-09
> **stchman said:**
> 
If you want to make your wired ethernet static then highlight the device and hit properties.  This will bring up a window and the Enable box is not checked.  Check that box.  You can then either select static or DHCP.  Forget the icon in the notification area.

You can enter your IP, Gateway, etc in that box.

This is the way I know how to do it.

Since you are wanting to do wireless, you do know that you will not be able to do encryption (WEP, WPA, WPA2) and static IP through Ubuntu.  If your router supports it you can bind a certain IP to a certain MAC address.

See, when I go there, the "checkbox" is already full, it has a dash in it.  I can't uncheck it, or check it.  I can only disable roaming mode.  If i disable roaming mode, and enter a static IP, whatever is controlling the card never establishes a connection with the router.  And my router is set up so that my wireless cards mac address is given a static IP, I don't know how to force my computer to use it though outside of setting a static IP address in the network settings.

---

### Post by stchman on 2007-05-09
> **ryboto said:**
> See, when I go there, the "checkbox" is already full, it has a dash in it.  I can't uncheck it, or check it.  I can only disable roaming mode.  If i disable roaming mode, and enter a static IP, whatever is controlling the card never establishes a connection with the router.  And my router is set up so that my wireless cards mac address is given a static IP, I don't know how to force my computer to use it though outside of setting a static IP address in the network settings.

The dash in all the boxes is normal.  Now highlight the wireless card and select properties.  You can check a box with enable.  This will enable the card and not use network-manager.  There are a few things you need:

1.  Your router's SSID
2.  The static IP you wish to select (outside the DHCP range preferrably)
3.  The gateway (usually 192.168.1.1)
4.  The subnet mask (usually 255.255.255.0)

Also, you won't be able to use wireless encryption when you are using a ststic IP.  I don't recommend doing this as your wireless connection will be subject to others connecting to it.  Even MAC filter is not enough protection.  I recommend using WPA/WPA2 and MAC filtering on your wireless connection.  Now remember I am using Edgy and Feisty might be a little different.

If your router has the ability to assign a certain IP to a certain MAC address then go that route definitely.  In the router you can assign an IP address to a MAC address outside your DHCP range.  My Linksys router does not have this capability so I have to use DHCP for my laptop using wireless.  Encryption is more important than static IP to me when it comes to wireless.

---

### Post by ryboto on 2007-05-09
I have done ALL of that already.  Still, I cannot connect to my network if I give a static IP.  I am entering the SSID, gateway, subnet mask, etc. correctly.  There is just something wrong with this software.  My router IS setup to reserve a static IP for my MAC address, but I don't know how to take advantage of that.  If i set the wireless to roaming mode, it grabs an IP in the range of the DHCP IP's in my routers setup.  I cannot turn off DHCP on my router because others use this network and setting static IP's for everyone would be a hassle.

---

### Post by whayong on 2007-05-11
Did you try disabling MAC filtering?  That could be the culprit.  Does wireless work on DHCP?  I use gnome-network-manager when using WPA on DHCP network but when I connect to WEP on a static network I click on "manual configuration", enter all the required info including DNS and select the apply icon (green check).  The the gnome-network-manager icon displays "No network connection" but guess what?  Here I am posting this.  I suggest you try doing it again.  If it still doesn't work, open terminal and do

```
sudo ifdown eth1
sudo ifup eth1
```

where "eth1" is your wireless card.

---

### Post by ryboto on 2007-05-11
> **whayong said:**
> Did you try disabling MAC filtering?  That could be the culprit.  Does wireless work on DHCP?  I use gnome-network-manager when using WPA on DHCP network but when I connect to WEP on a static network I click on "manual configuration", enter all the required info including DNS and select the apply icon (green check).  The the gnome-network-manager icon displays "No network connection" but guess what?  Here I am posting this.  I suggest you try doing it again.  If it still doesn't work, open terminal and do

```
sudo ifdown eth1
sudo ifup eth1
```

where "eth1" is your wireless card.

Outside of the terminal commands you've suggested, I have tried exactly what you describe doing with the network-manager.  Although, applying the static info doesn't work right away.  If i set it to manual, and click the green check, the settings don't take.  I have to disable networking by right clicking the manager in the task bar, and then enable it again for the manual settings to take.  Once they are applied, it appears like I have no connection based on the icon in the task bar.  When I try to connect with gaim, or open a webpage, I am assured that my connection isn't working.  I have to then switch back to the roaming mode.  

By MAC filtering, is that an option on my side, or something i change on the router?

---

### Post by whayong on 2007-05-14
MAC filtering is set by the router.  If you didn't enable it, you shouldn't worry about it, but from your previous posts, it sounded like you in fact did enable MAC filtering which is why I mentioned it.

---

### Post by GS2 on 2007-05-14
Post the output of 
```
cat /etc/network/interfaces
```

---

### Post by ryboto on 2007-05-14
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

I've tried changing eth0 and wlan0 to static, and provided the IP(address), netmask and gateway, but it didn't make a difference.

---

### Post by GS2 on 2007-05-15
Give this a go back up your current /etc/network/interfaces
```
sudo cp /etc/network/interfaces /etc/network/interfaces_old
```

Then edit the interfaces file - try these entries:
[http://textsnippets.com/posts/show/319](http://textsnippets.com/posts/show/319)

EDIT>>
Set you network to open (no encryption key) to connected easiest - can work on encryption later

---

### Post by B-&gt;J-&gt;Eagle on 2007-05-15
How do you say?
If you go in to network under administration yes you can say check to the wireless device that i am using, but it does not help. Every time i uncheck roaming and set up my ip nothing happens. And why do i have to write the password there and choose if it is AASI or HEX i use i don't use any of those. 

Is'nt there just an easy step by sted guide to tell how to set up a static ip in ubuntu? I'm used to windows, but i like Ubuntu way better in many aspects but this task should be simple but i can't figure it out. 
There must be an easy way.

---

### Post by ryboto on 2007-05-15
I followed that guide, which I had already done before, and this was the result when I tried to restart the networking,
```
rybot@metro:~/Desktop$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                         
eth0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth1.
eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 6847440
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
wifi0: unknown hardware address type 801
Bind socket to interface: No such device
Failed to bring up eth2.
wlan0: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
wlan0: ERROR while getting interface flags: No such device
Failed to bring up wlan0.

```

---

### Post by GS2 on 2007-05-16
Ok the cat of your interfaces file indicated that all the devices were set up for DHCP, which indicates that none of settings have taken.

Replace your interfaces file with the original one, and rename it accordingly. reboot the PC.

What is the wireless extension for your card  - wlan0 or eth1 ? - should tell you in the networking GUI.

now you have found the wireless extension set it up to connect to the router with DHCP first 
. This can be done using the GUI. Now check you are connected to the router:
```
ping -c 4 192.168.0.1
``` 
where 192.168.0.1 is the IP address of your router (adjust accordingly)

- ensure your router is setup to allow a static connection from the MAC address of your PC card - to find that out do:
```
ifconfig
```
note the HWaddr - that is the MAC address of your card against the extension of your card eg wlan0

Go to router config page and choose a static IP within the  DHCP addresses, my DHCP goes up to 51 so choose the IP your router has given you via DHCP you can choose any below the assigne DHCP range eg:
192.168.0.11

if that is the correct IP range for your router

Open a shell, and edit  your /etc/network/interfaces file (my wireless is eth1):

```
auto eth1
iface eth1 inet static
address 192.168.0.11
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid Router
```

Obviously removing the dhcp section for eth1 if that is your wireless extension. I have also commented out the wired extension (eth0) by adding a # in front of the lines associated with.

Now reboot the Ubuntu PC.
My icons do not indicate there is a wireless network - but if you type
ifconfig
then you will see a IP address is assigned to your wireless extension.

I went through these steps on Ubuntu, and Kubuntu and they worked without problems.
If you have problems post the output of:
ifconfig
iwconfig

---

### Post by ryboto on 2007-05-16
> **GS2 said:**
> Ok the cat of your interfaces file indicated that all the devices were set up for DHCP, which indicates that none of settings have taken.

Replace your interfaces file with the original one, and rename it accordingly. reboot the PC.

What is the wireless extension for your card  - wlan0 or eth1 ? - should tell you in the networking GUI.



Go to router config page and choose a static IP within the  DHCP addresses, my DHCP goes up to 51 so choose the IP your router has given you via DHCP you can choose any below the assigne DHCP range eg:
192.168.0.11

if that is the correct IP range for your router



I'd like to follow those steps, but I'm not sure what extension my device uses.  The connection properties I added to my task panel says "connection properties" and it refers to my active connection as ath0.  Otherwise, I see no extensions referenced anywhere, not even in hardware information.  

As for the IP..The static IP that my router reserved for my MAC address is not within the DHCP range.  Why should this be a problem?  I have zero issues connecting to it in windows.

---

### Post by ryboto on 2007-05-16
So, I edited the interfaces file, and added a line for ath0.  I put in the proper information, rebooted, and after I logged in the connection icon looked like a hard-wired connection, not wireless, basically the same thing that happens if I choose a manual connection from the GUI.  So, I typed ifconfig.  It showed I had not sent or recieved any data.  I tried to ping the router, didn't work.  Opened firefox, no dice.  Waited a few more minutes, initiated gaim, no connections could be established.  So, editing the interfaces file gets me to the same place as manually inputting the settings into the GUI, it just doesn't connect.  

Maybe I'll try adjusting the DHCP range, or the static IP that I want to use.  Not sure why it works for Windows, oh well.

---

### Post by GS2 on 2007-05-16
Try to bring up 1 extension at a time:
eg:
sudo ifconfig eth1 up

then type

ifconfig

do you have an output for eth1 ? (or any of the interfaces apart from lo ?)
If you want help, you will need to post the output I asked for, can you connect with DHCP instead of static ok - are you using encrytion ? - if you get no output from ifconfig (apart from lo interface) then you card is not configured correctly with the OS driver wise

And yes unlike windows you can do everything you need by the command shell, without the need of a GUI :)

This is handy for reference [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by ryboto on 2007-05-16
here's the output from ifconfig and iwconfig.

```

ath0      Link encap:Ethernet  HWaddr 00:13:46:9A:9F:54  
          inet addr:192.168.0.124  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:46ff:fe9a:9f54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:509697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:560609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:305399495 (291.2 MiB)  TX bytes:163876127 (156.2 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:85493470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85493470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:974689416217 (907.7 GiB)  TX bytes:974689416217 (907.7 GiB)

wifi0     Link encap:UNSPEC  HWaddr 00-13-46-9A-9F-54-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:819453 errors:0 dropped:0 overruns:0 frame:57101
          TX packets:567879 errors:422 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:357743337 (341.1 MiB)  TX bytes:176896801 (168.7 MiB)
          Interrupt:21 

```  


```

lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"brattnet"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:F0:BD:95   
          Bit Rate:11 Mb/s   Tx-Power:17 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=26/94  Signal level=-63 dBm  Noise level=-89 dBm
          Rx invalid nwid:243702  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


Like I've said before, I can connect fine if i set the connection to "roaming mode" which I assume is dchp.

edit: I should not that the MAC listed for ath0, 00:13:46:9A:9F:54, matches with my router settings.  And also, the network is an open, one, no security key required.

---

### Post by GS2 on 2007-05-16
ok type

sudo wifi0 down

and comment out that interface in the 

/etc/network/interfaces

file using a #

then bring ath0 down and up using 
sudo ifconfig ath0 down
sudo ifconfig ath0 up

see if that helps (may need a reboot also)

---

### Post by ryboto on 2007-05-16
I opened the interfaces file, only this time, the only three devices shown were lo, eth1, and wlan0.  I commented out eth1 and changed wlan0 to ath0, and added the static info.  Then I tried your suggestion and it works fine, but only if it's in roaming(dhcp) mode.  Bring it down and up just disconnects me momentarily from the network.  I tried it using the manual(static) mode, but it still doesn't make a connection to the network, can't ping anything, or use the internet.

when I ping my router it just returns " connect : Network unreachable".

---

### Post by GS2 on 2007-05-16
Check your router documentation for setting static IP addresses with DHCP also running, if it states you need to assign an IP within the DHCP range do that (which is what my router states) - then adjust the /etc/network/interfaces file accordingly.

---

### Post by ryboto on 2007-05-16
> **GS2 said:**
> Check your router documentation for setting static IP addresses with DHCP also running, if it states you need to assign an IP within the DHCP range do that (which is what my router states) - then adjust the /etc/network/interfaces file accordingly.

The router documentation doesn't stat that it has to be in the range of the dhcp addresses.  I can change the static IP to be within the range, but it doesn't make sense that it's a router issue if the same static IP works in windows.

---

### Post by GS2 on 2007-05-16
Fair enough

iwconfig indicates you have a link, and packets have been sent - although the link has a very low strength. 
Seems odd you cannot connect or ping the router, when you have a link. I tried the steps above once on my network at home on 2 Ubuntu based systems and have just tried it on slackware (a bit different but still linux)- and they worked straight away and with/without encryption (although 32 bit systems).

---

### Post by ryboto on 2007-05-16
This is what I find strange.  My router's help says this, 
"Add/Edit Static DHCP Client

    This option lets you reserve IP addresses, and assign the same IP address to the network device with the specified MAC address any time it requests an IP address. This is almost the same as if a device has a static IP address except that it must still request an IP address from the D-Link router. The D-Link router will provide the device the same IP address every time. Static DHCP is helpful for server computers on the local network that are hosting applications such as Web and FTP. Servers on your network should either use a static IP address or use this option. "

So, basically, I should have the IP i set in my router, but I don't.  My friend uses ubuntu, and all he does is set his wireless to dhcp, have his router reserve a static IP, and presto, he has the IP he set in his router.  I have done exactly as he has, yet ubuntu requests, and is granted a different IP.

---

### Post by ryboto on 2007-05-16
problem solved.  After I extended the dhcp range to include the IP I had configured the router to use(it's a QoS router, so changing the IP would have been annoying) the wireless manager requested an IP from the router and was givent he one I had reserved for it. Works now.

---

### Post by GS2 on 2007-05-17
Good news - nothing to do with the OS then ;)

The same is true for my router - if setup as a DHCP server - the IP has to be within the range of allowed leased IP addresses, as I posted earlier.

Enjoy the brilliant OS you now have :)

---

