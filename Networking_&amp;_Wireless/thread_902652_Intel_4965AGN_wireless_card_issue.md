---
title: "Intel 4965AGN wireless card issue"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by epilogue on 2008-08-27
Hi everyone,

I have been looking for a solution for nearly half an hour and here i'm having my last chance. 

I have HP Pav DV5-1040et notebook that has intel4965 wireless card. The driver for my card is out of box with new kernel but my ubuntu does not recognise it. 

here a part of my lspci results

```
01:00.0 VGA compatible controller: GeForce 8800 GT 512 GeForce 9600M GT (rev a1)
02:00.0 Network controller: Intel Corporation Unknown device 4237
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. Unknown device 2380
06:00.1 System peripheral: JMicron Technologies, Inc. Unknown device 2382
06:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381
06:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383
06:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384
```

i read somewhere that i should use command "sudo modprobe iwl4965" but it did not work. it gives no output, error or any reaction like that, simply get downs to a new line.

i want to use my ubuntu as my first os and i have to solve this problem. So i would be glad if you can help me.

---

### Post by soxs on 2008-08-27
Iam quite intrested in this aswell, I read some threads about... but I couldn't conclude anything usefull (except thet ndiswrapper doesn't allow big data volume downloads)

---

### Post by epilogue on 2008-08-27
looks like hopeless :/

---

### Post by soxs on 2008-08-27
> **epilogue said:**
> looks like hopeless :/

For many it seems to work out of the box...

---

### Post by jruden on 2008-08-28
Same problem here, but with dv5-1095eo (another laptop in same series with same wireless wifi, Intel 4965). I have been searching for a solution part time a couple of days now...

It seems that the kernel module is not loaded on boot and I think it is normal that the "sudo modprobe iwl4965" command doesn't give any feedback. Instead look in syslog (you can follow it in another terminal with tail -f /var/log/syslog. For me, 2 lines are printed there about the intel iwl4965 being loaded.

The kernel module loads fine and lshw -C network shows one unclamimed intel interface, but no wlan0, nothing appears in network manager applet, etc.

According to compliance matrices this wifi controller should be fully supported.

Help please someone!

---

### Post by Crafty Kisses on 2008-08-28
Look at this link > [http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller](http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller)

---

### Post by jruden on 2008-08-28
> **Codename said:**
> Look at this link > [http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller](http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller)

Thank you but that link is for 7.04 and 7.10. I don't know about epilogue but in my case I am using 8.04. 8.04 has kernel 2.6.24 which already contains the drivers.

Please epilogue, confirm if this is the case, don't wanna steal your thread!

This is why I am lost on how to proceed! It seems that the drivers are in there but the actual device never gets created/activated. Doing lshw -C network lists the device as UNCLAIMED. What does that mean?

And the sympthom is that both before and after modprobe iwl4965 iwconfig lists only:
```

lo        no wireless extensions.
eth0      no wireless extensions.

```

The strange thing is that modprobe only gives 2 lines:

```

iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
iwl4965: Copyright(c) 2003-2007 Intel Corporation

```

From what I have seen in other outputs on the internet lines like:
```

iwl4965: Detected Intel Wireless WiFi Link 4965AGN

```
should also be present...but is NOT for me.

Seems the driver DOES NOT recognize the controller!

lspci shows for wireless controller:
```

02:00.0 Network controller: Intel Corporation Unknown device 4237

```

Now....I am starting to think that our controller is TOO new and is not yet supported simply to the fact that this one reports as "4237". modinfo iwl4965 give only these two lines for alias:

```

alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*

```

This seems to indicate that the current driver shipped with latest hardy can ONLY handle 4230 and 4229. And we both have 4237! :-(

Maybe the driver still works and can be told to work with 4237?

Help!

---

### Post by epilogue on 2008-08-28
Jruden we have exactly same problems(so you are not stealing :)).

You got a point there. So looks like we have to wait for a driver update?

---

### Post by jruden on 2008-08-28
Now...I have also tested a little with ndiswrapper as some people seem to think this is the universal workaround for wifi. However I run into the problem that ndiswrapper fails with the current driver that Intel offers (version 12 with .inf-file called NETw5x32.INF).

