---
title: "[SOLVED] Trouble installing pkg ttf-bpg-georgian-fonts"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Frogbarf on 2008-12-30
I've been trying to install a Georgian font package.

I first tried installing from

[http://mirrors.cs.wmich.edu/ubuntu/pool/universe/t/ttf-bpg-georgian-fonts/ttf-bpg-georgian-fonts-udeb_0.5_all.udeb](http://mirrors.cs.wmich.edu/ubuntu/pool/universe/t/ttf-bpg-georgian-fonts/ttf-bpg-georgian-fonts-udeb_0.5_all.udeb)

but this turned out to be only a partial package, containing only one font, Glaho.

I then tried installing via

sudo apt-get install ttf-bpg-georgian-fonts

and got an error when trying to overwrite

/usr/share/fonts/truetype/ttf-bpg-georgian/BPG_Glaho.ttf

I manually removed that file and its directory via gksudo nautilus

and retried sudo apt-get install ttf-bpg-georgian-fonts. I'm still getting the same error:


```
dpkg: error processing /var/cache/apt/archives/ttf-bpg-georgian-fonts_0.5_all.deb (--unpack):
 trying to overwrite `/usr/share/fonts/truetype/ttf-bpg-georgian/BPG_Glaho.ttf', which is also in package ttf-bpg-georgian-fonts-udeb
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ttf-bpg-georgian-fonts_0.5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I think my manual removal of BPG Glaho.ttf and the directory ttf-bpg-georgian have screwed something up.

What to do?

Update: I tried

```
sudo apt-get purge ttf-bpg-georgian-fonts-udeb
```

but this aborted.

Second update:

I tried getting rid of the unwanted package using dpkg instead of apt-get:

[CODE sudo dpkg -P ttf-bpg-georgian-fonts-udeb[/CODE]

This completed okay.

I then tried installing the package I wanted and it appears to have completed without any errors. I had rebooted in the interim, so that may have had something to do with sorting out the mess, too, but it looks like if you intall a .deb package other than by apt-get, you should use dpkg -P <pkg name> to remove it.

---

