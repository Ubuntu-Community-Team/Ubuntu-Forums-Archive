---
title: "ndiswrapper upgrade on Feisty AMD64 for gaining more stability --&gt; startup problems"
date: 2007-07-25
forum: Networking &amp; Wireless
---

### Post by beneedict on 2007-07-25
When I upgraded my ndiswrapper module (remove ndiswrapper.ko, install ndiswrapper-1.47 manually), do all the
```
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```
everything works fine. BUT, soon thereafter I get this during startups:
```
[   53.920611]  [<ffffffff8846ee47>] :ndiswrapper:win2lin2+0xe/0x11
[   53.920670]  [<ffffffff88465018>] :ndiswrapper:IofCompleteRequest+0x48/0x160
[   53.920712]  [<ffffffff8846aa07>] :ndiswrapper:miniport_init+0xa7/0x190
[   53.920738]  [<ffffffff88465b40>] :ndiswrapper:IoSyncForwardIrp+0x90/0xd0
[   53.920769]  [<ffffffff8846ab9b>] :ndiswrapper:NdisDispatchPnp+0xab/0xcb0
[   53.920819]  [<ffffffff88464d7b>] :ndiswrapper:IoInitializeIrp+0x3b/0x70
[   53.920851]  [<ffffffff8846ee47>] :ndiswrapper:win2lin2+0xe/0x11
[   53.920878]  [<ffffffff8846472b>] :ndiswrapper:IofCallDriver+0x8b/0xc0
[   53.920904]  [<ffffffff88464700>] :ndiswrapper:IofCallDriver+0x60/0xc0
[   53.920930]  [<ffffffff8846556f>] :ndiswrapper:IoBuildSynchronousFsdRequest+0x2f/0x50
[   53.920957]  [<ffffffff88466c2c>] :ndiswrapper:IoSendIrpTopDev+0xac/0x100
[   53.920993]  [<ffffffff88466f1f>] :ndiswrapper:pnp_start_device+0x4f/0xb0
[   53.921028]  [<ffffffff8846718b>] :ndiswrapper:wrap_pnp_start_device+0x20b/0x250
[   53.921063]  [<ffffffff88467220>] :ndiswrapper:wrap_pnp_start_pci_device+0x50/0x60
[   53.921161]  [<ffffffff8845b41c>] :ndiswrapper:loader_init+0x15c/0x250
[   53.921180]  [<ffffffff8806d07e>] :ndiswrapper:wrapper_init+0x7e/0xb6
```

and I have to push "ctrl+alt+del" to go on with the bootup process!

Do you have any ideas how to fix this? I would prefer going on with the updated ndiswrapper since the bcm43xx has limited range and the ndiswrapper version (1.38 ) provided in Feisty eventually causes random crashes (had some mayself)!

THX in advance!
Benedikt

---

