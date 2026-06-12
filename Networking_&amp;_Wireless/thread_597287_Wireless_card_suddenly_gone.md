---
title: "Wireless card suddenly gone"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by tgvail on 2007-10-30
Hi--

I've been using Gusty since it's release, and it has been working fine until yesterday the wireless suddenly stopped working. I can still connect to the internet through the wired connection, but wireless is completely gone. I have it dual booted with windows, and wireless works fine on the windows side, so it's not the the hardware.

I ran lshw, and I got this part that I think is the problem

           *-network:1 UNCLAIMED
                description: Network controller
                product: PRO/Wireless 2200BG Network Connection
                vendor: Intel Corporation
                physical id: 3
                bus info: pci@0000:02:03.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                configuration: latency=64 maxlatency=24 mingnt=3

Is the "Unclaimed" part why it's not working? And how to I claim it again?

Thanks

---

### Post by Lambert on 2007-10-30
Run the following command

```

lsmod | grep ipw

```

You should see output showing ipw2200, if not run this command.

```

sudo modprobe ipw2200

```

Check again lsmod along with lshw commands.

---

