---
title: "wireless connection"
date: 2007-05-14
forum: Networking &amp; Wireless
---

### Post by ep3w on 2007-05-14
I have a dell M65 with the 1390 wireless card.  I just got back from college and my wireless was working fine there.  I got home and now I can't get it to connect to my home network.  I am new to ubuntu and manually setting up wireless connections.  Any ideas?

---

### Post by kilroy423 on 2007-05-14
can you please post more information ie: iwconfig and your router/wifi card

GL,

dan

---

### Post by jlsheehan on 2007-05-14
> **ep3w said:**
> I have a dell M65 with the 1390 wireless card.  I just got back from college and my wireless was working fine there.  I got home and now I can't get it to connect to my home network.  I am new to ubuntu and manually setting up wireless connections.  Any ideas?

Hi,

I am assuming that you are:
[LIST=1]
[*]Using the gnome network manager to manage your connections
[*]Your network card was automatically detected and working fine
[*]This is the first time you have tried to connect at home
[/LIST]

Then the answer is probably that you have to left click on the network manager icon in the notification area and force it to connect to your home network the first time.  Subsequent times it will connect automatically but not the first.

Jeff

---

### Post by ep3w on 2007-05-14
Its a dell wireless1390 card.  Here is what I get for iwconfig:
lo     no wireless extensions
eth0     no wireless extensions
eth1     IEEEE 802.11g ESSID:"maas"
            mode:managed      frequency: 2.437 GHz  Access Point: 00:11:95:39:20:49
            Bit Rate=36 Mb/s  Tx-power:32 dBm
            RTS thr=2347 B Fragment thr=2346 B
            Power management:off
           Link Quality:32/100  Signal Level:-75dBm Noise level:-96dBm
           Rx invalid nwid:0    Rx invalid crypt:0  Rx invalid frag:0
           tx excessive retries:0 invalid misc:0 missed beacon:0

it is a D-link 802.11g/2.4ghz  DI-524 router.  The wireless works fine when i boot with windows.

---

### Post by ep3w on 2007-05-14
> **jlsheehan said:**
> Hi,

I am assuming that you are:
[LIST=1]
[*]Using the gnome network manager to manage your connections
[*]Your network card was automatically detected and working fine
[*]This is the first time you have tried to connect at home
[/LIST]

Then the answer is probably that you have to left click on the network manager icon in the notification area and force it to connect to your home network the first time.  Subsequent times it will connect automatically but not the first.

Jeff

i am using the manager that came with feisty.  my card was working fine with wireless at school.  this is the first time connecting here and I have tried clicking it and telling it to connect.  it attempts for a while then quits.

---

### Post by kilroy423 on 2007-05-14
If your wifi networks name is maas, then it appears that you are connected to it...do you have any kind of security enabled on the router?  You might also try to ping the router at 192.168.0.1 if that doesnt work then try 192.168.1.2 or 192.168.1.1 if you can successfully reach the router then it is a router config problem and not your Ubuntu.

GL,

dan

---

### Post by jlsheehan on 2007-05-14
> **ep3w said:**
> i am using the manager that came with feisty.  my card was working fine with wireless at school.  this is the first time connecting here and I have tried clicking it and telling it to connect.  it attempts for a while then quits.

Ok, can you investigate the settings on your windows setup and make sure they are identical to your Ubuntu settings?

Meaning: static or dynamic IP, any wireless security key, dns settings etc?

Jeff

---

### Post by ep3w on 2007-05-14
> **jlsheehan said:**
> Ok, can you investigate the settings on your windows setup and make sure they are identical to your Ubuntu settings?

Meaning: static or dynamic IP, any wireless security key, dns settings etc?

Jeff

how do i check/change my ubuntu settings? i should be able to handle the windows part...

---

### Post by ep3w on 2007-05-14
in windows it is set to dynamic IP and auto get DNS server. there is no password on the network.

---

### Post by jlsheehan on 2007-05-15
> **ep3w said:**
> in windows it is set to dynamic IP and auto get DNS server. there is no password on the network.

So what image do you have in the notification area?  Is it the blue steps showing connection strength (meaning you are connected) or a picture of network computers with a red cross (meaning you are not connected)?

I have read of other people having problems with Linux machines and DHCP from the Dlink 524, perhaps google might be helpful?

Since you can confirm your wireless network works elsewhere the router seems suspect as Kilroy has said, even though it works under windows.

Jeff

---

### Post by ep3w on 2007-05-15
its the little computers with the red x.  i will look into problems with the router then. thanks!

---

