---
title: "VPN connection editor missing and reinstalling has not helped"
date: 2014-10-05
forum: Networking &amp; Wireless
---

### Post by Robbyx on 2014-10-05
I decided I wanted to use openvpn but usually I need to update the password. This time I can not edit any of the entries in the vpn connection.  I tried creating a new connection but instead of giving me the options to set it up, the network mangager asks that I import from file. I do not have a file to import.

I have tried reinstalling some of the files from synaptic but that has made no difference. 

Any suggestions, please?

Robin

---

### Post by Robbyx on 2014-10-05
I tried this suggesion:
> Now, you can add vpn connection to your system using NetworkManager itself. You may need to restart the NetworkManager as follows:

# /etc/init.d/network-manager restart


It did not work. There is no network-manager app in init.d!

The following reported the lastest versions were already installed:
sudo apt-get install network-manager-openvpn
sudo apt-get install network-manager-openvpn-gnome

---

### Post by ricey155 on 2014-10-05
I used this just a min ago on 14.04 and it installed and works - just started using VPN today so hope it helps - just need a reliable free service for p2p usage 

sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome

---

### Post by Vladlenin5000 on 2014-10-05
> **ricey155 said:**
> I used this just a min ago on 14.04 and it installed and works - just started using VPN today so hope it helps - just need a reliable free service for p2p usage 

sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome

Supposedly the OP already have them, the problem is a password that can't be changed...

---

### Post by Robbyx on 2014-10-07
> **ricey155 said:**
> 
sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome

Unfortunately it made no difference:

> sudo apt-get install openvpn network-manager-openvpn network-manager-openvpn-gnome 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager-openvpn is already the newest version.
network-manager-openvpn-gnome is already the newest version.
openvpn is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 7 not to upgrade.
robins@robins-EP35-DS3L:~$ 


I am wondering what else to do to bring back the VPN connection editor. Any other suggestions please?

I have also deleted the old openvpn connection (that gives the error message) I have tried to recreat it using a saved conf file which used to work. Now when I try to import it there is an error message that it is incorrect or contains no vpn information. 

I am unable to create the vpn connection manually. I only have the choice to import a file.

---

### Post by weatherman2 on 2014-10-07
> **Robbyx said:**
> 
It did not work. There is no network-manager app in init.d!

 
FYI, with recent versions of Ubuntu, the correct way to restart a service is:

```
sudo service network-manager restart
```

And not use /etc/init.d .  (Of course, rebooting which I'm sure you've already done restarts the process anyway.)

You can use openvpn directly from the command line to connect to a VPN server, without using Network Manager at all.  In fact, I would try this once to make sure i works.  If it does, then Network Manager is probably messed up, in which case I would try completely uninstalling and then re-installing it.  But if you are unable to connect to the VPN using openvpn from the command line, then something else is probably wrong.  And you might get clues in error messages from openvpn when trying to run it.

---

### Post by Robbyx on 2014-10-08
Weatherman:

I am able to access the internet presumably by way of the network manager. Any case the NM is working from the command line. My problem might be different. It is the absence of the vpn network editor. As you can see above I have tried various reinstalls and now that I have deleted the old VPN connection I can not create a new one.

---

