---
title: "Bluetooth not working anymore"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by elektronaut on 2007-02-27
Hi,

I haven't been using the bluetooth connection in a while, but now I wanted to synch my Palm again. As both JPilot and the Palm showed no progress during the synchronization - no handshake, nothing - I decided to pair my computer and the Palm again. So I deleted the computer in the 'Trusted Device' list on my Palm and tried to pair them again. As I'm using Edgy, the PIN is not stored on the computer, but can supposedly be chosen first on the Palm, then on the computer after calling ```
sudo passkey-agent --default /usr/bin/bluez-pin
```But this doesn't work here, I just get an empty line in the terminal after this command, and that's it. 'hcitool scan' shows the Palm. In /var/log/syslog I find this: 
```
Default passkey agent (:1.15, /org/bluez/passkey_agent_27146) unregistered
```

Any advice welcome.


[EDIT: Problem solved. I noticed you still need a ```
passkey "12345"
```line in /etc/hcid.conf. I commented that out while troubleshooting, so at least I could pair again. But synching still doesn't work.]

---

