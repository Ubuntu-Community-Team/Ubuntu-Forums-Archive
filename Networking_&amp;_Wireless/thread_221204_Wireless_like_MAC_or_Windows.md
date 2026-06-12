---
title: "Wireless like MAC or Windows"
date: 2006-07-22
forum: Networking &amp; Wireless
---

### Post by krypto_wizard on 2006-07-22
When will Ubuntu have a wireless support as seamless as MAC and windows.

I want that whenever I move my laptop take the best connection but currently it doesnt do that. 

IT does show me listing of wireless networks but connecting to it takes a long time while MAC and win doesn't take time.

I am Ubuntu loyalist but why is Ubuntu lacking in this field or AM I missing on something. I knew there is wireless manager but it hasn't come vrey well.

Please help.

---

### Post by misha680 on 2006-07-22
```
sudo apt-get install network-manager network-manager-gnome
```

or go to Synaptic and install the network-manager and network-manager-gnome packages. Then reboot and you will have this functionality.

Misha

---

### Post by vapour on 2006-07-22
Just installed ubuntu 6.06 and no issues at all. Default install and my wireless works flawlessly (IBM T41 laptop)..

V

---

### Post by krypto_wizard on 2006-07-23
I installed it but still cannot see anything in KDE. In gnome I couldnt obtain network-manager-gnome from repos.....may be those servers are down.


Ok, how to use the network-manager. Does it sit in the taskbar or menubar. I can see atleast 8 networks in windows and it doesn't show me anything. 

May be I dont know if I am using the right program.

Could somebody please let met know step by step procedure to get this thing fixed.

Every help is appreciated.

Thanks

---

### Post by misha680 on 2006-07-23
Sorry, I can't help with the KDE part because I use gnome and don't know much about the KDE. Yesterday, I think some of the repos servers were in fact down, so you should try network-manager-gnome again.

However, the important thing that I forgot to put in is that network manager configures your network connections differently than ubuntu does by default, so what you should do is type the following command in a terminal window:

```
sudo gedit /etc/network/interfaces
```

And make sure the only two line in there are:

```
auto lo
iface lo inet loopback
```

(Note, this means that NetworkManager will manage _all_ your interfaces, if you do not want this, then you need to leave lines in there for the appropriate interfaces - I definitely have no problems with this as I just have a wired and wireless connection, so I just have NetworkManager manage those).

Save the file, install network-manager, and then reboot. When you log in, you should see a network manager panel app sitting on your panel (in my installation, and I think on Ubuntu default installation, it is on the top right corner of the screen, by the little separator bar thingy). You can click on it, and it should show you all the available wireless connections along with their strengths. You can click on one to connect to it, and once it has connected to a connection once, if the connection is available again network manager will try to connect to it.

I hope that helps. I'm really not sure about the KDE stuff :(

Misha

---

### Post by krypto_wizard on 2006-07-24
Misha,

No success with what you said. It wont bring up any little thingy up there.

It stopped my active wireless ......

what else shd I do man ?

---

### Post by krypto_wizard on 2006-07-24
My /etc/network/interfaces looks like this


```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.

auto ath0

iface ath0 inet dhcp
wireless-essid XYZ
wireless-key ABABABABAB

iface eth0 inet dhcp
auto eth0

```

I commented other lines as per u said but then those didnt help. I have installed both network-manager and network-manager-gnome.


Any more suggestions.

---

### Post by kpolice on 2006-07-24
Install network manager as they said maybe you have to enable other repositories ( [help here]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") ).

If you don't use gnome then you will have to install knetworkmanager instead of network manager gnome. 

After you installed those packages your interfaces file should look like
```
auto lo
iface lo inet loopback
```

And only those line, nothing else and nothing more. Now it's time to reboot and you should see the network manager icon on your panel.

If after you edit your interfaces and rebooted your pc you don't see anything then try to run nm-applet on the terminal and post any error message if it appears.

---

### Post by wieman01 on 2006-07-24
I used to use Network Manager under KDE. The GUI in KDE for the Network Manager Daemon is called KNetworkManager. Nice little GUI that helps you configure wireless networks within reach.

Now, your "interfaces" file definitely needs a face-lift. As far as I remember (I've stopped using Network Manager because I require static IP and hidden ESSID which NM can't do) the file needs to be empty when used in connection with Network Manager. So no lines, just a blank file. 

Check it out... If that does not work, look for it in the forum, there a many posts that will guide you through it.

---

### Post by wieman01 on 2006-07-24
> **kpolice said:**
> Install network manager as they said maybe you have to enable other repositories ( [help here]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") ).

If you don't use gnome then you will have to install knetworkmanager instead of network manager gnome. 

After you installed those packages your interfaces file should look like
```
auto lo
iface lo inet loopback
```

And only those line, nothing else and nothing more. Now it's time to reboot and you should see the network manager icon on your panel.

If after you edit your interfaces and rebooted your pc you don't see anything then try to run nm-applet on the terminal and post any error message if it appears.

Oh well, nothing to add. Was a minute late I guess. ;-) But it's that easy, really.

---

### Post by krypto_wizard on 2006-07-26
I have network-manager installed and so is network-manager-gnome. I am now using gnome.

I cant see the small icon sitting on panel as u guys have said. Am I doing something worng ?

Please help

---

