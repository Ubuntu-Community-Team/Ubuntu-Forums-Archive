---
title: "reinstall"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by DarinB on 2010-02-07
if i reinstall and i have /home on a separate Hdd
what will i lose?
will i keep my self made login screens, emails, codex???
i hope to lose the plugins, since i messed that up and tbird 3.0 which does not work and crashes all the time as well as tons of panel crashes. 
what will be on my /home and what will be on my /????

---

### Post by warp99 on 2010-02-07
You don't need to reinstall if you're having a problem with Thunderbird. All of your settings are kept locally in /home/$user so if you save them and reinstall you'll have the exact same problems. Best thing is to set up another user, give that user sudo access, and then delete the messed up account once your new account is working properly.

---

### Post by Post Monkeh on 2010-02-07
> **DarinB said:**
> if i reinstall and i have /home on a separate Hdd
what will i lose?
will i keep my self made login screens, emails, codex???
i hope to lose the plugins, since i messed that up and tbird 3.0 which does not work and crashes all the time as well as tons of panel crashes. 
what will be on my /home and what will be on my /????

all your application configuration is stored in your home folder, so resinstalling will likely leave you in the same position you're in now.

if thunderbird in particular is causing you grief then you could try renaming your .mozilla-thunderbird folder in your /home/myuser directory, that will basically be like a brand new install of thunderbird

---

### Post by DarinB on 2010-02-07
if i replace the .mozilla will i lose my emails?

---

### Post by warp99 on 2010-02-07
> **DarinB said:**
> if i replace the .mozilla will i lose my emails?

Yes you will, but you can backup the files and directories for your mail if they're not corrupt and copy them back to your new directory. Just make sure that in your Thunderbird preferences your pointing to the correct directory were your mail folders reside.

---

### Post by Post Monkeh on 2010-02-07
just for the record, all my thunderbird settings are stored in .mozilla-thunderbird 

my .mozilla forlder only stores my firefox files

---

### Post by warp99 on 2010-02-07
> **Post Monkeh said:**
> just for the record, all my thunderbird settings are stored in .mozilla-thunderbird 

my .mozilla forlder only stores my firefox files

Ditto, save the mail files from the .mozilla-thunderbird directory.

---