Some people with 4965s with device ids other than 4237 seem to have had success by using the older driver (11.5) which is also available on Intels download center in previous releases section. Problem with this one is that ndiswrapper doesn't handle it properly. NOT EVEN the latest ndiswrapper at the moment (1.53) available from ndiswrappers web page which you have to compile yourself can handle the latest Intel Pro wireless 4965 driver for 32-bit windows xp!

So for the time being it seems we are stuck with wired networking! :-(

Help!

---

### Post by soxs on 2008-08-28
I dislike ndiswrapper, never worked as it was supposed to. The drivers are simply notmade for linux...

Did anybody try to run 8.10 alpha? Maybe the new kernel got the driver update? (Recent 2.6.25-2.6.27 kernels got _A_ _LOT_ wlan drivers, though I don't know for what exact chips...)

---

### Post by urk_nono on 2008-08-28
I guess we will have to wait for the new kernel. I even rang HP support centre, but they didn't have anyone with linux experience. They even told me they weren't allowed to give support on another OS than Vista, which came with my dv5-1095 laptop.

---

### Post by jruden on 2008-08-29
> **soxs said:**
> 
Did anybody try to run 8.10 alpha? Maybe the new kernel got the driver update? (Recent 2.6.25-2.6.27 kernels got _A_ _LOT_ wlan drivers, though I don't know for what exact chips...)

I couldn't resist so i installed 8.10 alpha 4. At first it uses kernel "2.6.26-5-generic" and things seem to work no better, but after upgrading a few times (sudo apt-get upgrade and rebooting) things start to come alive with the "2.6.27-1-generic" kernel. Now I see a wlan0! :-)

First problem I run into now seem to be that the wifi controller behaves as shut off. I see the following in dmesg and wifi indicator on laptop still goes red:

[   28.711642] iwlagn: Radio disabled by HW RF Kill switch

Would be nice to get this wifi going so we could have a play with it in wait for beta/RC/final release. (this alpha seem a little shaky on my laptop at least).

Here is some more output from dmesg (unrelated lines cut were away):
```

[   13.108486] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   13.108486] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   13.112005] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.112005] iwlagn 0000:02:00.0: setting latency timer to 64
[   13.112005] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   13.140004] iwlagn: Tunable channels: 13 802.11bg, 24 802.11a channels
[   13.188004] iwlagn 0000:02:00.0: PCI INT A disabled
[   13.204003] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   28.476103] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   28.476369] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   28.480517] firmware: requesting iwlwifi-5000-1.ucode
[   28.711642] iwlagn: Radio disabled by HW RF Kill switch
[   28.797873] NET: Registered protocol family 17
[   43.098499] NET: Registered protocol family 10
[   43.104383] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

And here is the output of modinfo iwlagn (seems to replace iwl4965):
```

filename:       /lib/modules/2.6.27-1-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2008 Intel Corporation
version:        1.3.27ks
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
srcversion:     AB700033C5A9D44F30AB15E
alias:          pci:v00008086d0000423Asv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd*bc*sc*i*
alias:          pci:v00008086d00004236sv*sd*bc*sc*i*
alias:          pci:v00008086d00004235sv*sd*bc*sc*i*
alias:          pci:v00008086d00004232sv*sd*bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,cfg80211,mac80211
vermagic:       2.6.27-1-generic SMP mod_unload modversions 586
parm:           disable50:manually disable the 50XX radio (default 0 [radio on]) (int)
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           debug50:50XX debug output mask (int)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           qos_enable50:enable all 50XX QoS functionality (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)

```

So, this "Radio disabled by HW RF Kill switch" seems to be the problem that stops from getting it working :-(

---

### Post by jruden on 2008-08-29
Adding some more information...

According to a googled source out there

([http://article.gmane.org/gmane.linux.drivers.ipw3945.devel/3398](http://article.gmane.org/gmane.linux.drivers.ipw3945.devel/3398))

iwlagn is indeed the iwl4965 module renamed and with support for intel 5000 added in it. I am starting ot suspect that the problem I see on intrebid is due to that my 4965 is falsely detected as a 5xxx series card. The dmesg output listed in previous post seem to hint about it:
```

[   13.112005] iwlagn: Detected Intel Wireless WiFi Link 5100AGN REV=0x54

```

So maybe the kernel module iwlagn used in alpha 4 (with current upgrade) has a bug?

---

### Post by urk_nono on 2008-08-29
Keep up the good work jruden! You seem to have a good understanding on how to get this up and running. You're doing us all a favour. Thank you.

---

### Post by jruden on 2008-08-31
I haven't yet understood why the radio is off and how to control it, but one interesting thing I found is that the HP web page is faulty! The specs for my laptop (both at the web shop that sold it and HP's own web pages) said I have a Intel 4965. This is wrong. I do in fact have a 5100 in my pavilion. I suspect that this is also the case for epilogue. I think this also explains why very recent drivers are needed to detect the card. The continues on how to bring the radio to life...

Edit: Now got it to work! For the first time wireless indicator on laptop lit up! I don't know how/why, but I have been using it in Vista on other partition so maybe it depends on how you leave it before you boot Ubuntu(?). I am still struggling a bit to get authenticated on my private WPA auth network, but using my publicly open network, it works. This is using intrepid and having then upgraded to using linux-image-2.6.27-1-generic.

Edit2: Now, with the latest (at the moment) kernel with intrepid testing it even works like a charm to join my private (WPA key) WLAN.

---

### Post by urk_nono on 2008-08-31
You're saying we should upgrade to the 8.10 alpha?

---

### Post by epilogue on 2008-08-31
Glad to hear that you made it jruden :) 

now you mean we have to wait intrepid? (or use alpha as urk_nono said)

maybe there is a way to upgrade drivers or get new drivers to hardy?

---

### Post by jruden on 2008-08-31
Best thing would of course be if we could use good ol hardy, I totally agree. For the time being though, to be honest, I am just happy that there is a solution waiting "around the corner".

I will see if I have time to investigate this more before a more stable intrepid arrives cause I agree that these alphas isn't worth going for fully yet (my humble). There is almost a full month left to beta freeze though...

[https://wiki.ubuntu.com/IntrepidReleaseSchedule](https://wiki.ubuntu.com/IntrepidReleaseSchedule)

---

### Post by soxs on 2008-09-01
> **epilogue said:**
> Glad to hear that you made it jruden :) 

now you mean we have to wait intrepid? (or use alpha as urk_nono said)

maybe there is a way to upgrade drivers or get new drivers to hardy?

Upgrade your kernel, well.. compile it yourself. Jump through the hoop...

---

### Post by urk_nono on 2008-09-01
I'm not a pro like you guys, so I'll have to wait a while :(

---

### Post by CRIMPS on 2008-09-23
I am really happy to find this thread.  I too have an Intel 4965AGN wireless card in my new laptop.  The current state is I have a newly fresh installation of Hardy Heron.  I have updated as well.  I cannot get the card to be recognized either.  Now for the interesting part.

I have had my Dell XPS 1530 for about 2 months now.  Original card was a broadcom card, which I could never get consistently working.  So I decided I would install a new card especially since I had a Wireless-N Router.  I installed the Intel card, booted, started surfing almost immediately.  Right out of the box, everything worked great.

I reinstall Hardy for unrelated reasons and now I can't get wireless to work whatsoever.

My main point is that there is a way for the card to work.  I just need to figure what I might have installed or changed when I was trying to get my Broadcom wireless card working.

Im interested to see what you are going to find JRuden.

---

### Post by jruden on 2008-09-24
> **CRIMPS said:**
> 

Im interested to see what you are going to find JRuden.

In my case the problem was that the HP site falsely proclaimed (and still proclaims) that my laptop model contains a 4965AGN. I discovered after installing hardy that it couldn't recognize the card even though the device was listed in lspci and the driver was installed and loaded. After a lot of confusion I finally came to the conclusion that my 4965 is in fact a 5100AGN.

For the 5100 to work the 2.6.27 kernel is needed. This is why I run intrepid even though it is just alpha yet (beta freeze tomorrow btw, yihaa).

In your case (as you probably have 4965 for real) I think you would get the card working easier by upgrading to intrepid but also there are some threads that cover 4965 on hardy which you can check out. Just search for "4965 hardy" on this forum.

---

