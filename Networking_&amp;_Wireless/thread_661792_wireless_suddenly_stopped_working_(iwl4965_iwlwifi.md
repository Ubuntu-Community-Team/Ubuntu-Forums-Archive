---
title: "wireless suddenly stopped working (iwl4965 iwlwifi)"
date: 2008-01-08
forum: Networking &amp; Wireless
---

### Post by thruxton on 2008-01-08
Hello, I have xubuntu 7.10 installed on my HP dv9000 series laptop.
I don't recall doing anything special during installation to get wireless working, it worked right out of the box. 

kernel is 66bit 2.6.22-14-generic
modules loaded are:
iwl4965                       113512  0
iwlwifi_mac80211      200456  1 iwl4965

sudo iwconfig                    
lo        no wireless extensions.

eth0      no wireless extensions.

So now all of a sudden I have no wlan0 device.
here is some dmesg output:
[ 1024.933136] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[ 1024.933518] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[ 1024.933540] PCI: Setting latency timer of device 0000:02:00.0 to 64
[ 1024.934690] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[ 1024.984961] iwl4965: Radio disabled by HW RF Kill switch

So, what is the next step? what can I do to troubleshoot this?
Thanks in advance

---

### Post by thruxton on 2008-01-08
the problem as it turned out was that there is a slide switch on the front of the laptop to turn off wireless..

[ 1024.984961] iwl4965: Radio disabled by HW RF Kill switch

as soon as I slide this over, wireless is enabled again.

---

### Post by Casual Fan on 2008-01-08
One time I declared the fax machine broken...and the phone line wasn't plugged in.

Sometimes it's the really obvious things! :lolflag:

---

### Post by thruxton on 2008-01-08
yeah, I feel foolish now, but when the problem first arises, you *always* tend to think its a software issue, without going through the basic hardware checks first :(

---

