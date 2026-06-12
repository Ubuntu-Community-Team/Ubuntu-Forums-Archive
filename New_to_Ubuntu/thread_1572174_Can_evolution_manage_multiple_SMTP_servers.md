---
title: "Can evolution manage multiple SMTP servers?"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by boroborolama on 2010-09-10
I am running Evolution on Ubuntu 10.04.  I cannot configure Evolution so that it can send emails through different SMTP servers (one is Gmail, another is a university server).  It seems to only use the one chosen as a default.

---

### Post by lisati on 2010-09-10
On the copy of Evolution that I have on my laptop (v 2.28.3 on Ubuntu 10.04 64-bit) I can associate a different SMTP server with each email account I have set up. 

Within Evolution, go to Edit->Preferences->Mail Accounts, select the email account you want to edit, click on the "edit" button, and then open the "Sending email" tab. From there you can choose the smtp server settings for that particular email account.

---

### Post by boroborolama on 2010-09-10
I am also using Version 2.28.3.  I have associated different SMTP servers, as you describe, but still emails don't send.  They lie in waiting in the Outbox folder under "On This Computer."  When I refresh (F9), each of the IMAP servers is listed, but only the SMTP associated to the default account, and it usually freezes while saying "Sending message 1 of 1."  (The one message is from an address that does _not_ use that SMTP server).

Is this an issue with ports and/or encryption (SSL, TSL?)

Sometimes, I get this error message as well:

    Welcome response error:  Connection reset by peer

---

### Post by lisati on 2010-09-10
It *could* be an issue with your SSL/TLS settings, or your ISP could be blocking port 25. Beyond that, I'm currently stuck for suggestions of things to check.

---

### Post by jtarin on 2010-09-10
Where did you obtain your settings for that account?

---

### Post by cruising on 2010-09-13
Eureka Eureka! I've found the solution to my sending predicament! I just did a google search and voila! Here's the link that rescued me: [This site :)]("http://boolix.net/2010/04/22/configure-evolution-to-use-goggle-mail-with-imap-and-ssltls/")

Plus [this forum]("http://ubuntuforums.org/showthread.php?t=793609") was where I first landed! Looks like there may be multiple solutions to the problem. Choose one that works for you.

Glad I could help! Cheers!

---

