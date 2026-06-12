---
title: "zyxel (zydas) g-120 pcmcia wifi card"
date: 2007-07-24
forum: Networking &amp; Wireless
---

### Post by michalon on 2007-07-24
Hi there,

I've just bought IBM ThinkPad T41 and installed Ubuntu 7.04. Everything went perfect. Then I got Zyxel G-120 wifi pcmcia card and it doesn't work. I've googled all the days and found russian instructions exactly for the same card. I don't speak russian but as my friend told me: follow the commands.

Just check [http://zyxel.ru/content/support/knowledgebase/KB-1573]("http://zyxel.ru/content/support/knowledgebase/KB-1573"). There is also link to zyxel driver. I can send it to you if you are not able to get it.

And now the problem.

After lspci command, it outputs correctly:```
Network controller: ZyDAS Technology Corp. Unknown device 2116 (rev 01)
```

Then I unziped the driver package, also correctly.

The problem occurred after "make menuconfig" (or "sudo make menuconfig"):
```
chmod a+x scripts/lxdialog/lxdialog
/bin/sh scripts/Menuconfig
Menuconfig requires bash
make: *** [menuconfig] Error 1

```

Also "make install" or "sudo make install" leads to some problems:
```
echo -e -I/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/include -fomit-frame-pointer -O -Wall -Wstrict-prototypes -pipe -Wno-unused -DAMAC -DGCCK -DOFDM -DTXQ_IN_ISR -DHOSTAPD_SUPPORT -DLOGO_ENABLE=1 -DfTX_PWR_CTRL -DZDCONF_CHIP1212_16=1 -DZDCONF_CHIP1212_ONLY=0 -DZDCONF_CHIP1212_ONLY=0 -DZDCONF_80211H_SUPPORT=1 -DZDCONF_80211E_SUPPORT=1 -DZDCONF_WDS_SUPPORT=1 -DZDCONF_VAP_SUPPORT=1 -DZDCONF_LP_SUPPORT=1 -DZDCONF_BANDEDGE_ADJUST -DZD_DEBUG -DZDCONF_GF_MTU_CONF -DZDCONF_GF_HWADDR_CONF -DX86_EMBEDDED -DZDCONF_EXTRA_FIX_IPC -DZDCONF_PROC_FS_SUPPORT -DZDCONF_INFRA_SUPPORT -DZDCONF_WE_STAT_SUPPORT -DZDCONF_WE_PRIV_SUPPORT -DZDCONF_SW_RETRY -DZDCONF_SW_ADAPTION -DZDCONF_ADHOC_SUPPORT -DZDCONF_MENUDBG -DZDCONF_APDBG -DZDCONF_AP_SUPPORT -DZDCONF_80211A_SUPPORT -DZDCONF_PRINTK -DPRODUCTION -DZDCONF_WIN_PROD_IFACE -DZDCONF_RF_UW2453_SUPPORT -DZDCONF_RF_AL2230_SUPPORT -DZDCONF_RF_AL2232_SUPPORT -DZDCONF_RF_AL7230B_SUPPORT -DZDCONF_CHIP1212_ONLY=0 -DZDCONF_CHIP1216_ONLY=0
-I/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/include -fomit-frame-pointer -O -Wall -Wstrict-prototypes -pipe -Wno-unused -DAMAC -DGCCK -DOFDM -DTXQ_IN_ISR -DHOSTAPD_SUPPORT -DLOGO_ENABLE=1 -DfTX_PWR_CTRL -DZDCONF_CHIP1212_16=1 -DZDCONF_CHIP1212_ONLY=0 -DZDCONF_CHIP1212_ONLY=0 -DZDCONF_80211H_SUPPORT=1 -DZDCONF_80211E_SUPPORT=1 -DZDCONF_WDS_SUPPORT=1 -DZDCONF_VAP_SUPPORT=1 -DZDCONF_LP_SUPPORT=1 -DZDCONF_BANDEDGE_ADJUST -DZD_DEBUG -DZDCONF_GF_MTU_CONF -DZDCONF_GF_HWADDR_CONF -DX86_EMBEDDED -DZDCONF_EXTRA_FIX_IPC -DZDCONF_PROC_FS_SUPPORT -DZDCONF_INFRA_SUPPORT -DZDCONF_WE_STAT_SUPPORT -DZDCONF_WE_PRIV_SUPPORT -DZDCONF_SW_RETRY -DZDCONF_SW_ADAPTION -DZDCONF_ADHOC_SUPPORT -DZDCONF_MENUDBG -DZDCONF_APDBG -DZDCONF_AP_SUPPORT -DZDCONF_80211A_SUPPORT -DZDCONF_PRINTK -DPRODUCTION -DZDCONF_WIN_PROD_IFACE -DZDCONF_RF_UW2453_SUPPORT -DZDCONF_RF_AL2230_SUPPORT -DZDCONF_RF_AL2232_SUPPORT -DZDCONF_RF_AL7230B_SUPPORT -DZDCONF_CHIP1212_ONLY=0 -DZDCONF_CHIP1216_ONLY=0
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.o
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:32:26: error: linux/config.h: No such file or directory
In file included from /home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.h:39,
                 from /home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdeeprom.h:3,
                 from /home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:36:
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdapi.h:458:5: warning: "fTX_GAIN_OFDM" is not defined
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:975:5: warning: "fANT_DIVERSITY" is not defined
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:980:5: warning: "fWRITE_WORD_REG" is not defined
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:998:5: warning: "fTX_GAIN_OFDM" is not defined
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c: In function ‘zd1212_open’:
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:1371: warning: passing argument 2 of ‘clear_bit’ from incompatible pointer type
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:1439: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c: In function ‘zd1212_pci_setup’:
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:2625: warning: format ‘%lX’ expects type ‘long unsigned int’, but argument 3 has type ‘resource_size_t’
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:3179:42: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c: In function ‘zd1212_found1’:
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:3179: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:3179: error: (Each undeclared identifier is reported only once
/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:3179: error: for each function it appears in.)
make[2]: *** [/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0/src/zdmain.o] Error 1
make[1]: *** [_module_/home/ms/zyxel/ZD1212LnxDrv_2_15_0_0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [all] Error 2

```

Ok. That's it. Is there any generous soul which is able to help me a bit? Thanks! If there is any other possibilities to make this card running, please tell me :) (I have also tried ndiswrapper but it didn't work either...)

