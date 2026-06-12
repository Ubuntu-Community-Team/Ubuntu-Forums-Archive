---
title: "Boot into windows from Ubuntu on exit automatically."
date: 2009-09-11
forum: New to Ubuntu
---

### Post by powel212 on 2009-09-11
Wouldn't it be nice if I never had to boot into windows? I am sure the day will soon come.

But, I was thinking until that day comes wouldn't it be nice if we could have an additional choice under the "restart" button that said "reboot into windows" 

Then on shutdown Ubuntu sent a signal to Grub telling it to select windows from the grub list on reboot.

Just a thought. It would be nice to do the same thing from within windows, "reboot into Ubuntu"

Well, in a perfect world...

Powel

---

### Post by RealG187 on 2009-09-11
You could select Windows as default.

I wonder if there would be a way to send grub commands like that or script it.

---

### Post by talsemgeest on 2009-09-11
> **powel212 said:**
> Wouldn't it be nice if I never had to boot into windows? I am sure the day will soon come.

But, I was thinking until that day comes wouldn't it be nice if we could have an additional choice under the "restart" button that said "reboot into windows" 

Then on shutdown Ubuntu sent a signal to Grub telling it to select windows from the grub list on reboot.

Just a thought. It would be nice to do the same thing from within windows, "reboot into Ubuntu"

Well, in a perfect world...

Powel
I know this works for vista, but I am not so sure about XP.

First, download [EasyBCD]("http://neosmart.net/dl.php?id=1"), install it and go to the utilities tab. Click the button to install iReboot. iReboot puts an icon in the system tray, allowing you to click reboot into Ubuntu.

---

### Post by freak42 on 2009-09-11
you actually can do that with a script called grub reboot

just count the lines on your grub screen before booting down to your windows line (first entry is 1) including separator lines and let's say windows is on line 5 then enter

sudo grub-reboot 5
on the command line

I am not sure what happens afterwards if you issue a reboot in windows (wheter it reboots again line 5 or goes back to your default, because I messed around with savedefaults and stuff and I don't know what the normal behaviour is (My bet's on it boots in your default settings again)

HTH!

---

### Post by talsemgeest on 2009-09-11
> **freak42 said:**
> you actually can do that with a script called grub reboot

just count the lines on your grub screen before booting down to your windows line (first entry is 1) including separator lines and let's say windows is on line 5 then enter

sudo grub-reboot 5
on the command line

I am not sure what happens afterwards if you issue a reboot in windows (wheter it reboots again line 5 or goes back to your default, because I messed around with savedefaults and stuff and I don't know what the normal behaviour is (My bet's on it boots in your default settings again)

HTH!
Shouldn't Ubuntu already be the default though?

---

### Post by freak42 on 2009-09-11
> **talsemgeest said:**
> Shouldn't Ubuntu already be the default though?

well.. there are different setups, you can enable savedefaults, so grub defaults to the last booted entry, I just don't know if grub-reboot only changes settings for one boot or if it actually also changes the default entry, for instance if you have save-default enabled if the switching done by grub-reboot also makes the default switch over to windows, so if you reboot, windows will be selected or not.

---

### Post by talsemgeest on 2009-09-11
> **freak42 said:**
> well.. there are different setups, you can enable savedefaults, so grub defaults to the last booted entry, I just don't know if grub-reboot only changes settings for one boot or if it actually also changes the default entry, for instance if you have save-default enabled if the switching done by grub-reboot also makes the default switch over to windows, so if you reboot, windows will be selected or not.
Ok, but the other thing is: why use a script? All you have to do is open the menu.lst and change the number next to "default".

---

### Post by powel212 on 2009-09-11
> sudo grub-reboot 5

Awesome

> download EasyBCD

Awesome

Thanks guys

P.

---

### Post by muteXe on 2009-09-11
> **powel212 said:**
> 
wouldn't it be nice if we could have an additional choice under the "restart" button that said "reboot into windows" 


No.

---

### Post by talsemgeest on 2009-09-11
> **muteXe said:**
> No.
Or yes. Also, feel free to elaborate on your post, it isn't a very persuasive argument.

---

