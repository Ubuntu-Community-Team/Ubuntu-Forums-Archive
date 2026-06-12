---
title: "Video problem after power outage"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by donclay23 on 2010-01-21
Hello,
   I'm very new to this so please excuse any major or minor mistakes I make.
 
I had a power outage for a short time time today. Of course my computer shut down and when the power came back on and I turned it on, a small window appeared which said: "Running in Low graphics mode. 
The following error was encountered. Need to update your configuration to solve this.
(EE) [drm] drm open failed
(EE) fglrx (0): DRIScreenInit Failed!"

So I pressed OK and it took me to another screen that gave me 4 options that had radio buttons. I tried the setting the default setting and that didn't work and I tried all of them except the first one which said" Run Obuntu in low graphics mode for just one session". I was now able to get into my computer and get on line. I tried a few things like going into "System" and tested a few things and then "Systemtesting" and came up with nothing.At one point during some test, the graphics all went funny and everything suddenly turned into weird colors and I had to restart to fix the colors. 

Currently I'm able to access the internet and everything looks OK, but it is not. When I log off or turn it off completely and then turn it on again, it goes through the whole thing again about the the errors and won't boot up regularly.

Can anyone help me and if so, how do I find your answer? As I said, I'm really new at this. If you want to call (480-824-3123) or email me at [email]donclay23@hotmail.com[/email], please do. I have to get this up and running well again. It's my wife's computer.

Thanks,
Don
:confused:

---

### Post by mikewhatever on 2010-01-21
It looks like the problem is related to the ATI graphics driver. You can try booting the recovery mode (usually second boot option) and selecting xfix, when done type 'reboot'. This will reconfigure your xserver, and hopefully solve the problem. If not, try disabling the driver from System->Admin->Hardware Drivers, then reboot and re-enable the driver.

---

