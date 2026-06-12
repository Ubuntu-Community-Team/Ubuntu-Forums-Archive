---
title: "Kernel network config"
date: 2007-03-19
forum: Networking &amp; Wireless
---

### Post by Ephilei on 2007-03-19
I'm building the driver for my wireless card and [http://madwifi.org/wiki/UserDocs/KernelConfig](http://madwifi.org/wiki/UserDocs/KernelConfig) tells me this:

> The following options should be included in your kernel for the best MadWifi experience:

Kernel 2.6.x: 

    * General setup &#8594; Configure standard kernel features (for small systems) &#8594; Sysctl support: enabled
    * Loadable module support &#8594; Module versioning support: disabled
    * Device Drivers &#8594; Network device support &#8594; Wireless LAN (non-hamradio) &#8594; Wireless LAN drivers (non-hamradio) & Wireless Extensions: enabled
    * Cryptographic options &#8594; Cryptographic API: enabled
    * Cryptographic options &#8594; Cryptographic API &#8594; HMAC support: enabled
    * Cryptographic options &#8594; Cryptographic API &#8594; AES cipher algorithm: enabled (optional, needed for WPA/WPA2 with CCMP) 

How do I set these options?

---

### Post by Thirsteh on 2007-03-19
You will need to re-compile your kernel to make any changes. There are a plethora of how to's on how to do this out there. All of these options can be set in the 'menu makeconfig' stage of setup/compiling.

Don't quote me on this, but I think all of the above is set like that by default. Are you experiencing any problems with the driver? If not, I'd say it's safe to ignore these settings.

---

### Post by Ephilei on 2007-03-19
Thanks. If it's that much work, I'll won't change these settings unless something the driver works poorly.

---

