---
title: "E-mail (console)"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by for.i.am.root on 2009-01-29
Hi:

I set up mutt as my primary e-mail client using fetchmail and esmtp for receiving and sending. I am trying to set up my pc so that when I receive an e-mail, mutt auto executes. When mutt opens it checks /var/mail/$user for new e-mails, which changes it's attributes and causes dnotify to run mutt again. I am currently using a custom script to prevent the loop I was getting without it, however, this is leading to "zombie" problems. I added the -o tag to tell dnotify to only run once, instead of opening mutt infinite number of times, but then dnotify closes after running the first time.

I set-up fetchmail to run every 60 seconds through ~/.fetchmailrc. I would like to find a clean way to run mutt every time I receive an e-mail, then if necessary, restart the dnotify program or whichever program is best suited for this task. The code I am currently using is posted below. I know it's very, very sloppy, however, it's somewhat functional right now. The code is attached as a txt file.

Sorry for being long winded, just trying to give as much detail as possible.

System:
Ubuntu 8.10 x86_64
fetchmail version 6.3.8+GSS+NTLM+SDPS+SSL+NLS+KRB5
esmtp 0.6.0 (I think, apt-get reports newest version)
mutt version 1.5.18
dnotify version 0.18.0

Thanks for all the help!

EDIT: File didn't attach because I forgot to add the .txt extension

---

