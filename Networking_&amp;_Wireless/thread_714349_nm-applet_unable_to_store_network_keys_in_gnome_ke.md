---
title: "nm-applet unable to store network keys in gnome keyring"
date: 2008-03-03
forum: Networking &amp; Wireless
---

### Post by jjclark on 2008-03-03
Hi,

I'm running Hardy on my laptop (HP dv9000 family), and the gnome network manager ver0.6.5  is unable to store network keys in the gnome keyring.

After I enter the passphrase/encryption key for my home wireless network, I get the following dialog:

The application applet nm-applet wants access to the default keyring, but it is locked.
Password:____________

I don't think I set a password during the install, but I tried ones I would have used, and nothing works.  Fortunately, "deny"ing access (by nm-applet to the keyring) is an option.  At which point I have wireless access.

Questions :
Did I hose up my install?  Was there something I should have done so I can grant access to the keyring?

I thought that I could set the keyring access password using gnome-keyring-manager, but that package isn't available in Hardy.  Should I force the installation of the keyring-manager package?  If so, from where?

Now, it seems that for Hardy (8.04), the direction is to use polkit to manage user-level access to hardware and services.  Is that the case?  Is it possible to "fix" the policy settings to allow the nm-applet access to the keyring?  Or does the nm-applet (version 6.5) need to be upgraded?

Thanks in advance for your time and patience.

---

