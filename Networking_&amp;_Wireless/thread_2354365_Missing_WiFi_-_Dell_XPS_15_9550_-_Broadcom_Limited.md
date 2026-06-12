---
title: "Missing WiFi - Dell XPS 15 9550 - Broadcom Limited BCM43602 802.11ac"
date: 2017-03-02
forum: Networking &amp; Wireless
---

### Post by Campster on 2017-03-02
Hi

Posting here as a last resort.

2 days ago I upgraded from 16.04 to 16.10.  Something went wrong, icons went missing and my background was white, I fixed it by continuing the dist upgrade via terminal.

Everything was working for about a day, and then the next time I rebooted my computer there was no WiFi.  When I go to Settings > Network there is nothing :(

I looked around online and tried the suggestions I could find.  Enabled and disabled secure boot again, purged [FONT=courier new]bcmwl-kernel-source[/FONT], tried [FONT=courier new]firmware-b43-installer[/FONT], went back to [FONT=courier new]bcmwl-kernel-source[/FONT].

I have attached the wireless-info script results, but here are a few brief details as well

```

~ uname -r
4.8.0-39-generic
~ lspci -nn -d 14e4:
02:00.0 Network controller [0280]: Broadcom Limited BCM43602 802.11ac Wireless LAN SoC [14e4:43ba] (rev 01)
~ sudo lshw -C network
  *-network                 
       description: Network controller
       product: BCM43602 802.11ac Wireless LAN SoC
       vendor: Broadcom Limited
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:16 memory:dd800000-dd807fff memory:dd400000-dd7fffff


```

Thanks

---

### Post by chili555 on 2017-03-02
```
auto lo
iface lo inet loopback

[COLOR="#FF0000"]iface dsl-provider inet ppp
pre-up /bin/ip link set wlp2s0 up # line maintained by pppoeconf
provider dsl-provider
[/COLOR]
auto wlp2s0
iface wlp2s0 inet manual
```This is your /etc/network/interfaces file. First, do you really have DSL authentication required for wireless only and not ethernet? I suspect that you got these from some forum post and really don't require them. If you do have DSL, the *by far* better way to accomplish authentication is in the router or DSL modem.

Second, the 'iface wlp2s0 inet manual' line is meaningless. It probably should read 'static' and not manual, and then the address, gateway, SSID, password, etc. need to be declared. It isn't. I suggest that you edit the file to return it to its default state:```
auto lo
iface lo inet loopback
```Then let Network Manager do its job. If NM doesn't see your connection, then something else is wrong and putting random lines in /etc/network/interfaces isn't going to fix it.

And, as we see, something else *IS* wrong:```
[    3.050625]  [<ffffffffc1988084>] wl_module_init+0x84/0x1000 [wl]
```That type of entry in the message log usually means that there is a problem loading and initializing the module. I think it has trouble initiating because it's the wrong driver! [http://askubuntu.com/questions/884291/ubuntu-14-04-wireless-not-working-on-macbook-pro-dual-boot](http://askubuntu.com/questions/884291/ubuntu-14-04-wireless-not-working-on-macbook-pro-dual-boot)

Please try:```
sudo apt-get purge bcmwl-kernel-source
```Reboot and then:```
sudo modprobe brcmfmac
```If the wireless doesn't start immediately, let's check the log for clues (firmware?): ```
dmesg | grep brcm
```

---

### Post by Campster on 2017-03-02
Hi

Thanks so much for your help.

It's working now, sorry I was testing a bunch of different DSL accounts on my laptop, but I thought I turned it off after I was done.

Thanks thanks thanks you just made my evening!

---

