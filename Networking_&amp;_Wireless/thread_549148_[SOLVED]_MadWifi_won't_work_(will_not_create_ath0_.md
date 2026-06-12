---
title: "[SOLVED] MadWifi won't work (will not create ath0 interface)"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by melonenmelli on 2007-09-12
hello everyone!

im a kind of stuck right now and hope you guys can help me out!

Im trying to install MadWifi WLAN drivers for my intel 3945 device.
Im running ubuntu 7.10 gutsy on a thinkpad z61m.

the problem is, that modprobe' ing the MadWifi Module will not create any WLAN interface.

What i did:

downloaded recent MadWifi version from [http://sourceforge.net/project/showfiles.php?group_id=82936]("http://sourceforge.net/project/showfiles.php?group_id=82936")

unzipped it to
```
/usr/src/madwifi-0.9.3.2
```

then:

cd to that directory and

sudo make clean

```
sudo make clean
```

Then builded the module:

sudo make

```
alex@book:/usr/src/madwifi-0.9.3.2$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-11-generic/build SUBDIRS=/usr/src/madwifi-0.9.3.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-11-generic'
  CC [M]  /usr/src/madwifi-0.9.3.2/ath/if_ath.o
  CC [M]  /usr/src/madwifi-0.9.3.2/ath/if_ath_pci.o
  LD [M]  /usr/src/madwifi-0.9.3.2/ath/ath_pci.o
  CC [M]  /usr/src/madwifi-0.9.3.2/ath_hal/ah_os.o
  HOSTCC  /usr/src/madwifi-0.9.3.2/ath_hal/uudecode
  UUDECODE /usr/src/madwifi-0.9.3.2/ath_hal/i386-elf.hal.o
  LD [M]  /usr/src/madwifi-0.9.3.2/ath_hal/ath_hal.o
  CC [M]  /usr/src/madwifi-0.9.3.2/ath_rate/amrr/amrr.o
  LD [M]  /usr/src/madwifi-0.9.3.2/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /usr/src/madwifi-0.9.3.2/ath_rate/onoe/onoe.o
  LD [M]  /usr/src/madwifi-0.9.3.2/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /usr/src/madwifi-0.9.3.2/ath_rate/sample/sample.o
  LD [M]  /usr/src/madwifi-0.9.3.2/ath_rate/sample/ath_rate_sample.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/if_media.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_beacon.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_crypto.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_crypto_none.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_input.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_node.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_output.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_power.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_proto.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_scan.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_wireless.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_linux.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_monitor.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_rate.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_acl.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_scan_ap.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_scan_sta.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_crypto_tkip.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_crypto_wep.o
  CC [M]  /usr/src/madwifi-0.9.3.2/net80211/ieee80211_xauth.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_wep.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_tkip.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_ccmp.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_acl.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_xauth.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_scan_sta.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 13 modules
  CC      /usr/src/madwifi-0.9.3.2/ath/ath_pci.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/ath/ath_pci.ko
  CC      /usr/src/madwifi-0.9.3.2/ath_hal/ath_hal.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/ath_hal/ath_hal.ko
  CC      /usr/src/madwifi-0.9.3.2/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/ath_rate/amrr/ath_rate_amrr.ko
  CC      /usr/src/madwifi-0.9.3.2/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/ath_rate/onoe/ath_rate_onoe.ko
  CC      /usr/src/madwifi-0.9.3.2/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/ath_rate/sample/ath_rate_sample.ko
  CC      /usr/src/madwifi-0.9.3.2/net80211/wlan.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan.ko
  CC      /usr/src/madwifi-0.9.3.2/net80211/wlan_acl.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_acl.ko
  CC      /usr/src/madwifi-0.9.3.2/net80211/wlan_ccmp.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_ccmp.ko
  CC      /usr/src/madwifi-0.9.3.2/net80211/wlan_scan_ap.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_scan_ap.ko
  CC      /usr/src/madwifi-0.9.3.2/net80211/wlan_scan_sta.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_scan_sta.ko
  CC      /usr/src/madwifi-0.9.3.2/net80211/wlan_tkip.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_tkip.ko
  CC      /usr/src/madwifi-0.9.3.2/net80211/wlan_wep.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_wep.ko
  CC      /usr/src/madwifi-0.9.3.2/net80211/wlan_xauth.mod.o
  LD [M]  /usr/src/madwifi-0.9.3.2/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-11-generic'
make -C ./tools  all || exit 1
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/tools'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I..  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I..  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I..  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I..  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I..  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I..  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I..  wlanconfig.c
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/tools'
alex@book:/usr/src/madwifi-0.9.3.2$ 

```

then install:

sudo make install

```
alex@book:/usr/src/madwifi-0.9.3.2$ sudo make install
sh scripts/find-madwifi-modules.sh 2.6.22-11-generic 

WARNING:
It seems that there are modules left from previous MadWifi installations.
If you are unistalling the MadWifi modules please press "r" to remove them.
If you are installing new MadWifi modules, you should consider removing those
already installed, or else you may experience problems during operation.
Remove old modules?

[l]ist, [r]emove, [i]gnore or e[x]it (l,r,i,[x]) ? 
r
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath'
test -d //lib/modules/2.6.22-11-generic/net || mkdir -p //lib/modules/2.6.22-11-generic/net
install ath_pci.ko //lib/modules/2.6.22-11-generic/net
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_hal'
test -d //lib/modules/2.6.22-11-generic/net || mkdir -p //lib/modules/2.6.22-11-generic/net
install ath_hal.ko //lib/modules/2.6.22-11-generic/net
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_hal'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate'
for i in amrr/ onoe/ sample/; do \
                make -C $i install || exit 1; \
        done
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/amrr'
test -d //lib/modules/2.6.22-11-generic/net || mkdir -p //lib/modules/2.6.22-11-generic/net
install ath_rate_amrr.ko //lib/modules/2.6.22-11-generic/net
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/amrr'
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/onoe'
test -d //lib/modules/2.6.22-11-generic/net || mkdir -p //lib/modules/2.6.22-11-generic/net
install ath_rate_onoe.ko //lib/modules/2.6.22-11-generic/net
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/onoe'
make[2]: Entering directory `/usr/src/madwifi-0.9.3.2/ath_rate/sample'
test -d //lib/modules/2.6.22-11-generic/net || mkdir -p //lib/modules/2.6.22-11-generic/net
install ath_rate_sample.ko //lib/modules/2.6.22-11-generic/net
make[2]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate/sample'
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/ath_rate'
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/net80211'
test -d //lib/modules/2.6.22-11-generic/net || mkdir -p //lib/modules/2.6.22-11-generic/net
for i in wlan.o wlan_wep.o wlan_tkip.o wlan_ccmp.o wlan_acl.o wlan_xauth.o wlan_scan_sta.o wlan_scan_ap.o; do \
                f=`basename $i .o`; \
                install $f.ko //lib/modules/2.6.22-11-generic/net; \
        done
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/net80211'
(export KMODPATH=/lib/modules/2.6.22-11-generic/net; /sbin/depmod -ae 2.6.22-11-generic)
make -C ./tools  install || exit 1
make[1]: Entering directory `/usr/src/madwifi-0.9.3.2/tools'
install -d /usr/local/bin
for i in athstats 80211stats athkey athchans athctrl athdebug 80211debug wlanconfig; do \
                install $i /usr/local/bin/$i; \
                strip /usr/local/bin/$i; \
        done
install -d /usr/local/man/man8
install -m 0644 man/*.8 /usr/local/man/man8
make[1]: Leaving directory `/usr/src/madwifi-0.9.3.2/tools'
alex@book:/usr/src/madwifi-0.9.3.2$ 
```

then load the module:

sudo modprobe ath_pci

```
alex@book:/usr/src/madwifi-0.9.3.2$ sudo modprobe ath_pci

```

From what i've read WLAN should work from this point on.
Only think to do now is to edit "/etc/modules" to autoload MadWifi Modules.

But unfortunately i still got no WLAN devie:


```
alex@book:/usr/src/madwifi-0.9.3.2$ ifconfig
eth0      Protokoll:Ethernet  Hardware Adresse 00:16:36:CF:A2:CE  
          inet Adresse:192.168.0.122  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6 Adresse: fe80::216:36ff:fecf:a2ce/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21155 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:51283441 (48.9 MB)  TX bytes:1889947 (1.8 MB)
          Interrupt:16 

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:1800 (1.7 KB)  TX bytes:1800 (1.7 KB)

```

```
alex@book:/usr/src/madwifi-0.9.3.2$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

```

```
alex@book:/usr/src/madwifi-0.9.3.2$ iwpriv
lo        no private ioctls.

eth0      no private ioctls.

irda0     no private ioctls.

```

```
alex@book:/usr/src/madwifi-0.9.3.2$ lsmod | grep ath
ath_pci                98080  0 
wlan                  205892  1 ath_pci
ath_hal               192720  1 ath_pci

```

does anyone have an idea what i did wrong?

any comment appreciated!

Thanks in adance!

---

### Post by spd106 on 2007-09-12
I think you got your wires crossed somewhere, Madwifi doesn't support Intel cards only Atheros ones. You probably want the ipw3945 driver.

The Restricted Drivers Manager should sort out the wireless card driver for you.

---

### Post by melonenmelli on 2007-09-13
alright....

thats embarrassing indeed :oops::oops:

you are right, madwifi is just the wrong driver for my hardware.

i cannot use the restrictred driver module due to my custom kernel.

i looked in the description of this module and there is only madwifi mentioned.

thatswhy i thought madwifi should be the right driver.

nerver mind, topic solved, i think ;)

---

### Post by Hakachukai on 2008-03-12
I have exactly the same problem... but I actually DO have an Atheros card. I followed the same procedure exactly.

The modules: ath_pci, ath_hal and wlan are all loaded

but I never get any wlan0 or ath0 interface. it just does nothing.

My card is an Atheros 5006EG

I can't find any conflicting drivers, I don't even have any Ndis drivers loaded



any Ideas?

---

