---
title: "Evolution mail"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by jnmjr on 2010-01-13
Hi all, I've got this weird problem, Evolution doesn't start, it just happened all of a sudden, it has always worked, one thing, this morning I installed some updates but it was working as of this afternoon, now as of tonight it just stopped, when I click it on I get a quick flash of the screen and it goes off....anyone has had this happen before?:confused:

---

### Post by Dark_Stang on 2010-01-13
Hmm, perhaps a configuration file is corrupted. Try renaming the .evolution folder in your home directory to .evolution-backup and starting evolution again. If that works you may want to try importing the old files from .evolution-backup to .evolution a few at a time to see what the offending file was.

---

### Post by mvalviar on 2010-01-13
Try Alt-F2 and type in ```
evolution --force-shutdown
```

If evolution starts back up your settings under File>Backup Settings just it case the problem reoccurs.

---

### Post by jnmjr on 2010-01-14
> **Dark_Stang said:**
> Hmm, perhaps a configuration file is corrupted. Try renaming the .evolution folder in your home directory to .evolution-backup and starting evolution again. If that works you may want to try importing the old files from .evolution-backup to .evolution a few at a time to see what the offending file was.

Thanks, your suggestion worked, the folder that's corrupted is the MAIL folder, I had two important e-mails saved when I last closed Evolution this afternoon Can they be recovered?:)

---

### Post by jnmjr on 2010-01-14
> **jnmjr said:**
> Thanks, your suggestion worked, the folder that's corrupted is the MAIL folder, I had two important e-mails saved when I last closed Evolution this afternoon Can they be recovered?:)

Thanks again guys all is well, recovered e-mails:popcorn:

---

### Post by senorian on 2010-01-24
I seem to have the same problem.
A box flashes on the screen (when receive is clicked) and says
"waiting for pop summary'
I renamed .evolution and then went to synaptic and uninstalled and re-installed evolution.
Cannot find the wizard to set up evolution
Thank you

---

### Post by jnmjr on 2010-01-24
> **senorian said:**
> I seem to have the same problem.
A box flashes on the screen (when receive is clicked) and says
"waiting for pop summary'
I renamed .evolution and then went to synaptic and uninstalled and re-installed evolution.
Cannot find the wizard to set up evolution
Thank you

I never un-installed, I followed the previous poster's suggestion. 
You may need to re-set your accounts, open evolution edit/preferences and make sure all your settings are correct. If this doesn't work I suggest you start a *new thread*, this one is solved and your problem seems a bit different. Good Luck.

---

