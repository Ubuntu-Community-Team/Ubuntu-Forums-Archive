---
title: "Cisco aironet 350"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by GeorgeAD on 2006-08-19
I've had this card working fine in Ubuntu (the standard Dapper version) - all I did was put it in the slot, run 'networking' from the system menu and there'd be an option to activate it. I'm pretty certain it worked in Xubuntu before that. But now I've installed Xubuntu again it doesn't work - it doesn't appear in the network-admin window. 

I've tried rebooting with the card in and without. 

var/log/messages says:

Aug 19 11:49:13 george-laptop kernel: [  952.609258] pccard: PCMCIA card inserted into slot 0
Aug 19 11:49:13 george-laptop kernel: [  952.609294] cs: unable to map card memory!
Aug 19 11:49:13 george-laptop kernel: [  952.609308] cs: unable to map card memory!

Can anyone tell me what's wrong please?

---

### Post by GeorgeAD on 2006-08-22
I've just tried reinstalling Xubuntu with the card in the slot, with the same result: cs: unable to map card memory!

I don't think it ever worked with Xubuntu installed, only with Ubuntu standard. The time I had it working with Xubuntu was using the live cd. Using  the live cd I get: 

Aug 22 17:01:45 ubuntu kernel: [  647.945136] pccard: PCMCIA card inserted into slot 0
Aug 22 17:01:45 ubuntu kernel: [  647.945418] pcmcia: registering new device pcmcia0.0
Aug 22 17:01:46 ubuntu kernel: [  649.145342] airo: MAC enabled eth0 0:e:38:4f:fd:bb
Aug 22 17:01:46 ubuntu kernel: [  649.145894] eth0: index 0x05: Vcc 5.0, Vpp 5.0, irq 4, io 0x0100-0x013f

and everything works fine. but not once it's installed on the hard disk!

---

### Post by blkcamarozr28 on 2006-09-20
Im running Xubuntu 6.06 and was getting this error below in /var/log/messages.

Sep 19 22:10:35 localhost kernel: [17180312.460000] pccard: PCMCIA card inserted into slot 1
Sep 19 22:10:35 localhost kernel: [17180312.460000] cs: unable to map card memory!
Sep 19 22:10:35 localhost kernel: [17180312.460000] cs: unable to map card memory!

To fix the problem I had to install these packages on my Sony PCG-XG39 laptop and added a script that I found online to automatically switch the preamble to Long. Give it a try and let me know if this fixes the problem for you. I see lots of other people online having problems.

sudo apt-get install pcmcia-cs
sudo apt-get install pcmciautils

sudo vi /etc/network/if-pre-up.d/cisco-aironet
==============Paste Config below for Preable = Long=================
#!/bin/sh
#
# This script takes care of configuring cisco wireless
# cards using the airo driver such as 340 and 350 cards.
# It is run by ifup.

AIROPROC=/proc/driver/aironet
CONFIG=Config
SLEEP=2

#some sanity checks
if [ ! -d $AIROPROC ] ; then
exit 0
fi

for i in $AIROPROC/* ; do
if [ -w "$i/$CONFIG" ] ; then
echo "Preamble: long" > "$i/$CONFIG"
fi
done
sleep $SLEEP
============================END PASTE============================
sudo chmod 755 /etc/network/if-pre-up.d/cisco-aironet

shutdown -h now
Power back on

==Run pccardctl in terminal==
pccardctl ident
==Output from pccardctl ident==
x@x-laptop:~$ pccardctl ident
Socket 0:
product info: "Cisco Systems", "350 Series Wireless LAN Adapter", "", ""
manfid: 0x015f, 0x000a
function: 6 (network)
Socket 1:
no product info available

==Goto Applications -> System -> Networking==
You should see a Wireless Card Interface now

---

