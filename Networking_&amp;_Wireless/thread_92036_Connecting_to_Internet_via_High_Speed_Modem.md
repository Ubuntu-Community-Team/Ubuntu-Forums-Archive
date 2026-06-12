---
title: "Connecting to Internet via High Speed Modem"
date: 2005-11-18
forum: Networking &amp; Wireless
---

### Post by BobSongs on 2005-11-18
Greetings;

I just set up my friend's PC with Edubuntu (5.10). He doesn't have a router; he only has a high speed modem with which he dials in to his Internet service provider. He keys in a username and password each time.

I set up his machine on my LAN, under my router. So I gave him a static IP address. Now we're trying to finalize the setup at his place. We've removed the static IP for DHCP. Now we're wondering what he uses to connect to the Internet.

Any ideas?

[Addition]

I guess what we're looking for is 'pppoe' of some sorts. Thanks.

[Edit]

Okay. We've tried 'pppoeconf'. It detected his network card. (Yay.) However, it returned an error:[INDENT]'Sorry, I scanned one interface but the access concentrator of your provider did not respond. Please check your network and modem cables. Another reason for scan failure may also be another running pppoe process.'[/INDENT]His high speed modem is a 'GNet' model EA700, if that's of any value.

Thanks.

---

### Post by BobSongs on 2005-11-19
Just a note.

The system returned an error when using 'pppoeconf' because we changed the network card's IP info (System > Administration > Networking; under Connections tab highlight 'Ethernet Connection', edited its settings and changed it from a Static IP to DCHP) and didn't reboot the PC before using 'pppoeconf'.

So, for the sake of posterity, here's what I've found from the [Chennai Broadband Guide]("http://www.chennailug.org/wiki/Chennai_Broadband_guide") (the following reflects some corrections and replaces 'ppp0e' with 'pppoe'):

> **[SIZE=4]Configuring PPPoE for ADSL Connection in Ubuntu:[/SIZE]**[LIST]
[*]PPPoE configuration is installed default during most Ubuntu installations. To check whether it has been installed, type the following in a terminal box:[/LIST]```
dpkg -l | grep -i pppoe
```[LIST]
[*]If Ubuntu has installed pppoeconf, the output willl be something like this:[/LIST][quote]ii   pppoeconf   1.8ubuntu2   configures PPPoE/ADSL connections[LIST]
[*]If it's not the above output then you have to install pppoeconf, as follows:[/LIST]```
sudo apt-get install pppoeconf
```[/quote](**Edit**: *How on **earth** am I supposed to 'apt-get' without an Internet connection?*)
> [LIST]
[*]After the installation you can configure the pppoeconf. You will need just your username and password and a bit of common option answers. Select always on, as it is best suggested by Ubuntu itself.[/LIST](**Edit**: *Before you go messing with this wizard it might be a good idea to backup your original 'dsl-provider' file with the following code, **please***):
```
sudo cp /etc/ppp/peers/dsl-provider /etc/ppp/peers/dsl-provider.backup
```> **To configure:**
```
sudo pppoeconf
```**Extra Tips:**[LIST]
[*]To start the connection:[/LIST]```
pon dsl-provider
```(I have a doubt ?! as to whether we have to type it as 'dsl-provider' or type the name of the provider such as 'dataone' or the username 'user@dataone'??)(**Edit**: *From experience **pon dsl-provider** is the way to connect. The problem with switching from 'dsl-provider' to something else is whether such a file exists in the /etc/ppp/peers folder. If you don't have an alternative file there's no point invoking it.*)
> [LIST]
[*]To end the connection:[/LIST]```
poff -a
```For more information about 'pon', 'poff' and 'plog', open the manual in a terminal box. Hit 'q' to quit:
```
man pon
``````
man pppoeconf
```**To the community**: if you see an error, please notify me and I'll edit this post. Thanks.

---

### Post by BobSongs on 2005-11-21
:p  And to bring this thread to a conclusion: after my friend rebooted his PC, logged into Linux, opened a terminal and retried 'pppoeconf' and keyed in all the correct info he was immediately connected to the Interwebb. :D 

So all is well and he's merrily Ubuntuing as he uses basic PC features.

Thanks all!

---

