---
title: "New D-Link network card not working"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by MonsterDuc on 2014-02-16
Hi,
I struggled to get an older Belkin card (Realteak 8169) to work so decided to get a new one.  The new D-Link DGE-528T turns out to also be a Realtek though...  I've seen many many posts on these subjects but I've struggled to find anything that seems to fit my setup.

```
Some details:
me@hpamd:~$ uname -a
Linux hpamd 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

me@hpamd:~$ sudo lshw -C network
[sudo] password for me:
  *-network UNCLAIMED
       description: Ethernet controller
       product: DGE-528T Gigabit Ethernet Adapter
       vendor: D-Link System Inc
       physical id: a
       bus info: pci@0000:01:0a.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=64 mingnt=32
       resources: ioport:cc00(size=256) memory:fdefe000-fdefe0ff memory:fdec0000-fdedffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:9
       logical name: wlan0
       serial: 00:16:44:ac:1b:0e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rt73usb driverversion=3.11.0-15-generic firmware=1.7 ip=192.168.1.40 link=yes multicast=yes wireless=IEEE 802.11bg

me@hpamd:~$ lspci | grep -i ether
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
01:0a.0 Ethernet controller: D-Link System Inc DGE-528T Gigabit Ethernet Adapter (rev 10)

jlie@hpamd:~$ lsmod | egrep -i "real|r8"
snd_hda_codec_realtek    56448  1
snd_hda_codec         194727  2 snd_hda_codec_realtek,snd_hda_intel
snd                    73753  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

Ifconfig doesn't see the new card, only the onboard:
me@hpamd:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1f:c6:3a:59:b2
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
(skipping loopback and wireless card output)

```

Any suggestions where to go from here??

---

### Post by chili555 on 2014-02-16
We'd love to see a few additional details about the card:```
lspci -nn | grep 0200
```Thanks.

---

### Post by MonsterDuc on 2014-02-16
Of course:
me@hpamd:~/2.4.x_2.6.x/src$ lspci -nn | grep 0200
01:0a.0 Ethernet controller [0200]: D-Link System Inc DGE-528T Gigabit Ethernet Adapter [1186:4300] (rev 10)

---

### Post by chili555 on 2014-02-16
Good/bad news! It is also an r8169 card. Have you physically removed the old card or is it built-in to the motherboard? Is r8169 blacklisted by chance? I see that the card is unclaimed. Does it spring to life if you do:```
sudo modprobe r8169
```

--------

Reference:```
$ modinfo r8169 | grep 4300
alias:          pci:v0000[COLOR="#FF0000"]1186[/COLOR]d0000[COLOR="#FF0000"]4300[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*
```

---

### Post by MonsterDuc on 2014-02-16
me@hpamd:~$ sudo modinfo r8169
ERROR: modinfo: could not find module r8169

(likely removed as part of trying a solution to the old card a long time ago)

---

### Post by MonsterDuc on 2014-02-16
Reinstalling 12.04 to eliminate old mistakes...

(why is it so hard with these Realtek cards!!)

---

### Post by MonsterDuc on 2014-02-16
I was kind of hoping a reinstall didn't fix it but it did.  Up and running with the old r8169 driver, on the new card.

me@hpamd:~/Videos$ sudo lsmod | grep -i r8
r8169                  73299  0 
mii                    13981  1 r8169

Solved-ish I guess...


Now, disable all updates and enjoy for the next 3 years :)

Thanks for trying to help Chili555!

---

### Post by chili555 on 2014-02-16
I'm glad it's solved-ish. Post back if you have more trouble; we'll be happy to help.

---

