---
title: "Ubuntu Problem"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by h8uthemost on 2010-05-07
I'm on Ubuntu 9.04. And I was trying to install an app. But this app said it needed python-gtk2 2.16 installed. Well Ubuntu only had 2.14 installed. So I uninstalled 2.14 from Synaptics. Then after that was uninstalled the 2.16 .deb wouldn't install for some reason.

So, I went ahead and reinstalled 2.14 from Synaptics. But when I restarted Ubuntu, I only get a black screen now. Grub will pop up when I turn on my computer. But when I choose Ubuntu, I only get that Ubuntu splash screen(you know, with the bar underneath it that tells you Ubuntu is starting up). Then usually the Ubuntu desktop would be the next screen I see. But after that splash screen all I get is a black screen.

Is there anyway I can recover? I plan on updating to 10.04 anyways, but there are some files I would like to get off my 9.04 first. So if someone knows of a way to recover I would really appreciate the help.

Thank you.

---

### Post by Mustard on 2010-05-07
> **h8uthemost said:**
> I'm on Ubuntu 9.04. And I was trying to install an app. But this app said it needed python-gtk2 2.16 installed. Well Ubuntu only had 2.14 installed. So I uninstalled 2.14 from Synaptics. Then after that was uninstalled the 2.16 .deb wouldn't install for some reason.

So, I went ahead and reinstalled 2.14 from Synaptics. But when I restarted Ubuntu, I only get a black screen now. Grub will pop up when I turn on my computer. But when I choose Ubuntu, I only get that Ubuntu splash screen(you know, with the bar underneath it that tells you Ubuntu is starting up). Then usually the Ubuntu desktop would be the next screen I see. But after that splash screen all I get is a black screen.

Is there anyway I can recover? I plan on updating to 10.04 anyways, but there are some files I would like to get off my 9.04 first. So if someone knows of a way to recover I would really appreciate the help.

Thank you.

Just off the top of my head I wonder whether you could go to 'recovery mode' from Grub and at the root prompt try this command

```
aptitude install ubuntu-desktop
#this should install all packages the are required by the ubuntu desktop
#if some are missing it might add them back in
```

Then try rebooting and see how you go

```
shutdown now -r
#this will shutdown, immediately (now) and reboot (-r)
```

---

### Post by h8uthemost on 2010-05-07
I did try the Recovery Mode already. But I didn't try what you suggested by using the root command. I'll give aptitude aptitude install ubuntu-desktop a shot.

Thanks.

---

### Post by h8uthemost on 2010-05-07
Nope. Unfortunately that didn't work. Thank you for the suggestion though.

Looks like I may just have to reinstall.

---

### Post by vivek40 on 2010-05-07
I am not sure but why dont you just go to the reoery mode and try startx... I guess it should work.. by the way when you give "install ubuntu-desktop" .. what does it say..!

---

### Post by warfacegod on 2010-05-07
You can always run Ubuntu from a CD or USB and get your files that way.

---

### Post by 3rdalbum on 2010-05-07
You need to be more careful. When you go to remove python-gtk2, it tells you that it also will remove a hundred packages that also depend on python-gtk2. That should have warned you that this wasn't the safest thing to do.

The 2.16 deb package was probably made for a later version of Ubuntu which is why it wouldn't install.

Don't mess with system internals unless you really know what you're doing. Even then, you need to read everything carefully.

The 'sudo apt-get install ubuntu-desktop' command should have put things back to normal, assuming you are connected to the internet. What error message did you get?

---

