---
title: "GPG Error in sending mail - Evolution"
date: 2010-09-17
forum: New to Ubuntu
---

### Post by randolf_ambrose on 2010-09-17
I'm unable to sent mails via Evolution. I dont see any configuration error.

It was working fine till yesterday.

Now i'm getting GPG error message when i try to send a mail.

There is no such issue in receiving mails. That is working perfectly.

Only sending is having this issue.

what could be wrong??? i havent changed any of the settings in evolution from yesterday.

---

### Post by jtarin on 2010-09-17
. Get your correct key ID (do this anyway just to double check)

$ gpg --list-keys

You will get some output like this:

pub 1024D/5BECD197 2004-09-19 Reboot Kid <rebootkid@nateandamy.org>
sub 2048g/ACE9C67B 2004-09-19

The key ID you need is the one on the 'sub' line, i.e. ACE9C67B

Obviously yours will be different 

2. Open evolution select Edit -> Preferences 

3. Select the mail account you want to update and click Edit
and go to the Security Tab

4. Fill the "PGP/GPG Key ID" field with 8 zeros (00000000)

5. Press OK

6. Repeat steps 3, 4 and 5 only this time paste/transcribe the sub key
ID in to the "PGP/GPG Key ID" field

---

