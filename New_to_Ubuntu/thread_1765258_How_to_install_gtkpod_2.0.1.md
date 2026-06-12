---
title: "How to install gtkpod 2.0.1?"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by chromatica86 on 2011-05-22
I can't find anywhere how to install this version of gtkpod.
The version available through my software center is 1.0, so I would like to get a newer version.

I have downloaded the files from gtkpod.org, but don't know what to do with them .

---

### Post by bowens44 on 2011-05-22
> **chromatica86 said:**
> I can't find anywhere how to install this version of gtkpod.
The version available through my software center is 1.0, so I would like to get a newer version.

I have downloaded the files from gtkpod.org, but don't know what to do with them .

I haven't tried it but there is a PPA for it at the following link:

[https://launchpad.net/~phantomjinx/+archive/gtkpod-2.0.1-beta](https://launchpad.net/~phantomjinx/+archive/gtkpod-2.0.1-beta)

---

### Post by chromatica86 on 2011-05-22
Thank you. I couldn't find what the ppa was searching google. thanks.

---

### Post by bubkusjones on 2011-05-29
Was trying to upgrade from the default 1.0 that's included, and used the aformentioned PPA.

After removing the old version I get the following while trying to install the new one. 

```

Unpacking libgtkpod (from .../libgtkpod_2.0.0-0ubuntu1ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libgtkpod_2.0.0-0ubuntu1ppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/locale/fr/LC_MESSAGES/gtkpod.mo', which is also in package gtkpod-data 1.0.0-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking gtkpod (from .../gtkpod_2.0.0-0ubuntu1ppa1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/gtkpod_2.0.0-0ubuntu1ppa1_amd64.deb (--unpack):
 trying to overwrite '/usr/share/man/man1/gtkpod.1.gz', which is also in package gtkpod-data 1.0.0-0ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libgtkpod_2.0.0-0ubuntu1ppa1_amd64.deb
 /var/cache/apt/archives/gtkpod_2.0.0-0ubuntu1ppa1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Any idea what's going on? I'm trying to use it with an older 80gig classic (5th gen or something). It sometimes worked and sometimes didn't with 1.0, so I thought the upgrade may help.

---

### Post by wolfen69 on 2011-05-29
Did you completely remove the old one first?

---

### Post by bubkusjones on 2011-05-29
Thought I did. Going to take out the PPA, reinstall and uninstall it again.


EDIT: just reinstalled 1.0 and uninstalled it, and it still gives me the same error when trying to put in 2.0

Man, I miss the old Songbird. It worked beautifully with this ipod. Nothing's been as easy or complete since.

---

