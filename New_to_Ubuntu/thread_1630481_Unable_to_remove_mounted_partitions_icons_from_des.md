---
title: "Unable to remove mounted partitions icons from desktop"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by Dalle85 on 2010-11-25
hey there...

After doing a fresh install of Maverick (the update manager bricked the computer during upgrade - NICE) I am having a lot of trouble removing the mounted partition icons from my desktop! On the other installs I've done, the gconf-editor trick worked just fine, however on this install, it has absolutely no effect... any ideas? These two icons are an eyesore on my otherwise clean desktop (I loathe icons on my desktop)!

When i check the gconf-editor nautilus settings, the visible volumes option is unchecked.

---

### Post by Jeanke on 2010-11-25
Hey,

Could you enter following command:

```
nano ~/.gconf/apps/nautilus/desktop/%gconf.xml
```

You should get something like:

```
<?xml version="1.0"?>
<gconf>
        <entry name="volumes_visible" mtime="1290692912" type="bool" value="true"/>
</gconf>
```

If the value is "true" then change it to "false" and reboot.
Anyway, it _should_ change when you adjust gconf-editor, so probably there is something wrong, but I'm not sure what.

---

### Post by Dalle85 on 2010-11-25
Cheers a bunch! I had no directory called "desktop" under the nautilus tab, so I simply created one and made a %gconf.xml file with this content:

```
<?xml version="1.0"?>
<gconf>
        <entry name="volumes_visible" mtime="1290692912" type="bool" value="false"/>
</gconf>
```

However, now I come to think of it, I'm pretty sure the problem lies with the noob user and not the software... I ran gconf-editor using sudo, so it didn't change my user, but the root user... STUPID!! Anyway, thanks again!

---

