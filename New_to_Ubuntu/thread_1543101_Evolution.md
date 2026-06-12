---
title: "Evolution"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by LadyA on 2010-07-31
I am on Ubuntu 10.04 and trying to setup evolution with gmail. The incoming mail works, but the outgoing mail gives an error message. How can I fix this?

---

### Post by davidmohammed on 2010-07-31
have you been following a guide such as [this]("https://help.ubuntu.com/community/UsingGmailWithEvolution") one?

---

### Post by TNT1 on 2010-07-31
Try here:
[http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)

I have a gmail account in Evolution, sending using smtp as per that link. works fine.

---

### Post by corrytonapple on 2010-07-31
Or you could use Thunderbird if that doesn't work.
[http://www.mozillamessaging.com/en-US/thunderbird/](http://www.mozillamessaging.com/en-US/thunderbird/)

---

### Post by LadyA on 2010-07-31
Followed TNT1 guide, but when trying to send mail a popup box comes us asking for password. After putting gmail password in another box comes up asking for password for keyring, which no password has been made. How do I get rid of the keyring box?

---

### Post by da burger on 2010-07-31
I'm fairly sure the default keyring password is your own login password.

---

### Post by TNT1 on 2010-07-31
> **LadyA said:**
> Followed TNT1 guide, but when trying to send mail a popup box comes us asking for password. After putting gmail password in another box comes up asking for password for keyring, which no password has been made. How do I get rid of the keyring box?

Keyring will usually be your login password if you haven't set up another one.

---

### Post by LadyA on 2010-08-01
Thanks everyone who helped with this problem. Everything is working fine now. I followed TNT1's guide and the logon password worked for the keyring.

---

### Post by JustinR on 2010-08-01
A quick note

**Applications > Accessories > Passwords and Encryption Keys**

Right click 'Password: login' and click 'Change password'.

And change it to nothing - then you won't be bothered by the Gnome-Keyring application.
Unless you have to have your passwords encrypted.

---

