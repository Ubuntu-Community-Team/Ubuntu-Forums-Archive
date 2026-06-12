---
title: "Problems with Intel Pro/Wireless 2200"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by dachin on 2007-04-01
I'm new to Ubuntu and I've been trying to setup my laptop's built in wireless card for a couple days now.  Basically I've followed the entire troubleshooting guide and I'm still coming up empty.

Here is where I am.  lshw shows that I'm using the ipw2200 driver and it is loaded.  My card associates with my router fine and iwconfig confirms it.  However, if I set the connection (eth1) to DHCP I never get an IP address.  ifconfig confirms this, the interface is up and I see the normal info but no IP information.  I've tried running dhclient eth1 and it eventually comes back with no DHCP offers received.  I know my router is handing out addresses because all of my windows machines are using it.  If I manually configure an IP I can ping loopback (127.0.0.1) but not my router (192.168.1.1).   When I ping 192.168.1.1 I get destination host unreachable.

I'm using WEP and 1 thing that I can't seem to determine through the GUI or config file, is how to specify WEP.  The GUI just has a network password, it does not specify if it's WEP or WPA or some other.  Currently I'm back to trying a static address again.  Here is the eth1 entry from my /etc/network/interfaces file:

auto eth1
iface eth1 inet static
wireless-essid [www.theempirestatemusic.com](www.theempirestatemusic.com)
wireless-key xxxxxxxxxxxxxxxxxxxxxxxx
address 192.168.1.40
netmast 255.255.255.0
gateway 192.168.1.1

I know my ssid is not really what someone would expect, but it never seemed to cause any issues.  Could it be that the . is a special character?  

I'm pretty much at the end of my rope here.  Any suggestions would be appreciated.

Thanks

Dan

---

