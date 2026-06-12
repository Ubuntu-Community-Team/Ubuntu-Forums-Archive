---
title: "[SOLVED] Wireless gone :("
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by spice_vs on 2008-04-15
hi,
i am very much new to linux and ubunntu as well. i had my Intel Pro wireless working when i installed from CD. but then i updated the system from net. and now  the network icon does not list my wireless at all :(

I check some of the posts and found that 
`**lspci**` and `**lshw -C network**` list the wireless card but the `**ifconfig wlan0 up**` says no such device
Can anyone help me with this.

---

### Post by wieman01 on 2008-04-15
Please again post the results of:
> sudo lshw -C network
> sudo iwlist scan
> sudo cat /etc/network/interfaces
Let us know...

---

### Post by spice_vs on 2008-04-15
hi here are the outputs.

>  
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1b:38:c2:ce:2e
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.3-0 ip=10.66.79.33 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965


>  sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.



 > 
sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback



i cant see anything related to wireless in /etc/network/interfaces
help pleaaase

---

### Post by wieman01 on 2008-04-15
> iwl4965
What wireless adapter is this? Are you on 32-bit Ubuntu or 64-bit?

---

### Post by prshah on 2008-04-15
> **spice_vs said:**
> i cant see anything related to wireless in /etc/network/interfaces
help pleaaase

The output of ```
iwconfig
```  please?

> **wieman01 said:**
> What wireless adapter is this? Are you on 32-bit Ubuntu or 64-bit?

Intel offering for wireless; natively supported from 7.10 up, and prior to that, one has to download and compile the driver.

---

### Post by spice_vs on 2008-04-15
here is the output of iwconfig

>  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


so what do i do to get my wireless back ?

---

### Post by wieman01 on 2008-04-15
Did you press any button and perhaps have turned it off? Is the LED lit?

---

### Post by spice_vs on 2008-04-15
nope. the LED is on and the wireless works fine on windows. i have dual boot system.  
one thing to note is while booting the LED is on and 
at the login page its off. i have to turn it on again. i have HP laptop with touch buttons.

---

### Post by wieman01 on 2008-04-15
Turn it on, then open a terminal and do:
> sudo ifdown -v eth1
Then wait for a few seconds and do:
> sudo iwlist scan

---

### Post by prshah on 2008-04-15
> **spice_vs said:**
> 
so what do i do to get my wireless back ?

```
sudo modprobe iwl4965
iwconfig
```

If you don't get the wireless listed this time, please post the output of ```
dmesg | tail -15
```

---

### Post by petefryatt on 2008-04-15
This just happened to me, I thought I did something wrong so reinstalled ubuntu. I don't know which update does it but I lose my wireless AND my sound after updating.

---

### Post by spice_vs on 2008-04-16
> **wieman01 said:**
> Turn it on, then open a terminal and do:

Then wait for a few seconds and do :

> sudo ifdown -v eth1
[sudo] password for spice:
ifdown: interface eth1 not configured

> sudo iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

 i still don get the wireless detected

---

### Post by spice_vs on 2008-04-16
> **prshah said:**
> ```
sudo modprobe iwl4965
iwconfig
```

If you don't get the wireless listed this time, please post the output of ```
dmesg | tail -15
```

```
sudo modprobe iwl4965
spice@bettercause-lx:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

spice@bettercause-lx:~$ dmesg | tail -15
[  745.748000]  [<c015aad0>] handle_IRQ_event+0x30/0x60
[  745.748000]  [<c015c25b>] handle_fasteoi_irq+0xbb/0xf0
[  745.748000]  [<c0106b1b>] do_IRQ+0x3b/0x70
[  745.748000]  [<c013eb4b>] enqueue_hrtimer+0x6b/0x110
[  745.752000]  [<c0105223>] common_interrupt+0x23/0x30
[  745.752000]  [<f886999a>] acpi_processor_idle+0x24f/0x425 [processor]
[  745.752000]  [<f886974b>] acpi_processor_idle+0x0/0x425 [processor]
[  745.752000]  [<c0102413>] cpu_idle+0x53/0xe0
[  745.752000]  [<c03e3a85>] start_kernel+0x325/0x3b0
[  745.752000]  [<c03e31f0>] unknown_bootoption+0x0/0x260
[  745.752000]  =======================
[  745.752000] handlers:
[  745.752000] [<f8a378e0>] (yenta_interrupt+0x0/0xe0 [yenta_socket])
[  745.752000] [<f8b3bae0>] (sdhci_irq+0x0/0x550 [sdhci])
[  745.752000] Disabling IRQ #19

```
i am very new to all this. i don get any of this. :|

---

### Post by prshah on 2008-04-16
> **spice_vs said:**
> ```

[  745.752000] Disabling IRQ #19

```


BINGO! Ok not actually but guessing: My wireless is also on IRQ 19. Why is IRQ 19 being disabled? That needs some thinking... maybe you should try booting with the acpi=off parameter? (Since it looks like acpi is turning off IRQ 19).

For your reference, an extract from my "/proc/interrupts"
> ```
cat /proc/interrupts 
           CPU0       
  0:        151   IO-APIC-edge      timer
  1:       2104   IO-APIC-edge      i8042
  6:          5   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          3   IO-APIC-edge      rtc
  9:          1   IO-APIC-fasteoi   acpi
 12:      22226   IO-APIC-edge      i8042
 14:      20513   IO-APIC-edge      libata
 15:      12230   IO-APIC-edge      libata
 16:          0   IO-APIC-fasteoi   Intel ICH5
 17:     118026   IO-APIC-fasteoi   uhci_hcd:usb1, uhci_hcd:usb4, i915@pci:0000:00:02.0
 18:          0   IO-APIC-fasteoi   uhci_hcd:usb2
[color=red] 19:      32170   IO-APIC-fasteoi   uhci_hcd:usb3, wifi0[/color]
 20:          0   IO-APIC-fasteoi   ehci_hcd:usb5, eth0
NMI:          0 
LOC:     109551 
ERR:          0
MIS:          0

```

Could your please paste your "/proc/interrupts" file contents?

A further thing: I seem to be sharing a USB port with my wireless. But I am NOT using any usb devices right now. Maybe you have some conflicting USB device.. try changing any usb devices to some other free ports.

Note this is guesswork all through. Nothing here should harm or break your system, but maybe you should consider whether you would like to try this or not, since it is at your own risk.

---

### Post by spice_vs on 2008-04-16
> **prshah said:**
> BINGO! Ok not actually but guessing: My wireless is also on IRQ 19. Why is IRQ 19 being disabled? That needs some thinking... maybe you should try booting with the acpi=off parameter? (Since it looks like acpi is turning off IRQ 19).

For your reference, an extract from my "/proc/interrupts"


Could your please paste your "/proc/interrupts" file contents?

A further thing: I seem to be sharing a USB port with my wireless. But I am NOT using any usb devices right now. Maybe you have some conflicting USB device.. try changing any usb devices to some other free ports.

Note this is guesswork all through. Nothing here should harm or break your system, but maybe you should consider whether you would like to try this or not, since it is at your own risk.

alright here is the output
> 
 cat /proc/interrupts 
           CPU0       CPU1       
  0:    3003500    3353378   IO-APIC-edge      timer
  1:          9          7   IO-APIC-edge      i8042
  7:          0          0   IO-APIC-edge      parport0
  8:         22         24   IO-APIC-edge      rtc
  9:        193        181   IO-APIC-fasteoi   acpi
 12:          8          7   IO-APIC-edge      i8042
 14:     125494     124186   IO-APIC-edge      libata
 15:          0          0   IO-APIC-edge      libata
 16:    1291538     978178   IO-APIC-fasteoi   uhci_hcd:usb1, i915@pci:0000:00:02.0
 17:         60         46   IO-APIC-fasteoi   uhci_hcd:usb2, iwl4965, HDA Intel
 18:     158526     125969   IO-APIC-fasteoi   uhci_hcd:usb5, ehci_hcd:usb6, yenta
 19:      47188      52823   IO-APIC-fasteoi   yenta, sdhci:slot0
 20:      66503      58844   IO-APIC-fasteoi   uhci_hcd:usb4, eth0
 21:         28         22   IO-APIC-fasteoi   uhci_hcd:usb3, ehci_hcd:usb7, ohci1394
 22:      26723      25995   IO-APIC-fasteoi   ahci
NMI:          0          0 
LOC:    2135755    2320911 
ERR:          0
MIS:          0


And regarding the usb device query i don have any USB connected anywhere.
thanks for looking into my prob.

---

### Post by prshah on 2008-04-16
> **spice_vs said:**
> alright here is the output
```

16: 1291538 978178 IO-APIC-fasteoi uhci_hcd:usb1, i915@pci:0000:00:02.0
[color=red]17: 60 46 IO-APIC-fasteoi uhci_hcd:usb2, iwl4965, HDA Intel[/color]
18: 158526 125969 IO-APIC-fasteoi uhci_hcd:usb5, ehci_hcd:usb6, yenta

```
And regarding the usb device query i don have any USB connected anywhere.
thanks for looking into my prob.

Looking at your interrupts listing, looks like your wifi and sound are sharing an irq. That's usually OK nowadays, but still... (Earlier, a long time ago, before the brave new world of PCI, the sharing of irq's was a BAD thing...)

If your sound is _still not working_ try this:

```

sudo rmmod iwl4965
sudo rmmod snd_hda_intel
sudo modprobe iwl4965
sudo /etc/init.d/networking restart
iwconfig

```

In essence, I am removing the sound (since it's not working anyway). The first two "rmmod" commands may return an error "...not found in ..." which you can ignore. Any other errors please report. 

And if your iwconfig command now detects something, then we will crack the problem of sound.

btw, do you also have a wired connection? Just confirming. If you don't have a LAN port, then probably your wireless is setup at eth0, but not in a way that is recognized as wireless. Just covering all bases.

Finally, if nothing else works, maybe we should try another route. Do you have the Windows drivers to this wireless card? Are you dual booting?

Summary:
1) Try the above commands
2) Answer the below questions if the commands do not show a wireless network card:
  a) Do you ALSO have a LAN port?
  b) Do you have access to the windows drivers for your wireless card?

---

### Post by spice_vs on 2008-04-18
hii
i got my wireless back. thanks for all your help. i found another issue. 
I have HP compaq6910p laptop with intel centrino Duo.

The problem was i had once disabled wireless from the **HP panel** in windows and then even if i try the wireless button(the physical) in front pane of my laptop it actually didnt  activate the wireless.
 i figured out yesterday when using windows that if i enable from there then my ubuntu detects wireless and works fine..

So if any of ppl have trouble with wireless because of dual boot system then please check the settings of not just windows but also any other 3rd party software disabling the hardware.

@prshah thanks a lot dude. you really help a lot. but after all it was something else issue.
thanks once again.

---

