---
title: "restore default graphics card settings"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by olderek on 2010-10-25
hi,
recently, i installed NVIDIA and when i restarted my pc, my compiz effects stopped working. when i try to change the visual effects, it tells me **Desktop effects cannot be enabled. **
 i removed the NVIDIA and still couldn't enable my desktop effects. when i check my graphics card using...

$ lspci
$ lspci -v
$ lspci -v | less

[CENTER]**the above, gives me this output...**
[/CENTER]

00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
        Subsystem: Acer Incorporated [ALI] Device 0212
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
        Memory at 80000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 50f0 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915



i want to restore to the defaults so that i can use the compiz theme effects again. somebody pliz help me go back to the default. 
pliz 
olderek

---

### Post by Verbeck on 2010-10-25
try removing the xorg.conf[B]
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.b[/B]

---

### Post by olderek on 2010-10-26
**when i do that, **


olderek@olderek:~$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.b
[sudo] password for olderek: 
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory
olderek@olderek:~$


[B]that's the output. is does this mean i have a serious problem?
[/B]

---

