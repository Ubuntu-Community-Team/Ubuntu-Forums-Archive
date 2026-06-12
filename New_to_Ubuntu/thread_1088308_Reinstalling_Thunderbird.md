---
title: "Reinstalling Thunderbird"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by TRANQU111TY on 2009-03-05
If I uninstall Thunderbird and install it again, will all my emails and profiles still be there?

---

### Post by Tim Sharitt on 2009-03-06
I believe your profiles should be fine unless you remove it with the apt-get purge. If you want to be sure you don't lose everything, you can back up your ~/.mozilla-thunderbird directory.

---

### Post by TRANQU111TY on 2009-03-06
> **Tim Sharitt said:**
> I believe your profiles should be fine unless you remove it with the apt-get purge.

What exactly do I type in the terminal to completely remove Thunderbird with the purge?

Thanks for reading!

---

### Post by Bios Element on 2009-03-06
> **TRANQU111TY said:**
> What exactly do I type in the terminal to completely remove Thunderbird with the purge?

Thanks for reading!

Pretty sure it's this. Remember you'll lose your thunderbird config files for every user.

> sudo apt-get purge thunderbird

---

### Post by TRANQU111TY on 2009-03-06
> **Bios Element said:**
> Pretty sure it's this. Remember you'll lose your thunderbird config files for every user.

I ran the command and installed Thunderbird again but my profiles, emails etc are still there. How can I completely remove everything to do with Thunderbird the easy way?

---

### Post by Tim Sharitt on 2009-03-06
I thought you wanted to keep the profiles and emails. apt-ger purge may not remove it (in your case it obviously did not). You can remove the ~/.mozilla-thunderbird directory to get rid of them.

---

