---
title: "Update from &quot;unauthenticated source&quot; won't complete"
date: 2011-01-19
forum: New to Ubuntu
---

### Post by PaulHA2 on 2011-01-19
Hi again,

My update manager has 24 updates it wants to do. When I try to get the updates, it gives me an error message about unauthenticated sources. The "details" gives me this:
```
apparmor apparmor-utils cups cups-bsd cups-client cups-common cups-ppdc dpkg ifupdown libapparmor-perl libapparmor1 libc-bin libc-dev-bin libc6 libc6-dev libcups2 libcupscgi1 libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 liblcms1 xserver-common xserver-xorg-core
```

Running 10.10 on this machine.

Any ideas what's going on?

---

### Post by t0p on 2011-01-19
Not really sure what you mean is happening.  Usually, if there's an update or installation from an unauthenticated source, update manager will tell you it's an unauthenticated source and ask if you want to continue.  If you click "Yes" (or "OK" or whatever), the update will continue.  If you say you don't want to continue, the update won't happen and you'll get an error message.

So: is update manager asking if you want to go ahead, or is it just saying it can't continue because the update is from an unauthenticated source?  If it's asking whether you want to go ahead, click "Yes" and it'll go ahead.  I've never heard of the update manager just refusing to do an update from an unauthenticated source unless you've specifically said you don't want to continue.

---

### Post by PaulHA2 on 2011-01-19
Sorry for not being clear--It will not complete the update; instead, it cycles back to the update screen, I press the update button, it gives me the same message again.

---

### Post by t0p on 2011-01-19
As I've never encountered this myself, I can't give you a guaranteed solution.  But I would *suggest* that you open a terminal (**Applications > Accessories > Terminal**) and type in the command

```

sudo apt-get update

```

It'll ask for your password.  Type your password in - it won't appear on the screen as you type, but that's normal, it's a security measure.  Agree to anything it asks (by typing in Y).  If the update doesn't happen, copy all error messages and paste them into this thread.  The error messages will help us diagnose the problem.

---

### Post by t0p on 2011-01-19
As I've never encountered this myself, I can't give you a guaranteed solution.  But I would *suggest* that you open a terminal (**Applications > Accessories > Terminal**) and type in the command

```

sudo apt-get update

```

It'll ask for your password.  Type your password in - it won't appear on the screen as you type, but that's normal, it's a security measure.  Agree to anything it asks (by typing in Y).  If the update doesn't happen, copy all error messages and paste them into this thread.  The error messages will help us diagnose the problem.

---

### Post by zozio32 on 2011-04-22
I have a similar problem:

that's what i get from the shell:

```

...
Hit http://downloads.sourceforge.net all/main i386 Packages
Fetched 491B in 4s (116B/s)
Reading package lists... Done
W: GPG error: http://www.mendeley.com  Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D800C7D66F036044

```

is there a way to force it to go on with the update?

---

### Post by oldos2er on 2011-04-22
Mendeley's gpg key is here: [http://www.mendeley.com/repositories/xUbuntu_11.04/mendeleydesktop.key](http://www.mendeley.com/repositories/xUbuntu_11.04/mendeleydesktop.key)

---

