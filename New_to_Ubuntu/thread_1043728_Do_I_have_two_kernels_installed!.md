---
title: "Do I have two kernels installed?!"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Ben Page on 2009-01-18
This might be a stupid Q...
When I was resolving a open-close DVD tray issue, one nice fella pointed me to a link where there was similar issue described and solved - it was an official ubuntu page. In there it sayed that I have to download some packages (pre-released updates -- interpid proposed), so I did. This didn't solve my issue, but another even nicer fella provided to me a single package download link - so I downloaded the package - installed and all was great! (it was a small package). But When I rebooted from Win after some time I was presented with different GRUB boot options, I had *.*.11 kernel boot and *.*.7 kernel boot (stars are for 2.16 or what ever, don't know the kernel version from head now).  And for each option I have failsafe with something and without...So, now my grub is overcrouded + win7, how to get it sorted, but more importantly...do I have two kernels installed? Why I have options to boot to both? Isn't it supposed to be updated? Am I actually dualbooting betwen two kernel now? Is it recomended to delete the older one?

---

### Post by ibutho on 2009-01-18
Boot your system using the kernel you wish to keep and then uninstall the ones you do not want using Synaptic. Their grub menu entries will be automatically removed during the deinstallation.

---

### Post by MenZa on 2009-01-18
The reason why Ubuntu keeps your old kernel is in case of a problem with the new one - if you for some reason cannot boot the new kernel, you can always go back to the old one and troubleshoot the issue.

It's recommended that you keep at least one or two older kernels around for troubleshooting purposes.

---

### Post by Bachstelze on 2009-01-18
> **Ben Page said:**
> do I have two kernels installed?

Yes.

> **Ben Page said:**
> Why I have options to boot to both?

So you can still boot the old one if the new one happens to fail somehow.

> **Ben Page said:**
> Isn't it supposed to be updated?

No. As far as the package manager is concerned, those two versions of the kernel are totally different packages, that are not related in any way.

> **Ben Page said:**
> Am I actually dualbooting betwen two kernel now?

Yes and no. You could say that you are dual-booting since you have the option to boot one or the other, but keep in mind that the kernel is just a small part of the system, and that whichever kernel you boot, the rest of the system will be the same.

> **Ben Page said:**
> Is it recomended to delete the older one?

The choice is up to you, but it is recommended to keep at least two versions of the kernel, for the reason explained above.

---

### Post by Ben Page on 2009-01-18
Ah..so I do indeed have two kernel - and that is normal.
You say that its recomended to leave at leas two? Is this new one, I'm guessing prereleased *.*.11 good? I mean, it works fine, but is it like beta?

---

