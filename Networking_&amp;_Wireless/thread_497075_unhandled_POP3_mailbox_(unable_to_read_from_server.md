---
title: "unhandled POP3 mailbox (unable to read from server: EOF)"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by be4truth on 2007-07-09
Hi Everybody,
when trying to check my pop mailbox with the mail notification utility  - rediffmailpro.com (I live in India) with my username  I get this error with no reference when I google around.
In Thunderbird and Evolution the checking works without problems.

I get this error message:

[SIZE="6"]unhandled POP3 mailbox (unable to read from server: EOF)[/SIZE]

Any idea what this is?

It tries to log in with:

[email]user@userdomain@rediffmailpro.com[/email]

Thx for any help.

---

### Post by john8791 on 2007-08-03
> **be4truth said:**
> Hi Everybody,
when trying to check my pop mailbox with the mail notification utility  - rediffmailpro.com (I live in India) with my username  I get this error with no reference when I google around.
In Thunderbird and Evolution the checking works without problems.

I get this error message:

[SIZE="2"]unhandled POP3 mailbox (unable to read from server: EOF)[/SIZE]

Any idea what this is?

It tries to log in with:

[email]user@userdomain@rediffmailpro.com[/email]

Thx for any help.

I had a somewhat similar problem.  In the  mail-notification properties window, I have found that under "Account -> Username:" you have to adjust your username to what the server expects.  For example for my Gmail account, username is simply  "username".  With another account I have, you have to put "username@domain.com".  If it's not right, for some reason things get appended to each other and you get that error.

---

### Post by roschell on 2007-08-03
Hi guys, I have got similar prob as I could set-up european server on evolution, but yahoo.com just doesnt want to work. 
correct username and password even I receive notifications that the username or password are incorrect.
I use pop server as pop.mail.yahoo.com and stmp.mail.yahoo.com for outgoing mail. 

Thank you for any advice

---

### Post by john8791 on 2007-08-03
If Yahoo mail is like Gmail, it uses SSL authentication for POP and SMTP.  By default, Debian packages do not compile ssl support because of some licensing issue.  Her is a link showing how to recompile and build the package with ssl support.  It worked for me running Feisty 7.04.

[http://www.howtoforge.com/repackage_deb_packages_debian_ubuntu](http://www.howtoforge.com/repackage_deb_packages_debian_ubuntu)



> **roschell said:**
> Hi guys, I have got similar prob as I could set-up european server on evolution, but yahoo.com just doesnt want to work. 
correct username and password even I receive notifications that the username or password are incorrect.
I use pop server as pop.mail.yahoo.com and stmp.mail.yahoo.com for outgoing mail. 

Thank you for any advice

---

### Post by john8791 on 2007-08-03
Here are the .deb files I recompiled if you want to mess with them.  Remember these are not official!.  You will have to "Lock Version" in Synaptic or it will try to roll back the version.  I'm sure there is a better way but this is the first time I have built a deb package.

---

### Post by be4truth on 2007-10-30
I am on Gutsy now but problem continues. rediff is not a question of SSL.

---

