---
title: "Allow application access to Keyring? message"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by dalewcw on 2010-01-23
Message box popped up with the following: The application 'application' (/usr/lib/evolution/evolution-dataserver-2.28) wants to access the password for 'Desktop Couch user authentication' in the default keyring.  

What is this about. I chose 'Deny' until I know more about it.

I have just loaded 9.10 from the .iso downloaded in Oct and haven't updated it yet. I might start there. However I would like to know about the keyring.

My password also does not work in synaptic package management or when trying to install a Java plug-in with Firefox. I went back to Ubuntu Software Center and my password works.

I really enjoy this version. I have used 8.04 and like what they've done with it. A lot more user friendly for beginners like me.  I believe it is now easier than Windows.

---

### Post by rogue_0111 on 2010-01-23
> **dalewcw said:**
> The application 'application' (/usr/lib/evolution/evolution-dataserver-2.2


1. Evolution is your mail access program. It's like Outlook for Windowz.

2. About your password, check out this page:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

--

---

### Post by dalewcw on 2010-01-23
I solved my synaptic password issue by logging off the present users account and logging in under my account. Installed updates and Firefox plugins. Should I 'Always allow' access to keyring with evolution?

---

### Post by rogue_0111 on 2010-01-23
Yes, only if use Evolution. If you don't Deny, Deny, Deny.

---

### Post by mcduck on 2010-01-24
> **rogue_0111 said:**
> Yes, only if use Evolution. If you don't Deny, Deny, Deny.

There's no reason to deny Evolution. If it tries to access the keyring, it's trying to access some information you have yourself saved in the keyring for it. Like login information for your e-mail account..

And of course it only does that if you start Evolution yourself to read your mails or use the calendar. It's not going to start on it's own so it's pretty much safe to say that every time you see some program asking for keyring access it's some program you just started yourself, and you need to allow the access to be able to use that program. And there's really never any reason to deny, if you don't want to use some program then just don't, and you'll never even get a change to deny it's keyring access. :D

There's no need for paranoia in Ubuntu. You don't need to worry about any piece of program spying on you, at least unless you start installing software from outside of Ubuntu's repositories.

---

### Post by dalewcw on 2010-01-24
mcduck,
Thank you, I really am not too paranoid(I do like backups,however).  I just installed this OS a few day ago for my daughter(she loves it) I was exploring around and did click on the evolution envelope button then canceled as I am not ready to configure it yet.  Again, thanks for the info.

---

