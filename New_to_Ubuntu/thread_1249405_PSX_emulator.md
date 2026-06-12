---
title: "PSX emulator"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Falc7 on 2009-08-25
I am trying to install PSX, using this guide
[http://maketecheasier.com/guide-to-playstation-emulator-on-ubuntu/2008/03/19](http://maketecheasier.com/guide-to-playstation-emulator-on-ubuntu/2008/03/19)

However after selecting the BIOS i get these errors

I thought i should mention that since the libgtkglext.deb file linked in that guide is out of date, i downloaded the libgtkglext1 package through synaptic


```
jamie@jamie-laptop:~$ cd /home/jamie/pSX
jamie@jamie-laptop:~/pSX$ ./pSX

(pSX:8894): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:8894): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:8894): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:8894): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:8894): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:8894): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:8894): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:8894): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:8894): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:8894): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:8894): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:8894): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:8894): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:8894): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:8894): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:8894): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

```

Anyone know whats causing them?

---

