---
title: "Ralink RT5370 Wireless Adapter driver installation."
date: 2022-08-14
forum: Networking &amp; Wireless
---

### Post by ghoulie on 2022-08-14
Hello all, 

I am newbie with ubuntu. Couple of weeks ago I bought a HPCompact 8300 desktop pc and installed ubuntu server. I connected a small router to it with ethernet cable to make internet connection but would like run it with wifi dongle. I checked couple of threads and youtube videos to install the driver of dongle and couldn't success. While my checkings I saw couple of commands that the experts asked for more detailed information and I prepared them below. Looking forward to your helps. Thanks in advance

> 
Hostnamectl status:
Static hostname: server
       Icon name: computer-desktop
         Chassis: desktop
      Machine ID: 29e74fa4ebae47b88c84a4366c34f668
         Boot ID: cb3b29c5ffef417aa3b66174e646c502
Operating System: Ubuntu 22.04.1 LTS
          Kernel: Linux 5.15.0-43-generic
    Architecture: x86-64
 Hardware Vendor: Hewlett-Packard
 Hardware Model: HP Compaq Elite 8300 SFF


> 
lshw -c network:
 *-network
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection (Lewisville)
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eno1
       version: 04
       serial: b4:b5:2f:bc:55:be
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=5.15.0-43-generic duplex=full firmware=0.13-4 ip=192.168.1.46 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:24 memory:f7c00000-f7c1ffff memory:f7c38000-f7c38fff ioport:f060(size=32)
  *-network DISABLED
       description: Wireless interface
       physical id: 4
       bus info: usb@1:1.4
       logical name: wlx6c60eb57a006
       serial: 6c:60:eb:57:a0:06
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=5.15.0-43-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11


> 
iwconfig:
lo        no wireless extensions.


eno1      no wireless extensions.


tun0      no wireless extensions.


br-ffaa9de23c18  no wireless extensions.


br-1fa402e976fd  no wireless extensions.


br-4978496bf08d  no wireless extensions.


br-57197483bc0a  no wireless extensions.


br-cf5a1dd196bf  no wireless extensions.


br-a2c08b284cff  no wireless extensions.


br-e42609727897  no wireless extensions.


br-0058216221e7  no wireless extensions.


br-29b923ed1d8d  no wireless extensions.


br-3a6a4bdc2ceb  no wireless extensions.


docker0   no wireless extensions.


vethb4a1872  no wireless extensions.


veth3508253  no wireless extensions.


veth40f5b4b  no wireless extensions.


veth4a19021  no wireless extensions.


veth2140144  no wireless extensions.


veth642c381  no wireless extensions.


vethb4c0ed6  no wireless extensions.


veth2aaa5ea  no wireless extensions.


wlx6c60eb57a006  IEEE 802.11  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
          Retry short  long limit:2   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off


> 
lsusb:
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


---

### Post by morrownr on 2022-08-15
Hi ghoulie,

>  I checked couple of threads and youtube videos to install the driver of dongle and couldn't success. 

The driver (module) for the rt5370 chipset has been in the Linux kernel for several years. There should be no need to install a driver unless the server version is doing something I am unaware of.

> ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter

Yup. Good ole rt5370 chipset.

After plugging in the adapter, did you check to see if you have a wireless interface?

$ iw dev

The following site providing USB WiFi information for Linux users:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Regards

---

### Post by morrownr on 2022-08-15
Opps... reread your msg. Your wireless interface is there: wlx6c60eb57a006

So that means the driver did its job.

> *-network DISABLED
description: Wireless interface
physical id: 4
bus info: usb@1:1.4
logical name: wlx6c60eb57a006
serial: 6c:60:eb:57:a0:06
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=rt2800usb driverversion=5.15.0-43-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11

Try running the following:

$ rfkill unblock wlan

---

