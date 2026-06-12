---
title: "problems with hibernation..."
date: 2009-06-26
forum: New to Ubuntu
---

### Post by heyyy on 2009-06-26
my pc,on its way to hibernation,gives the following messages:
> [6010.147991] ipw2200: Unable to load ucode: -22
[...        ] ipw2200: Unable to load firmware: -22
[...        ] ipw2200: Failed to up devise

except that  everything else seems to work fine
some help?

---

### Post by porchrat on 2009-06-26
> **heyyy said:**
> my pc,on its way to hibernation,gives the following messages:


except that  everything else seems to work fine
some help?

Does it actually go into hibernate fine?

ipw2200 looks like your wireless module, it fails to load firmware and then can't bring the device up as a result. Does this happen when you make it hibernate or when you bring it out?

I'm not 100% sure, but I don't think you intel PRO/Wireless wifi module should be affecting your ability to hibernate

---

### Post by heyyy on 2009-06-26
> **porchrat said:**
> Does it actually go into hibernate fine?

ipw2200 looks like your wireless module, it fails to load firmware and then can't bring the device up as a result. Does this happen when you make it hibernate or when you bring it out?

I'm not 100% sure, but I don't think you intel PRO/Wireless wifi module should be affecting your ability to hibernate

i think the hibernation does work despite the messages (although they are a bit annoying) which appear when i make it to hibernate.
when i bring it out everything seems to work fine
as for my wireless it seems to fine too but usually is turned off

---

### Post by porchrat on 2009-06-26
I actually went and looked up the ipw2200 on ubuntu 9.04 and the some people do update the firmware as it causes issues on some systems.

See [this]("http://ubuntuforums.org/showthread.php?t=1117522") link for an example.

However if it is all working I would recommend that you put up with the error rather than risk breaking something by updating the firmware. Remember that firmware is a little more serious than standard drivers.

---

### Post by heyyy on 2009-06-26
> **porchrat said:**
> I actually went and looked up the ipw2200 on ubuntu 9.04 and the some people do update the firmware as it causes issues on some systems.

See [this]("http://ubuntuforums.org/showthread.php?t=1117522") link for an example.

However if it is all working I would recommend that you put up with the error rather than risk breaking something by updating the firmware. Remember that firmware is a little more serious than standard drivers.

thanks i'll probably leave it the way it is

---

