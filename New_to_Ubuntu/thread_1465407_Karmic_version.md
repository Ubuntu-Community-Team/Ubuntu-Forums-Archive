---
title: "Karmic version"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by jnmjr on 2010-04-29
Hey all, I've been browsing the forums and found I may have a problem with my up-dates, at present I'm using kernel 2.6.31-17 but from what I see there have been several updates up to 2.6.31-21, I don't have any problems with -17 but I'm worried my update manager is not working properly due to not notifying me of updates, besides the kernel changes I may have missed some other important updates, any suggestions?.....THX

---

### Post by Jon Monreal on 2010-04-29
Have you tried hitting the "Check" button in the Update Manager?

Thanks.

---

### Post by zeroseven0183 on 2010-04-29
> **jnmjr said:**
> I'm worried my update manager is not working properly due to not notifying me of updates

It depends if Update Notifier is in your Startup Programs (System > Preferences). You can also check which option is set for Automatic Updates

- Install security updates without confirmation
- Download all updates in the background
- Only notify about available updates

These can be found on your Software Sources.

---

### Post by JakeLawrence on 2010-04-29
Not sure if this is the same thing Jon said, but try going into your Terminal (Applications, Accessories) and typing in ```
sudo apt-get update
```.

---

### Post by Jon Monreal on 2010-04-29
> **JakeLawrence said:**
> Not sure if this is the same thing Jon said, but try going into your Terminal (Applications, Accessories) and typing in ```
sudo apt-get update
```.

Yeah, it does the same thing, so either is fine.

Just realized that the wording of the original post is a bit ambiguous. Do you mean that updates are showing up but you aren't updating because you don't know they're there, or they simply don't show up?

---

