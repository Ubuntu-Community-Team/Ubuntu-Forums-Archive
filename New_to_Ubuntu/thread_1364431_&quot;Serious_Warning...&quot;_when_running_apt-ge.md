---
title: "&quot;Serious Warning...&quot; when running apt-get or installing"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by xnerdx on 2009-12-25
I wouldn't consider myself an absolute beginner, not to be cocky, but this seems to be the most alive forum section and this is getting annoying. I don't recall when this started but everything on the system works fine, except for mounting isos for some reason, but I am working on that. Really every time I install using the console or when I download and install synaptic packages using apt-get I always get this serious warning output:
```

dpkg: serious warning: files list file for package `xinit' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `passwd' missing, assuming package has no files currently installed.

```
But it continues installing without any noticeable problems, does anyone know why this happens and how I can "fix" it?

BTW: Running 9.04 Stable - Latest Updates Installed

---

### Post by kansasnoob on 2009-12-25
I think I'd go to Synaptic and use the "broken" filter or Edit > Fix Broken Packages.

You might even try marking both xinit and passwd for reinstallation. Both packages are absolutely necessary!

---

### Post by sandyd on 2009-12-25
mounting isos -> [acetoneiso]("http://www.acetoneteam.org/")

---

### Post by xnerdx on 2009-12-25
I tried installing a package and I didn't see the warnings, thank you.
But now I have another problem, I am trying to mount ISOs but I still cannot:
```

linus@SuDoX:~$ sudo mount -t iso9660 -o ro,loop=/dev/loop0 <iso image> /mnt/fallout1
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by kansasnoob on 2009-12-26
> **xnerdx said:**
> I tried installing a package and I didn't see the warnings, thank you.
But now I have another problem, I am trying to mount ISOs but I still cannot:
```

linus@SuDoX:~$ sudo mount -t iso9660 -o ro,loop=/dev/loop0 <iso image> /mnt/fallout1
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Well I'm a gui guy, and a lazy c&p'er too :) So I always install gisomount which then shows up in System Tools:

[ATTACH]141188[/ATTACH]

You can see there that I have gISOMount open and I've right clicked the Lucid iso on my desktop, chosen Properties, then right clicked the Name which will allow me to copy. Then I can just paste the name into gISOMount with the prefix "/home/<username>/Desktop/", ie: "/home/lance/Desktop/lucid-desktop-i386". Or click on Browse, double click Desktop, and select the iso, etc.

Note: I do **not** use it for burning iso's. I can't say it doesn't work well, I've just never used it for that purpose.

Hope that's helpful.

---

