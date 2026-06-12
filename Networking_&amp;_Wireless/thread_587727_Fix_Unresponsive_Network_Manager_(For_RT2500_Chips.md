---
title: "Fix Unresponsive Network Manager (For RT2500 Chipset) Using Default Modules"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by bigboy_pdb on 2007-10-23
I was able to get my wireless card working using the default modules with the following solution. Please post whether or not this worked for you if you were having the same problem.

**The Problem**
The networks could be seen, but "network manager" wouldn't connect. The "network manager" graphic where there are two dots and a blue arc that circles through them wouldn't dissappear and neither of the dots would turn green (which indicates that no connection was being made with the router).

**Network Setup**
My wireless networking card is a PCI card that has an rt2500 chip. My router is set up so that it broadcasts and so that it is using WPA-TKIP encryption. I have also tested the solution using WPA-AES, WEP64-bit, and I've tried connecting without encryption. If you are not using encryption then the solution is not necessary, otherwise the solution works with WPA-TKIP, WPA-AES, and WEP-64bit (and is should work with WEP-128bit).

**The Solution**
For WPA encryption, I changed the "/etc/network/interfaces" file so it contains:
```

iface wlan0 inet dhcp
pre-up ifconfig wlan0 down

wpa-psk *encryption_key*
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid *ssid*

pre-up sleep 20
pre-up ifconfig wlan0 up

```
where *encryption_key* is the encryption key and *ssid* is the SSID on the router I wanted to connect to.

For WEP encryption, I changed the "/etc/network/interfaces" file so it contains:
```

iface wlan0 inet dhcp
pre-up ifconfig wlan0 down

wireless-key *encryption_key*
wireless-essid *ssid*

pre-up sleep 20
pre-up ifconfig wlan0 up

```
where *encryption_key* is the encryption key and *ssid* is the SSID on the router I wanted to connect to.

Everything starting with "wpa"/"wireless" was added from "network manager" when I performed a manual configuration (meaning you can use "manual configuration" in "network manager" to get those lines). If the solution doesn't work, it might be a good idea to try to change the number after "sleep" to a larger number.

**NOTE:** If you use the "manual configuration" option in "network manager" and the window appears but the widgets aren't showing up, be patient because it does eventually come up.

Run the command "sudo /etc/init.d/networking restart" (or "sudo /etc/init.d/dbus restart") to restart your network interfaces using the "/etc/network/interfaces" file. _It will pause for 20 seconds so don't close the terminal_. If you don't want to wait 20 seconds, comment out the sleep line when you run the command "sudo /etc/init.d/networking restart", but uncomment it again after you've run the command so that it will be used when your computer restarts.

**File Permissions**
Since the file "/etc/network/interfaces" has the group & other read bit enabled this means that users other than root can see the encryption key. If you want to change this then do the following. Use the command "sudo chmod 600 /etc/network/interfaces" to change the permissions of "interfaces" so that only root can read/write from/to the file. Also, if you're using gedit to edit the file, run "sudo rm /etc/network/interfaces~" to get rid of the temporary file (which will still be readable by the group & others).

**Additional Information**
**NOTE:** If the solution worked then you might not need to read this additional information. I'm writing how I figured out a solution to the problem to help the developers correct it.

After encountering the problem, I tried to set up a manual connection and I restarted my computer. After that only a set of monitors would show up. I tried pinging the router, but it didn't work. I then brought the interface down (using the command "sudo ifdown wlan0") and then back up (using the command "sudo ifup wlan0") and I was able to connect to the router. This worked, but the commands needed to be used every time the computer was restarted. I tried editing "/etc/network/interfaces" to use "pre-up ifconfig wlan0 down" and "pre-up ifconfig wlan0 up" to bring the interface down and up during startup, but it wasn't working. Since a connection could be made after logging in (with the use of the command "sudo /etc/init.d/networking restart"), I figured that maybe another process had to be started before a connection could be made. I added the sleep command to create a delay before the interface was brought up (and it worked).

---

### Post by LordYama on 2007-10-23
Unfortunately this hasn't helped in my case :(

I've tried the included rt2500 and rt2x00 drivers,  ndiswrapper and compiling the rt2500 driver from the rt2500-source package. No luck so far. Next I'll download the source from serialmonkey and see how that goes.

I previously had the card working in Dapper with ndiswrapper. With Gutsy, not even that works. I can see the hardware and interface, but I can't see any networks and I can't connect manually either.

---

### Post by kashms on 2007-10-23
My router is also setup for WPA-PSK. With the Serial Monkey drivers sometime the network manager would go in a loop and repeatedly ask for a password. Now I'm using ndiswrapper and it happens alot less. But I found doing 

"sudo /etc/init.d/networking restart"

actually didn't affect network manager if it had hung. Instead I use 

"sudo /etc/init.d/dbus restart"

which effectively restarts network manager and usually connects.

P.S. Network manager is set for roaming so my /etc/network/interfaces file is minimal:

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by bigboy_pdb on 2007-10-23
LordYama, I'm aware that you're having trouble with getting your wireless networking card to work while you have a wired networking card in your computer (which I think is an issue with your interfaces), but did the solution here work when the wired networking card was removed? (You post here: "http://ubuntuforums.org/showthread.php?p=3611013#post_message_3610630" makes it sound as though it might have worked for you).

I need some feedback because this solution hasn't been widely used (granted that I was the first one to try this). It would be good to know if it might work for other people.

---

### Post by bigboy_pdb on 2007-10-23
Thank you for the suggestion kashms. I'll mention that in the first post.

---

### Post by d_in_Conduct on 2007-10-23
This solution didn't work for me in Gutsy 64-bit.

The adapter is USB and it sees the router and all available wireless networks, but according to lshw, no driver gets associated with the device.  

What had worked for me in Gutsy-32 (compile the legacy rt2570) doesn't work in 64-bit.  It looks like the sources are laid out differently.

Oh, well.  Back to search, read, try, search some more, read some more, try some more...

---

### Post by LordYama on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/152027) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **bigboy_pdb said:**
> LordYama, I'm aware that you're having trouble with getting your wireless networking card to work while you have a wired networking card in your computer (which I think is an issue with your interfaces), but did the solution here work when the wired networking card was removed? (You post here: "http://ubuntuforums.org/showthread.php?p=3611013#post_message_3610630" makes it sound as though it might have worked for you).

I need some feedback because this solution hasn't been widely used (granted that I was the first one to try this). It would be good to know if it might work for other people.

That's correct. Your instructions are fine, except that **I needed to remove my wired networking card for the wireless to see anything**.

As for chmoding /etc/network/interfaces, I haven't done so because other apps might need to read it. Ideally, we shouldn't be storing passphrases in there.

---

### Post by bigboy_pdb on 2007-10-24
> **d_in_Conduct said:**
> 
This solution didn't work for me in Gutsy 64-bit.


I'm sorry to hear that. If need be then perhaps you could use the 32-bit version until the bugs in the 64-bit version are fixed. It might also be a good idea to post your bug on launchpad if no one else has posted it.

---

### Post by Agent86 on 2007-10-26
Thanks, I got my RT2500 and WPA operating in Ubuntu 7.10 Gutsy with this fix. It wasn't working at first until I added the **auto wlan0** line at the end. And when I do **/etc/init.d/networking restart** I get these errors:```
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - There is already a pid file /var/run/dhclient.wlan0.pid with pid 867530911

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
```But after the 20 second timeout, the RT2500 associates with the access point, gets an IP through DHCP, and surfs the net.

Here is my functioning /etc/network/interfaces. I have an onboard Ethernet port, but the fix works whether my Ethernet is enabled/connected or disabled in BIOS (it's disabled now).```
auto lo
iface lo inet loopback

# auto eth0
# iface eth0 inet dhcp

iface wlan0 inet dhcp
pre-up ifconfig wlan0 down

wpa-psk KeyAfterRunning_wpa_passphrase_AndWithoutQuotes
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid MyESSID_WithoutQuotes
pre-up sleep 20
pre-up ifconfig wlan0 up

auto wlan0
```Here is the relevant line from the output of an **lspci** command:```
00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
```It's nice to know that the out-of-the-box driver is working (with some effort) for the RT2500 at least - I had to compile the legacy driver to get the RT61 and WPA working in Xubuntu 7.10 Gutsy.

EDITED TO ADD: Well, [it works with the RT61, too!]("http://ubuntuforums.org/showpost.php?p=3644427&postcount=5")

---

### Post by bigboy_pdb on 2007-11-02
Sorry I haven't responded in a while.

LordYama, the interfaces file is for configuring "ifup" and "ifdown" so I don't think that other programs should be using it. I've tried removing all group and world permissions from the file and I didn't have any problems with it (although this isn't to say that others may not experience any problems from doing this). Removing the permissions shouldn't affect "ifup" and "ifdown" since both commands need root privileges to be run. The only time that I can think of the world/group readability of "/etc/network/interfaces" as being a significant security risk is if both a person is in your area (or knows where you are located) and he/she has access to one of your accounts. Since Edgy (and possibly beforehand), "/etc/network/interfaces" has contained encryption keys for cards with Ralink chips. The Ubuntu documentation suggests typing WAP keys in "/etc/network/interfaces".

**Ubuntu WAP documentation:**
[https://help.ubuntu.com/community/WifiDocs/RalinkRT2500Old?highlight=%28rt2500%29](https://help.ubuntu.com/community/WifiDocs/RalinkRT2500Old?highlight=%28rt2500%29)
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28rt2500%29](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28rt2500%29)
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

I'm not suggesting that this is a good way to do things. I'm just stating that it shouldn't be a high level security risk.

The only way that I can think of setting up a wireless connection without using "/etc/network/interfaces" is if a person uses "wpa_cli" to set up a wireless connection after "wpa_supplicant" has been started.

---

### Post by bigboy_pdb on 2007-11-02
Agent86, thank you for the feedback. I got the same errors.

"wmaster0" is another interface although I'm not sure what it's for and whether or not "wlan0" somehow relies on it. "/var/run" is the directory where the process IDs for programs that were started during a system boot are stored. When I checked, the processes listed in the pid files in "/var/run" each corresponded with a running process, but the process ID of "dhclient.wlan0.pid" did not match the process ID displayed in the error message.

I tried some things to determine what was causing those error messages, but I wasn't successful in determining what was causing them. I also searched to find out what might be causing them, but there wasn't too much information on them.

I'm guessing that the error about "wmaster0" is occurring because the interface cannot be brought down/up and that the first process id of "dhclient" is being stored somewhere and the newly created process id for "dhclient" is being compared to the original process id. I remember reading that SIOCSIWAUTH is a constant/macro in C/C++ and I'm guessing that the "SIOCSIWAUTH" message is related to that. I don't think that the first two errors would be problematic, but I don't know about the last one. Perhaps someone else will have more information regarding these errors.

---

### Post by Soglad on 2007-11-02
I have got this exact same problem, only I'm using a Broadcom 4311 chipset....anyone know what the problem is??

I made a thread nobody seems to be answering here:

[http://ubuntuforums.org/showthread.php?t=601025](http://ubuntuforums.org/showthread.php?t=601025)

---

### Post by sramkrishna on 2007-11-04
It could be sound.  I had the same problem and I was able to get it working manually by clicking on the network manager applet and then disablign wireless.  THen going to command line and typing in the iwconfig wlan0 essid MyEssid key 73849a3 and then doing a dhclient wlan0.

That seemed to work.  It wasn't apparent what was causing the problem until somehow sound stopped working because I installed the new alsa (sound doesn't work either in gutsy).  Then NM started workign perfectly.

sri

---

### Post by walzi on 2008-03-03
I did exactly the same as told in the post from Agent86 and also see the same error messages. However everything is working now. So the trick is to add the down/sleep/up lines.

I think one way to figure out if this also helps for you is to connect to your AP by using the GUI of the network manager i.e. re-entering the passphrase. The side effekt is that you get most of the needed lines in the /etc/network/interfaces file and just have to add the down/sleep/up lines.

BTW: I have a rt61 based PCI card working in WPA (AES) encryption mode.

---

