---
title: "laptop keyboard freezes after login"
date: 2011-04-01
forum: New to Ubuntu
---

### Post by kermeel on 2011-04-01
Just did a new install of 10.10 on my ancient Acer Aspire 1605lc, had a few issues to get it to complete the install process and finally prevailed only to find that after logging in (keyboard works fine for the login screen), the laptop's internal keyboard freezes up after typing 1 character, doesn't seem to matter which one. 
I've tried a few keyboard layouts, they don't seem to make any difference. 
The touchpad also seemed to cause the system to freeze up although using a usb mouse got around that - haven't tried a usb keyboard yet, I think I have an old mac one lying around, I'll try that out later. In any case I'd rather have the internal keyboard and touchpad functional than be reliant on external addons. 
Any ideas on getting this stuff working?
This isn't my main machine so I won't be heartbroken if this isn't easily fixed, I just hoped to breathe a bit of life into the old thing and make it useful.
Cheers!

---

### Post by Dutch70 on 2011-04-01
I'm thinking you've got the AGP 4x - ATI Mobility Radeon 9000 Graphics card after a google search. Have you checked for drivers? 

Try going to System>>Preferences>>Appearance, click the visual effects tab & select "none". See if that helps you to use your internal keyboard.

You may also find that Xubuntu or Lubuntu works much better on your hardware. 
[[COLOR="DarkOrange"]Recommended Minimum System Requirements[/COLOR]]("https://help.ubuntu.com/community/Installation/SystemRequirements")

You'll also find links to Xubuntu & Lubuntu there. Try them on a live cd/usb.

---

### Post by kermeel on 2011-04-01
Tried the visual effects thing, it had already defaulted to none so no progress yet, although I found that usb keyboard (it seems to work reliably) so I can at least get around for the moment. 

Might give those other distros a try, Ubuntu was just the default choice because it's what I've used (a little) in the past.

---

### Post by Dutch70 on 2011-04-01
Xubuntu & Lubuntu are very similar to Ubuntu, with a lighter desktop environment, made for older machines. Lubuntu is the lightest, but I would try Xubuntu first to see how it runs.

---

### Post by kermeel on 2011-04-02
Update:

Tried out Xubuntu 10.10 and had the same issues as with Ubuntu, erratic installer/live cd loading behaviour, and when operational it froze up pretty quickly with use of the internal keyboard and touchpad. 

On the positive side I found an old disc with a copy of Ubuntu Studio (Hardy Heron) and tried installing that with instant success. So all is not lost, although i'm now in the process of trying to get that to recognise my wireless card...

So far it seems there's something underlying in 10.10 that doesn't agree with the machine. I'll try a couple of other distros and see what happens, maybe the 10.10 Lubuntu and an older Ubuntu (10.04, 9.?). But that'll have to wait a couple of days until my isp clicks over into another billing period.

Thanks for your help so far, any further thoughts would be appreciated.

---

### Post by Dutch70 on 2011-04-02
Ahh, I loved Ubuntu Studio on Hardy. Only problem is, support for 8.04 & 9.10 ends this month. 10.04 is probably your best bet with anything in the buntu family. 

Have you checked to see if maybe you need some drivers?
I've never had to mess with them, so I don't know much about them.

---

### Post by kermeel on 2011-04-03
Yeah needed to do the ndiswrapper thing with the windows driver for my card, worked though so I'm pretty happy for the moment, and everything else appears to function well, although sooner or later I'll need to try to get my firewire audio box to work which I'm guessing may be challenging...
 
Will be giving 10.04 a try soon. Thanks

---

### Post by Dutch70 on 2011-04-03
Great, sounds like you're on the right track. Hope everything else goes well for you.

---