### Post by Floppyjoe on 2007-04-01
Are you using ndiswrapper to get your card to work?
I pulled this off the ndiswrapper list site for your card.
> Card: [Intel] PRO/Wireless 2200BG

    * pciid: 8086:4220
    * Driver: version 8.0.0 [ftp://aiedownload.intel.com/df-support/7440/eng/intel%20wireless%20proset%20%20-%208.0.0.167%20generic%20.exe](ftp://aiedownload.intel.com/df-support/7440/eng/intel%20wireless%20proset%20%20-%208.0.0.167%20generic%20.exe)
    * Driver (latest): version 8.1.1.0 [ftp://aiedownload.intel.com/df-support/7819/eng/wireless%208.1.1.0%20-%20generic%20tic%2088663.exe](ftp://aiedownload.intel.com/df-support/7819/eng/wireless%208.1.1.0%20-%20generic%20tic%2088663.exe) Other: Tested on Debian with kernel 2.6.8, ndiswrapper 0.11, w22n51.inf from version 8.1.1.0. w22n50.inf from version 8.0.0 does not appear to work. 

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#I](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#I)

---

### Post by dachin on 2007-04-02
Thanks for the reply.  I'm not really familiar with NDISwrapper.  It looks like it would allow me to use windows drivers with the Linux kernel?  I guess I'll read up on it.  I tried the links on sourceforge to download the drivers but they weren't working.  I'll read up on it and try again.

Thanks

---

### Post by aysiu on 2007-04-02
Intel Pro Wireless 2200 doesn't need *ndiswrapper*. I put an Intel Pro Wireless 2200 in my Dell Inspiron 500m, and it works perfectly. Install *network-manager*, and you should be able to browse available wireless networks without any further tweaking.

Especially if you're using WEP (and not WPA), everything should work with IPW2200 out of the box.

Go to System > Administration > Network and configure the wireless portion. It should be more or less self-explanatory.

---

### Post by Sencer on 2007-04-02
I also have an ipw2200, and I use network-manager as well. With WPA and WEP (different APs obviously), and it works very well. It's completely GUI-driven, and it relies on DHCP (no manual configuration). You select the network you want to connect to, and it will ask you for the key (in case of WEP/WPA), you enter it, click connect, and it will do the rest.

---

### Post by dachin on 2007-04-02
Thanks, but I've tried everything through the GUI.  If I go to System --> Administration --> Networking I see my connections (I assume this is what you are calling network manager).  However I don't get a list of wireless networks, I simply am able to configure my wireless connection manually which I have done.  Is there another network manager package I should install?

I can use iwlist to scan the available wireless networks just fine.  I see mine and 1 other in range but I have no GUI that allows for this.  I'm using GNOME. btw.

Like I've said, everything seems to work fine except actually getting an IP address.  I can associate with the router and view it's statistics with iwconfig.  It's almost as if TCP/IP is not working or available.....sort of like back with Windows 95/98 when you could uninstall TCP/IP.

---

### Post by aysiu on 2007-04-02
No, System > Administration > Networking is different from *network-manager*.

The regular network admin you have to configure manually (specifying the network name, the password, etc.)

You should install *network-manager*

Read more here:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by dachin on 2007-04-02
OK, thanks.  Now if I could just get online to download packages......doh!

---

### Post by aysiu on 2007-04-02
> **dachin said:**
> OK, thanks.  Now if I could just get online to download packages......doh!
It's a bit annoying, but if you have a connected computer, you can download the package (and all its dependencies) from [http://packages.ubuntu.com](http://packages.ubuntu.com) and then move them over to the desktop of your Ubuntu laptop and type these commands into the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
``` Do you not have a wired connection you can use with your laptop?

---

### Post by mrund on 2007-04-02
I have the same problem with my wireless connection, so I installed network-manager. As far as I can tell, its executable is named nm-applet, and it doesn't do much for me. Plugging the machine into the wired network, the applet tells me "woot, you are online". Unplugging, the applet says "boo-hoo, you are offline". It seems unaware of my wireless adapter, which is in plain view to iwconfig.

Apparently I have to run a background service also, named NetworkManager. Gah.

---

### Post by aysiu on 2007-04-02
If you right-click the Network Manager applet, there should be an option to *Enable Wireless*.

If you left-click it, you should then see a list of available wireless networks to join.

---

### Post by mrund on 2007-04-02
Yeah, I definitely agree. It should.

---

### Post by dachin on 2007-04-03
I hooked my laptop up to my router with the on board ethernet (which requires a 35' cable to my roommates room) and downloaded Network Manager.  I seem to be in the same boat as mrund.  Within Gnome the network manager basically does nothing.  Within KDE it actually gives me the option to disable wireless or view wireless networks.  However, it does not seem to recognize any wireless networks.  iwlist however sees the networks fine!!!! 

What is going on here?  I'm about to switch to FC6.  Any suggestions would be much appreciated.

---

### Post by GeneW on 2007-04-21
> **aysiu said:**
> If you right-click the Network Manager applet, there should be an option to *Enable Wireless*.

If you left-click it, you should then see a list of available wireless networks to join.

If I right click, I see:

[IMG]http://farm1.static.flickr.com/207/467113232_15b4d4ff48_m.jpg[/IMG]

And here is what I see if I left click:

[IMG]http://farm1.static.flickr.com/188/467113230_0528bc74ac.jpg[/IMG]

How do I get that "Wired Network" item enabled?  I'm using the standard ipw2200 driver for the card, should I be using some other driver?  I looked in the "restricted drivers" utility but no network driver is listed there.

The wireless works fine through the old network configuration tool (pre-fawn) but I'd really like to be able to use the nm-applet to find local networks when I am away from home.  Right now I still have to use "iwlist scan" in a shell and then paste the name of the node into the network settings, not really very convenient.

---

### Post by aysiu on 2007-04-21
I have no idea.

I wish I knew how to help fix this. It just works for me.

The best I can do is show you how it's *supposed* to work. Here are screenshots of how it works for me.

---

### Post by Buffalo Soldier on 2007-04-21
If nm-applet not managing your network connections, you'll need to comment out the references to all interfaces (except lo) in /etc/network/interfaces to let Network Manager handle them.

```
sudo gedit /etc/network/interfaces
```

Example:> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
# auto eth1

# iface eth1 inet dhcp

---

### Post by GeneW on 2007-04-21
Buffalo Soldier, thanks that did it.  Awesome.

---

### Post by xflbret on 2007-05-07
it didnt work for me. why? all i have is wired network

---

### Post by s_telios on 2007-07-20
> **Buffalo Soldier said:**
> If nm-applet not managing your network connections, you'll need to comment out the references to all interfaces (except lo) in /etc/network/interfaces to let Network Manager handle them.

```
sudo gedit /etc/network/interfaces
```

Example:

It worked for me too, many thanks...\\:D/

---

### Post by outlaw686 on 2007-07-24
> **aysiu said:**
> I have no idea.

I wish I knew how to help fix this. It just works for me.

The best I can do is show you how it's *supposed* to work. Here are screenshots of how it works for me.

lawl team awesome

---

### Post by dfmalh on 2007-10-10
thanks ppl, at last I can see my available wifi networks

---

### Post by dfmalh on 2007-10-10
hmmmm... now I have another question: how do I set up a "secure"/"masked" wifi network?

in the Windows environment it was not much of a problem... the thing is, you have to set it up, otherwise the connection can not be made...

as I know only a little about setting up wifi networks and new to Ubuntu I am in unfamiliar waters...

this is the details of the "masked" network in windows:

Network Authentication: WPA
Data encryption: TKIP
EAP type: PEAP
     Authentication method: Secure password (EAP-MSCHAP v2)
- and of course "connect when network is in range"

thanks for the help.

---

