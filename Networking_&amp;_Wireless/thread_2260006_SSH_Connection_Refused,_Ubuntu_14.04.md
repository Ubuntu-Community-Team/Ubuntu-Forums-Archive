---
title: "SSH Connection Refused, Ubuntu 14.04"
date: 2015-01-08
forum: Networking &amp; Wireless
---

### Post by zach_ripper95 on 2015-01-08
I'm running crouton on a Chromebook (Toshiba Chromebook 2). I installed a Ubuntu Trusty Chroot with the Unity DE. I installed openssh-server and rebooted and I am unable to connect to it from another computer on the network. I followed the instructions [here]("https://github.com/dnschneid/crouton/wiki/Running-servers-in-crouton") and that didn't fix my problem.

Wireless Info:
```
########## wireless info START ##########

Report from: 08 Jan 2015 12:22 MST -0700


Booted last: 08 Jan 2015 11:55 MST -0700


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.10.18 #1 SMP Wed Dec 10 16:37:11 PST 2014 x86_64 x86_64 x86_64 GNU/Linux


cros_secure, console=, loglevel=7, init=/sbin/init, cros_secure, oops=panic, panic=-1, rootwait, ro, dm_verity.error_behavior=3, dm_verity.max_bios=-1, dm_verity.dev_wait=1, dm="1, vroot, none, ro, 1,0, 2506752, verity, payload=PARTUUID=e9d901b8-5d96-cc46-80ee-85329c14145d/PARTNROFF=1, hashtree=PARTUUID=e9d901b8-5d96-cc46-80ee-85329c14145d/PARTNROFF=1, hashstart=2506752, alg=sha1, root_hexdigest=bc5c7f1c045100879ed3fa610a11528819bb3f72, salt=b3813f2b3835f613c6e621f76e7b6cce27ff4d7c2ecdbfc70f4057a7f14b42c3", noinitrd, vt.global_cursor_default=0, kern_guid=e9d901b8-5d96-cc46-80ee-85329c14145d, add_efi_memmap, boot=local, noresume, noswap, i915.modeset=1, tpm_tis.force=1, tpm_tis.interrupts=0, nmi_watchdog=panic,lapic, 


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c170]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 04f2:b48b Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


./wireless_script: line 170: pccardctl: command not found


##### rfkill ############################


./wireless_script: line 176: rfkill: command not found


##### lsmod #############################


iwlmvm                183872  0 
iwl7000_mac80211      383225  1 iwlmvm
iwlwifi               139348  1 iwlmvm
cfg80211              297791  3 iwlwifi,iwlmvm,iwl7000_mac80211


##### interfaces ########################


source-directory /etc/network/interfaces.d


##### ifconfig ##########################


./wireless_script: line 186: ifconfig: command not found


##### iwconfig ##########################


./wireless_script: line 189: iwconfig: command not found


##### route #############################


./wireless_script: line 192: route: command not found


##### resolv.conf #######################


nameserver 192.168.2.1
search domain_not_set.invalid.
options single-request timeout:1 attempts:5


##### nm-tool ###########################


./wireless_script: line 198: nm-tool: command not found


##### NetworkManager.state ##############


cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory


##### NetworkManager.conf ###############


grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory


##### NetworkManager profiles ###########


Acquisition of admin privileges failed.


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


./wireless_script: line 244: iwlist: command not found


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'salklake' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"salklake"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013b3f1ceb88
                    Extra: Last beacon: 9ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'salklake' [AC2]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"salklake"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013b3ef90c0a
                    Extra: Last beacon: 9ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ad32bf787e
                    Extra: Last beacon: 9ms ago
          Cell 04 - Address: <MAC 'salklake-guest' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:off
                    ESSID:"salklake-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013b3f1c2ecc
                    Extra: Last beacon: 9ms ago
          Cell 05 - Address: <MAC '' [AC5]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004160b825e
                    Extra: Last beacon: 3355ms ago
          Cell 06 - Address: <MAC 'myqwest5509' [AC6]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"myqwest5509"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004160b8249
                    Extra: Last beacon: 3355ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


./wireless_script: line 268: modinfo: command not found
[iwlmvm]


./wireless_script: line 268: modinfo: command not found
[iwl7000_mac80211]


./wireless_script: line 268: modinfo: command not found
[iwlwifi]


./wireless_script: line 268: modinfo: command not found
[cfg80211]


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


[iwl7000_mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
debug: 0
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1
xvt_default_mode: N


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


mkdir -p -m0755 /var/run/sshd
/usr/sbin/sshd
/sbin/iptables -P INPUT ACCEPT
exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[    8.202531] iwlwifi 0000:01:00.0: irq 106 for MSI/MSI-X
[    8.740126] iwlwifi 0000:01:00.0: loaded firmware version 25.222.9.0 op_mode iwlmvm
[    8.817867] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    8.825842] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S (repeated 2 times)
[    9.039280] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    9.095071] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S (repeated 2 times)
[    9.111172] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.789272] wlan0: authenticate with <MAC 'salklake' [AC1]>
[   12.791985] wlan0: send auth to <MAC 'salklake' [AC1]> (try 1/3)
[   12.814241] wlan0: authenticated
[   12.814688] wlan0: associate with <MAC 'salklake' [AC1]> (try 1/3)
[   12.837363] wlan0: RX AssocResp from <MAC 'salklake' [AC1]> (capab=0x411 status=0 aid=13)
[   12.838164] wlan0: associated
[   12.838217] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############
```

