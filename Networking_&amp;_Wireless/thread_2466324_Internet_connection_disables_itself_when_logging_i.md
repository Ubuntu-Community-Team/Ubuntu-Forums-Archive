---
title: "Internet connection disables itself when logging in and out of user profiles"
date: 2021-08-25
forum: Networking &amp; Wireless
---

### Post by unsyvylyzzd on 2021-08-25
I'm on a Lenovo G50 laptop:
> Linux 4.15.0-154-generic #161-Ubuntu SMP Fri Jul 30 13:04:17 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
> No LSB modules are available. 
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.5 LTS 
Release:    18.04
Codename:   bionic 

I have three user profiles set up on the machine. Only two are ever used. One (the administrator, myself) stays logged in usually, and uses the "switch user" command to return to the main login screen. Another profile, which is given most, but not administrator, privileges, logs in and out most of the time, and sometimes switches out.

During periods when only I switched in and out, things worked as needed. When both parties logged or switched in and out, after a few days it always happened that I logged in to find the internet connection lost. On the indicator panel in my toolbar, there's a button for viewing and editing connections. When it was viewed, the "Enable WiFi" option was unchecked, and grayed-out so it couldn't be re-checked. The Wi-Fi was of course working fine, and neither I nor the other manually did anything with any connection options (on this computer, Wi-Fi is left on always). I found the only way to settle the issue was a restart. This was annoying, but I did it for a time because I couldn't then be bothered to look into it.

Lately, I tried to settle the issue by connecting the laptop directly to Ethernet, just to see if it would change things. But in a few days it happened again, in the same way: this time, the "Wired connection 1" option under "Ethernet Network" was disabled and grayed-out.

And now I appeal to you, dear friends...

---

### Post by not-published on 2021-08-25
Users may not have the same provider, may not use the same devices, may not be ALLOWED to see the same VPN, and then there's power savings turning things off which it should.

And it should auto re-connect - I don't see where you've said it hasn't - so you don't have a question to answer.

*What you have is a properly working system.*

So.  you will have to "customize / kinda damage" your Ubunto: disable (gnome wifi managing widget), connect the wifi manually by shell scripting, and use more scripting to make sure it auto-reconnects if disconnected for some other reason other than log-out, and make sure gnome apps get notified if the connection changes (which you might not be able to do!)

Or just leave it the way it is like you would an iPhone :)

---

### Post by unsyvylyzzd on 2021-08-26
> **not-published said:**
> Users may not have the same provider, may not use the same devices, may not be ALLOWED to see the same VPN, and then there's power savings turning things off which it should.

And it should auto re-connect - I don't see where you've said it hasn't - so you don't have a question to answer.

*What you have is a properly working system.*

So.  you will have to "customize / kinda damage" your Ubunto: disable (gnome wifi managing widget), connect the wifi manually by shell scripting, and use more scripting to make sure it auto-reconnects if disconnected for some other reason other than log-out, and make sure gnome apps get notified if the connection changes (which you might not be able to do!)

Or just leave it the way it is like you would an iPhone :)

Thanks for your answer. There are a few things that I need to clarify.

All users have the same internet provider; they're on the same computer, and that computer is now connected to one ethernet cable, which is connected to one modem; all use the same device (the aforementioned computer); no VPN is used on this device; no power savings are activeted ever, as this laptop is always plugged to an outlet.

When the problem takes place, the internet *does not auto re-connect* and *does not let me manually reconnect*.

That being said, I don't know anything about shell scripting. I was hoping someone here could give me a specific fix based on my system specs...

---