### Post by ghoulie on 2022-08-15
Hello [COLOR=#000000]morrownr,

[/COLOR]Thank you for your reply. As I said I am newbie that even couldn't realize the the wifi dongle was already ready :) I typed $rfkill unblock wlan and the result is as in the picture below. Is there any tutorial or something that you have, how to connect wifi with a wifi dongle. I spent many hours to find out but couldn't find any documentation about it. Could you please help me how to connect to my wifi network with the wifi dongle ? 

Thanks in advance. 


[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAARkAAAAiCAIAAADkuDqaAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAASdEVYdFNvZnR3YXJlAEdyZWVuc2hvdF5VCAUAAAXQSURBVHhe7ZvtbeMwDIa7VLtOMkp/tQN0iAOSCbpCgOsEXeEON8LxQ5QoSpRjxblDEgKPC4uWSIl6abtN8/T0GgTBFth2EARz2HYQBHPYdhAEc9j2lfh4//nrz2/i8KO5erM8f379/Hx5en15 754XSpF2SedND0RvPr713GnjDAZHn6mfSPctW8Ud5yHFVw5D1vXEk73 /3Z2FElX28fzfntszuxjC6vpVYxYw3h1b4mfhzX2S9lae2Xxh3nYT3XysO/qCWba izZWr K1JL 8OlN4jWw6yGopbGXLWWsABOe4qBT0A1b1xG77HYsasHaIbEAW5NdcGjCcLROWgx99f7UexqbHeeFFfPDURZlnC HwGHdx6tLTK8ZrRJS3EHtcQJTx1Uqnvh0P8auwVjlb2AUSkbbKf8IHm2bOcZIrauOnFLZ3tJvejquN089NCdE5guvaG9PCgd5kvoqrdeHzjS3nC88g5G8xbRUx8O49mlWQsRZklry3M67iAE9Wk75yHZP55LH2ee6Lnae5nPSj8MzbOaFe9f5UptLY1FJ3Z7WvpxccKcmUzJMwWiCVRTInqamLFbMJxXS1lSKp9sT0NojXUUG5f6d/WDPZtSpP6jPNToTWcwhLY0eYAOOWizrna9PnDU6xdpWn0s2amJrqqQMCGcTVohbwx4oD4UN81VAQ6VMWvOmyfbldDlfLWfPiIm8Ywplv4wlvxIn2pgwzBuPVuENbTHHdVSyDSamLRb9AL10s6ztwsxcX39qL3TLOWhJoshe4OT6kk1zsPyen3g0Fos2JDi2rNTE11VIVltKb8pkNRS6s834zwKc02WgqqBbjbL9qiNnPDTQ3fG7QE/NNV0XlPtWcMwbiNBSiy7VUpVeJpYa7d4GjrPrmqj9NRx7TTycOMng/ZRHgxpYvvD9xHYtW7tBBqpLKzXB47 HtuQkiPPTk10VYWEq/RSR0PSHQI82HCULzZiZ6OqhK9FWbZe8Iyflci6znQ47NavpZSu7kLsRszaLZ6GzrO3aTdx7TSyfmS95RKzlAcDb8rHHzBfRGv8gN50MTKHG9dRW7DxzOHmOMbMfbcPLl2Qm7YOgM84afYExJgXBtytBP8ondupobaRHinvaUu2yc8sOrW8waI/kdOiwsxTVCSemCcxzYyghT3auNtXaLyhvqcvE XdnVPgo2rquf/jIX82BByb19HrEbhD4d03t4pjcfEaTefW 9PnD4e0yumcqRZ0cwO kq1w//RMvhBMsoQ1RP4yf1N5eWtAidjVZm/TSL6iP5hYW0d4eWpbhGJTj57JZzRVtbLwrhgWvtPlxCyHFXNIR vFoqzssCB3Fd/VC1mEvop5cHD4qbxurddOejgn5BEer q2vpqpypsyC4eWx7c oX6GdOoOQXAf2PY1KO8M/V9gguAesO0gCOaw7SAI5rDtIAjmsO0gCOaw7SAI5rDtK6H lDf8oO3GeN7we7XBrWPbl4EfIbcfD uPmOqPm26d3Wbfqw1uH9u jF4tWZ3JvbxYbheppfY/gILHAw4sgFN8r5bR/8E1RIbXmH8IDB4JOFIZsIDKOxgVjIheSdazS7MWIqiZxJr/nfFxv1cb3Dlw1PUg0rT6WLJTsymPpLYka35GgQfqQ3G1jhlwqIxK6/15sl3XTDpf7acPz7l4xtKS/jCW/EifamDwaMChtVhQN3hCNOTZqYmuKlWx2pKsUyCppdQfH1bqUYCi5ydYRtVAO08Ah/CUVP1M OmhO2M5gZ9cWpVzpH5dDB4MOPrasjUj92/PTk101daSaB30h2oDDzYcFmQyYmephxq/BlSdVzW51s9KZF2bOQxuGjgcKWCRZDvehpNMPTuBlaYVTLWEP8GIiodagnDt/Rv9JJ qrmpGkqX6BCe5qif98Oqq24GPlG7UUoDA4UuBhMVU8vLsCFZFusr1k6oILA/ vdrgzrHtrQmdBY CbW9O/XtLfK82uE9en/4Cb79EmjJXW/sAAAAASUVORK5CYII=[/IMG]
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAASQAAAAnCAIAAAApeKKhAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAASdEVYdFNvZnR3YXJlAEdyZWVuc2hvdF5VCAUAAAaSSURBVHhe7ZtbTiNLDIazKdhOWAI7OPMEC2ARI5EV8HwAQYBwE/cAEiDxNKOzgzm26 ZyXTrdCT0icesTStwuu8rlv7shZLC5uTn4MVAU5ctRsSlKT6jYFKUn hPbzvbZr/9 E7s/k7PflrW9ydne uDH tZ07nWxEvmY9CLxRPDs71 jITPCZMzwGe0Lorj2BeWt16EFX1yHJhYuNlzPdHtN2LGNJls7yevvz3Bs mx saUtVW8yPJtvmp jdvZ5aVr7vHnrdWjPV9WhiV7EJjcDfBZZu7 KE9vG7rxXkDRC1yZTsdX5u2JDhYw3aBJ4k2ULw3Xm7rwZO7tHe6h7IKyQH9zcIB29hmb1/nzDgp2Nzc6T8vK5QdeGJcwex4HDMzfnFDc8praLTXkrYjMFtw6s1Ll0GL NXYK5wl7AKFsNY6f6IH62xm5miEjhZfIGZ3mKPUvzvNk65ODOFiwX39BcHVgf lMYKrfergSx bWFxzxamFMF Zh5lOzubdypsAxavJ/0aAgpyCd19kN8fHztfArzxMhRc7j5tIxjoHlGszIbHIVie09jMYjcv5R8XpywqYwn1JkS0QSiKRG5pulil2C6kth8z7F6GrsdQmuMs8i85J/tH/RMtEr tTrE8E03YApuSeoADj5psq50vV1hYvPpXe/KBmqy01sMFc0JZozTtSUwOwcRyIfy2sUwICAz qYszdPYmRLc69Zx8rhuc5FxD5w/jKU4zicamFDNG88WMU22gVvOe8WTNE1Hu4QvkC9tNnu6EJG33D9s7zhNdYjxzeCjwYvoXlevQ/N6uxI9Ropzck4ud8lObzFUNCfTjnYDbCInNutvLud FG4GWQJMJNlyh/1jO90hTg7ujPsHcWiq9nVMtKkJ1bxJj1JhTVjWyoxS07S1S0pNNpudiSd48rxyGn64iONBe60OAjuxjd3pCBimYeUEklZpWG9X2ojNFbFkp7cYKpoTnKXnRhpirzEQQaajghojOou2s5Sb1dWFV6RLnJa4dc0YsOqWF5stV3YhciO62iWlJpvNnpZd5JXT8P3j1htOGZrqIDCbsrO9u7cO/Ua/TFbnQxMIeUvrCvau1MRGk/B2vJDbZCU7ISsCzrAw AlGWzVIl9YU49iY6JZtylqzQt7xBhXXGzvFMaubsaxuA6oBA015RSfZcsFrHJj2GZY6J562dgmrGzZu45U srN9dMi8xf7JL7OxDhJsua29EbpB6vHIPup7cvNxDcl3v7TerlTFBlBuQ5SpZEewfPasEZj5iZbdMawzDGGeIo71F6eamhWcRTN1jZMsKo/bAFhIevlIacor2ggn78OaWtHex4tCzMC29jJGY8hoGJoM45TEFoKHBVbyFvuH5CROYZxcHUpQXjuW72ZxPizpBFTK/Rcvti9lxkZUlCWnB7GJh/g1c3/nDoqyCvQhNiA8luR/iVKU5acnsSmKomJTlJ5QsSlKT6jYFKUnVGyK0hP9iY39QbL6ieQ3Y22B39RWlpuFiw0/jE8/aOcftcUfu313hgv7pray7PQiNtmI7m4QLN8XJ7b0n60UJcaIDRUy1m9qG/h/01Vxw2PEP2cqiiOIDRrFdFh4zCNFOVWwni7Z3du4U6HdqZv9/56u7je1lZWGic33iutd2UBNdnqb6Me2o 17c5eDCORDeXmjGyAgMzIx5Odp7FxU9nXrOHnMnENk1J7zh7EUx/lEAxWFEz1GinPsFkG4JivZ6S2GitrOtKPte5vIic364 2O3UxQFeYe6GEiSecJ4BAzJSawDnFycGfUG8Tx2ouCI/ETqaIw2ojN3QFKdnqLoVKxOTFAg2I7QgSZDhVrjejsBBNTFgm7EESibRunJW5dCwuoLDE1sZGKvB0v5LaPS3YCpchbnMSGP8GIkgCxQbr0DoBxbEwmvJhaT5OAIYiXfcc4ZnXR9aKM07aKTWmmKjaAOs8Q9V/JjqBs7FkjMCszsKzyN7X//PMni3BTlhYjti9llkZcBYTGPMJNWVp6EJv43Wllv6ktNOYRbsrS0ofYANSbe5Zb1d9thMY8wk1ZWnoSm6JiU0BseuihRw/H4OXl5eHh4fb29vr6 uLiYjKZnJ6enpycHB8fHx0dHR4eHhwc7O/v/6uHHnrMdwze399fX1 n0 nj4 Pd3d3NzQ2o7urqCoR3fn5 dnZmtKeHHnrMeQw Pz8/Pj7e3t5Acs/Pz09PT6C6 /t7uNcZ4RntXeqhhx7zHJeX/wMES6gSSioDLgAAAABJRU5ErkJggg==[/IMG]

---

### Post by morrownr on 2022-08-15
Don't worry about the newbie thing. I am a newbie to Ubuntu Server. Been using Linux since 1994 but never tried Ubuntu server. Correct me if I am wrong but the server version does not have a gui desktop so we need to know how to use the command line interface to connect. Try the following guide:

[https://itsfoss.com/connect-wifi-terminal-ubuntu/](https://itsfoss.com/connect-wifi-terminal-ubuntu/)

---

### Post by ghoulie on 2022-08-15
> **morrownr said:**
> Don't worry about the newbie thing. I am a newbie to Ubuntu Server. Been using Linux since 1994 but never tried Ubuntu server. Correct me if I am wrong but the server version does not have a gui desktop so we need to know how to use the command line interface to connect. Try the following guide:

[https://itsfoss.com/connect-wifi-terminal-ubuntu/](https://itsfoss.com/connect-wifi-terminal-ubuntu/)


Thanks to encouraging me :) Yes you are right. There is no gui but terminal. I am running some docker containers on it. So to reduce the hardware consumes, I have been using ubuntu-server. By the way I tried the link but it didn't work. There are many explanations like it but they don't work. I think this linux thing is not standart. All explanations have different ways and none of them work.

---

### Post by ghoulie on 2022-08-15
Finallyyyyyyyyy !!!! :popcorn:

[https://www.linuxfordevices.com/tutorials/ubuntu/connect-wifi-terminal-command-line](https://www.linuxfordevices.com/tutorials/ubuntu/connect-wifi-terminal-command-line)

this link works. I connected to wifi with the wifi dongle :D Thank you [COLOR=#000000]morrownr :D[/COLOR]

---

### Post by morrownr on 2022-08-15
You are welcome. You taught me a thing or two. I did not know that Network Manager was installed in Ubuntu server.

A couple of things to keep in mind as you press forward:

The two lines below are using commands that have been depreciated and are subject to removal so learning them is a waste of time:

> $ iwconfig

> $ sudo ifconfig wlan0 up

Recomment you go with nmcli, ip and iw.

Be careful with the numerous guides that are out there. Seek out the most recent guide that is available for your specific issue if possible. Things change over time and there are many 10-20-30 year old guides for various things that are just not useful anymore.

Good luck

---

### Post by ghoulie on 2022-08-15
> **morrownr said:**
> You are welcome. You taught me a thing or two. I did not know that Network Manager was installed in Ubuntu server.

A couple of things to keep in mind as you press forward:

The two lines below are using commands that have been depreciated and are subject to removal so learning them is a waste of time:

> $ iwconfig

> $ sudo ifconfig wlan0 up

Recomment you go with nmcli, ip and iw.

Be careful with the numerous guides that are out there. Seek out the most recent guide that is available for your specific issue if possible. Things change over time and there are many 10-20-30 year old guides for various things that are just not useful anymore.

Good luck

You are right. My situation was a little urgent for me. Normally I don't give up untill deep searches. I spent 5 days to find out the solution. But from now I begin to work from 0 to .... for learning linux systems and distributions. Thanks again. :)

---

