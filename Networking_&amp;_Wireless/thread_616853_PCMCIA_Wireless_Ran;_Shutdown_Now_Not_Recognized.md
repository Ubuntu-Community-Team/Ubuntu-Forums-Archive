---
title: "PCMCIA Wireless Ran; Shutdown Now Not Recognized"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by kcyarn on 2007-11-18
Thus far, I love the operating system... but, I have a small problem. 

I have a DLink DWL-G650M PCMCIA card on a IBM Thinkpad T22 running Ubuntu Gutsy 7.10. I originally started out with Feisty and upgraded to Gutsy. Since this is a Thinkpad, I had change the acpi and apm settings in the boot file. After spending several frustrating hours with Madwifi (which still doesn't work and they should seriously reevaluated their instructions...), I decided to try ndiswrapper even though I have an atheros chipset. I downloaded the latest driver from dlink, installed it using ndisk, disabled all security on the router (was running WEP 128 hex and MAC filters), plugged in the card and IT WORKED!! I got online without the security enabled. Then, I uploaded my old settings (with security) to the router, changed my network configuration, and it still WORKED! 

Then, I suppose I made my first big mistake... I shut down the computer. (I am a firm believer in only working on one issue at a time, so all I altered during this time were the router settings and network configuration...). When I restarted, I had difficulty getting the card to turn on (aka no power). When I finally got power to it, nothing (including removing and reloading the driver and checking every pcmcia command and the internet config in the terminal) could make it register. So I went from a working PCMCIA card to a non-working on all in the space of about ten minutes. All system updates were made last night prior to installing the card. 

Please help!

---

