---
title: "Is there any way to run wireless networking without NetworkManager?"
date: 2024-01-08
forum: Networking &amp; Wireless
---

### Post by 0cs935-bill on 2024-01-08
As some of you may know, I've spent the last week trying to solve what started out as a forwarding issue between a wired and wireless interface. I've reinstalled the Ubuntu 22.04LTS workstation and server several times per day on multiple test rigs and have concluded NetworkManager (NM) is fatally broken **for what I want to do**, and is broken by design. I'm looking for a way to run wired and wireless interfaces on one box with the wireless being a hotspot (access point) without NM if that's at all possible.

NetworkManager.conf documentation is flat out wrong when it describes its use of its special dnsmasq directories (dnsmasq.d & dnsmasq-shared.d) . NM has hard coded command line directives when it starts dnsmasq which can be seen by issuing : 

```
# ps -ef | grep -e dnsmasq -e NetworkManager
root        761       1  0 Jan06 ?        00:10:06 /usr/sbin/NetworkManager --no-daemon
nobody     23986     761  0 08:09 ?        00:00:00 /usr/sbin/dnsmasq --conf-file=/dev/null --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=192.168.2.1 --dhcp-range=192.168.2.10,192.168.2.254,60m --dhcp-lease-max=50 --dhcp-leasefile=/var/lib/NetworkManager/dnsmasq-wlp1s0.leases --pid-file=/run/nm-dnsmasq-wlp1s0.pid --conf-dir=/etc/NetworkManager/dnsmasq-shared.d

```

This shows NM starting dnsmasq with command line arguments that include a directive to ignore the config file in dnsmasq.d and use command line arguments instead. The result of this is that no matter what one puts into NM's /etc/NetworkManager/ (dnsmasq.d and/or dnsmasq-shared.d) the command line arguments win and step on what I, the user, want when I put my information into dnsmasq-shared.d . It arbitrarily starts a dhcp for, in my case, 192.168.2.10 thru 192.168.2.254 as can be seen in the above. What I want is control over the dhcp range myself and I see no way to do that.

Below is what actually happens via journalctl:

```
dnsmasq[1185]: started, version 2.86 DNS disabled
dnsmasq[1185]: compile time options: IPv6 GNU-getopt DBus no-UBus i18n IDN2 DHCP DHCPv6 no-Lua TFTP conntrack ipset auth cryptohash>
dnsmasq[1185]: chown of PID file /run/nm-dnsmasq-wlp1s0.pid failed: Operation not permitted
dnsmasq-dhcp[1185]: DHCP, IP range 192.168.2.50 -- 192.168.2.254, lease time 12h
dnsmasq-dhcp[1185]: DHCP, IP range 192.168.2.10 -- 192.168.2.254, lease time 1h
dnsmasq-dhcp[1185]: DHCP, sockets bound exclusively to interface wlp1s0

```

My specs are never used.


For a while I used isc-dhcp-server to configure my range, but that led to the initial forwarding issue where traffic was forwarded in only one direction, so that's not a full solution.

I've tried ```
pkill -9 dnsmasq
``` but NM apparently has a watchdog on its dnsmasq because it restarts it in an instant. I see no way of stopping NM from starting dnsmasq when it decides to do so which is when there's a wireless interface intended for hotspot use. 

Can anyone suggest a way of having a hotspot in the same box with a wired NIC and have forwarding going on between the two where the end user has control over the wireless dhcp leasing?

BTW I've also discovered a reproducible bug in NM when used in conjunction with netplan's generate and apply that produces a network configuration that works one time but won't survive a reboot and no amount of netplan this or that will fix it.

---

### Post by 0cs935-bill on 2024-01-17
I thought I'd answer my own question here for documentation in case someone else is interested in the solution I came up with. What you'll read took me dozens of O/S installs and many days of testing to figure out. I'm still not done, since my application also requires qemu/KVM and that hauls in lots of nftables/iptables to contend with but the interfaces are as I want them with wireless dhcp under my control.


My goal was to get rid of NetworkManager as it relates to a WiFi connection and its idiotic hard coded dhcp settings when it calls dnsmasq. The man page for NetworkManager is wrong and completely misleading on how it handles instructions for what an end user might want in dhcp settings. I discovered that NetworkManager starts a watchdog on dnsmasq so it's impossible to permanently kill its dnsmasq invocation because it immediately starts another one.


I decided to get rid of NetworkManager entirely and just use networkd for everything.


Installed Ubuntu 22.04LTS workstation and fully patched it (apt update/upgrade) with enough network configuration to get that job done. I also tried it on Ubuntu Server and it works there also. If you're new to netplan, server is the install to use to see how it writes the yaml files from the networking data you provide during the installation process. I also installed ubuntu-desktop on server because I want a GUI.




Everything as root, of course!


```
apt -y install hostapd dnsmasq


systemctl disable NetworkManager
systemctl disable wpa_supplicant
systemctl mask wpa_supplicant	# This is started even if its disabled, so requires a mask.

