---
title: "No ethernet connection after installing Ubuntu-Mate 18.04.1 Bionic"
date: 2018-12-17
forum: Networking &amp; Wireless
---

### Post by smith73 on 2018-12-17
Hi, 
so far I received nearly zero help on Ubuntu 16.04 issues, so after installing Ubuntu Mate 18.04.1 Bionic Beaver onto HP 250 G6 Notebook PC I can't even setup the Ethernet connection in order to get this help. 

What I did and what didn't work:

1) In Network Connections GUI (top right icon) I created a new Ethernet connection and entered IP address, subnet mask, DNS servers etc which worked ok in Ubuntu 16.04 installation. Same data entered into "Wired connection". ping google.com just shows packets being transmitted and 0 received.

2) I modified /etc/network/interfaces then changed to default. Also modified resolv.conf to enter DNS server addresses then changed to default (nameserver 127.0.0.53). Now there seem to appear 2 additional resolv.conf related files in etc directory: resolve.conf and resolv.conf.save (one of them seems to be empty despite restoration to default).

3) I successfully activated ethernet connection via "nmcli up" command. Various nmcli commands (from man nmcli) show active status and full connectivity of ethernet connection on recognized network interface, also correct assigned IP, DNS etc, but "ping google.com" renders packets being transmitted and 0 received.

4) I modified 01-network-manager-all.yaml file under "netplan" directory as was mentioned in the internet for the new network management system in 18.04. from
default 

network:
   version: 2
   renderer: NetworkManager
 
to something similar to (provided at netplan.io as examples) except for another prefix for IP denoting the relevant subnet mask
        network:
  version: 2
  renderer: networkd
  ethernets:
    enp3s0:
      addresses:
        - 10.10.10.2/24
      gateway4: 10.10.10.1
      nameservers:
          search: [mydomain, otherdomain]
          addresses: [10.10.10.1, 1.1.1.1]
     
        
 "ping google.com" still rendered packets being transmitted and 0 received. So I restored the .yaml file to default (managed by Network Manager).


Also after plugging in the ethernet cable into the new installation of Ubuntu Mate 18.04 Bionic top right notifications that 
your're connected/disconnected have been displayed on step 1) and have not been displayed at steps 2-4). So now there are no notifications
that you're connected displayed after connecting the ethernet cable.


Is it possible to get any help on establishing the wired ethernet connection on Ubuntu Mate 18.04 on this forum?

---

### Post by QIII on 2018-12-17
It appears that your first query with regard to 16.04 in February was left to sink to the bottom of the ocean because you didn't bump it back to the top after about 12 hours with no response.  Remember that we are all end-users such as yourself, living in all time zones around the world and living a life outside of the Ubuntu Forums.  If nobody with just the right answer is around to see your initial post, you may not get an immediate response.  Bump your posts after about 12 hours if you have no response.

Please take care to avoid a snarky attitude.  Few people are interested in providing volunteer support to those who demonstrate a poor attitude.

Yes.  Somebody can help you with this.  At this very moment, however, they may be having a meal with their family, at work, sleeping or enjoying some time working at a hobby.

---

### Post by smith73 on 2018-12-20
I'm not sure why you're identifying basic beginner-type user frustration as some sort of "snarky" or "poor" attitude, sorry, if anything.

So now I applied .yaml file configuration as specified in netplan.io example for setting a static IP address (rendered by networkd, mentioned above)
(I'm not sure why do they use dash and a new line before the IP address with a subnet prefix, but I tried both with same result):

```
Error in network definition //etc/netplan/01-network-manager-all.yaml line 5 column 9: expected mapping
```

I used my network interface device name and addresses provided by network provider. The prefix for subnet mask I took from Neworks GUI (top right icon) IPV4 tab.

This error is displayed also under a default .yaml configuration with less than 5 lines.
network:
  version: 2
  renderer: NetworkManager


This error is displayed after the command *sudo netplan apply*. Before several reboots I also used the command *sudo netplan generate *once before this command (after saving a new configuration into .yaml file).

Previously I also deleted the 01-network-manager-all.yaml.save (probably) file from default home folder (on the desktop). This file appeared when I saved a
.yaml file configuration which didn't work. Now there is a 01-network-manager-all.yaml file (duplicate?) in the home folder on the desktop with the same content
as the .yaml file in /etc/netplan.

I may reinstall Ubuntu Mate 18.04 if I were given some potentially working advice (if I deleted or modified some crucial files) or install 16.04 if updates for it will be available 
after 2019-04.

---

### Post by Nick Kruger on 2018-12-24
I had exactly the same error message &#8230; "expected mapping"

I tried further with netplan &#8230; but then discovered that my network interface was dead !  I'm serious ! I think netplan killed my onboard network &#8230; so I had to go and buy a PCIe network card today. Now I have just re-installed ubuntu 18.04. I'm not touching netplan again ! :(

---

### Post by smith73 on 2018-12-25
It would be useful if you'd mention some of the commands you used. Because I just erased 18.04 and installed Ubuntu Mate 16.04.3 on this HP notebook (and the installation guide didn't detect any OS previously installed) which doesn't use netplan (with system crash due to non-rebooting after prompting to eject the installation DVD). The connected notification appeared as usual, so I configured ethernet connection via GUI as I did on Asus notebook when connection worked, and it didn't work. When I checked the boxes on "Other software" tab in "Update Settings" to download from Canonical, while updating cache the structure, description and description signature of Ubuntu Mate 16.04.3 have been displayed as downloaded and for subsequent packets - network not available. I checked via terminal commands *nmcli networking connectivity* and *nmcli connection show --active*, and the ethernet connection was displayed as active and on full connectivity on my network interface device name on HP, *ifconfig  *displays the same interface device name recognized, so I may suppose my network interface device is ok. But still packets were transmitted and 0 received. 

However in Mozilla browser I've got the page displayed by my internet provider when I didn't pay for the internet in time (that my internet services are being blocked due to unauthorized etc connection or due to payment being late). While after connecting the same ethernet cable to an Asus notebook with Windows,
the connection worked as usual undisturbed.

So i may contact my internet provider and HP. I don't know how my ethernet connection got working on 16.04 on Asus, there were same issues with ethernet after installation. I configured it via GUI and in Welcome screen while trying to update there was a notification that an internet connection required to download updates. This notification persisted for about a month even after the connection got working, and probably got working after I installed the updates from terminal. So I may suppose connection gets working after updating so may download updates on an USB and install onto OS with non-working connection. But how can I find the necessary updates for this download?

[SIZE=1]I don't know if this is relevant, but this HP is equipped with some security device which in BIOS is displayed as "hidden" (non-visible to OS).[/SIZE]

---

### Post by smith73 on 2019-01-02
Apologies, if anything, I'm sort of panicker.

I needed to only contact my ISP and they authorized the new network HP device, so ethernet now is ok on 18.04 after entering data just via GUI "Network" icon.

The problem was that my ISP's page with a notice that internet services are blocked due to unauthorized connection or after changing 
the network device appeared in Mozilla only after I installed Ubuntu Mate 16.04 on this PC. A similar message appeared while trying 
to update via terminal (it tried to connect to the servers and asked does this network require authentication). And after the initial installation 
of Ubuntu Mate 18.04 and trying to connect to the ethernet none of these appeared in Mozilla or in the terminal so there was no clue 
that ISP hadn't actually authorized my connection from a new device.

---

