---
title: "[SOLVED] Ubuntu 18.04, Samba 4.7.6 not showing up in Windows 10 without SMB1"
date: 2018-12-29
forum: Networking &amp; Wireless
---

### Post by dttsou on 2018-12-29
Hi all, first post to these forums, nice to be back in the Linux world after a 20 year absence, wow has it changed for the better. So much easier to install, I had to install 0 drivers manually myself nor compile kernels. Happy days.

Whats not so happy... Samba not showing up from a Windows 10 Home laptop when I browse the network. I can put directly do this \\ubuntu-machine-name\  and it will show the shares for the machine, and everything works fine from there. But I would like to get it to show up in the network discovery process. Have already done the following in smb.conf:
   local master = yes
   wins support = yes
   preferred master = yes

I have seen some posts online that says we can enable the SMB1/CIFS support again from Windows 10 Home to make it show up, and yes I tested that and it does show up, but what I don't really understand is why my QNAP NAS shows up without the SMB1 support enabled even though its also using Linux + SMB. 

Is there a setting in SMB that I am missing in my ubuntu box? Is it possible to get this box to show up without having to enable SMB1/CIFS support in Windows 10?

Many thanks in advance.

---

### Post by zorlax on 2018-12-29
I would hazard a guess at QNAP having implemented WSD (The slightly weirdly named Web Services for Devices that replaced the network neighbourhood, part of SMB1, introduced in vista and default since win8) for their devices.

Configuration wise I'm sad to say that I don't know how to make samba shares announce themselves these days.

---

### Post by Morbius1 on 2018-12-29
> but what I don't really understand is why my QNAP NAS shows up without  the SMB1 support enabled even though its also using Linux + SMB. 
Because the QNAP is broadcasting it's presence via mDNS ( What QNAP and macOS call Bonjour ). In Linux it's called Avahi and it's there by default and works regardless of the smb dialect version used.

Netbios "discovery" isn't possible unless you use smb1. It doesn't mean name resolution doesn't work so you can use \\hostname in WIn10. And in another strange quirk Win10 can also use the mDNS name so a \\hostname.local will work if done explicitly. What Win10 cannot do regrettably is "discover" - as in browse for the machine - via mDNS. 

netbios name and smb1 are linked I'm afraid. Can't have one without the other.

If I were king of the universe I would:

** Either force Samba to implement the WSD / WS-Discovery thingy that zorlax mentioned.
** Or Force Windows to incorporate mDNS as part of that WS-Discovery mechanism.

Windows is almost there and they have the resources and talent to make it happen - if they wanted to.

---

### Post by dttsou on 2018-12-29
Thanks for these interesting leads to look into.. few follow up questions

> **Morbius1 said:**
> Because the QNAP is broadcasting it's presence via mDNS....
What Win10 cannot do regrettably is "discover" - as in browse for the machine - via mDNS. 


Think I might be misunderstanding something. I am reading this as a contradiction? If QNAP is making its presence known successfully by my Windows 10 laptop through mDNS (I think it also uses Avahi... I can see /etc/avahi/ folder when I ssh into it), it would see like Win10 is able to browse for the QNAP machine via Avahi's mDNS?

---

### Post by Morbius1 on 2018-12-29
To my knowledge Win10 cannot "browse" for mDNS registered SMB servers although it can access one if accessed explicitly. Win10 is likely "discovering" the QNAP through WS-Discovery because QNAP wants it's device to be discoverable by any means possible.

QNAP even has a setting for it based on what I found on the Web: [https://www.synology.com/en-us/knowledgebase/DSM/help/DSM/AdminCenter/file_service_discovery](https://www.synology.com/en-us/knowledgebase/DSM/help/DSM/AdminCenter/file_service_discovery)
> **To make your Synology NAS discoverable via WS-Discovery:**

 The WS-Discovery service allows users to find SMB service on the Synology NAS via Windows network discovery.
 
[LIST=1]
[*]Under the **WS-Discovery** section, tick the **Enable Windows network discovery to allow file access via SMB** checkbox. 
[*]Click **Apply** to save the settings. 
[/LIST]

There's one way to confirm all this. In Win10 go to Explorer and add a column under the Details view for Discovery Method:
[ATTACH=CONFIG]282034[/ATTACH]
It will list NETBIOS if you enabled smb1 or WSD.[ATTACH=CONFIG]282035[/ATTACH]

**EDIT**: > Because the QNAP is broadcasting it's presence via mDNS....
What I meant by this was this is why the Linux client can see it.

---

### Post by dttsou on 2018-12-29
> **Morbius1 said:**
>  There's one way to confirm all this. In Win10 go to Explorer and add a column under the Details view for Discovery Method:
[ATTACH=CONFIG]282034[/ATTACH]
It will list NETBIOS if you enabled smb1 or WSD.[ATTACH=CONFIG]282035[/ATTACH]


This is brilliant, thank you so much. Confirmed, it is WSD indeed. Appreciate your help Morbius!. Time to google how to install WSD.

---

### Post by zorlax on 2018-12-29
I was going to say that then you would be out of luck but since I last tried to get this fixed someone has made this, [github.com/christgau/wsdd]("http://github.com/christgau/wsdd") , based on a patch submitted to the samba team in 2015... I have tried briefly and AFAICT it works. This is the only solution I'm aware of apart from compiling your own version of samba using the 2015 patch.

---

### Post by dttsou on 2018-12-30
Hi zorlas, you beat me to it. :-)

Google did indeed point me to Christgau's wsdd, and just spend the last 30min installing it, and very happy to confirm that it works a treat.

For anyone who is going through the same journey, here is what I did to get it working:
- download the zip file from [https://github.com/christgau/wsdd](https://github.com/christgau/wsdd)
- rename wsdd-master/src/wsdd.py to wsdd
- sudo -i (if you are not logged in as root already)
- copy wsdd to /usr/bin/
- copy /wsdd-master/etc/systemd/wsdd.service to /etc/systemd/system/
- I had to comment out USER=nobody and GROUP=nobody lines in the wsdd.service file, otherwise it wouldn't work on my system
- execute command 'systemctl daemon-reload' to pick up the presence of the new wsdd.service file (although not sure if its strictly neccessary?)
- execute command 'systemctl start wsdd'  to start up wsdd as a service  (if you don't have firewall enabled on your Ubuntu box, then you should now see your box show up on your Windows Network browser, but if you have a firewall in place, then see below)
- execute command 'systemctl enable wsdd' if you want to start wsdd on reboot.

Now, if you are using iptables like I am for a firewall, then add the following two rules to your /etc/default/iptables file:
-A INPUT -s 192.168.1.0/24 -d 239.255.255.250 -m pkttype --pkt-type multicast -j ACCEPT
-A INPUT -p tcp --dport 5357 -j ACCEPT
then just restart iptables by executing the command 'systemctl restart iptables'.

That should do it. Enjoy full transparency without the security holes of SMB1. :-)

---

### Post by uttam.hathi on 2019-02-06
i went thru this headache.
all the win7 machines were reflecting my server in windows explorer networking but not win10, it was reading as \\192.168.1.xx , did my resetting to smb1 in win10 nothing worked, then i found the issue was with Kaspersky. the solution i solved was:
Change the network card type into KIS Firewall Settings: 
Product Main(kaspersky) GUI > Settings > Protection(left) > Firewall > Networks > Change the network type of Local network card to "Trusted Network" or "Local Network" > Close all windows. 
voila!

---

