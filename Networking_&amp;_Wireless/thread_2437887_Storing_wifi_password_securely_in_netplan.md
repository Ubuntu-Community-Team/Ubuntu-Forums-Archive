---
title: "Storing wifi password securely in netplan"
date: 2020-03-02
forum: Networking &amp; Wireless
---

### Post by baby-shark on 2020-03-02
Hello everyone,

So I have just finished configuring my wifi with netplan however I am slightly concerned with the wpa-psk being stored in clear text both in the .yaml file and also in the wpa_supplicant .conf file.

I read about the wpa_passphrase function to generate a hashed version of the password, however I have run into two problems.

1. If I simply edit the wpa_supplicant conf file located in /run/netplan/wpa-xxx.conf file (this one is created by netplan itself), it gets written over at every boot and or every netplan apply.

2. If I put the hashed password in the yams file using the syntax

```
password: hash: hashedpass
```

The generated .conf file always puts the hashed parts in quotation marks in the .conf file. It seems there was a bug report about this:

[https://bugs.launchpad.net/netplan/+bug/1819831](https://bugs.launchpad.net/netplan/+bug/1819831)

The bug seems to be fixed in that thread, however even after an apt-get update/upgrade I am experiencing this problem.

_**My questions:**_

Is what I am trying to do possible? Or is there a better approach to secure the wifi password?

If this is the right approach, how do I install this bug fix?

Thanks!

---

### Post by chili555 on 2020-03-02
The bug report suggests:> 
This bug was fixed in the package netplan.io - 0.98-0ubuntu1~18.04.1
What does this report?```
sudo dpkg -s netplan.io
```We hope it reports:> 
Version: 0.98-0ubuntu1
Finally, the bug report suggests that the syntax is:```
password: hash:[redacted]
```And not:```

password: hash: hashedpass

```In other words, without a space betwwen 'hash:' and the actual hashed password. Please try it and follow with:```
sudo netplan generate
sudo netplan -debug apply
```

---

### Post by baby-shark on 2020-03-07
No bueno.

I have

```
[SIZE=3][COLOR=#000000]*Version: 0.98-0ubuntu1*[/COLOR][/SIZE]
```

Yet the wpa supplicant file is still created with quotes.

My netplan yaml:

```

[SIZE=3][FONT=&amp]network:  
 version: 2[/FONT]
[FONT=&amp]   renderer: networkd[/FONT]
[FONT=&amp]   wifis:[/FONT]
[FONT=&amp]     wlan0:[/FONT]
[FONT=&amp]       access-points:[/FONT]
[FONT=&amp]         [redacted]:[/FONT]
[FONT=&amp]          password: hash:[redacted][/FONT]
[FONT=&amp]       dhcp4: yes[/FONT][/SIZE]
```

Generates the following wpa_supplicant conf:

```

[SIZE=3][COLOR=#000000][FONT=&amp]network={[/FONT][/COLOR][COLOR=#000000][FONT=&amp]  
 ssid=&#8220;[redacted]&#8221;[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  key_mgmt=WPA-PSK[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]  psk="hash:[redacted]&#8221;[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]}[/FONT][/COLOR][/SIZE]

```

There is another bug report here with the same issue, this one doesn't seem to be resolved?

[https://bugs.launchpad.net/netplan/+bug/1735175](https://bugs.launchpad.net/netplan/+bug/1735175)

---

