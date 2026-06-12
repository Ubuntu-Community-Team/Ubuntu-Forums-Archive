---
title: "Upgraded to Bionic, now I can't browse SAMBA shares"
date: 2018-10-06
forum: Networking &amp; Wireless
---

### Post by jchiso2 on 2018-10-06
I asked a question in a related thread but the thread was subsequently closed, and I was advised to start a unique thread:

I've been wrestling with problems browsing SAMBA shares for about six weeks now, since I  foolishly chose to update some Ubuntu systems to 18.04.  None of the  solutions offered on these forums have helped; and the curious thing is  that SAMBA shares on my (three) pi devices appear and function as  expected.  Shares on Windows 7, Windows 8.1, and Ubuntu distributions  prior to 18.04 are not browseable at all.

Here are some of the proposed solutions I've tried on the two Bionic systems:
[LIST]
[*]modified smb.conf file to include "client min protocol = NT1"
[*]modified smb.conf file to include "client max protocol = NT1"
[*]modified smb.conf file to include "client max protocol = SMB3"
[*]midified smb.conf files on 18.04 and earlier servers to name resolve order of "bcast host lmhosts wins"
[/LIST]

Quite a few more; honestly it's been close to two months now and I have six or seven Ubuntu-based systems of various vintages.

It does not seem like it should even be possible to disable share  browsing for all connected PCs by changing the configuration of a single  server.  There must be something terribly amiss about Bionic's SAMBA  protocols.

If anyone out there has had a similar experience and found a working  solution I'd be interested in hearing it and open to trying at this  point ...[INDENT][/INDENT]
[INDENT][/INDENT]

---

### Post by Morbius1 on 2018-10-07
Please post the output of the following command:
```
testparm -s
```
In the meantime for all those "Ubuntu distributions  prior to 18.04 are not browseable at all" I would suggest adding a file to each so as to bring them up to the new century:

Create a file at **/etc/avahi/services/samba.server **with this content:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">%h SMB</name> ## Display Name
   <service>
       <type>_smb._tcp</type>
       <port>445</port>
   </service>
</service-group>
```
This wont do jack for your Windows machines but you will be able to see all your older Ubuntu machines.

---

### Post by jchiso2 on 2018-10-08
This is the output from one of the Bionic systems:

> Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "syslog" option is deprecated
Processing section "[printers]"
Processing section "[print$]"
Processing section "[mpeg]"
Loaded services file OK.
Server role: ROLE_STANDALONE


# Global parameters
[global]
    bind interfaces only = Yes
    client max protocol = NT1
    dns proxy = No
    log file = /var/log/samba/log.%m
    map to guest = Bad User
    max log size = 1000
    name resolve order = bcast lmhosts host wins
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    security = USER
    server role = standalone server
    server signing = if_required
    server string = %h server (Samba, Ubuntu)
    syslog = 0
    unix password sync = Yes
    usershare allow guests = Yes
    wins support = Yes
    idmap config * : backend = tdb




[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes




[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers




[mpeg]
    comment = mpeg dir on WinData
    create mask = 0777
    directory mask = 0777
    guest ok = Yes
    guest only = Yes
    path = /media/WINDATA/mpeg
    read only = No




---

### Post by Morbius1 on 2018-10-08
Hm.....

See nothing wrong with the client side settings in your smb.conf. I added your additions to my own smb.conf:
> bind interfaces only = Yes
    client max protocol = NT1
name resolve order = bcast lmhosts host wins

And I can browse the Windows machine as expected.

The only way I can reproduce your symptom is to enable ufw. Then I can't browse - for Windows machines - to save my life.

If you have ufw enabled disable it:
```
sudo ufw disable
```
Should that fix it you might want to see this solution: [https://wiki.archlinux.org/index.php/samba#.22Browsing.22_network_fails_with_.22Failed_to_retrieve_share_list_from_server.22](https://wiki.archlinux.org/index.php/samba#.22Browsing.22_network_fails_with_.22Failed_to_retrieve_share_list_from_server.22)

---

### Post by jchiso2 on 2018-10-09
I tried the ufw disable, but nothing changed.  It just seems strange that the Windows systems can see the Windows shares, the Ubuntu systems can see the Ubuntu and pi shares, but none of the desktop systems can see all of the shares, and generic Windows (SAMBA) share browsing is disabled on desktops and networked streaming devices ...

---

### Post by jchiso2 on 2018-11-13
I stumbled upon something that solved my problems.  I've tried several suggestions since early September when these problems started, so I probably have a mess of configs in use, but the thing that made browsing work on all my systems was changing the samba.conf file in each of the Ubuntu share hosts to include the following lines:

```
domain master = no
local master = yes
preferred master = yes
```

I cannot find the thread that suggested this, but it has solved my persistent problems ...

---

