---
title: "Two problems:"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by nomad980 on 2009-12-10
I have two problems I need to try to solve:
1) I was going through the output of dmesg and saw that there was a message saying Nvida taints the kernel. Should I be worried about this, and do I know for sure that the module is being loaded? How can it be fixed if its not.

2) I don't remember what I had previously installed but something made it so that sabnzbd and ushare services no longer start at boot. They were working fine a few reboots ago. Any way I could get a list of the packages I had just installed?

Thanks guys in advance for your help.

---

### Post by t0p on 2009-12-10
> **nomad980 said:**
> I have two problems I need to try to solve:
1) I was going through the output of dmesg and saw that there was a message saying Nvida taints the kernel. Should I be worried about this

The NVidia driver is not Free software - it is proprietary code provided by the NVidia developers.  So when it says NVidia "taints the kernel", all it means is that you have non-Free software in the kernel.  Nothing to worry about, unless you have a problem with non-Free software.

> **nomad980 said:**
>  and do I know for sure that the module is being loaded? How can it be fixed if its not.

What makes you think it hasn't been loaded?  If dmesg says it has?

> **nomad980 said:**
> 
2) I don't remember what I had previously installed but something made it so that sabnzbd and ushare services no longer start at boot. They were working fine a few reboots ago. Any way I could get a list of the packages I had just installed?


If you want a list of all installed packages, open a terminal and type in the command:

```
dpkg --get-selections > packages.txt
```

Now look in the file 'packages.txt'.  Everything with 'install' after it is installed on your computer.

---

### Post by nomad980 on 2009-12-10
Thank you very much. The reason I ask about the nvidia being loaded or not is because I was having problems before getting the nvidia-settings to save the xorg.conf. I had to delete it, get nvidia-settings to give me the preview and then paste that in to get it to finally save without an issue.

Now its time for me to go step by step trying to figure out what I installed that changed my settings.

---

