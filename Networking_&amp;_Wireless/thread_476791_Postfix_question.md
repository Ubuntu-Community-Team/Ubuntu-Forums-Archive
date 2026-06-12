---
title: "Postfix question"
date: 2007-06-17
forum: Networking &amp; Wireless
---

### Post by squinter on 2007-06-17
Hi,

I've installed and configured postfix as described in: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Now how do I use it to send and receive emails?

Cheers,

Sid

---

### Post by squinter on 2007-06-18
Never mind, I read [https://help.ubuntu.com/community/PostfixBasicSetupHowto#head-482856d455635e6a191866474ad6af86c67f61ba](https://help.ubuntu.com/community/PostfixBasicSetupHowto#head-482856d455635e6a191866474ad6af86c67f61ba) and figured it out.

I just use "mutt -f pop://user@domain.com" to check my pop3 account :D

After I enabled the virtual ports on my firewall, I can now send and receive emails from the world wide web.

---

