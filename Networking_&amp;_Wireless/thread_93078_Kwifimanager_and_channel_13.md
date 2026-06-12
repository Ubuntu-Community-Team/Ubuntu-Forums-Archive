---
title: "Kwifimanager and channel 13"
date: 2005-11-21
forum: Networking &amp; Wireless
---

### Post by Loggy on 2005-11-21
When I set up my Dell Inspiron 6000 recently, it found the wifi card loaded it and connected OK.  I am using channel 13 and yesterday I installed quite a lot of other software - not AFAIK upgrading kwifimanager or any configuration but mainly from the DVD.

Now I can set the card with iwconfig to any channel 1-11 but not 12 or 13.  So no internet:(.  

I have a number of other machines on channel 13 so I would rather not move the access point.  I know in some systems channels>11 are commented out but that is one reason why I want to use channel 13 - most of my neighbours - who all have wireless - are using lower channel numbers...

Can anyone advise - a) what could have happened and b) how to reset the card.  Should I reinstall something?  Edit a config file?  Commit suicide?

TIA

---

### Post by Loggy on 2005-11-21
A life is saved!

I checked using Syaptic all the packages that I installed yesterday for the string wifi and uninstalled the linux-restricted-modules for i386 and PPro/Celeron/PII/PIII/PIV and it didn't work.  But when I rebooted, the wireless came up.

Can anyone explain that?  I checked the modules loaded and in fact none of the restricted modules were loaded at all.

Very funny (peculiar that is!).:p

---

### Post by Loggy on 2005-11-21
A life is saved!

I checked using Synaptic all the packages that I installed yesterday for the string wifi and uninstalled the linux-restricted-modules for i386 and PPro/Celeron/PII/PIII/PIV and it didn't work.  But when I rebooted, the wireless came up.

Can anyone explain that?  I checked the modules loaded and in fact none of the restricted modules were loaded at all.

Very funny (peculiar that is!).:p

---

