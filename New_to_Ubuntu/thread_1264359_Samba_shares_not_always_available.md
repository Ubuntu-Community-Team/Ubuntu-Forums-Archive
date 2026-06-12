---
title: "Samba shares not always available"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by KIAaze on 2009-09-12
Hi,

I have a strange problem:
I managed to configure my samba shares under Kubuntu 9.04 on my desktop PC so that they are available as read-only without a password on the network.
However, for some reason, I can't always access them from my laptop.
Sometimes, it works, sometimes it tells me my desktop PC can't be accessed.

Here's my /etc/samba/smb.conf:
```
[global]
    ; General server settings
;	netbios name = kiaaze-desktop
	server string = 
	workgroup = workgroup
	announce version = 5.0
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

	passdb backend = tdbsam
	security = share
	null passwords = true
	name resolve order = hosts wins bcast

;	wins support = no

;	printing = cups
	printcap name = CUPS

;	syslog = 1
	syslog only = yes
;	encrypt passwords = yes
;	guest ok = no
;	guest account = nobody
	username map = /etc/samba/smbusers

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
	path = /var/lib/samba/printers
;	browseable = yes
	guest ok = yes
;	read only = yes
	write list = root
	create mask = 0664
	directory mask = 0775

[printers]
	path = /tmp
	printable = yes
	guest ok = yes
	browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[SharedMusic]
	path = /home/kiaaze/Music
;	browseable = yes
        read only = yes
	writeable = no
	guest ok = yes
	create mask = 0644
;	directory mask = 0755
	force user = kiaaze
	force group = kiaaze

[SharedVideos]
	path = /home/kiaaze/Videos/SharedVideos
;	browseable = yes
        read only = yes
	writeable = no
	guest ok = yes
	create mask = 0644
;	directory mask = 0755
	force user = kiaaze
	force group = kiaaze

```

The directory permissions:
```
[14][~]$  ls -ld /home/kiaaze/Music /home/kiaaze/Videos/SharedVideos
drwxr-xr-x 4 kiaaze kiaaze 4096 2009-08-23 13:05 /home/kiaaze/Music
drwxr-xr-x 4 kiaaze kiaaze 4096 2009-08-23 13:30 /home/kiaaze/Videos/SharedVideos

```

The samba users:
```
[17][~]$  sudo pdbedit -Lw
[sudo] password for kiaaze:
nobody:65534:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:...
kiaaze:1000:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX:...

```

---

### Post by izziere on 2009-09-12
What OS are you using on your laptop?

Are you getting a constant LAN connection on your desktop?  

I had a problem for a while because my junky wireless device was rubbish.  Problem solved when i installed new card

---

### Post by KIAaze on 2009-09-12
I have both Ubuntu and Windows XP (and puppy linux ^^) on my laptop.
It's the same problem with both.
Under Windows, I made sure to deactivate the firewall (ZoneAlarm).

My desktop PC is connected over wireless and has a dynamic IP.
I've also set it up so that it connects to the net+network before login.

edit: don't remember where I found the instructions for this, but here's how I set up wireless before login:
/etc/network/interfaces :
```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
# iface wlan0 inet static
# address 192.168.168.40
# gateway 192.168.168.230
# dns-nameservers 192.168.168.230
# netmask 255.255.255.0
# wpa-driver rt61pci
wpa-driver wext
wpa-ssid *****
wpa-ap-scan 1
# wpa-proto RSN
wpa-proto WPA
# wpa-pairwise CCMP
# wpa-group CCMP
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
# generated with wpa_passphrase <your_essid> <your_ascii_key>
wpa-psk *****
```
howto used: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

---

### Post by KIAaze on 2009-09-12
Ok, I think I solved it: I still had an openvpn tunnel open.

I tried to ping my laptop from my desktop (both connected over wireless) and vice-versa and it failed in both directions.
When I connected my laptop to the router over a cable, I could ping in both directions and access the shares.

After checking ifconfig, I noticed the open tunnel (tun0).
So I ran ```
sudo service openvpn stop
``` and now everything works again. (actually, I also had an open VPN tunnel on the laptop under Ubuntu!) :)

I'll have to check if the openvpn service runs on startup again next time. It's also a security risk after all.

---

### Post by swerdna on 2009-09-12
FWIW you have this line: name resolve order = hosts wins bcast
and "hosts" should be "host"

Since hosts is meaningless to Samba, it will default to the next in the list, wins, as the preferred method for name resolution, but since wins is disabled it will then default to bcast, which will work. So what you've really got there is:```
name resolve order = bcast
```

If you want to "unconfuse" Samba each time it goes to look for a service on the LAN, you should use this form (for SOHO LANs):```
name resolve order = bcast host lmhosts wins
```

---

### Post by KIAaze on 2009-09-12
Thanks, I changed it, restarted samba and it still works, so everything seems ok. Just haven't rebooted the server/desktop yet.

I had a look at your homepage [http://ubuntu.swerdna.org/](http://ubuntu.swerdna.org/)
Might be useful if I have problems with samba again (especially the firewall part). Or if I want open sauces. :lol:

edit:
Mmh, the shares are still available after server reboot, but the VPN tunnel is open again. So, solved or not? I'm not sure anymore. :confused:
Perhaps the "name resolve order" change fixed it.
Anyway, I deactivated the openvpn service now with sysvconfig.

---

