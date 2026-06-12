---
title: "Ubuntu 16.04 LTS no internet"
date: 2016-11-17
forum: Networking &amp; Wireless
---

### Post by yegnal on 2016-11-17
My Ubuntu is not connecting to the internet via wired connection.  I already tried to edit [COLOR=black][FONT="Tahoma"]/etc/network/interfaces [/FONT][/COLOR]to:

```

auto lo
iface lo inet loopback

```

I also tried ignoring ipv6 but still no internet.   It used to work fine until an update, is on a dual boot machine so I know the adapter is working....

HELP

---

### Post by Hadaka on 2016-11-17
Hi, boot the computer and hold down the "*shift*" key, this should boot
you into the recovery mode. Select an older kernel and boot to it.
*If it boots up ok, then run and post the output of..,,Copy and paste.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
Thanks.

---

### Post by yegnal on 2016-11-17
I can boot into my current version, just have no internet...

---

### Post by Hadaka on 2016-11-17
Great,please post the wireless script from my first response,
it will build a file named *wireless-info.txt* in your home directory
copy and past the file to your response.
thanks.

---

### Post by yegnal on 2016-11-17
So silly me, although I can boot into it; my Ubuntu has no internet so, looking at the command it's not gonna work because it needs it..

I looked at the code though from the Windows side of my machine by opening in a browser.  Is there a way I could save the code in a text file and run it as a script in my Ubuntu..... ?

In the interim, I'm pasting the output of ifconfig from my 16.04 LTS...

```

[FONT=Calibri][SIZE=3][COLOR=#000000]yegnal@Me:~$ ifconfig[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]eno1[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]      [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Linkencap:Ethernet[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]HWaddr40:8d:5c:b0:55:a4[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]          [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]inet6 addr:fe80::428d:5cff:feb0:55a4/64 Scope:Link[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]          [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]UP BROADCASTRUNNING MULTICAST[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]MTU:1500[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Metric:1[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]          [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]RXpackets:16 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]          [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]TXpackets:35 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]         [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]collisions:0 txqueuelen:1000 [/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]          [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]RXbytes:6320 (6.3 KB)[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]TX bytes:5919 (5.9KB)[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]         [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Interrupt:20 Memory:fb100000-fb120000 [/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000] [/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]lo[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]        [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Linkencap:Local Loopback[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]          [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]inetaddr:127.0.0.1[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Mask:255.0.0.0[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]          [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]inet6 addr:::1/128 Scope:Host[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]          [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]UP LOOPBACKRUNNING[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]MTU:65536[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]Metric:1[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]          [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]RX packets:468errors:0 dropped:0 overruns:0 frame:0[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]          [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]TXpackets:468 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]         [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]collisions:0 txqueuelen:1 [/COLOR][/SIZE][/FONT]
[FONT=Calibri][SIZE=3][COLOR=#000000]          [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]RXbytes:34552 (34.5 KB)[/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]  [/COLOR][/SIZE][/FONT][FONT=Calibri][SIZE=3][COLOR=#000000]TX bytes:34552(34.5 KB)[/COLOR][/SIZE][/FONT]

```

---

### Post by Hadaka on 2016-11-17
Hi, try going into bios and try to disable secure boot.
and no, the windows drivers will not work with linux.
boot the ubuntu, bring up a terminal,.ctrl/alt/t and then enter..
```
lspci -n | awk '/0200/{print$3}'
```
this is the pcid for your ethernet card...please post the output.
and please try my suggestion of holding the shift key and then booting
to an older kernel and see if it will access the internet.
thanks

---

### Post by yegnal on 2016-11-18
[FONT=Calibri][SIZE=3][COLOR=#00000a]The output of lspci -n | awk '/0200/{print$3}' is:
8086:15a1

I accessed another kernel (still said 16.04 on the screen however) but the internet worked.   I was able to run the wireless-info script then because I had internet.  I re-booted into my original kernel (the one that didn't have internet) and surprisingly enough, I had internet.......

After a reboot however, I no longer had internet, I ran the wireless-info script and attached it here.   


[/COLOR][/SIZE][/FONT]

---

### Post by Hadaka on 2016-11-18
Hi, please open a terminal...ctrl/alt/t ...then Copy and paste..
```
echo 'e100e' | sudo tee -a /etc/modules
```
```
sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda
```
boot and test

---

