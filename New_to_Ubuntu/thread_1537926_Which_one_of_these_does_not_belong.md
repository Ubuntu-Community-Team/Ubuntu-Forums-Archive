---
title: "Which one of these does not belong?"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by bocaccio on 2010-07-24
I just added virtualbox and obviously something that I shouldn't have. I wanna ask which one needs to be deleted in the pic. I have two instances of Ubuntu in the boot screen.

---

### Post by Rubi1200 on 2010-07-24
> **bocaccio said:**
> I just added virtualbox and obviously something that I shouldn't have. I wanna ask which one needs to be deleted in the pic. I have two instances of Ubuntu in the boot screen.

Whenever there is a kernel upgrade for Ubuntu, the old versions are retained. You will see them in Synaptic and the boot menu entries. If you want, you can choose to delete the older kernels.

But, many people leave at least one older version as a sort of safety net in case an upgrade broke things that previously worked; meaning you can boot into a previous version.

And, you have to be very careful to make sure you delete the right versions and not the newest one.

Bottom line: this is normal and you do not need to be concerned.

---

### Post by ks07 on 2010-07-24
From the screenshot, I can't see anything that shouldn't be installed. I see you have two kernel versions installed, which is why you have two Ubuntu options on the GRUB screen. The more up-to-date version was probably added the last time you did an update, which coincidentally happened around the same time you installed virtualbox. So, the short answer is that nothing **needs** to be deleted, and it's probably safer to leave it how it is.

However, you can remove the extra entries in two ways.
1) Delete the older kernel version using synaptic (as long as you're sure everything is still working after the update). From your screenshot, that means removing linux-image-2.6.32-21 and linux-headers-2.6.32-21(-generic). Make sure you only delete the old 32-21 version, not the newer 32-23!

2) You could also edit your GRUB2 config to hide these extra options, but I don't know of a quick and easy change you can make to do this. There is almost certainly a how-to on these forums if you do some searching.

EDIT: A nice guide with screenshots can be seen here: [http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

---

### Post by bocaccio on 2010-07-24
> **Rubi1200 said:**
> Whenever there is a kernel upgrade for Ubuntu, the old versions are retained. You will see them in Synaptic and the boot menu entries. If you want, you can choose to delete the older kernels.

But, many people leave at least one older version as a sort of safety net in case an upgrade broke things that previously worked; meaning you can boot into a previous version.

And, you have to be very careful to make sure you delete the right versions and not the newest one.

Bottom line: this is normal and you do not need to be concerned.


So basically. "Get over it!! 2 does not matter; its somewhat of a safety feature?"

Thank you and I'll keep that in mind :)

---

### Post by Rubi1200 on 2010-07-24
> **bocaccio said:**
> So basically. "Get over it!! 2 does not matter; its somewhat of a safety feature?"

Thank you and I'll keep that in mind :)

> Get over it!!
I didn't say that.

I said you do not need to be concerned about it.

> 2 does not matter
I didn't say that either.

And, for your information, there are people who have 4 or 5 kernel versions in their boot menu.

>  its somewhat of a safety feature
You are misinterpreting/misrepresenting what I said.

I said there are people who like to keep at least one older kernel version that they can fall back on IF something went wrong with an upgrade.

ks07 already offered you a solution for getting rid of the older versions if it bothers you that much.

Have a nice day :)

---

### Post by bocaccio on 2010-07-24
> **Rubi1200 said:**
> I didn't say that.

I said you do not need to be concerned about it.


I didn't say that either.

And, for your information, there are people who have 4 or 5 kernel versions in their boot menu.


You are misinterpreting/misrepresenting what I said.

I said there are people who like to keep at least one older kernel version that they can fall back on IF something went wrong with an upgrade.

ks07 already offered you a solution for getting rid of the older versions if it bothers you that much.

Have a nice day :)


It seems that there is a miscommunication; while I did not get what you said I did understand what you said.

Thanks for the help. and you too have a nice day.

---

