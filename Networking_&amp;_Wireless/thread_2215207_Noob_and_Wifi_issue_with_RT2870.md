---
title: "Noob and Wifi issue with RT2870"
date: 2014-04-05
forum: Networking &amp; Wireless
---

### Post by Daniel_Burton on 2014-04-05
Hi,

I am new to Linux and really want to keep using it, but am having  exactly the same issue as this post [http://ubuntuforums.org/showthread.php?t=2210930](http://ubuntuforums.org/showthread.php?t=2210930)  , but I have tried to do the instructions  from it but it doesn't work for me :sad:.  Is there something that I am doing wrong?

```

I ran lsusb

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 148f:7601 Ralink Technology, Corp.


```

As you can see, I have the same device. I have downloaded the same driver and done the same instructions but still no wireless!! But I am on a newer kernel than on the previous post.

```

3.11.0-19-generic

```

I downloaded driver and ran this code and got this the second time.

```


daniel@daniel-NM70-T1-C847-ODM:~$ sudo apt-get install linux-headers-generic build-essential
[sudo] password for daniel: 
Sorry, try again.
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-kde-en kde-l10n-engb language-pack-kde-en-base
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.


```

And then did the clean one and this came up.

```


daniel@daniel-NM70-T1-C847-ODM:~$ cd ~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
bash: cd: /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913: No such file or directory
daniel@daniel-NM70-T1-C847-ODM:~$ make clean
make: *** No rule to make target `clean'. Stop.
daniel@daniel-NM70-T1-C847-ODM:~$ make
make: *** No targets specified and no makefile found. Stop.
daniel@daniel-NM70-T1-C847-ODM:~$ sudo make install
make: *** No rule to make target `install'. Stop.
daniel@daniel-NM70-T1-C847-ODM:~$ sudo modprobe mt7601Usta


```
I didn't want to do a new post, but the previous post was solved and I have same issue but its instructions don't work for me! I am a complete neewb and really want to not have to trail a ethernet  cable across room and certainly don't want to use windows again.  Any  advice on how to fix? Your help is very appreciated.

---

### Post by varunendra on 2014-04-05
Welcome to Ubuntu Forums Daniel !

Please edit your original post to correct the closing part of 'Code' tags in your post - it is a forward slash (/), not a backslash (\). :)

> **Daniel_Burton said:**
> ```
daniel@daniel-NM70-T1-C847-ODM:~$ cd ~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913
bash: cd: **/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913: [COLOR="#FF0000"]No such file or directory[/COLOR]**
..
```

As the above error indicates, there seems to be no "DPO_MT7601U_LinuxSTA_3.0.0.4_20130913" directory on your desktop. Are you sure it is there? Was the downloaded package on the Desktop when you extracted it?

You are following instructions of chili555 who is the best person for wifi troubleshooting here. I may not be available to reply back later, but I'm sure he'll reply your posts as soon as he notices it.

---

### Post by Daniel_Burton on 2014-04-05
Hello varunedra,

Many thanks for your reply and I have now fixed the codes, I think I was getting too mad at trying to get this working and completely didn't notice that backwards was forwards :-/

I also checked as you said and I had the wrong folder on desktop?! Downloaded the correct one (They were incorrectly marked on their website!) and ran the code to clean and this was the result.

