---
title: "Realtek gigabit ethernet card install - ARRGGGGHHH!!!"
date: 2008-07-13
forum: Networking &amp; Wireless
---

### Post by Jesus-Ninja on 2008-07-13
Right - I'm now very close to abandoning linux and going out to buy a copy of Windows XP...](*,)

I have a realtek gigabit ethernet card, which is running at 100mb. The only real reason for the system is to backup a NAS at gigabit speeds on a weekly basis.

I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=143982](http://ubuntuforums.org/showthread.php?t=143982) to force the system to use r1000.ko, however, it appears that r1000.ko is not present on the system.

So I downloaded the latest drivers from Realtek, and followed the instructions:

_**sudo make clean modules**_
```
make -C src/ clean
make[1]: Entering directory `/home/nick/r1000/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_version                                                                                            s Module.symvers Modules.symvers rset
make[1]: Leaving directory `/home/nick/r1000/src'
make -C src/ modules
make[1]: Entering directory `/home/nick/r1000/src'
make -C /lib/modules/2.6.24-19-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /src/r8169_n.o
/src/r8169_n.c: In function ârtl8169_init_oneâ:
/src/r8169_n.c:2432: error: implicit declaration of function âSET_MODULE_OWNERâ
make[3]: *** [/src/r8169_n.o] Error 1
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/nick/r1000/src'
make: *** [modules] Error 2

```

Of note is the line: [B]/src/r8169_n.c:2432: error: implicit declaration of function âSET_MODULE_OWNERâ
[/B]

After a morning of stress, I'm at a brick wall.

Someone help!

---

### Post by nixscripter on 2008-07-13
Could you post the surrounding few lines of code? ```
 sed -n -e '2416,2448p' <src/r8169_n.c
```

According to google those calls can often just be removed.

---

### Post by Jesus-Ninja on 2008-07-13
> **nixscripter said:**
> Could you post the surrounding few lines of code? ```
 sed -n -e '2416,2448p' <src/r8169_n.c
```

According to google those calls can often just be removed.

here you go...

```
nick@garage:~/r1000$ sed -n -e '2416,2448p' <src/r8169_n.c

        if (netif_msg_drv(&debug)) {
                printk(KERN_INFO "%s Gigabit Ethernet driver %s loaded\n",
                       MODULENAME, RTL8169_VERSION);
        }

        dev = alloc_etherdev(sizeof (*tp));
        if (!dev) {
#if LINUX_VERSION_CODE > KERNEL_VERSION(2,6,0)
                if (netif_msg_drv(&debug))
                        dev_err(&pdev->dev, "unable to alloc new ethernet\n");
#endif //LINUX_VERSION_CODE < KERNEL_VERSION(2,6,0)
                rc = -ENOMEM;
                goto out;
        }

        SET_MODULE_OWNER(dev);
        SET_NETDEV_DEV(dev, &pdev->dev);
        tp = netdev_priv(dev);
        tp->dev = dev;
        tp->msg_enable = netif_msg_init(debug.msg_enable, R8169_MSG_DEFAULT);

        /* enable device (incl. PCI PM wakeup and hotplug setup) */
        rc = pci_enable_device(pdev);
        if (rc < 0) {
#if LINUX_VERSION_CODE > KERNEL_VERSION(2,6,0)
                if (netif_msg_probe(tp))
                        dev_err(&pdev->dev, "enable failure\n");
#endif //LINUX_VERSION_CODE < KERNEL_VERSION(2,6,0)
                goto err_out_free_dev_1;
        }

        rc = pci_set_mwi(pdev);
You have new mail in /var/mail/nick
nick@garage:~/r1000$

```

---

### Post by nixscripter on 2008-07-13
Well, my non-expert advice, based upon Google's wisdom: take a deep breath, cross your fingers, and comment out the SET_MODULE_OWNER line (with // at the beginning). Any more compiler errors?

---

### Post by Jesus-Ninja on 2008-07-13
Well, that helped, and now it builds the module and installs. Doesn't fix the slow network....... :roll:

---

### Post by nixscripter on 2008-07-15
Silly question, though one which caused me to lose a lot of time in the past: you are using an ethernet cable capable of carrying 100 Mb (i.e. Cat 6), right?

---

### Post by Aurora_CA on 2008-07-22
> **nixscripter said:**
> Silly question, though one which caused me to lose a lot of time in the past: you are using an ethernet cable capable of carrying 100 Mb (i.e. Cat 6), right?

You can set the connection speed and protocol using the following:

Per the README file with the r1000 driver:
> <Force Media Speed>

 The media can be forced to one of the 5 modes as follows.

        Cmd: "insmod r1000 media = SET_MEDIA"
        For example:
         "insmod r1000 media = 0x04" will force PHY to operate in 100Mpbs Half-duplex.

         SET_MEDIA can be:
                _10_Half        = 0x01
                _10_Full        = 0x02
                _100_Half       = 0x04
                _100_Full       = 0x08
                _1000_Full      = 0x10


   Force media type for multiple cards could be performed as:

         "insmod r1000 media=0x04,0x10"

   which force PHY to operate at 100Mbps half-duplex and 1000Mbps full-duplex.

---

