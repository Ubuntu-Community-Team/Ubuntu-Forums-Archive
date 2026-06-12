---
title: "Update Mgr - New kernel installed"
date: 2010-04-29
forum: New to Ubuntu
---

### Post by jamere on 2010-04-29
Hi all,

Just received an Update Mgr notification that a new kernel (2.6.31-21) and security update was available. I installed the update and a 'restart' was called for and done. The new kernel didn't show up in boot menu. How do I get the NEW kernel to show up in the boot menu and how do I get OLD kernels removed? I did a 'sudo update-grub'. I'm on Karmic 9.10.

Thanks much for any suggestions.

---

### Post by Jon Monreal on 2010-04-29
When you do the sudo update-grub, you'll need to select "Install package maintainers version".

---

### Post by jamere on 2010-04-29
Jon, thanks for the reply.

> When you do the sudo update-grub, you'll need to select "Install package maintainers version". 

I did a 'sudo update-grub' in terminal and there was no option to select. Also checked man pages and didn't see options. :confused:

Thanks for any further explanation.

---

### Post by cuberts on 2010-04-29
> **jamere said:**
> Hi all,

Just received an Update Mgr notification that a new kernel (2.6.31-21) and security update was available. I installed the update and a 'restart' was called for and done. The new kernel didn't show up in boot menu. How do I get the NEW kernel to show up in the boot menu and how do I get OLD kernels removed? I did a 'sudo update-grub'. I'm on Karmic 9.10.

Thanks much for any suggestions.to get the old kernel removed, when you are at the GRUB menu, you press the key it tells you to to edit the kernels or whatever. I am not on Ubuntu right now so it is hard to explain. I dont know why the new kernel is not showing up, so try to reinstall it, and if that doesnt work then please tell me then.

---

### Post by Jon Monreal on 2010-04-29
It's likely [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/202009"). You can find a fix on that page.

If you need further assistance, please feel free to ask.

---

### Post by Miljet on 2010-04-29
That is a really OLD bug report. Especially considering that GRUB doesn't even use menu.lst file anymore.

---

### Post by Jon Monreal on 2010-04-29
> **Miljet said:**
> That is a really OLD bug report. Especially considering that GRUB doesn't even use menu.lst file anymore.

It's really not that old, and it still applies. Remember that Grub2 wasn't used until Karmic. If you upgrade from Jaunty to Karmic (and then even to Lucid) you'll still be using the old Grub and not Grub2 *unless you [upgrade it yourself]("https://wiki.ubuntu.com/Grub2#Installing%20%28Ubuntu%209.10%20and%20newer%29")*. Therefore, this bug can apply through to Karmic (and even Lucid).

@jamere: Did you update to Karmic from Jaunty (or another older version)? If so, did you upgrade to Grub2 or are you still using an older version?

Thanks.

EDIT: It would appear that at least one person in the comments had experienced similar problems with updating Grub2.

---

### Post by jamere on 2010-04-29
Thanks for the replies guys.

> @jamere: Did you update to Karmic from Jaunty (or another older version)? If so, did you upgrade to Grub2 or are you still using an older version?

I Installed 9.10 from ISO. Pretty sure I'm on GRUB2. (I think it says so at the top of the boot menu). I also have an Acer Aspire One netbook dual booting with Win Xp if that has any relevance.

Thanks for your interest in this problem.

---

### Post by Jon Monreal on 2010-04-29
I would first try reinstalling the latest kernel in Synaptic.

If that doesn't work, then [recovering Grub using the LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") might be your best bet.

---

### Post by jamere on 2010-04-30
Jon, thanks again for the info. Will try to install the new kernel in Synaptic. FWIW, my grub menu displays "GNU GRUB version 1.97 ~beta4". The menu lists the following kernels:

2.6.31-14,16,17,19,20 (currently booting 20)

-21 (newest kernel doesn't show in list)
-14,16,17 (were uninstalled in Synaptic weeks ago)

Don't know what the deal is, but new stuff isn't being added to the menu and old stuff isn't being removed. Rather than take a chance on upsetting the status quo, I'll just install 10.4 in a few weeks and that should take care of the listing problem for a while anyway.

Hopefully GRUB2 can be re-designed with a better UI. Not being overly critical here, but this kind of glitch can be a real stumbling block for new and old users alike.

---

### Post by Jon Monreal on 2010-04-30
> **jamere said:**
> I'll just install 10.4 in a few weeks and that should take care of the listing problem for a while anyway.

Hopefully GRUB2 can be re-designed with a better UI. Not being overly critical here, but this kind of glitch can be a real stumbling block for new and old users alike.

Sounds like a fairly good idea; if it doesn't work, I would try recovering Grub.

I don't think that you're being overly critical. It would be interesting to know the root cause, though (if the configuration simply isn't updating or what). [Filing a bug report]("https://bugs.launchpad.net/ubuntu/+source/grub2") might be a good idea.

---

