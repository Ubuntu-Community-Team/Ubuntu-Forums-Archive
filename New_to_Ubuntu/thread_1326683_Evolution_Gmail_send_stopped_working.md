---
title: "Evolution Gmail send stopped working"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by dndrich on 2009-11-14
Ubuntupals:

Here is an odd one. I have an IMAP Gmail account I am using with Evolution. It has been working just fine for the last week. Now, suddenly, I cannot send email through Evolution. The same account works fine on my Mac. I have the server set to smtp.gmail.com:587, just as before, but no dice. Thoughts here?  I ran it in terminal this time, and here is what it shows when starting up:

alex@alexkarmic-desktop:~$ evolution
** (evolution:2772): DEBUG: mailto URL command: evolution %s
** (evolution:2772): DEBUG: mailto URL program: evolution

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2772): DEBUG: New account: GMail (imap://danielgrich@imap.gmail.com/)
** (evolution:2772): DEBUG: Number of email accounts: 1
** (evolution:2772): DEBUG: EI: SHELL STARTUP

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
** (evolution:2772): DEBUG: EI: mail_read_notify
** (evolution:2772): DEBUG: Setting GMail to 0 unread messages

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (evolution:2772): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

---

### Post by dndrich on 2009-11-14
OK, very strange. I changed the server setting to tls encryption, and now it works. I have no idea why this would be the case. It was working fine just a few days ago with ssl. Any thoughts on this?

---

### Post by phydeaux98038 on 2009-11-14
I'd love to know how you managed to change the configuration, since I just finished upgrading to 9.10, and now Evo will not start at all.  I get the same atk_object_set_name error.

---

### Post by phydeaux98038 on 2009-11-14
Small change, but maybe significant.  My errors are prefaced with (evolution:6347).

---

### Post by dndrich on 2009-11-14
I have no idea. Evolution works perfectly for me, but this one problem was odd. After I changed to tls, all now works.

---

### Post by phydeaux98038 on 2009-11-14
You were able to make the change via Evolution itself, or did you make changes via command line?  I'd like to try changing the gmail account to TLS, if it can be done in the cli.

---

### Post by dndrich on 2009-11-14
I did it via Evolution. I'm afraid my problem is likely different than yours if your Evolution just won't start.

---

### Post by phydeaux98038 on 2009-11-15
Well, I'm not sure what the difference is, but going into Applications > Office > Evolution allows me to start Evo and work with it.  The panel shortcut I had was configured to call "evolution --component=mail", and it looks like the call under Applications is simply "evolution".

I still get the atk errors, and I can send just fine, so I'm not sure what's going on.  I'll be following the bug reports to see what happens there.

---

