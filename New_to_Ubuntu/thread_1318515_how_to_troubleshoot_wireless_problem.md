---
title: "how to troubleshoot wireless problem"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by mcshore on 2009-11-07
I recently purchased a System76 netbook running Ubuntu and the wireless has been working great. The other night I left it running updates when I went to bed and the next day the wireless was not working. I've confirmed that it is not my access point as I'm connected to it via my old Windows laptop. I suspect it is something in the update that caused the problem but, being a newbie to ubuntu, don't have a clue how to troubleshoot the problem or the updates to find out what was updated and if it's possible to roll them back. I've looked through the Ubuntu pocket reference guide I picked up but it's not providing anything helpful. What are things I can do to troubleshoot the wireless? And how do I get info about the updates that were made and if it's possible to uninstall them?

Thanks.

---

### Post by lkraemer on 2009-11-07
You most likely downloaded a kernel update that killed your wifi.
Just select a previous kernel from the grub ment and it should 
boot and come up working.

To find what Wifi you have open a Terminal window and do:
```

lspci -vvnn
lshw -C network
iwconfig

```

lk

---

