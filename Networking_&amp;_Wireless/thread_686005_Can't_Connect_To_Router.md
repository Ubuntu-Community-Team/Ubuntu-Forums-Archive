---
title: "Can't Connect To Router"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by Istrancis on 2008-02-02
Hi all!

I was wondering if you could help me with a little problem I'm having. I've been trying to connect a rather old Pentium III machine running an older Ubuntu distro (5.10, I think) to my Netopia 3347NWG router, via ethernet cable, without any success. It's not just that I can't access the web, I can even reach the router  itself! I've checked to ensure that all cables are correctly in place, but alas this did not yield any results. Any help that anyone here could offer me would be great.

Thanks in advance!!!

---

### Post by pytheas22 on 2008-02-02
What kind of ethernet card do you have?  You can find out with the lspci command.

Also, can you plug your computer into an ethernet cable coming directly from your modem, not the router, and have it work?  Or, can you get a connection by connecting to your router or modem via a USB cable, if available?

Also, what is the output of

```
ifconfig
```

at least in general (I realize that you can't copy and paste it easily, so just describe it general--in particular, is there an entry for "eth0"?)

---

### Post by Istrancis on 2008-02-03
I'm actually not sure what type my ethernet card is, Pytheas, but I'll use the lspci command and check it out.

Unfortunately I can't get any connection at all from the modem, but thanks for the suggestion.

I'll check out what my ethernet card is and what the feedback for ifconfig is and I'll post back when I've got results. Thanks!

---

### Post by stream303 on 2008-02-05
> **Istrancis said:**
> It's not just that I can't access the web, I can even reach the router  itself!

Make sure that you aren't using the same address for router and computer.  Been there. :)

Had to manually change my computer address so I could get into a router that had been used for testing..

---

### Post by Istrancis on 2008-02-08
```

conor@The-Old-PC:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82810E DC-133 GMCH [Graphics Memory Controller Hub]
(rev 03)
0000:00:01.0 VGA compatible controller: Intel Corp. 82810E DC-133 CGC [Chipset Graphics
Controller] (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corp. 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corp. 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corp. 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801AA Ac'97 Audio (rev 02)
_0000:01:09.0 Ethernet controller: Accton Technology Corporation SMC2-1211TX (rev 10)_

conor@The-Old-PC:~$ ifconfig
lo       Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU: 16436 Metric 1
          RX packets: 1972 errors:0 dropped:0 overruns:0 frame:0
          TX packets: 1972 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes: 165296 (161.4 KiB) TX bytes:165296 (161.4 KiB)

```

There, I hope that helps you guys to help me. I've underlined the part I think is important.

Thanks for the tip there, Stream, I'll check for that.

---

### Post by pytheas22 on 2008-02-11
try running these commands:
```

sudo modprobe 8139too
sudo ifconfig eth0 up
```

Network Manager should connect then.

If this works, you can make the fix permanent by typing

sudo gedit /etc/modules

and adding the line "8139too.ko" to the end of the file that pops up, and saving it.

If it doesn't work, run the command "ifconfig -a" again, after doing the modprobe command, and post the output.

EDIT: I remembered that you also mentioned in your first post that you're using Ubuntu 5.10.  I suspect that the reason your card isn't being recognized is just because your system is so out of date.  According to the Internet, your ethernet card should have support built into the kernel and should "just work" in modern versions of Linux (the steps above would just verify that the driver was properly engaged, but they won't do anything if your system is so old that it doesn't have the driver).  You could try compiling the driver yourself--if the commands I listed above don't work and you really want to do that, I can tell you how--but a much better solution would be to just download the latest version of Ubuntu, Gutsy 7.10, (or get it on CD if you don't have access to high-speed Internet), and everything will probably work.  Unless you have a compelling reason to be using 5.10, you should upgrade, and a lot of things will be easier.

---

