---
title: "Keyring manager appears if autologin is selected?"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by randysparks on 2008-05-24
I've set Ubuntu to log into automatically on boot but now the keyring dialog box pops up asking for my password before it will give wifi the WEP password. 

Is there any way around this?

---

### Post by owenll on 2008-05-24
Try this: [http://ubuntuforums.org/showthread.php?p=2776815](http://ubuntuforums.org/showthread.php?p=2776815)

or this: [http://ubuntuforums.org/showthread.php?t=187874&highlight=key+login](http://ubuntuforums.org/showthread.php?t=187874&highlight=key+login)

---

### Post by randysparks on 2008-05-24
> **owenll said:**
> Try this: [http://ubuntuforums.org/showthread.php?p=2776815](http://ubuntuforums.org/showthread.php?p=2776815)

or this: [http://ubuntuforums.org/showthread.php?t=187874&highlight=key+login](http://ubuntuforums.org/showthread.php?t=187874&highlight=key+login)

They don't seem to work :( I'm using Ubuntu Hardy and those instructions are old. 

I found a solution which I posted at the end of the first thread:

[quote=randysparks]I have a solution that's not perfect but is mostly fuss-free. Just stop using NetworkManager. Go back to using the old network configuration tool that doesn't need PAM.

To do this, click the NetworkManager icon and select Manual Configuration. In the dialog, click Unlock and then select the Wireless Connection entry. Then double-click. Remove the check from Enable Roaming Mode and enter your wifi base station name in the Network Name box, and the password in the relevant box. Change the configuration dropdown to read Automatic Configuration (DHCP). 

Note that I had to reboot before this started working. 

This will mean that you can't wirelessly roam, of course, but if you're using a desktop computer that doesn't leave the house then it's a good solution.[/quote]

---

