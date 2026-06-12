---
title: "wireless module loading"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by s1337m on 2009-07-12
i was testing out some wireless config in 9.04.  i tried to enable the atheros madwifi driver (i have the AR5212 card) to see if that worked better than the preset driver its been using.  now, when i reboot, i have no wireless and have to enable the wireless driver in that driver menu to get wireless to work.  when i click activate on that driver it says "the driver was just disabled, but is still in use".  anyway, i think i need to put the madwifi driver in a config file somewhere so it loads on boot.  how do i do this?

---

### Post by nothingspecial on 2009-07-13
```
gksudo gedit /etc/modules
```

add ```
ath_pci
``` to the end.

You may need to blacklist the driver you are using.

---

### Post by nothingspecial on 2009-07-13
It occurs to me that ath_pci is blacklisted by default in ubuntu.

```
gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
```

right at the bottom is a line that says blaclist ath_pci.

Put a # infront of it so that it now reads

```
# For some Atheros 5K RF MACs, the madwifi driver loads buts fails to
# correctly initialize the hardware, leaving it in a state from
# which ath5k cannot recover. To prevent this condition, stop
# madwifi from loading by default. Use Jockey to select one driver
# or the other. (Ubuntu: #315056, #323830)
#blacklist ath_pci
```

---