```

/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5306:7: warning: format &#8216;%X&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 5 has type &#8216;LONG&#8217; [-Wformat]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5359:3: warning: passing argument 2 of &#8216;RtmpDrvAllRFPrint&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rt_os_util.h:668:6: note: expected &#8216;UINT32 *&#8217; but argument is of type &#8216;PSTRING&#8217;
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:5209:22: warning: unused variable &#8216;rf_bank&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c: In function &#8216;RtmpIoctl_rt_ioctl_siwgenie&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../sta/sta_cfg.c:7610:13: warning: assignment from incompatible pointer type [enabled by default]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_md5.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Wrap&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c:1459:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c: In function &#8216;AES_Key_Unwrap&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_aes.c:1554:6: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 2 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c: In function &#8216;MlmeResetRalinkCounters&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c:543:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c:543:3: warning: cast from pointer to integer of different size [-Wpointer-to-int-cast]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c: In function &#8216;AsicRxAntEvalTimeout&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/mlme.c:5201:45: warning: unused variable &#8216;rssi_diff&#8217; [-Wunused-variable]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_wep.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/action.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c: In function &#8216;CmdRspEventCallbackHandle&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c:2509:8: warning: unused variable &#8216;Ret&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c: In function &#8216;StopDmaTx&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c:2684:8: warning: unused variable &#8216;IdleNums&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data.c:2682:20: warning: unused variable &#8216;UsbCfg&#8217; [-Wunused-variable]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c: In function &#8216;NICInitAsicFromEEPROM&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:981:9: warning: unused variable &#8216;i&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c: In function &#8216;NICInitializeAdapter&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:1292:22: warning: unused variable &#8216;GloCfg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c: In function &#8216;NICInitializeAsic&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:1367:11: warning: unused variable &#8216;KeyIdx&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init.c:1656:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_aes.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_sync.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/eeprom.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/eeprom.c: In function &#8216;RtmpChipOpsEepromHook&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/eeprom.c:34:9: warning: unused variable &#8216;e2p_csr&#8217; [-Wunused-variable]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c: In function &#8216;Set_DebugFunc_Proc&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c:1084:2: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 2 has type &#8216;const char *&#8217; [-Wformat]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c:1084:2: warning: too many arguments for format [-Wformat-extra-args]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c: In function &#8216;set_rf&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_info.c:5730:3: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int *&#8217;, but argument 5 has type &#8216;UCHAR *&#8217; [-Wformat]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c: In function &#8216;wmode_valid_and_correct&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c:279:8: warning: unused variable &#8216;mode&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c: At top level:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cfg.c:264:16: warning: &#8216;wmode_valid&#8217; defined but not used [-Wunused-function]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_radar.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/spectrum.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/spectrum.c: In function &#8216;PeerMeasureReportAction&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/spectrum.c:1972:3: warning: format &#8216;%d&#8217; expects argument of type &#8216;int&#8217;, but argument 3 has type &#8216;long unsigned int&#8217; [-Wformat]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rt_channel.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_profile.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_profile.c: In function &#8216;rtmp_read_multest_from_file&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_profile.c:2671:23: warning: unused variable &#8216;pWdsEntry&#8217; [-Wunused-variable]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_asic.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/scan.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/uapsd.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ps.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../rate_ctrl/ra_ctrl.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../rate_ctrl/alg_legacy.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../rate_ctrl/alg_ags.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/rtmp_chip.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/txpower.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mac/rtmp_mac.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mgmt/mgmt_hw.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mgmt/mgmt_entrytb.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rtmp_phy.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rtmp_phy.c: In function &#8216;NICInitBBP&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rtmp_phy.c:61:8: warning: unused variable &#8216;R0&#8217; [-Wunused-variable]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rlt_phy.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../phy/rlt_rf.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ba_action.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ba_action.c: In function &#8216;convert_reordering_packet_to_preAMSDU_or_802_3_packet&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ba_action.c:1574:2: warning: assignment makes integer from pointer without a cast [enabled by default]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mgmt/mgmt_ht.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rt_os_util.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOsUsDelay&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:179:8: warning: unused variable &#8216;i&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;duplicate_pkt&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:497:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.11.0-19-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:499:3: warning: passing argument 1 of &#8216;memmove&#8217; makes pointer from integer without a cast [enabled by default]
/usr/src/linux-headers-3.11.0-19-generic/arch/x86/include/asm/string_64.h:58:7: note: expected &#8216;void *&#8217; but argument is of type &#8216;sk_buff_data_t&#8217;
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;ClonePacket&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:650:20: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOsPktInit&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:669:2: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;wlan_802_11_to_802_3_packet&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:695:15: warning: assignment makes integer from pointer without a cast [enabled by default]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpDrvAllRFPrint&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: warning: passing argument 2 of &#8216;file_w->f_op->write&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2052:4: note: expected &#8216;const char *&#8217; but argument is of type &#8216;UINT32 *&#8217;
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:22: warning: unused variable &#8216;macValue&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2037:9: warning: unused variable &#8216;macAddr&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSIRQRelease&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_linux.c:2173:21: warning: unused variable &#8216;net_dev&#8217; [-Wunused-variable]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_mac_usb.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_mac_usb.c:562:31: warning: initialisation from incompatible pointer type [enabled by default]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RT28XXDMAEnable&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_mac_usb.c:1371:20: warning: unused variable &#8216;UsbCfg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_mac_usb.c:1370:22: warning: unused variable &#8216;GloCfg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_mac_usb.c: In function &#8216;RT28xxUsbAsicRadioOn&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_mac_usb.c:1931:22: warning: unused variable &#8216;GloCfg&#8217; [-Wunused-variable]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data_usb.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data_usb.c: In function &#8216;ComposeNullFrame&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data_usb.c:279:2: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data_usb.c: At top level:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/cmm_data_usb.c:222:13: warning: &#8216;rlt_usb_update_txinfo&#8217; defined but not used [-Wunused-function]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtusb_io.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtusb_io.c: In function &#8216;RTUSBWriteEEPROM&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtusb_io.c:682:9: warning: unused variable &#8216;Value&#8217; [-Wunused-variable]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtusb_data.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtusb_bulk.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtusb_bulk.c: In function &#8216;RTUSBCancelPendingBulkOutIRP&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtusb_bulk.c:1678:15: warning: assignment from incompatible pointer type [enabled by default]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_usb.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_usb.c: In function &#8216;cmd_rsp_event_tasklet&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_usb.c:537:22: warning: assignment from incompatible pointer type [enabled by default]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ee_prom.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/ee_efuse.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c: In function &#8216;USBLoadIVB&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c:68:9: warning: unused variable &#8216;Temp&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c:67:9: warning: unused variable &#8216;Index&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c:66:9: warning: unused variable &#8216;Value&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c:65:9: warning: unused variable &#8216;i&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c: In function &#8216;USBLoadFirmwareToAndes&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c:105:19: warning: unused variable &#8216;MCtrl&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c:104:20: warning: unused variable &#8216;UsbCfg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c: In function &#8216;MCUCtrlExit&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c:591:8: warning: unused variable &#8216;Ret&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c: In function &#8216;GetCmdRspNum&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c:634:16: warning: unused variable &#8216;IrqFlags&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c: In function &#8216;AndesLedOP&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_and.c:2071:9: warning: unused variable &#8216;Value&#8217; [-Wunused-variable]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_mcu.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_mcu.c: In function &#8216;MCUBurstWrite&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_mcu.c:32:2: warning: passing argument 3 of &#8216;RTUSBMultiWrite_nBytes&#8217; from incompatible pointer type [enabled by default]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/include/rtmp.h:7553:10: note: expected &#8216;PUCHAR&#8217; but argument is of type &#8216;UINT32 *&#8217;
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_mcu.c: In function &#8216;ChipOpsMCUHook&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_mcu.c:64:25: warning: assignment from incompatible pointer type [enabled by default]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_mcu.c:71:25: warning: assignment from incompatible pointer type [enabled by default]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_mcu.c:72:27: warning: assignment from incompatible pointer type [enabled by default]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_mcu.c: In function &#8216;MCURandomWrite&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_mcu.c:41:1: warning: control reaches end of non-void function [-Wreturn-type]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_mcu.c: In function &#8216;MCUBurstWrite&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_mcu.c:33:1: warning: control reaches end of non-void function [-Wreturn-type]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mcu/rtmp_M51.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rt_rf.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601_INIT_CAL&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:888:8: warning: unused variable &#8216;Temperature&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;NICInitMT7601RFRegisters&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:1006:9: warning: unused variable &#8216;IdReg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;NICInitMT7601MacRegisters&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:1044:9: warning: unused variable &#8216;IdReg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;NICInitMT7601BbpRegisters&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:1086:6: warning: unused variable &#8216;IdReg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601_ChipSwitchChannel&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:1442:3: warning: ISO C90 forbids mixed declarations and code [-Wdeclaration-after-statement]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:1272:6: warning: unused variable &#8216;IdReg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601DisableTxRx&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:1497:3: warning: &#8216;return&#8217; with no value, in function returning non-void [-Wreturn-type]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601UsbAsicRadioOff&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:1725:9: warning: unused variable &#8216;Value&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601UsbAsicRadioOn&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:1790:16: warning: unused variable &#8216;pChipOps&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:1789:22: warning: unused variable &#8216;GloCfg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601_ReadChannelPwr&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:1905:10: warning: unused variable &#8216;bUseDefault&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601AsicTemperatureCompensation&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:2282:6: warning: unused variable &#8216;IdReg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601_EnableTSSI&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:2478:9: warning: unused variable &#8216;ret&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:2477:15: warning: unused variable &#8216;BBPReg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:2477:8: warning: unused variable &#8216;RFReg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601_InitDesiredTSSITable&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:2611:16: warning: unused variable &#8216;offset&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:2611:9: warning: unused variable &#8216;index&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601_GetTssiCompensationParam&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:2682:9: warning: unused variable &#8216;ret&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:2681:7: warning: unused variable &#8216;count&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:2675:8: warning: unused variable &#8216;RFReg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601_AsicTxAlcGetAutoAgcOffset&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:2949:8: warning: unused variable &#8216;BBPReg&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c: In function &#8216;MT7601_Init&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../chips/mt7601.c:3399:24: warning: assignment from incompatible pointer type [enabled by default]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../mac/ral_omac.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_usb_util.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_usb_util.c: In function &#8216;rausb_autopm_put_interface&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_usb_util.c:120:7: warning: unused variable &#8216;pm_usage_cnt&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_usb_util.c: In function &#8216;rausb_autopm_get_interface&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_usb_util.c:151:7: warning: unused variable &#8216;pm_usage_cnt&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/rt_usb_util.c:157:1: warning: control reaches end of non-void function [-Wreturn-type]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/usb_main_dev.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/usb_main_dev.c: In function &#8216;rt2870_suspend&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/usb_main_dev.c:394:21: warning: unused variable &#8216;net_dev&#8217; [-Wunused-variable]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/usb_main_dev.c: In function &#8216;rt2870_resume&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../os/linux/usb_main_dev.c:450:21: warning: unused variable &#8216;net_dev&#8217; [-Wunused-variable]
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/frq_cal.o
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/frq_cal.c: In function &#8216;InitFrequencyCalibration&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/frq_cal.c:88:3: warning: format &#8216;%x&#8217; expects argument of type &#8216;unsigned int&#8217;, but argument 4 has type &#8216;ULONG&#8217; [-Wformat]
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/frq_cal.c: In function &#8216;FrequencyCalibrationMode&#8217;:
/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/../../common/frq_cal.c:130:9: warning: unused variable &#8216;PreRFValue&#8217; [-Wunused-variable]
  LD [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/mt7601Usta.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/mt7601Usta.mod.o
  LD [M]  /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/mt7601Usta.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-19-generic'
cp -f /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux/mt7601Usta.ko /tftpboot 2>/dev/null || :
daniel@daniel-NM70-T1-C847-ODM:~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ sudo make install
make -C /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/
install -m 644 -c mt7601Usta.ko /lib/modules/3.11.0-19-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.11.0-19-generic
make[1]: Leaving directory `/home/daniel/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913/os/linux'
daniel@daniel-NM70-T1-C847-ODM:~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ sudo modprobe mt7601Usta
daniel@daniel-NM70-T1-C847-ODM:~/Desktop/DPO_MT7601U_LinuxSTA_3.0.0.4_20130913$ LSUSB


