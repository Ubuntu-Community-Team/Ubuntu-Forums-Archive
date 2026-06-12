---
title: "Wireless: user vs machine authentication using PEAP/MSCHAPV2"
date: 2014-01-31
forum: Networking &amp; Wireless
---

### Post by Davorian on 2014-01-31
Hi all,

I am trying to connect to a wireless network that uses the WPA2 Enterprise protocol with PEAP/MSCHAPV2 inner authentication.  Currently Ubuntu reports that the username and password are rejected.  The network administrator tells me the logs show my machine is attempting to use the host name ('host/hostname') as the username when connecting to the router instead of the username that I have specified in the network configuration.

I have seen sparse references to this behaviour on various forums that describe this as 'machine authentication' vs 'user authentication', but nothing specific to Linux or Ubuntu.  Is there a way to force the network manager to use the username I specify?

I am using Ubuntu 13.10.

Cheers,
Chris.

---

### Post by varunendra on 2014-02-01
Can you post a screenshot of the connection settings in Network Manager?

Alt-F2 > nm-connection-editor > "Wireless" tab > double-click your connection > Wireless Security tab.

This is where you save the relevant info that NM would use to establish the connection. Make sure the "Authentication" type is PEAP, and the "Inner authentication" is MSCHAPv2, then save the username/password in the relevant fields.

---

### Post by Davorian on 2014-02-01
Yes, all the settings are in order.  Screenshot attached (username replaced, password blanked).  The syslog output shows that they are all accounted for, although it's not detailed enough to show me exactly what is sent and what isn't set.  The settings are identical to the Windows 7 dual boot on the same machine, which connects just fine.

[ATTACH=CONFIG]250004[/ATTACH]

---

### Post by varunendra on 2014-02-02
Have you seen this bug report yet : [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1104476](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1104476) ?

Accordingly, have you checked your connection's key file? That is - "/etc/NetworkManager/system-connections/eduroam". You will need root access to be able to read it. So either open it with "gksu gedit ...." or -
```
sudo cat /etc/NetworkManager/system-connections/eduroam
```
Is there the line "system-ca-certs=true" in it? If yes, try changing it to "false" -
```
sudo sed -i '/ca-certs=/ s:true:false:' /etc/NetworkManager/system-connections/eduroam
```
or delete it altogether -
```
sudo sed -i '/ca-certs=/ d' /etc/NetworkManager/system-connections/eduroam
```
(of course you can also do these from GUI if you opened the file on your text editor)

I have no idea about machine vs user authentication, but I guess NM should be able to take care of that once you saved the relevant information correctly in it. If it is unable to do that, maybe try its newer version (if available in your repositories) or a different manager, like **wicd** or the traditional '/etc/interfaces' file as mentioned in this post [http://ubuntuforums.org/showthread.php?t=2059808&p=12249233#post12249233](http://ubuntuforums.org/showthread.php?t=2059808&p=12249233#post12249233) (and the first post of the thread it links to). Although the 'interfaces' file method is not recommended for wireless interfaces (unless you have to stick with that one particular network), but if that method succeeds, it would indicate a possible bug in Network Manager, for which there maybe workarounds like the "system-ca-certs" one.

---

