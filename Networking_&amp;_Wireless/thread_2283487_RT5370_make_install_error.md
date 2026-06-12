---
title: "RT5370 make install error"
date: 2015-06-22
forum: Networking &amp; Wireless
---

### Post by txw on 2015-06-22
Hi all, 

hope som1 can help.

I dlded drivers from :
[http://www.mediatek.com/en/downloads/rt8070-rt3070-rt3370-rt3572-rt5370-rt5372-rt5572-usb-usb/](http://www.mediatek.com/en/downloads/rt8070-rt3070-rt3370-rt3572-rt5370-rt5372-rt5572-usb-usb/)

And set 
...
[I]# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR=#ff0000]**y**[/COLOR]
# Support Native WpaSupplicant for Network Manger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[/I][COLOR=#ff0000][B][I]y
[/I][/B][/COLOR]**as mentioned here:**
[http://bernaerts.dyndns.org/linux/74-ubuntu/229-ubuntu-precise-dlink-dwa160-revb2](http://bernaerts.dyndns.org/linux/74-ubuntu/229-ubuntu-precise-dlink-dwa160-revb2)

everything else seems fine so I didnt change.

**when I "make install" error happens. seems like it can´t find ".ko" file.**

tried to do a search into the drivers folder but cant find it.

any ideas?

many thanks ;)

edit:

I have been trying and making a lot of search. Seems like there is a problem with *rt_linux.c* code. I read in another post for another chipset that code is old for linux kernel but dunno how to fix.
I believe bug is over here as it tells "incompatible types when assigning to int"
[I]
#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,29)
        pOSFSInfo->fsuid = current->fsuid;
        pOSFSInfo->fsgid = current->fsgid;
        current->fsuid = current->fsgid = 0;
#else
        pOSFSInfo->fsuid = current_fsuid();
        pOSFSInfo->fsgid = current_fsgid();
#endif
        pOSFSInfo->fs = get_fs();
        set_fs(KERNEL_DS);
    } else {
        set_fs(pOSFSInfo->fs);
#if LINUX_VERSION_CODE < KERNEL_VERSION(2,6,29)
        current->fsuid = pOSFSInfo->fsuid;
        current->fsgid = pOSFSInfo->fsgid;
#endif
    }
}
[/I][B]
edit 2:

Seems like I´m auto solving it! LOL. Im on VM, I will try in the PC this WE[/B][I]

I left the code like this, following instructions
[I]
        pOSFSInfo->fsuid = current_fsuid();
        pOSFSInfo->fsgid = current_fsgid();

        pOSFSInfo->fs = get_fs();
        set_fs(KERNEL_DS);
    } else {
        set_fs(pOSFSInfo->fs);

    }
}
[/I]

[/I]

---

### Post by txw on 2015-07-03
Hi all, 

I made a mistake. the VM I dlded was **k**ubuntu and the PC giving trouble is **L**ubuntu.

So I made it work with kubuntu VM but it doesnt work with Lubuntu. Just tried with lubuntu 15.04 into VM and it doesnt compile using "make" as it does with kubuntu.

Any ideas?
another light linux desktop I could install?

many thanks!

---

