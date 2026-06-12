---
title: "Ethernet connection lagging"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by marcos4 on 2013-09-30
Hello, i have a problem.  Everytime i restart my computer, the ethernet light, in my modem, begins to blink and i can't connect to internet. Sometimes take 2 minutes to stop to blink and i can connect, but sometimes take 3 hours. It's very random. 
If i go to connection menu, in the left corner of the screen, and i tap over Enable Network, the light stop blinking, but i can't connect obviously. I think it isn't the modem or the wire, because i have perfect connection with the same wire in my playstation 3, or in another computer with windows xp. The problem begun like a month ago, but i use ubuntu 12.04 like a year ago.  

Description:
Ubuntu 12.04.3
Connection 10Mb
Modem ZyXEL P-600 series
Wire(Ethernet) Connection direct to the modem.

Sorry for my bad English and THANKS.

In spanish:
> Hola, tengo un problema con la coneccion a internet. Cada vez que reinicio mi computadora, la luz de Ethernet en mi modem comieza a parapadear y no puedo conectame a intenet. Luego de un tiempo la luz deja de parpadear y queda prendida y ahi puedo conectarme. Pero a veces tarda 3 minutos y otras 3 horas es aleatorio, o eso parece. Un dato importante cuando esta titilando, si voy a la esquina superior  derecha, donde esta el menu de conecciones y  desmarco Activar Red, la  luz deja de titilar, pero obiamente no puedo conectarme. No creo que sea el modem, o el servicio de internet o el cable, puesto que si conecto mi ps3 al modem por el mismo cable funciona perfecto y lo mismo con otra computadora que tiene windows.  Uso ubuntu hace 3 años y hace 1 aproximadamente Ubuntu 12.04, este problema comenzo hace un mes asi que no creo que sea devido a una incompatibilidad con linux.

Saludos y gracias.


---

### Post by marcos4 on 2013-10-01
I serch in others post and i saw that people post some information like "lspci -nnk | grep -iA2 net" or "lsmod"

lspci -nnk | grep -iA2 net
```
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Motherboard [1458:e000]
    Kernel driver in use: r8169
```
lsmod
```
Module                  Size  Used by
pppoe                  17772  2 
pppox                  13342  1 pppoe
nls_utf8               12557  1 
udf                    94509  1 
crc_itu_t              12707  1 udf
bnep                   18258  2 
rfcomm                 47864  0 
bluetooth             247165  10 bnep,rfcomm
nvidia               9430169  39 
usblp                  18284  0 
coretemp               13596  0 
kvm_intel             137899  0 
kvm                   455932  1 kvm_intel
binfmt_misc            17540  1 
snd_hda_codec_realtek    79916  1 
snd_hda_intel          44339  3 
snd_hda_codec         141761  2 snd_hda_codec_realtek,snd_hda_intel
ghash_clmulni_intel    13259  0 
aesni_intel            55495  0 
snd_hwdep              13668  1 snd_hda_codec
ablk_helper            13597  1 aesni_intel
snd_pcm               102477  2 snd_hda_intel,snd_hda_codec
cryptd                 20501  3 ghash_clmulni_intel,aesni_intel,ablk_helper
lrw                    13294  1 aesni_intel
snd_seq_midi           13324  0 
aes_x86_64             17255  1 aesni_intel
snd_rawmidi            30417  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
xts                    12922  1 aesni_intel
snd_seq                61930  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
gf128mul               14951  2 lrw,xts
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   287564  2 nvidia
snd                    69533  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
serio_raw              13215  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
shpchp                 37201  0 
gpio_ich               13526  0 
mac_hid                13253  0 
microcode              23017  0 
mei                    41820  0 
lpc_ich                17144  0 
ppdev                  17113  0 
parport_pc             28284  1 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
hid_generic            12540  0 
usb_storage            61749  0 
usbhid                 47346  0 
hid                   105549  2 hid_generic,usbhid
r8169                  68716  0 

```


cat /etc/NetworkManager/NetworkManager.conf
```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false
```

cat /var/lib/NetworkManager/NetworkManager.state
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

```

---

### Post by varunendra on 2013-10-02
Welcome to the forums marcos4 !

> **marcos4 said:**
> Everytime i restart my computer, the ethernet light, in my modem, begins to blink and i can't connect to internet. Sometimes take 2 minutes to stop to blink and i can connect, but sometimes take 3 hours. It's very random.

Please post back the outputs of -
```
ifconfig
sudo ethtool eth0
nm-tool
```
..when it gets connected.

And have you tried replacing the cable recently? Because the kind of behaviour you mentioned occurs usually when there is a bad contact or DHCP not working properly. As such, you may also try using a fixed IP/Gateway/DNS instead of a DHCP assigned one.

**PS:**
For posting the outputs, please use [noparse]```
..and..
```[/noparse] tags instead of the 'Quote' tags that you are using. Please follow the "Using Code Tags" link in my signature if you need to see how.

---

### Post by subhendu2 on 2013-10-02
As a hardware guy basically from the 386 and co- axial cable era , I can tell you that most problems with ethernet come from the cable and connector joints. If possible please change the connector joints on both side of the cable. 
Then go for software and OS tweaking

---

### Post by marcos4 on 2013-10-03
Hello, ant thanks for the welcome.
> For posting the outputs, please use[CODE..and../CODE tags instead of  the 'Quote' tags that you are using. Please follow the "Using Code  Tags" link in my signature if you need to see how.         
Done


> And have you tried replacing the cable recently? Because the kind of  behaviour you mentioned occurs usually when there is a bad contact or  DHCP not working properly.

> As a hardware guy basically from the 386 and co- axial cable era , I can  tell you that most problems with ethernet come from the cable and  connector joints. If possible please change the connector joints on both  side of the cable. 
Then go for software and OS tweaking         
 I tried with two tested (in my ps3) diferents cables, i think that the joint of the motherboard can be broken but if i move the cable the connection don't lose.

here is ethool :
```
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes

```
ipconfig is in the other post and nm-tool is normal.


Thanks Again.

---

### Post by varunendra on 2013-10-04
> **marcos4 said:**
> ipconfig is in the other post and nm-tool is normal.

That output of ifconfig is from when the system had no connection. I'd like to see that from when it is connected (connection light steady and it got an IP address). Output of nm-tool also from that state please.

From only the ethtool output everything looks normal to me. It also indicates that your modem port only supports upto 100 Mb/s speed. Is that correct?

And do you have a crossover cable available? We may run a test with it to possibly check if it is a loose port or loose cable problem or not (by connecting it directly to the XP machine, while manually assigning IP addresses to both machines).

---

