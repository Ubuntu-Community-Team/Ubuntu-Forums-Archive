---
title: "dmesg errors, no symptoms"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by &lt;mike&gt; on 2010-09-19
Hi.
I've got a couple of odd messages coming up when I run dmesg.
Should I be concerned?

There's a tv card which uses the bttv ( bt878 ) driver. It works fine (though it takes a long time - almost a minute and a half - to load the driver) but I see the following in dmesg:
```
[    9.058992] EXT3 FS on sda1, internal journal
[   37.970021] bt878: gave up waiting for init of module bttv.
[   37.970026] bt878: Unknown symbol bttv_read_gpio
[   67.970014] bt878: gave up waiting for init of module bttv.
[   67.970017] bt878: Unknown symbol bttv_write_gpio
[   97.970015] bt878: gave up waiting for init of module bttv.
[   97.970017] bt878: Unknown symbol bttv_gpio_enable
[   98.043955] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
```


ALSA runs fine, but dmesg shows the following:
```
[  104.411625] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[  104.411629] saa7134_alsa: Unknown symbol snd_ctl_add
[  104.411710] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[  104.411712] saa7134_alsa: Unknown symbol snd_pcm_new
[  104.411868] saa7134_alsa: disagrees about version of symbol snd_card_register
[  104.411869] saa7134_alsa: Unknown symbol snd_card_register
[  104.412025] saa7134_alsa: disagrees about version of symbol snd_card_free
[  104.412027] saa7134_alsa: Unknown symbol snd_card_free
[  104.412176] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[  104.412178] saa7134_alsa: Unknown symbol snd_pcm_stop
[  104.412343] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[  104.412345] saa7134_alsa: Unknown symbol snd_ctl_new1
[  104.412796] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[  104.412798] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[  104.413036] saa7134_alsa: disagrees about version of symbol snd_ctl_notify
[  104.413038] saa7134_alsa: Unknown symbol snd_ctl_notify
[  104.413113] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[  104.413115] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[  104.413350] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  104.413352] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[  104.413698] saa7134_alsa: disagrees about version of symbol snd_card_create
[  104.413699] saa7134_alsa: Unknown symbol snd_card_create
[  104.413773] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[  104.413774] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[  104.413848] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[  104.413850] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step
[  104.520017] tda1004x: setting up plls for 48MHz sampling clock
[  106.490020] tda1004x: found firmware revision 23 -- ok
[  107.382594] saa7134_alsa: disagrees about version of symbol snd_ctl_add
[  107.382599] saa7134_alsa: Unknown symbol snd_ctl_add
[  107.382680] saa7134_alsa: disagrees about version of symbol snd_pcm_new
[  107.382682] saa7134_alsa: Unknown symbol snd_pcm_new
[  107.382838] saa7134_alsa: disagrees about version of symbol snd_card_register
[  107.382840] saa7134_alsa: Unknown symbol snd_card_register
[  107.382995] saa7134_alsa: disagrees about version of symbol snd_card_free
[  107.382997] saa7134_alsa: Unknown symbol snd_card_free
[  107.383147] saa7134_alsa: disagrees about version of symbol snd_pcm_stop
[  107.383149] saa7134_alsa: Unknown symbol snd_pcm_stop
[  107.383315] saa7134_alsa: disagrees about version of symbol snd_ctl_new1
[  107.383317] saa7134_alsa: Unknown symbol snd_ctl_new1
[  107.383768] saa7134_alsa: disagrees about version of symbol snd_pcm_lib_ioctl
[  107.383770] saa7134_alsa: Unknown symbol snd_pcm_lib_ioctl
[  107.384009] saa7134_alsa: disagrees about version of symbol snd_ctl_notify
[  107.384011] saa7134_alsa: Unknown symbol snd_ctl_notify
[  107.384086] saa7134_alsa: disagrees about version of symbol snd_pcm_set_ops
[  107.384088] saa7134_alsa: Unknown symbol snd_pcm_set_ops
[  107.384322] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  107.384324] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_integer
[  107.384670] saa7134_alsa: disagrees about version of symbol snd_card_create
[  107.384672] saa7134_alsa: Unknown symbol snd_card_create
[  107.384745] saa7134_alsa: disagrees about version of symbol snd_pcm_period_elapsed
[  107.384747] saa7134_alsa: Unknown symbol snd_pcm_period_elapsed
[  107.384821] saa7134_alsa: disagrees about version of symbol snd_pcm_hw_constraint_step
[  107.384823] saa7134_alsa: Unknown symbol snd_pcm_hw_constraint_step

```

Should I be worried about either of these? Is there a way to get the first one to load more quickly?

Any help would be greatly appreciated,
mike

Linux monet 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:58:24 UTC 2010 x86_64 GNU/Linux

---

