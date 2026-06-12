---
title: "sending mail problem in thunderbird"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by richardy on 2007-08-15
Hi,
I am having a slightly weird problem in Thunderbird in that i can receive emails fine, when i send an email thunderbird says it is sent with no errors and i sent an email to myself and that went fine. So there would seem to be no problems except that no-one seems to receive my emails but at the same time they are not being bounced - just not received. Apparently the only one who can receive my emails appears to be me which is not very useful. I have checked the account settings against those i have in the windows version of Thunderbird (which runs fine) and they are exactly the same.

Thunderbird v1.5.0.10
Ubuntu feisty fawn

Any help you can give would be much appreciated.

Cheers.

---

### Post by ihristov on 2007-08-17
If you are connecting to the same server you can't possibly have different behaviour.

I would suggest trying to send a msg manually via telnet, just to be sure. I use a yahoo account for sending msgs to an external system for testing. Here is an example session

```
telnet mail.fakedomain.com 25

220 mail.fakedomain.com ESMTP ready
HELO 127.0.0.1
250 mail.fakedomain.com
MAIL FROM: test@fakedomain.com
250 2.1.0 Sender <test@fakedomain.com> ok
RCPT TO: test@fakedomain.com
250 2.1.5 Recipient <test@fakedomain.com> ok (local)
DATA
354 Enter mail, end with CRLF.CRLF
X-Mailer: Netburner Embedded Mailer
From:from@fakedomain.com
To:to@fakedomain.com
Subject: Random mail sent off to someone

stuff
some more
.starting with a dot

.
250 2.0.0 46c098e5-00000f77 Message accepted for delivery
QUIT
221 2.0.0 SMTP closing connection
```

Now you don't explain if this is from different networks. For example if your Windows machine which works fine is in the office and your Ubuntu machine is at home and you are using an ISP that denies traffic to external SMTP servers, than maybe this is your problem.

---

