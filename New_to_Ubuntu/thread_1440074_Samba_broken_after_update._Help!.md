---
title: "Samba broken after update. Help!"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by BikeHelmet on 2010-03-27
Hello there.

Does anyone know of a way to roll back to an older version of Samba? Mine just updated, and now my shares are broken. It just says "Access Is Denied" when I try to access them.

Ubuntu 9.04 is my NAS, and XP clients are trying to access the shares.

---

### Post by Gixxy on 2010-03-27
Maybe it overwrote you config file. You should check it.

```
sudo nano /etc/samba/smb.conf
```

or gedit 

```
sudo gedit /etc/samba/smb.conf
```

Also check the permissions on the shares.

It's probably going to be better to tackle the permissions issue rather than trying to roll back to a previous version. Besides, you will still probably have the issue even if you did.

---

### Post by HermanAB on 2010-03-27
Yup, I agree with the previous post - the problem will likely still be there even if you roll back.

When I do anything out of the ordinary on a machine (e.g. run Samba, NFS or any kind or daemon) I make a tar ball of /etc and keep it in /root, so I can refer to it when stuff-ups like this happen.  Note that I said when, not if!

You should also disable automatic updates on a server.  If your machine is used as a server, then auto-screw-ups is the last thing you want to happen.

---

### Post by BikeHelmet on 2010-03-27
Looks like it edited the config file. I'm just not sure what it added. I'll try and drill down by commenting stuff out. Too bad my backup copy seems to have vanished.

---

### Post by readycarpenter on 2010-03-27
I always use system-config-samba has a great gui, can config permissions, users, groups

---

### Post by Gixxy on 2010-03-27
That sucks dude... you should defiantly backup that kind of stuff before updates like that. Herman has it right, servers you have to very careful of updates. :cry:

---

### Post by BikeHelmet on 2010-03-27
I did create a copy with cp, but the copy disappeared. :P

I just tried setting up a new share, and the new share works fine using the exact same settings. Only old shares don't work?

I looked at the permissions on the folders, and they seem to be identical - but I'm doing it in Nautilus, so maybe someone has a text command that will reveal something?

---

### Post by BikeHelmet on 2010-03-28
Okay, figured it out. **ls -l** didn't reveal anything, so I started trying to think more linux-y. :P

Samba isn't working with linked folders anymore. If the share *is* a linked folder, that's fine, but my older shares were folders containing links to all the stuff on my storage drive.

Anyone more familiar with Samba have an idea on how to get around this? :)

---

### Post by BikeHelmet on 2010-03-28
Okay, I forced Samba back to the old version with the Synaptic Package Manager. I also locked it so this won't happen again. :)

---

### Post by carnahst on 2010-03-30
I have the exact same issue. It started after I ran the most recent updates on Saturday. Also, I have confirmed that my smb.conf wasn't changed. I did a comparison from an older version and they are identical.

Please, if you wouldn't mind tell me which packages you rolled back and to what versions. I see lots of samba entries, in the synaptic package manager and am concerned about missing a dependency.

Thanks!

---

### Post by carnahst on 2010-03-30
Solution?

Apparently, Samba will no longer follow wide links, if UNIX extensions are enabled. I added "unix extensions = no" to the [global] section of my /etc/samba/smb.conf file and restarted samba (restart samba with "/etc/init.d/samba restart"). This fixed the problem for me.

Here is a note I found referring to the security update:

                 This update was a security update, with  the following behavior change:
   * SECURITY UPDATE: arbitrary file disclosure via wide links
    - debian/patches/security-CVE-2010-0926.patch:  disable wide links when
      UNIX extensions are enabled in source3/include/proto.h,
      source3/param/loadparm.c, source3/smbd/service.c,
      source3/smbd/trans2.c, source3/smbd/vfs.c,
      docs/htmldocs/manpages/smb.conf.5.html and  docs/manpages/smb.conf.5.
    - CVE-2010-0926
  * WARNING: This changes the default samba behaviour. For security
    reasons, it is no longer possible to use wide links and UNIX
    extensions at the same time. After applying this security update,  wide
    links will be disabled automatically as UNIX extensions are turned  on
    by default. If wide links are required, you may re-enable them by
    adding "unix extensions = no" to the [global] section of
    the /etc/samba/smb.conf configuration file.

---

### Post by Alain Knaff on 2010-05-10
Just a remark for those gotten bitten by this behavior, and want to avoid similar occurrences in the future: The samba team doesn't read distribution's bug trackers and forums, but they do have their own list: 

[EMAIL="samba-technical@lists.samba.org"]samba-technical@lists.samba.org[/EMAIL]

The samba team lives under the impression that only a tiny minority of people are affected by this bug, and they can only be convinced otherwise if more people make their voices heard. So if you care, drop a note to [EMAIL="samba-technical@lists.samba.org"]samba-technical@lists.samba.org[/EMAIL]

Thanks,

Alain

---

