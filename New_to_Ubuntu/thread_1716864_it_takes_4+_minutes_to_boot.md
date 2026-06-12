---
title: "it takes 4+ minutes to boot"
date: 2011-03-29
forum: New to Ubuntu
---

### Post by hasanarbab on 2011-03-29
hi, i'm using Maverick Meerkat. My first impression about maverick was 'impresive'. But now from last 10 days it is taking too long to boot. I'm not a linux well known person so any step by step help please.

I have a bit old Dell optiplex GX280, 750 MB Ram, 160 GB sata.

Have boot manager and Avent Windows Navigator installed.

Besides, whatever information required, please ask me and tell me how to get that info.

I'll much appreciate any help.

---

### Post by Nutria on 2011-03-29
> **hasanarbab said:**
> hi, i'm using Maverick Meerkat. My first impression about maverick was 'impresive'. But now from last 10 days it is taking too long to boot. I'm not a linux well known person so any step by step help please.

I have a bit old Dell optiplex GX280, 750 MB Ram, 160 GB sata.

Have boot manager and Avent Windows Navigator installed.

Besides, whatever information required, please ask me and tell me how to get that info.

I'll much appreciate any help.

Edit bootlogd ([FONT="Courier New"]sudo nano /etc/default/bootlogd[/FONT]) and change "BOOTLOGD_ENABLE=No" to "BOOTLOGD_ENABLE=Yes", then reboot.  Once it comes up, copy syslog to your home dir [FONT="Courier New"]sudo cp /var/log/syslog .[/FONT], zip it and attach to the thread.

---

### Post by kerry_s on 2011-03-29
try removing boot manager, ubuntu uses upstart, so that might just screw your boot up.

---

### Post by hasanarbab on 2011-04-12
very sorry people. I had a crash in my 10.10 that it would not boot at all. It was booting to 'busy box' only. I tried a lot to get it fixed as it had happened before with my installation of maverick and at that time the fix was to change uuid of boot harddisk to its address like '/dev/sdax' in grub conf file. Well this and other suggestions found in ubuntuforums and in other google searches just could not help me a bit and l had to retreat back to lucid, which is just awsome.

So i could not give a kick to your suggestions. But thanks anyway and I'll keep this to try next time if i face same situation again.

---