```

But still have no wireless. This is about the tenth time i have installed ubuntu now. Other times I did get the wireless working and even connected to my Sky Router, but the moment I attempted to connect to a website ubuntu would crash! everytime this happened, so I would reinstall ubuntu and try again. Have tried 12.04 and 13.10.

---

### Post by Daniel_Burton on 2014-04-05
I managed to get wireless to connect after a couple of reboots, so I was able to connect to my Sky Router, but the moment that i tried to access a webpage in firefox the computer crashed and ended up with lots of white writing on a black screen! I dont know how to get the words onto here though. I did take a pic but cant upload it.

---

### Post by Daniel_Burton on 2014-04-05
[img]

---

### Post by Daniel_Burton on 2014-04-05
This is what appeared after the crash.

---

### Post by chili555 on 2014-04-05
I am running exactly the same kernel; 3.11.0-19. I get the same numerous warnings. I am unaware of any method to mitigate them, nor any alternate driver. The warnings are evidently why the driver doesn't work sufficiently well and, in fact, crashes the whole computer. I think we have three alternatives:

#Extract the Windows XP drivers, if we can, and try ndiswrapper. 
#Place the device under the rear wheel of your car as you drive to the store to get a fully supported USB wireless.
#Email Mediatek, the author of your driver and ask them how to fix the warnings.

I realize that none of these options are good. I wish I had a better option.

[http://ubuntuforums.org/showthread.php?t=2166676](http://ubuntuforums.org/showthread.php?t=2166676)

---

### Post by Daniel_Burton on 2014-04-05
Chili,

Hi and cheers for the information. To be honest I think that I will be taking your second piece of advice and running it over on my way to the shop in the morning to buy a Belkin N300. As looking on the thread you lionked to it works out the box.  And as its only £15 its more than worth losing my head over this thing anymore.

Many thanks for your help and great to see guys like you two helping out us novices to linux.

Cheers,

Dan

---

### Post by chili555 on 2014-04-05
Seriously, you could probably donate it somewhere or give it to a Windows friend. 

I suspect that this may be an 802.11ac device for which technology and especially Linux drivers are in development. We, however, need our mp3s, torrents and lolcats now, not three years from now.

---

### Post by Optimized_Coder on 2014-05-29
> **chili555 said:**
> Seriously, you could probably donate it somewhere or give it to a Windows friend. 

I suspect that this may be an 802.11ac device for which technology and especially Linux drivers are in development. We, however, need our mp3s, torrents and lolcats now, not three years from now.

I have this exact same chipset (new wireless adapter) and I'm hitting the same kernel panic on trying to get data (the association/authentication -from the supplicant works out-of-the-box).

Granted, this is a new chipset, but MTK seems to have a linux driver for it. Has anybody got it working at all? Is this only a problem for x64 machines?

I don't agree with the 'too new for linux' ideology. Shouldn't linux be at the fore-front of driver development for newer devices? If I'd like to contribute with developing/updating the driver (I have some driver/networking experience), how'd I do about it? Do I start off with the 'linux-wireless' mailing-list?

---

### Post by chili555 on 2014-05-29
> Shouldn't linux be at the fore-front of driver development for newer devices? It should except that drivers for most wireless and ethernet devices are written by the manufacturer, not the Linux or Ubuntu developers. Here is a snip from modinfo for my wireless device:```
$ modinfo iwlwifi
filename:       /lib/modules/3.13.0-27-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
[COLOR="#FF0000"]author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>[/COLOR]
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux

```In most cases, we get what the manufacturer gives us. You could email the manufacturer but past experience tells me that's unlikely to be productive. 

You could try to modify the existing manufacturer provided code to try to overcome the warnings and errors encountered in compiling; I suspect that a change in the 3.13 kernel and, possibly, gcc are responsible. See post #3 above. If you are successful, we need to post the amended version somewhere so that all can benefit.

---

