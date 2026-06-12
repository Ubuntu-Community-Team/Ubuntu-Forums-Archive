---
title: "pidgin troubles"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by watermelonsugar on 2009-04-20
suddenly i'm unable to connect to my pidgin account.  


Could not connect to authentication server:
Connection refused


it was working fine until this evening and nothing has changed as far as i can tell.   any ideas?

---

### Post by celthunder on 2009-04-20
what server which plugin (msn/aim/etc)  port etc would be helpful.

---

### Post by Ms_Angel_D on 2009-04-20
Since pidgin doesn't have it's own service you need to specify which messenger service are you referring to(MSN, Yahoo, AIM, etc..etc..etc.).

---

### Post by watermelonsugar on 2009-04-20
oh!  

the aim protocol if thats the right word.  thanks.

---

### Post by ptn107 on 2009-04-20
1. Accounts -> Manage Accounts
2. Select your username and click Modify.
3. Verify Protocol/Username/Password are correct on the Basic tab.
4. On the Advanced tab verify the AIM server (login.messaging.aol.com) and port (5190).
5. Uncheck 'Use SSL', uncheck 'Always use AIM/ICQ proxy server...', check 'Allow multiple simultaneous logins'
6. Set proxy type to 'Use GNOME Proxy settings'.
7. Try logging in again.

---

### Post by watermelonsugar on 2009-04-20
those were already the settings, so no dice.  thanks though.

---

### Post by nandemonai on 2009-04-20
Perhaps aim is down?

---

