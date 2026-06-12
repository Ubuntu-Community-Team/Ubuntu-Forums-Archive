---
title: "vmware-player and madwifi"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by flipybcn on 2007-04-12
I'm trying to install vmware-player on feisty using a madwifi wireless card.
I've found that using vmware-server is fine as I followed a how-to [1].
But now I'd like to use the player only, as I don't want to make new images (or I can find them from the OS website).
But the vmware-player installation keeps crashing all the time, and the worse is that now I'm not able to unistall/reinstall it, neither any other package.
```
Starting VMware services:
   Virtual machine monitor                                             done
   Virtual ethernet                                                    done
   Bridged networking on /dev/vmnet0                                  failed
   Host-only networking on /dev/vmnet1 (background)                    done
   Host-only networking on /dev/vmnet8 (background)                    done
   NAT service on /dev/vmnet8                                         failed
invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error al procesar vmware-player (--configure):
```
I've tried to download the SVN version of madwifi and modify the suggested file in the how-to [1], but it keeps crashing now...

Any suggestions?

Thanks in advance

[1] [http://ubuntuforums.org/showthread.php?t=285846](http://ubuntuforums.org/showthread.php?t=285846)

---

