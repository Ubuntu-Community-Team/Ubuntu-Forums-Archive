---
title: "Linux on my router"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by Pro-reason on 2008-10-21
Since my ADSL router (DLINK DSL-504T) has an IP address just like the computers on my LAN, I decided to ssh into it, on a whim.

```

ssh admin@router

```

It worked!  And what's more, once I was in, I could see that it runs Linux!

```

# ls *                                     
var.tar                                    

bin:
ash       chown     echo      ln        mv        sh        true
busybox   cp        false     login     ping      sleep     umount
cat       date      grep      ls        ps        sync            
chgrp     dd        hostname  mkdir     pwd       tar             
chmod     df        kill      mount     rm        touch           

dev:
console   kmem      mtdblock  ppp       random    tts
cua       led       netlink   ptmx      root      tty
full      log       null      pts       shm       urandom
klog      mem       port      pty       ticfg     zero   

etc:
config.xml      fstab           led.conf        services
config_ori.bin  gateways        linux-igd       shadow  
dhcp-fwd.cfg    group           passwd          shells  
dproxy.conf     host.conf       ppp             strings.xml
dropbear        hosts           progdefs.xml    sysdef.xml 
firewall_start  init.d          protocols       udhcpc     
firewall_stop   inittab         resolv.conf     udhcpd.conf
flush_firewall  iproute2        securetty       versions   

lib:
ld-uClibc-0.9.19.so   libdl.so.0            libtomcrypt.so.1.0.0
ld-uClibc.so.0        libm-0.9.19.so        libtommath.so       
libatm.so             libm.so.0             libtommath.so.1     
libatm.so.1           libnsl-0.9.19.so      libtommath.so.1.0.0
libatm.so.1.0.0       libnsl.so.0           libuClibc-0.9.19.so
libc.so.0             libpppoatm.so         libutil-0.9.19.so
libcm.so              libpppoe.so           libutil.so.0
libcmexpat.so         libpthread-0.9.19.so  libz.so
libcmexpat.so.0       libpthread.so.0       libz.so.1
libcmz.so             libresolv-0.9.19.so   libz.so.1.1.3
libcrypt-0.9.19.so    libresolv.so.0        modules
libcrypt.so.0         libtomcrypt.so
libdl-0.9.19.so       libtomcrypt.so.1

proc:
1            513          656          driver       loadavg      stat
2            523          657          execdomains  locks        swaps
244          575          671          filesystems  meminfo      sys
28           6            7            fs           misc         sysvipc
29           619          avalanche    interrupts   modules      ticfg
3            621          bus          iomem        mounts       tty
31           635          cmdline      ioports      mtd          uptime
37           639          cpuinfo      kcore        net          version
4            641          crypto       kmsg         partitions
5            646          devices      ksyms        self
512          647          dma          led_mod      slabinfo

sbin:
arp         ifconfig    ip          ledcfg      reboot      tc
dproxy      init        iptables    lsmod       rmmod       utelnetd
flashwrite  insmod      ledapp      modprobe    route

usr:
bin    lib    sbin   share  www

var:
cache     flash     lib       log       run       upgrader
dev       html      lock      proc      tmp       var

```

Any idea of what hacking fun I can have with this?

Surely this is all open-source, but I don't see any mention of open-source on the DLINK website.  Don't they have to make the source code available along with the firmware binaries that they offer on the site?

---

### Post by sonofusion82 on 2008-10-21
yes, many/most home routers are based on linux. while some manufacturer are more willing/helpful to comply with open source/GPL requirements, some don't.

i m not sure how much you can do with your factory firmware, but if your router is support by one of those custom/homebrew firmwares like [tomato]("http://www.polarcloud.com/tomato"), [dd-wrt]("http://www.dd-wrt.com/") or [openwrt]("http://openwrt.org/"), then you might have a lot of fun with it.

---

### Post by Pro-reason on 2008-10-21
The tomato site is down, dd-wrt doesn't support the DSL-504T, and openwrt seems to be for WiFi.

Oh well, never mind.  I'll restrict myself to being able to reboot it without having to go and pull its plug.

---

