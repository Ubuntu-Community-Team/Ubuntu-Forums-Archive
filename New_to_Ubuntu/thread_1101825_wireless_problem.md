---
title: "wireless problem"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by toehead2 on 2009-03-20
I am having trouble with my wireless connection in Ubuntu, I had the same issue with Kubuntu. I also boot with another linux distro and the wireless works fine. The driver in Ubuntu is ADM 8211 wireless adapter, the driver for the other distro is ADM 8201 wireless adapter. Is there a way to change the driver? Also having trouble getting the ethernet connection to work. I might add that upon first boot after fresh install the wireless connection was working as I updated the system via adept.
Thanks for any and all help
Mike

---

### Post by ibuclaw on 2009-03-20
Do you mind opening a terminal and posting output from the following commands that may help give people a better insight into what is actually going on/wrong with the card?

1) Is your card listed as being recognised?
```
lspci | grep -i Network
```

2) Is it seen as a wireless device?
```
sudo iwconfig
```

3) What kernel version are you running?
```
uname -r
```

Also, what are you using to connect to your Router in terms of encryption (WEP/WPA/Open System).

Regards
Iain

---

### Post by toehead2 on 2009-03-20
> **tinivole said:**
> Do you mind opening a terminal and posting output from the following commands that may help give people a better insight into what is actually going on/wrong with the card?

1) Is your card listed as being recognised?
```
lspci | grep -i Network
```

2) Is it seen as a wireless device?
```
sudo iwconfig
```

3) What kernel version are you running?
```
uname -r
```

Also, what are you using to connect to your Router in terms of encryption (WEP/WPA/Open System).

Regards
Iain

1) I don't recognize the symbol between the lspci and the grep commands.
Pardon my ignorance here please.
2)lo no wireless extensions
eth0 no wireless extensions
wmaster0 no wireless extensions
wlan0 IEEE 802.11b ESSID:"Blitzz"
Mode:Managed   Frequency:2.457 Ghz   Access Point: 00:E0:98:AC:09:12
Tx-Power=0dBm
Retry min limit:7    RTS thr:off   Fragment thr=2346B
Encryption Key:off
Link Quality:0   Signal level:0   Noise Level:0
Rx invalid nwid:0 Rx invalid crypt:0  Rx invalid fragment:0
Tx excessive retries:0  Invalid misc:0  Missed Beacon:0
3) 2.6.24-23-generic

---

### Post by 3rdalbum on 2009-03-20
The symbol between the lspci and grep commands is the pipe - |. It's usually on the key above your Enter/Return key. Shift - \.

---

### Post by toehead2 on 2009-03-21
ok thanks 3rd album. The results of command 1 are as follows 03:00.0 Network controller ADMtek ADM8211 802.11b Wireless Interface (rev 11).
Hope this helps the gurus figure out my problem.

---

### Post by PuddingKnife on 2009-03-21
I am not much to help, but another user provided me this link when I had a similar problem VERY recently :P

[http://ubuntuforums.org/showthread.php?p=6028741#post6028741](http://ubuntuforums.org/showthread.php?p=6028741#post6028741)


Hope this helps, good luck

---

### Post by ibuclaw on 2009-03-21
> **toehead2 said:**
> 
```
lo no wireless extensions
eth0 no wireless extensions
wmaster0 no wireless extensions
wlan0 IEEE 802.11b ESSID:"Blitzz"
Mode:Managed   Frequency:2.457 Ghz   Access Point: 00:E0:98:AC:09:12
Tx-Power=0dBm
Retry min limit:7    RTS thr:off   Fragment thr=2346B
Encryption Key:off
Link Quality:0   Signal level:0   Noise Level:0
Rx invalid nwid:0 Rx invalid crypt:0  Rx invalid fragment:0
Tx excessive retries:0  Invalid misc:0  Missed Beacon:0

```

It may seem to appear that your Wireless Card driver (adm8211) is broken, as evidenced by [this thread]("http://ubuntuforums.org/showthread.php?t=873449") in July 2008, and [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/105247") in April 2007 (albeit, an expired bug that you can gracefully ignore). [This user]("http://ubuntuforums.org/showpost.php?p=5572395&postcount=3") claims that he rectified the problem by blacklisting the native driver and using ndiswrapper and the Windows drivers instead.

Although, I would perhaps ask you to instead acquire the most recent release of Ubuntu ([8.10]("http://www.ubuntu.com/getubuntu/download")), and test your wireless card for Network Connectivity while booted on the LiveCD, and then we could probably look into attempting to fix it using ndiswrapper if it continues to not function properly.

Regards
Iain

---