---

### Post by bashiergui on 2015-01-08
Check that the ssh service is started and if not, start it. I'm not sure if it starts at boot by default.```
sudo seevics ssh status
``` Look here for details about configuring ssh so that it's accepting connections
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Also make sure your firewalls on both machines are allowing ssh traffic.

---

### Post by zach_ripper95 on 2015-01-08
```
sudo service ssh status
status: Unknown job: ssh
```

Both machines are allowing ssh traffic.

When I do install openssh-server I do get a few errors towards the end of the install:

```

runlevel:/var/run/utmp: No such file or directory
initctl: Unknown job ssh

```

---

### Post by Samundra_Shrestha on 2015-01-09
Hi There,

First verify that you have SSH server running. You can do that with `ps -aux | grep sshd` if you get he process-ids back then it means you have SSH server running. 

The article you followed, basically assume you have SSH server installed. So, Did you change your default port for SSH. See if you can `telnet {your_server_ip} 22` if you can then it means you have SSH server running and there might be something else blocking SSH connections. That might be firewall as well. First let's see output of the commands listed above.

---

### Post by Doug S on 2015-01-09
> **Samundra_Shrestha said:**
> First verify that you have SSH server running. You can do that with `ps -aux | grep sshd` if you get he process-ids back then it means you have SSH server running.Well, although there was a typo, what bashiergui said gives the same information. Example:```
doug@doug-64:~$ [COLOR=#ff0000]ps aux | grep sshd[/COLOR]
root      [COLOR=#ff0000]1188[/COLOR]  0.0  0.0  50036  2088 ?        Ss   Jan08   0:00[COLOR=#ff0000] /usr/sbin/sshd -D[/COLOR]
root      2670  0.0  0.1 134580  4544 ?        Ss   Jan08   0:00 sshd: doug [priv]
doug      2823  0.0  0.0 134972  2152 ?        S    Jan08   0:10 sshd: doug@pts/0
root      3106  0.0  0.1 134580  4536 ?        Ss   Jan08   0:00 sshd: doug [priv]
doug      3425  0.0  0.0 134716  2144 ?        S    Jan08   0:00 sshd: doug@pts/1
doug     18316  0.0  0.0   9384   876 pts/1    S+   07:31   0:00 grep --color=auto sshd
doug@doug-64:~$ [COLOR=#ff0000]sudo service ssh status[/COLOR]
ssh start/running, process [COLOR=#ff0000]1188[/COLOR]
```And the reply from zach_ripper95 shows that indeed sshd is not running. so:```
sudo apt-get install openssh-server
```See also the [Ubuntu serverguide]("https://help.ubuntu.com/lts/serverguide/openssh-server.html").

---

### Post by zach_ripper95 on 2015-01-09
This server is running. The openssh-server package is in fact installed if you read my earlier post:

> 
When I do install openssh-server I do get a few errors towards the end of the install:

Code:
runlevel:/var/run/utmp: No such file or directory
initctl: Unknown job ssh


---

### Post by bashiergui on 2015-01-10
> **zach_ripper95 said:**
> ```
sudo service ssh status
status: Unknown job: ssh
```When I do install openssh-server I do get a few errors towards the end of the install:```
runlevel:/var/run/utmp: No such file or directory
initctl: Unknown job ssh
```
> This server is running. The openssh-server package is in fact installed if you read my earlier postThe error you got "Unknown job ssh" indicates that ssh was not successfully installed. If it was installed your computer would recognize "ssh" as a service. The fact that it doesn't know what ssh is indicates something went wrong in the installation process. You won't be able to ssh to that machine until the output of ```
sudo service ssh status
```looks similar to Doug's.

I haven't used crouton or ssh with Chroot and the Unity DE. I don't know how that would be different from a vanilla Ubuntu installation, but surely it is different in some crucial way. I would recommend you do an internet search for each & all the errors you get during the installation. You'll probably find someone somewhere had a similar issue, and with a bit of luck they posted their resolution.

---

### Post by marcosfede on 2015-06-26
> **zach_ripper95 said:**
> I'm running crouton on a Chromebook (Toshiba Chromebook 2). I installed a Ubuntu Trusty Chroot with the Unity DE. I installed openssh-server and rebooted and I am unable to connect to it from another computer on the network. I followed the instructions [here]("https://github.com/dnschneid/crouton/wiki/Running-servers-in-crouton") and that didn't fix my problem.

Wireless Info:
```
########## wireless info START ##########

Report from: 08 Jan 2015 12:22 MST -0700


Booted last: 08 Jan 2015 11:55 MST -0700


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.10.18 #1 SMP Wed Dec 10 16:37:11 PST 2014 x86_64 x86_64 x86_64 GNU/Linux


cros_secure, console=, loglevel=7, init=/sbin/init, cros_secure, oops=panic, panic=-1, rootwait, ro, dm_verity.error_behavior=3, dm_verity.max_bios=-1, dm_verity.dev_wait=1, dm="1, vroot, none, ro, 1,0, 2506752, verity, payload=PARTUUID=e9d901b8-5d96-cc46-80ee-85329c14145d/PARTNROFF=1, hashtree=PARTUUID=e9d901b8-5d96-cc46-80ee-85329c14145d/PARTNROFF=1, hashstart=2506752, alg=sha1, root_hexdigest=bc5c7f1c045100879ed3fa610a11528819bb3f72, salt=b3813f2b3835f613c6e621f76e7b6cce27ff4d7c2ecdbfc70f4057a7f14b42c3", noinitrd, vt.global_cursor_default=0, kern_guid=e9d901b8-5d96-cc46-80ee-85329c14145d, add_efi_memmap, boot=local, noresume, noswap, i915.modeset=1, tpm_tis.force=1, tpm_tis.interrupts=0, nmi_watchdog=panic,lapic, 


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c170]
    Kernel driver in use: iwlwifi


##### lsusb #############################


Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07dc Intel Corp. 
Bus 001 Device 002: ID 04f2:b48b Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


./wireless_script: line 170: pccardctl: command not found


##### rfkill ############################


./wireless_script: line 176: rfkill: command not found


##### lsmod #############################


iwlmvm                183872  0 
iwl7000_mac80211      383225  1 iwlmvm
iwlwifi               139348  1 iwlmvm
cfg80211              297791  3 iwlwifi,iwlmvm,iwl7000_mac80211


##### interfaces ########################


source-directory /etc/network/interfaces.d


##### ifconfig ##########################


./wireless_script: line 186: ifconfig: command not found


##### iwconfig ##########################


./wireless_script: line 189: iwconfig: command not found


##### route #############################


./wireless_script: line 192: route: command not found


##### resolv.conf #######################


nameserver 192.168.2.1
search domain_not_set.invalid.
options single-request timeout:1 attempts:5


##### nm-tool ###########################


./wireless_script: line 198: nm-tool: command not found


##### NetworkManager.state ##############


cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory


##### NetworkManager.conf ###############


grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory


##### NetworkManager profiles ###########


Acquisition of admin privileges failed.


##### iw reg get ########################


'iw' is not installed (package "iw").


##### iwlist channels ###################


./wireless_script: line 244: iwlist: command not found


##### iwlist scan #######################


Channel occupancy:


      2   APs on   Frequency:2.417 GHz (Channel 2)
      2   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:5.18 GHz (Channel 36)


lo        Interface doesn't support scanning.


wlan0     Scan completed :
          Cell 01 - Address: <MAC 'salklake' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"salklake"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013b3f1ceb88
                    Extra: Last beacon: 9ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'salklake' [AC2]>
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"salklake"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013b3ef90c0a
                    Extra: Last beacon: 9ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC '' [AC3]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000ad32bf787e
                    Extra: Last beacon: 9ms ago
          Cell 04 - Address: <MAC 'salklake-guest' [AC4]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:off
                    ESSID:"salklake-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000013b3f1c2ecc
                    Extra: Last beacon: 9ms ago
          Cell 05 - Address: <MAC '' [AC5]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004160b825e
                    Extra: Last beacon: 3355ms ago
          Cell 06 - Address: <MAC 'myqwest5509' [AC6]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"myqwest5509"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000004160b8249
                    Extra: Last beacon: 3355ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


##### module infos ######################


./wireless_script: line 268: modinfo: command not found
[iwlmvm]


./wireless_script: line 268: modinfo: command not found
[iwl7000_mac80211]


./wireless_script: line 268: modinfo: command not found
[iwlwifi]


./wireless_script: line 268: modinfo: command not found
[cfg80211]


##### module parameters #################


[iwlmvm]
init_dbg: N
power_scheme: 2


[iwl7000_mac80211]
beacon_loss_count: 7
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500


[iwlwifi]
11n_disable: 0
amsdu_size_8K: 0
antenna_coupling: 0
bt_coex_active: Y
debug: 0
fw_restart: Y
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: Y
wd_disable: 1
xvt_default_mode: N


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


##### modprobe options ##################


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


mkdir -p -m0755 /var/run/sshd
/usr/sbin/sshd
/sbin/iptables -P INPUT ACCEPT
exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


[    8.202531] iwlwifi 0000:01:00.0: irq 106 for MSI/MSI-X
[    8.740126] iwlwifi 0000:01:00.0: loaded firmware version 25.222.9.0 op_mode iwlmvm
[    8.817867] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    8.825842] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S (repeated 2 times)
[    9.039280] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    9.095071] iwlwifi 0000:01:00.0: L1 Enabled; Disabling L0S (repeated 2 times)
[    9.111172] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.789272] wlan0: authenticate with <MAC 'salklake' [AC1]>
[   12.791985] wlan0: send auth to <MAC 'salklake' [AC1]> (try 1/3)
[   12.814241] wlan0: authenticated
[   12.814688] wlan0: associate with <MAC 'salklake' [AC1]> (try 1/3)
[   12.837363] wlan0: RX AssocResp from <MAC 'salklake' [AC1]> (capab=0x411 status=0 aid=13)
[   12.838164] wlan0: associated
[   12.838217] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready


########## wireless info END ############
```

exact same problem here, have you found any solutions?

---

