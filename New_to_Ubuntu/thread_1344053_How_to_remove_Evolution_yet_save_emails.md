---
title: "How to remove Evolution yet save emails"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2009-12-02
While making a clean install of Karmic Koala v 9.10, I changed ext3 to ext4.

After the re-install, Evolution broke. It would download about 3000 emails from the servers. Then if I clicked Send/Receive again (next day), the same 3000 emails would again be retrieved from the mailbox, again. And every new day the same 3000 would be d/l.

I have fixed this partially by changing some of the permissions in 

/home/mark/.evolution/mail/POP/filename(s)

They were set (mostly) to root

User and group were set to me (user named: mark) and group mark. Create & Delete and I applied permissions to files in folders.

Two folders permssion's could not be changed under gksudo nautilus, they had to be changed in a terminal using chown.

Now when I click Send/Recieve, I see, at the bottom of the Evolution window, Junk Mail Failure (or something similar), over and over as each email is brought into my inbox. I never configed Junk mail settings. I suspect this is another permissions problem, but I want a clean install of Evo.

HERE is my question: How do I purge Evolxxxyyyzzz-ution and reinstall it without losing my emails. I don't mind reconfiguring the POP and SMTP settings, but I want Evolution to work as it had in the past.

---

### Post by zkriesse on 2009-12-02
I use Thunderbird which is a little easier but the steps should still work. Go into your email file. For Thunderbird it's "/home/user/.mozilla-thunderbird/" It should be close to something like that for Evolution. Save your folders which you find there. Then re-install Evo and put those folders in the new Evo folder! Hope it helps.

---

### Post by laidback on 2009-12-02
There is a backup and restore plugin for evolution. I believe it saves all your data in a tar ball file.

---

### Post by Devport on 2009-12-02
**Use a maildir**

[http://en.wikipedia.org/wiki/Maildir](http://en.wikipedia.org/wiki/Maildir)

I store my emails in a maildir folder ( e.g. ~/.myMail ) with sub-folders ( e.g. Unsorted, Work/Todo, Work/Sent, Private/Friends, Private/Friends/Sent ) to organize them. Then I setup my mail-accounts and sorted all emails into their respective folders. That has several advantages :

- emails wont be stored on an external mail-server after being downloaded which is more secure
- emails are stored independently of the mail client being used - the mail client can be removed / changed without any risk of data loss - even the mail client configuration can be deleted without loosing those mails
- maildir is supported by several mail clients ( e.g. evolution, kmail - sadly it seems thunderbird doesn't support maildir yet ) so that mail-clients can be changed on the fly or they can even be used at the same time with all of them having access to the emails
- emails can be easily backup-ed by just copying the maildir folder
- its a well known container so that many tools like converters can be found if needed
- its supported by mail servers as well

Its the smartest solution I found after trying other things like e.g. a local imap server. Even if it doesnt solve your problems now it may prevent them in the future.

---

### Post by Devport on 2009-12-14
Forget about my post concerning maildir - I switched from evolution to kmail and using maildir for email storage is not as flawless as I expect and a hard migration is necessary. Sorry for my bad suggestion !

---

