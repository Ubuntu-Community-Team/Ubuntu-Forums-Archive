---
title: "Intrepid Trying (Again) To Install Madwifi"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by N00bB00b on 2008-11-23
GAH!  I did a clean install of Intrepid on my Acer Aspire 3680.

It comes with Ahteros drivers, and it recognizes the radio, but it doesn't configure it, and despite trying to set up a network connection for it, I can't enable it.

The radio is turned on in Windoze.

I then decided to try to install madwifi, although this didn't work in Hardy due to a variety of configuration issues that were never resolved.

Anyway, here's what we have:

```

$sudu su
#*./madwifi-unload.bash*
FATAL: Module wlan is in use.

```
(although I can't seem to get the wlan running, and I must be stupid because I don't see it in ifconfig).

I then used
```

* #./find-madwifi-modules.sh $(uname -r)*
```
which seems to work

Then
```

[I]#cd ..
#make install[/I]
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/yuk/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /home/yuk/Desktop/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /home/yuk/Desktop/madwifi-0.9.4/ath_hal/uudecode
  UUDECODE /home/yuk/Desktop/madwifi-0.9.4/ath_hal/i386-elf.hal.o
  LD [M]  /home/yuk/Desktop/madwifi-0.9.4/ath_hal/ath_hal.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/ath_rate/amrr/amrr.o
  LD [M]  /home/yuk/Desktop/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/ath_rate/minstrel/minstrel.o
  LD [M]  /home/yuk/Desktop/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/ath_rate/onoe/onoe.o
  LD [M]  /home/yuk/Desktop/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/ath_rate/sample/sample.o
  LD [M]  /home/yuk/Desktop/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/net80211/if_media.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/net80211/ieee80211.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/net80211/ieee80211_beacon.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto_none.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/net80211/ieee80211_input.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/net80211/ieee80211_node.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/net80211/ieee80211_output.o
  CC [M]  /home/yuk/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o
/home/yuk/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/yuk/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/yuk/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/yuk/Desktop/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/yuk/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```

now what?

---

### Post by Olivier2371 on 2008-11-23
Which Atheros adapter are using?

---

### Post by N00bB00b on 2008-11-24
Ar5bxb63

---

### Post by kevdog on 2008-11-24
Try installing subversion and then grabbing the svn source of madwifi and try to recompile.  Make sure you have the linux-header files installed for your kernel.  You are definitely on the right track!

---

### Post by N00bB00b on 2008-11-24
I installed svn, then per [http://madwifi-project.org/ticket/2189](http://madwifi-project.org/ticket/2189) I installed that version, but make still gives

/home/yak/Desktop/madwifi-branch-0.9.4/net80211/ieee80211_linux.c: In function 'ieee80211_load_module': /home/yak/Desktop/madwifi-branch-0.9.4/net80211/ieee80211_linux.c:338: error: format not a string literal and no format arguments make[3]: *** /home/yak/Desktop/madwifi-branch-0.9.4/net80211/ieee80211_linux.o Error 1 make[2]: *** /home/yak/Desktop/madwifi-branch-0.9.4/net80211 Error 2 make[1]: *** [_module_/home/yak/Desktop/madwifi-branch-0.9.4] Error 2 make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic' make: *** [modules] Error 2


FYI, I also tried the straight 0.9.4 version, but that still doesn't work.

---

### Post by homa2142 on 2010-09-29
rostam@rostam-laptop:~/Desktop/vahid$ make install
make: *** No rule to make target `install'.  Stop.
rostam@rostam-laptop:~/Desktop/vahid$ make
make: *** No targets specified and no makefile found.  Stop.
rostam@rostam-laptop:~/Desktop/vahid$ make
make: *** No targets specified and no makefile found.  Stop.
rostam@rostam-laptop:~/Desktop/vahid$ cd madwifi-0.9.4/
rostam@rostam-laptop:~/Desktop/vahid/madwifi-0.9.4$ make install
sh scripts/find-madwifi-modules.sh 2.6.32-25-generic 
for i in ath/ ath_hal/ ath_rate/ net80211/; do \
        make -C $i install || exit 1; \
    done
make[1]: Entering directory `/home/rostam/Desktop/vahid/madwifi-0.9.4/ath'
test -d //lib/modules/2.6.32-25-generic/net || mkdir -p //lib/modules/2.6.32-25-generic/net
mkdir: cannot create directory `//lib/modules/2.6.32-25-generic/net': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/rostam/Desktop/vahid/madwifi-0.9.4/ath'
make: *** [install-modules] Error 1
my wifi card is tp link tl-wn321g

---

### Post by arjuntank on 2010-09-29
try this?
[http://ubuntuforums.org/showthread.php?t=865971]("http://ubuntuforums.org/showthread.php?t=865971")

---

