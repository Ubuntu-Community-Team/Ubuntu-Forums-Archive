---
title: "How to diagnose connecting to wireless network?"
date: 2007-11-24
forum: Networking &amp; Wireless
---

### Post by dkuhlman on 2007-11-24
I can see my wireless network, but I cannot connect.  I've tried Network Manager, Wireless Assistant, and Wicd.  All of them can see (show) my wireless network, but none of them can connect to my wireless router.

Is there something I can do to diagnose this and discover what the problem is?

I'm running Gutsy Gibbon x86_64 on a Toshiba A215-S4697 laptop.  It has the Atheros AR5006EG device (but possibly AR5007EG).

Here is what I've done:

1. Used restricted-manager to disable the Atheros Hardware Access Layer.

2. Installed ndiswrapper and ndisgtk and then used ndisgtk to install the net5211 driver from the following:

[ftp://ftp.work.acer-euro.com/noteboo...5.1.1.9_XP.zip](ftp://ftp.work.acer-euro.com/noteboo...5.1.1.9_XP.zip)
ZR3_Atheros_XB63_5.1.1.9_XP_WHQL/XP_5.1.1.9_LED_Negative_Pole/WHQL_5-1-1-9_X64

3. Added the following to /etc/modprobe.d/blacklist:

blacklist ath_pci
blacklist ath_rate_sample
blacklist new_ath_pci

4. Reboot.

When I try to connect using Wicd, it stalls while displaying: "Connecting ... Optaining IP address ...". Is this a clue?  Is there something I need to configure on my router so that it provides an IP address?  If so, I have not found that option in my Web based router configuration tool.  What should I look for?

Is there something else I can do to diagnose this problem?

Dave

---

### Post by elctb on 2007-11-24
> **dkuhlman said:**
>  it stalls while displaying: "Connecting ... Optaining IP address ...". Is this a clue?  Is there something I need to configure on my router so that it provides an IP address?  If so, I have not found that option in my Web based router configuration tool.  What should I look for?

Is there something else I can do to diagnose this problem?

Dave

This means that the wireless interface on your laptop is configured as DHCP. DHCP is a protocol to request an ip address from a server. Most wireless routers are configured as DHCP servers, so I think the problem is that your router is using encryption and you haven't configured your wireless interface with the encryption key:

To find out do the following:

. Type the command "iwlist scan"
. Make sure your router in on the list of found networks and check the field "Encryption key". If it's on, you need to enter the encryption key using the command "sudo iwconfig eth1 key <your-key>".

---

### Post by kevdog on 2007-11-24
Can you post 

lshw -C network


Why are you opting for ndiswrapper over the ath_pci (madwifi) driver?

---

### Post by dkuhlman on 2007-11-24
Thanks for the help.

The "iwlist scan" thing is helpful.  Thanks.

Here is a little more info -- I've tried setting my router at (different times)  to use (1) security disabled or (2) WPA Personal security.  I am unable to connect either way.  And, when using WPA Personal security, I'm pretty confident that I'm entering the correct password into Wireless Assistant and Wicd.

I also tried (in Wicd) to specify a static IP address for the computer from which I am trying to connect.  I seemed to get a connection, but could not ping anything.

But neither of these tools tell me *why* they are failing to connect.  So, I don't know what the problem is.

Are there any tools that do wireless network diagnostics?

Dave

---

### Post by elctb on 2007-11-24
The ultimate network diagnostic tool is wireshark (you can install it via synaptic). It's a packet sniffer so you need to know a little about tcp/ip to figure out what's going on. To be able to capture it must be run as root (sudo wireshark). However, you'll only see what's going on at the ip layer. To see what's going on at the 802.11 level (wireless) you might need to enable debugging on the driver or something like that.

Also, make sure the interface is up. Type "ifconfig" and verify you see the wireless interface and it's up (it should say something like: "UP BROADCAST RUNNING MULTICAST".

---

### Post by dkuhlman on 2007-11-25
> **elctb said:**
> Also, make sure the interface is up. Type "ifconfig" and verify you see the wireless interface and it's up (it should say something like: "UP BROADCAST RUNNING MULTICAST".

Thanks for that suggestion.  Well, using "ifconfig", I find out that *sometimes* wlan0 is there, but usually it is not.  I guess that explains why I am able to connect via wireless once in a while (but then only when my router is not in secure mode) and why I am usually not.

So I have two problems:

1. How to get wlan0 to come up consistently -- Something wrong in my configuration?  I need to re-read some posts in this forum, I suppose.

2. How to negotiate and connect to the wireless network when the router is in secure mode -- Apparently, typing in a password to Wireless Assistant or Wicd is not enough.

Maybe, as suggested above by kevdog, I should explore the Madwifi drivers.  I'm running 64-bit Gutsy Gibbon.  Not sure whether they have 64-bit drivers.

Thanks again for help.

By the way, I can dual boot this laptop.  It came with MS Windows Vista installed.  Under Vista, I have not had problems getting a wireless connection.  So, that suggests to me that it's not a hardware problem.

Dave

---

### Post by elctb on 2007-11-25
To get the wireless interface to come up automatically every time you reboot the pc you need to add the "auto" keyword to the wlan0 interface in the /etc/network/interfaces file. This is what my /etc/network/interfaces file looks like:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

Then use this command to set the encryption key "sudo iwconfig wlan0 key <your-key>"

And to get an ip address use this command "sudo dhclient wlan0"

If this doesn't work, post any errors from the above commands.

---

### Post by dkuhlman on 2007-11-26
> **elctb said:**
> 

Then use this command to set the encryption key "sudo iwconfig wlan0 key <your-key>"

And to get an ip address use this command "sudo dhclient wlan0"

If this doesn't work, post any errors from the above commands.

Super.  Thanks.  Now I know how to bring up the interface, for those times when I boot and it is not there already.

After doing "sudo dhclient wlan0", I run "ifconfig" and I see:

```

wlan0    ....
         UP BROADCAST MULTICAST

``` 

However, when I do "sudo dhclient wlan0", after several seconds, I see:

```
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Is that normal?  Is it a router problem?  Or, is there something I need to configure on my client machine.  And, neither Wireless Assistant nor Wicd nor Network Manager can connect to the network.  This client machine, by the way, can connect with this router when I boot it in MS Windows Vista.

Thanks again for the help.  I apologize for being so dense about this.  I'd better get back to work.  I've spent too many days on this already.

Dave

---

### Post by buccaneere on 2007-11-26
> **elctb said:**
> To get the wireless interface to come up automatically every time you reboot the pc you need to add the "auto" keyword to the wlan0 interface in the /etc/network/interfaces file. This is what my /etc/network/interfaces file looks like:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

Then use this command to set the encryption key "sudo iwconfig wlan0 key <your-key>"

And to get an ip address use this command "sudo dhclient wlan0"

If this doesn't work, post any errors from the above commands.

chuckb@chuckb-laptop:~$ sudo iwconfig eth1 key p............e
Password:
Error for wireless request "Set Encode" (8B2A) :
    invalid argument "p............e".
chuckb@chuckb-laptop:~$ sudo iwconfig eth1 key <p............e>
bash: syntax error near unexpected token `newline'

What did I do wrong? What did I do right?

---

### Post by elctb on 2007-11-26
If you specify an ascii password, you need the add "s:" to the password. For example if your password is "my-password" the command looks like:

```
sudo iwconfig wlan0 key s:my-password

```

---

### Post by buccaneere on 2007-11-26
> **elctb said:**
> If you specify an ascii password, you need the add "s:" to the password. For example if your password is "my-password" the command looks like:

```
sudo iwconfig wlan0 key s:my-password

```

I don't know if my password is ascII or hex. It's WPA/tkip/psk.

In any respect, I didn't get a 'wrong passphrase' return; I'm not that far along configgin' yet:(

---

