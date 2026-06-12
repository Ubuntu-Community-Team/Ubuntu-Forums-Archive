---
title: "Wireless has always been a hurdle..."
date: 2008-04-29
forum: Networking &amp; Wireless
---

### Post by linux_newf on 2008-04-29
I had a very hard time getting the wireless and flash to work from fedora 8, spent hours at it.

Anyhow, ubuntu has been excellent so far and once i installed the non-free drivers most things worked. But i like to make sure my wireless is working before i need to use it.

Here is what i got when i ran ```
lspci -v | less

```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b7
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: 66MHz, fast devsel

00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
        Subsystem: Hewlett-Packard Company Presario V6133CL.

Edit: Just realized there was no mention of the broadcom hardware i have. 
Question: Is broadcom and nividia the same physical unit? Are they both "physicalware"?

---

