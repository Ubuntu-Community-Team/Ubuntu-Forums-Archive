---
title: "Can't install on Windows 7"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by rchogan on 2010-12-07
I'm running Windows 7 and want to install Ubuntu 10.04. After trying unsuccessfully to create a CD I tried installing with Wubi.  At the end of the process I was told to reboot. I did so, expecting to find Ubuntu as a an option on a boot screen. No boot screen, Windows automatically opens. In Explorer I can see that Ubuntu is there. How do access it? Thanks.

---

### Post by bcbc on 2010-12-07
In System properties, there is a Startup & Recovery option (maybe the advanced tab). Check if Ubuntu is an option... sometimes it's just that the Timeout is still set to 0, so it boots the default Windows. If you change that to 15, then you'll get the menu.

If there is no Ubuntu option, then the install failed to add an entry to the BCD.

If you manage to boot 10.04, do NOT update packages grub-pc or grub-common when the update manager prompts you (within the "Recommended" update list). They will break Ubuntu (or your drive MBR if you didn't install on C: )

---

### Post by Hippytaff on 2010-12-07
hi rchogan, welcome to the forums
+1 bcbc

for clarity sake - about updating, grub is what boots ubuntu...the newer updates don't like wubi (for some reason they are no configured for the wubi) so when prompted to update by update manager deselect anything with the word grub in it...namely grub-pc / grub-common as bcbc said.
:-)

If you like ubuntu it is advisable to do a 'real' install (dual boot with windows), rather than a wubi (inside windows) install. for this very reason. If you decide to do that and need help search the forums and the ubuntu help documentation (below) and if you still need help start a thread :-)

---

### Post by rchogan on 2010-12-07
There is no Ubuntu option in Startup and Recovery, which is set for 30 seconds, so the install made no entry. So much for wubi.

---

### Post by bcbc on 2010-12-07
> **rchogan said:**
> There is no Ubuntu option in Startup and Recovery, which is set for 30 seconds, so the install made no entry. So much for wubi.

I've seen one other case like this (the user added it manually using bcdedit). I've seen a few more where the timeout is set to zero.

Go for the normal install, live CD or USB.

---