```

At this point the box has no connectivity.


```
systemctl unmask hostapd
mv /etc/netplan/* /root/someplace/	# Just for reference purposes. Never needed them.

```

The /etc/netplan directory needs to be empty of any automatically generated files because new ones will replace them. Ubuntu Server mixes networkd and NetworkManager to control the interfaces so reading the automatically generated yaml files is informative if you go that route.


Put new files in place for /etc/dnsmasq.conf, /etc/hostapd/hostapd.conf and /etc/netplan/* that describe the wanted environment for dhcp leases, the WiFi environment and the interfaces needed respectively.


Here are the files I used for a box that has two wired NICs and one wireless interface. The wired NICs are for one private side and one public side and the wireless is private.


/etc/dnsmasq.conf:
```
log-dhcp
port=0
domain-needed 
bogus-priv
interface=wlp3s0
domain=private.abc
dhcp-range=192.168.3.50,192.168.3.254,255.255.255.0,12h
dhcp-option=3,192.168.1.100 # Gateway
dhcp-option=6,8.8.8.8       # DNS Servers
dhcp-option=6,8.8.4.4       # DNS Servers


dhcp-range=192.168.3.1,static
dhcp-host=00:0f:0a:42:a2:c,testbox.private.abc,192.168.3.1,infinite


dhcp-range=192.168.3.2,static
dhcp-host=D4:62:55:7B:E8:42,billphone.private.abc,192.168.3.2,infinite


dhcp-range=192.168.3.3,static
dhcp-host=24:C6:13:6F:F1:B9,billtablet.private.abc,192.168.3.3,infinite  
# Pattern continues for more boxes. I want almost everything static.

```

/etc/hostapd/hostapd.conf	# I stripped out all the comments for display here
```
interface=wlp3s0
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
ssid=mywifi
country_code=US
hw_mode=g
channel=11
beacon_int=100
dtim_period=2
max_num_sta=255
rts_threshold=-1
fragm_threshold=-1
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wmm_enabled=1
wmm_ac_bk_cwmin=4
wmm_ac_bk_cwmax=10
wmm_ac_bk_aifs=7
wmm_ac_bk_txop_limit=0
wmm_ac_bk_acm=0
wmm_ac_be_aifs=3
wmm_ac_be_cwmin=4
wmm_ac_be_cwmax=10
wmm_ac_be_txop_limit=0
wmm_ac_be_acm=0
wmm_ac_vi_aifs=2
wmm_ac_vi_cwmin=3
wmm_ac_vi_cwmax=4
wmm_ac_vi_txop_limit=94
wmm_ac_vi_acm=0
wmm_ac_vo_aifs=2
wmm_ac_vo_cwmin=2
wmm_ac_vo_cwmax=3
wmm_ac_vo_txop_limit=47
wmm_ac_vo_acm=0
eapol_key_index_workaround=0
eap_server=0
own_ip_addr=127.0.0.1
wpa_passphrase="whateveryouwant"
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP

```

/etc/netplan/00.internetConnection.yaml
```
network:
  version: 2
  renderer: networkd
  ethernets:
    enp4s0:
      addresses:
      - 148.255.34.244/25
      nameservers:
        addresses:
        - 8.8.8.8
        - 8.8.4.4
        search:
        - private.abc
      routes:
      - to: default
        via: 148.255.34.129

```

/etc/netplan/10.bridge.yaml	
```
# I needed a bridge for eventual VM needs. 
# This took quite a while for me to get it right.
# The intent is to think of 192.168.1.1 as the 'real' NIC with the others as virtual but
# they are all virtual.
# If you want a plain NIC, use the model in 00.internetConnection.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp2s0:
      dhcp4: false
      dhcp6: false
  bridges:
    br0:
      interfaces:
      - enp2s0
      addresses:
      - 192.168.1.1/24
      - 192.168.1.101/24
      - 192.168.1.102/24
      - 192.168.1.103/24
      - 192.168.1.104/24
      - 192.168.1.105/24
      nameservers:
        addresses:
        - 8.8.8.8
        - 8.8.4.4
        search:
        - private.abc
      routes:
      - to: 148.255.34.244/25
        via: 148.255.34.244

```

/etc/netplan/20.wifiHotSpot.yaml
```
# The trick is to treat the wireless as though its a NIC as far as networkd is concerned.
network:
  version: 2
  renderer: networkd
  ethernets:			        # Not wifis:
    wlp3s0:
      addresses:
      - 192.168.3.1/24		# This gets used eventually, but not immediately.
      nameservers:
        addresses:
        - 8.8.8.8
        - 8.8.4.4
        search:
        - private.abc
      dhcp4: false
      dhcp6: false

```

```
cd /etc/netplan
netplan generate
netplan apply


systemctl enable hostapd
systemctl enable dnsmasq
reboot

```

It takes all three components, networkd, hostapd and dnsmasq to give the wireless interface an IP address. If you do an ip a right after the netplan apply, you'll see that interface has no IP address. It gets an address after hostapd and dnsmasq add their magic.

---