---

### Post by jamesbelsey on 2007-09-26
Hi,

I am in the same situation.  However the drivers seem to have disappeared from the download site.

It would be great if you could somehow send me the files.  Also how did you try the ndiswrapper?  The install disk I got with the card has the driver  contained in an exe so I can't get it out to even try it...

Thanks!

---

### Post by michalon on 2007-10-09
Please try this driver: [http://www.divno.cz/temp/G-120LinuxDriver.zip](http://www.divno.cz/temp/G-120LinuxDriver.zip)

I have found somewhere inf and sys files for WXP and Wvista but it doesn't work, ubuntu just freezes during the start...

please let me know if there is any news about Zyxel G-120 driver and running it under ubuntu...

thanks

---

### Post by elggarc on 2007-10-28
Hi There,

I am having similar problems, but I'm one step ahead of michalon.

```
error: linux/config.h: No such file or directory
```

I found this on another forum:
> linux/config.h is deprecated from kernel 2.6.19.
Simply sed or patch out any references to linux/config.h with linux/autoconf.h

I replaced config.h with autoconf.h in zdmain.c and retried the make.

That resulted in this:

```

make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-386'
  CC [M]  /a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.o
In file included from /a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.h:39,
                 from /a folder/ZD1212LnxDrv_2_15_0_0/src/zdeeprom.h:3,
                 from /a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:36:
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdapi.h:458:5: warning: "fTX_GAIN_OFDM" is not defined
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:975:5: warning: "fANT_DIVERSITY" is not defined
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:980:5: warning: "fWRITE_WORD_REG" is not defined
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:998:5: warning: "fTX_GAIN_OFDM" is not defined
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c: In function ‘zd1212_open’:
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:1371: warning: passing argument 2 of ‘clear_bit’ from incompatible pointer type
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:1439: warning: ‘deprecated_irq_flag’ is deprecated (declared at include/linux/interrupt.h:66)
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:1439: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c: In function ‘zd1212_pci_setup’:
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:2625: warning: format ‘%lX’ expects type ‘long unsigned int’, but argument 3 has type ‘resource_size_t’
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:3179:42: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c: In function ‘zd1212_found1’:
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:3179: error: ‘INIT_WORK’ undeclared (first use in this function)
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:3179: error: (Each undeclared identifier is reported only once
/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.c:3179: error: for each function it appears in.)
make[2]: *** [/a folder/ZD1212LnxDrv_2_15_0_0/src/zdmain.o] Error 1
make[1]: *** [_module_/a folder/ZD1212LnxDrv_2_15_0_0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-386'
make: *** [all] Error 2

```

I also get the "Menuconfig requires bash" error.

Anyone got any further with this?

C :confused:

---

### Post by elggarc on 2007-10-28
BTW

Note for those with time on their hands,

Altavista have a (poor) Russian to English translation service here:
[http://babelfish.altavista.com/tr](http://babelfish.altavista.com/tr)

It might help things along?

When I've got a moment, I'll try it out.

C

---

### Post by elggarc on 2007-11-03
Additional note.

I've found I couldn't get Menuconfig to work  until I installed the essential build stuff.  Install it with this command:

```
apt-get install build-essential
```

Also, I've translated the Russian instructions and attached them.  MS Word format I'm afraid, but OO seems to read it just fine.  The translation is dreadful, but you get the gist.

Finally, I've been looking at the zd1211 (as opposed to the zd1212 from this post) and I've found older versions of the driver, intended for kernel versions 2.6.19 and earlier, result in very similar error messages to those we've seen for zd1212.  I guess, therefore, that the zd1212 v2.15 driver is also intended for kernel 2.6.19 or earlier.

The zd1211 driver has an unsupported patch ([click here]("http://dsd.object4.net/zd1211-vendor/UNSUPPORTED-patches/")) which updates the driver code for use with kernel 2.6.20

This is now defunct as the zd1211 driver was included as part of recent kernels (certainly it is in 2.6.23 because I'm using it :) ), but I think it might be possible to use the patch as a template for doing the same thing with the zd1212 driver code.

Any thoughts?

Is anyone still reading this?;)

---

### Post by michalon on 2007-11-21
> **elggarc said:**
> 
Is anyone still reading this?;)

I am still reading it.. :) but no clear solution yet :(....

---

