---
title: "My issues with 10.10"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by flyver on 2010-10-14
On my Sony computer, Plymouth doesn't work during boot, and I also had this problem with 10.04...

The "tray" icons on the panel sometimes look weird after boot. This still happens with 10.10...

But the new problem I have with 10.10 (64-bit) is that there is some kind of problem with Java and/or Flash. I've tried Adobe's offering, I've tried Icedtea, it seems I have tried all combinations but when a web page with Java/Flash opens, my computer freezes (sometimes I can move the cursor but can't actually click anything).

I am going to reinstall 10.10 64-bit and see if something gets better, but does anyone have any good advice on what to do with Flash and Java?

I have 4 GB of RAM and I think it would be better for me to stick with 64-bit. Would performance be worse with the 32-bit version?

Thank you!

---

### Post by Tykin on 2010-10-14
Most programs in Linux (and windows/Mac for that matter) aren't optimized for 64bit.  Plus, ubuntu will still pick up all your RAM. You should definitely give the 32-bit version a try. Overall, it's much better supported. 

I actually run the 32bit version on my AMD Phenom II X4 and I have no issues

---

### Post by migs73 on 2010-10-14
If you install the 32 bit version the kernel should automatically change to the PAE kernel, which will allow your system to utilise your 4GB RAM, even if the software you'll use will only be able to address about 3GB at a time.

---

### Post by neotasic1 on 2010-10-14
Do you have proprietary video drivers installed? Do you have desktop effects enabled.  I have found on some machines using the wrong video driver can cause problems, also compiz on some machines caused problems with flash presentations.

---

### Post by beew on 2010-10-14
sorry, wrong thread

---

### Post by tgm4883 on 2010-10-14
I just felt the need to chime in and say that the 64-bit version of 10.10 works for me

---

### Post by x C0MMAND0 x on 2010-10-14
Completely off topic, but Tykin, nice Avatar!

---

### Post by flyver on 2010-10-14
Thanks for the replies.

I think I might skip reinstalling the 64-bit version and go straight for the 32.

Too bad about these problems, I would otherwise really love Ubuntu. I was assuming these tiny (but annoying) problems would disappear with the arrival of 10.10. One other problem I have is that I have to reboot after "suspend" to get my wireless working. Grr.

---

### Post by flyver on 2010-10-17
Fixed my problem with the cursor (actually, the left-click) not working. Was due to my wireless Microsoft keyboard and the shortcut buttons, especially when being used when a video was playing. The fix is [here]("https://bugs.launchpad.net/udev/+bug/637208/comments/40").

---

### Post by lazyworkhorse on 2010-10-17
Flash has a history of problems with 64-bit. Unless you have software that needs 64bit (like cinelerra, for example) stick to 32-bit.

---

### Post by mister_playboy on 2010-10-17
> **flyver said:**
> On my Sony computer, Plymouth doesn't work during boot, and I also had this problem with 10.04...

The workaround is to create a file named splash containing the line FRAMEBUFFER=y and put in the /etc/initramfs-tools/conf.d folder.  Then run: ```
update-initramfs -u
```  I believe this makes your boot a bit slower but it should get plymouth displaying rather than a bunch of text.

---

