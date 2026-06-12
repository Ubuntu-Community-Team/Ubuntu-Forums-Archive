---
title: "VPN connection on feisty"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by hortimech on 2007-03-18
I am trying to set up a VPN connection to my workplace, on windows xp it just works, on  Ubuntu it just doesn't.

I have read every howto etc I could find, I even upgraded to Feisty but I cannot get it to work.
I am trying to get it to work on kubuntu, so am using Knetworkmanager (the nm-applet did not appear as per the howto's I found).

So basically what I asking for is help from someone (anyone?) who has got it working, just how did they do it.

this is what I get from sudo tail -f /var/log/syslog

well it would be if I could post it here, I just kept getting advised to remove the 12 images from the text I cut and pasted here, how do I post my syslog? 


Any help gratefully received

Rowland

---

### Post by spin2cool on 2007-03-18
What program are you using to establish the connection?  I had no luck with the Cisco client, but VPNC worked perfectly.  May be worth a shot.

---

### Post by hortimech on 2007-03-18
I am trying to set up a PPTP link, vpnc would seem to ipsec based, as I said, connecting from windows works, I ran the wizard, entered the ip address to connect to, entered username, entered password, pressed the button and I was connected.
On the same laptop running kubuntu, pptp-linux and knetworkmanager, I ran the wizard, entered the the same info and tried to connect. It tries to connect but seems to drop the connection

Mar 18 16:33:20 desknote NetworkManager: <WARNING>^I nm_vpn_service_stop_connection (): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'gibsons' because service $
Mar 18 16:33:20 desknote pptp[11946]: anon log[callmgr_main:pptp_callmgr.c:255]: Closing connection (shutdown)
Mar 18 16:33:20 desknote pptp[11946]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Mar 18 16:33:20 desknote pptp[11946]: anon log[call_callback:pptp_callmgr.c:78]: Closing connection (call state)
Mar 18 16:33:20 desknote pppd[11939]: Modem hangup
Mar 18 16:33:20 desknote pppd[11939]: Connection terminated.
Mar 18 16:33:20 desknote pppd[11939]: Child process /usr/sbin/pptp XX.XX.XXX.XXX --nolaunchpppd (pid 11940) terminated with signal 15
Mar 18 16:33:20 desknote pppd[11939]: Exit.

---

### Post by wilbur.harvey on 2007-03-19
I have been using the vpnc client for about a year and it has been working fine, but recently it starts disconnecting after about 20 seconds. I am running the latest feisty. I think that it got broken somewhere during recent updates. My windows box will stay connected all night.

Here is my /etc/vpnc/default.conf file. This is all you need to set up.
Just run sudo vpnc

IPSec gateway [ipaddress here]
IPSec ID ciscovpn (not sure if this is unique to your locatoin)
IPSec secret [group password here] (maybe this will help [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode))
Xauth username [your login name to the system you are connecting to]
Xauth password [password to the system you are connecting to]

Wilbur

---

### Post by hortimech on 2007-03-19
Thanks for the info but it is not applicable to me. I am trying to set up a VPN connection, no IPSEC involvment just like on XP.
XP just connects and works, I wish I could upgrade to VPNC but this would involve me touring half of Lancashire to setup up everybody elses computers, it's easier to stick with XP.
I have just two things I need to get to work, this and syncing my wm5 Phone, then I can wave bye-bye to windows. Can anybody help me with this VPN connection?

---

### Post by Joe_Bishop on 2007-03-21
I have the similar problem, I have just upgrade to feisty, and now pptp connection doesn't establish, the log is simalar to yours. Yesterday it works, but not perfectly, it was taking too much time to connect. Today it just doesn't work. I'm in shock, Feisty looks worse than Breezy.

---

### Post by Hortinstein on 2007-03-21
i cant even get VPN working in Edgy....any guides aboot?

---

### Post by pdxsam on 2007-04-04
I've got the same issue with vpnc it's borked. It'll connect for a few minutes and drop.
Hopefully  it'll get fixed before release.

---

### Post by dthompto on 2007-04-06
> **wilbur.harvey said:**
> I have been using the vpnc client for about a year and it has been working fine, but recently it starts disconnecting after about 20 seconds. I am running the latest feisty. I think that it got broken somewhere during recent updates. My windows box will stay connected all night.

Here is my /etc/vpnc/default.conf file. This is all you need to set up.
Just run sudo vpnc

IPSec gateway [ipaddress here]
IPSec ID ciscovpn (not sure if this is unique to your locatoin)
IPSec secret [group password here] (maybe this will help [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode))
Xauth username [your login name to the system you are connecting to]
Xauth password [password to the system you are connecting to]

Wilbur

am running edgy 6.10 on a powerbook G4
have installed vpnc, tried using it via KVpnc gui, have the vpnc.conf set up, used the cisco pw decoder, it does run and try to connect to my vpn but times out after about 10 seconds and then disconnects.
do you have any ideas about what I'm doing wrong?
thanks

---

### Post by dthompto on 2007-04-06
> **dthompto said:**
> am running edgy 6.10 on a powerbook G4
have installed vpnc, tried using it via KVpnc gui, have the vpnc.conf set up, used the cisco pw decoder, it does run and try to connect to my vpn but times out after about 10 seconds and then disconnects.
do you have any ideas about what I'm doing wrong?
thanks

I removed the KVpnc gui. then ran sudo vpnc, now it looks like it works, am trying to confirm now

---

### Post by dthompto on 2007-04-06
> **dthompto said:**
> I removed the KVpnc gui. then ran sudo vpnc, now it looks like it works, am trying to confirm now

yup, installed Gnome-rdp and was able to connect to one of my windows servers just fine.

:)

---

### Post by generaltao on 2007-04-25
I found a fix that does not require downgrading.

> 
cd /usr/src
sudo apt-get source vpnc
cd vpnc-0.4.0/debian/patches

sudo gedit 00list

remove the line 06_stolen_from_head

cd ../..
sudo debian/rules binary

cd ..

sudo apt-get remove vpnc
sudo dpkg -i vpnc_0.4.0-2ubuntu1_i386.deb

if you had installed network-manager-vpnc you'll have to reinstall it

be careful when upgrading the system, don't update vpnc or you will get the patched version

Reference: [https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/93413/comments/26](https://bugs.launchpad.net/ubuntu/+source/vpnc/+bug/93413/comments/26)

---

### Post by trapperjohn on 2007-05-09
The fix works - but you need things like dpatch, debhelper etc. installed to compile the package.

Does someone know how to tell apt, not to install the vpnc version from the repository again?

'apt-cache policy vpnc' shows, there are two versions, the self-compiled and the repository version - both have the same version number (0.4.0-2ubuntu1). The version from the repository seems to have higher priority, so Synaptic always wants to install it. Any ideas?

---

