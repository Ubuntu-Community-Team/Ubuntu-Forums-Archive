---
title: "Wireless broke after update!"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by enoughsaid05 on 2010-01-09
Hi guys

I just updated my system, and I think there is some sort of kernel update from 2.6.31-17 to 18. But my wireless broke after that.

I tried modprobe of all sorts read the manual and experimented on my own, only to realise that the only way to work around is to switch back to 17 via GRUB.

Anyone knows how to fix this update problem? 

Thanks

---

### Post by enoughsaid05 on 2010-01-10
bump

---

### Post by warfacegod on 2010-01-10
The 2.6.31-17 was just released as stable a short while ago. I doubt -18 is anything but in testing. Go to: System> Admin.> Software Sources> Update tab and uncheck Pre-release updates and possibly Unsupported updates. You will need to find a way to revert to the old kernel.

---

### Post by Vined Adobo on 2010-01-10
> **enoughsaid05 said:**
> Hi guys

I just updated my system, and I think there is some sort of kernel update from 2.6.31-17 to 18. But my wireless broke after that.

I tried modprobe of all sorts read the manual and experimented on my own, only to realise that the only way to work around is to switch back to 17 via GRUB.

Anyone knows how to fix this update problem? 

Thanks

Hi.  I experienced the same problem.  I was never able to use my wireless until 9.04.  Even after that, I had problems with speed when some updates arrived.  The same thing happened a day or two ago.  I had to go back to my lame wired connection.  Today (01/09/10,) I got another update, and WOW, wireless is back to normal!  Don't know how to explain it, but I love it.  BTW, I have an ACER with an atheros 5001 wireless adapter, which is known to be problematic with Linux.  Perhaps you can update again.  If you're using your wireless, it may be VERY slow.
Let me know if I helped!
Dave

---

### Post by warfacegod on 2010-01-10
Alternatively, when grub loads you can boot into the -17 header from there. 

The only way I can think of that might work to remove the -18 header would be to install Ubuntu Tweak (making sure you've booted under the -17 header) and go to the Applications tab> Package Cleaner sub tab> click unlock> click clean kernel> click clear. That *should* work but it's not very elegant. Warning: I've never tried what I just proposed so I don't know if it will break your system. I only thought of it because when I got the -17 kernel before I rebooted, I happened to be looking at that screen and it listed -17 to be cleaned. Search softpedia for ubuntu tweak if you are willing to try this. Make a backup if you do.

---

### Post by warfacegod on 2010-01-10
I just realized that the guitar smilie looks like Kirk Hammet of Metallica.

---

### Post by enoughsaid05 on 2010-01-10
After this episode i just realised everything is just soooo lame...

Initially I wanted to uninstall the linux headers -18 version, but chickened out because I didn't want any of my stupid actions to break the OS and make me reinstall the whole thing again.

So I just changed the GRUB's default OS

Unchecked backports and proposed updates. I didn't know proposed updates can potentially break the system. What a shame :(

Everything's back to normal. Thanks for all the advices!

---

### Post by warfacegod on 2010-01-10
It's a very new one and those tend to be rather volatile. They're really there for omni-geeks to play with and improve.

---

### Post by warfacegod on 2010-01-10
Don't forget to mark as solved under thread tools.

---

