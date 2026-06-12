---
title: "Laptop as WiFi Repeater"
date: 2021-04-02
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2021-04-02
I have a Toshiba Satellite running Ubuntu 18:04 LTS

Experimenting with trying to get a reasonable wifi signal in part of my garden without resorting to ethernet I tried plugging an Edimax USB adapter into laptop which gave me two wifi connections.

Individually each wifi gave me my expected speed when checked with speedtest-cli  - the onboard gave me 32mbps download and the USB adapter gave me 28mbps which is within expectations for my set up.

I used iptables to forward each adapter to each other and all seemed to work except download speed extremely low, checked twice I got 0.55mbps and 0.60mbps though upload, whilst slower did fare a lot better showing 2.75mbps and 4.31mbps

Obviously original speedtest-cli done directly on laptop whereas subsequent speedtest done via netpad using speedtest app.

Now appreciate wifi repeaters can halve speed due to receiving and transmitting same signal but on laptop I am using two different wifi devices so expected a reasonable speed.

Is my theory wrong on this or are two wifi devices on same computer an issue?

Geoff

---

