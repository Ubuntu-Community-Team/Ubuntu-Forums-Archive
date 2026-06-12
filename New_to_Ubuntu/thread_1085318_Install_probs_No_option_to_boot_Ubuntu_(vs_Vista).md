---
title: "Install probs: No option to boot Ubuntu (vs Vista)"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Ubuntrew on 2009-03-02
New here so sorry if this has been answered before--I searched around and couldn't find an answer.

I just installed Ubuntu 8.10 on top of Vista according to the apcmag.com "How to dual-boot Vista with Linux (Vista installed first)" instructions [here]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3").

I'm hung up on this step "When the install is complete the system will reboot. When the GRUB boot menu is displayed, have a look at the last entry in the list."  Problem is, I restart my computer (without the CD in) and it boots straight to Vista with no other options.

The drive is partitioned as such:
NTFS (Vista) | Ex3 \home | Ex3 \ | SWAP

Any help appreciated...thanks!

---

### Post by Sysero on 2009-03-03
Hi.

We just need to reinstall GRUB for you.  

Put the LiveCD back in and reboot.  When the desktop is running do the following:

From the menu, select:

[COLOR="Navy"]Applications - Accessories - Terminal[/COLOR]

Once the terminal is open, type:

```
sudo grub
```

At the [COLOR="Navy"]grub>[/COLOR] prompt, type:

```
find /boot/grub/stage1
```

Grub should return something that looks like this:

[COLOR="Navy"]hd(0,4)[/COLOR]

The numbers in the parentheses might be different on your computer, but it will still be in the format of hd(Number,Number).   

So, for example, let's just assume grub told you [COLOR="Navy"]hd(0,4)[/COLOR].

Then next, at the [COLOR="Navy"]grub>[/COLOR] prompt, you would type:

```
root hd(0,4)
```

And then, type:

```
setup (hd0)
```

And finally, type:

```
Quit
```

Now, reboot your computer.  See if the GRUB menu comes up.  If so, it should show both Ubuntu and Windows.

---

