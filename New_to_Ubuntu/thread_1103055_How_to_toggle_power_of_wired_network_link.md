---
title: "How to toggle power of wired network link?"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by ThatGuyOverThere on 2009-03-22
Current Operating System: Linux computer 2.6.27-11-generic #1 SMP
                          Thu Jan 29 19:28:32 UTC 2009 x86_64

Vista x64 handles the NIC's link properly by toggling it off during sleep and during shutdown.  Ubuntu leaves it always on.  To look at the router, you'd think somebody left the machine on downstairs or it's crashed during sleep/shutdown!  Go check, and it's shut-down cold.  How can I make Ubuntu toggle the interface properly?

I'm not an expert, I just want to get this one aspect of the machine fixed so it can be ready for general users, saving a lot of wasted trips to check on things.

```

*lshw -C network*
shows the following:

       description: Ethernet interface
       product: MCP73 Ethernet
       vendor: nVidia Corporation
       physical id: f
       bus info: pci@0000:00:0f.0
       logical name: eth0
       version: a2
       serial: 00:28:38:46:b1:14
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61
       ip=192.168.0.4 latency=0 maxlatency=20 mingnt=1 module=forcedeth
       multicast=yes
```

---

### Post by ThatGuyOverThere on 2009-03-23
Additional tests have shown that the following LiveCD versions of Ubuntu:

Hardy Heron 8.04 32 bit
Hardy Heron 8.04 64 bit
Intrepid Ibex 8.10 64 bit

All leave the network link ON after shutdown, on two machines, both HP, one a laptop, the other a desktop.

All are using the forcedeth NIC driver, but I don't know if that's the cause of the problem, or if it lies elsewhere.

In addition, **Ibex LiveCD refuses to even finish shutting down the machine and eject the CD without the Internet available!**  I was using the router with no WAN connection to do the tests, and Ibex would just hang there on a black screen, flicking the link light on the router every so often.  So I got curious and decided to see if it was trying to access a resource out on the net, so I plugged in the WAN cable, and only **then** did it proceed with shutdown!

WTF????

---

### Post by brokenLockpick on 2009-03-23
I find it strange that you say Vista does something different. As far as I've seen where I work, freshly un-boxed machines will show network activity(lights) when plugged in even if they haven't been powered on scince they left the factory.

I always thought this was related to how the hardware vendors did things scince it effects computers that haven't been booted scince plugged in.

For the record, you may have found a quirk of HP branded computers. Though I've run into many desktops that appear to leave the NIC up prior to initial boot and after shutdown, I've never seen this with laptops, including Compaq, Dell, Acer, Lenovo and a few others.

I investigated when I first noticed the behavior on my home network. Even though the light for that router port is on the IP address assigned to that computer still expires as the computer is obviously not "on" enough to renew the address.

I would suggest turning off "wake on lan" and "boot from NIC" in the bios if such options are present and you never use these features.

---

### Post by ThatGuyOverThere on 2009-03-23
Hello!  I was starting to think of this as my personal blog. :)

Yes, I did check the BIOS settings.  There is no BIOS option for wake-on-lan for the HP machines.  I also disabled the "network group" boot priority options, so it's just CD & HDD.

Tried something else too:

At line 63 of Ubuntu's /etc/init.d/halt

replacing $netdown with -i doesn't work.


Experimenting with Vista has shown that setting the NIC's advanced properties parameter **[Reset PHY if not in use]** to **Enabled** allows a boot/shutdown through Vista to shut off the stuck interface!  That's the key parameter here, not the power management or wake-on-lan settings.  Even if you don't have wake-on-lan enabled in Vista, the link stays up unless that PHY parameter is set.

Hey, Vista's good for something after all!

Alas, that's not going to be a practical solution when the machine is being used by the general public.

From what I gather, the PHY is not the nForce chipset NIC for which the forcedeth driver was written, but is a device between the chipset and the ethernet port.  In the case of the HP desktop example here, that would be the Realtek [RTL8201CL]("http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PFid=13&Level=5&Conn=4&ProdID=25") PHY on the Irvine board that comes with their Intel systems.

The AMD 64x2 HP laptop I was working on earlier also had this link-state issue.  Not sure what chipset & PHY it has.  When I see it again, I'll check.

I found a very technical [thread]("http://www.mail-archive.com/netdev@vger.kernel.org/msg56592.html") from late 2007 in which this very issue is discussed.  Quite a steep learning curve for me just to get this solved.  Can one of the big-shots here chime in with some insight?

---

