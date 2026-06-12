---
title: "how do I receive system mail"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by aBitLater on 2009-02-05
I want to receive system mail, in case there is a system message that I should know about.

But, I don't want or need to have my laptop be a mail server or be set up to access anything outside.

How do I do this?

Thanks.

---

### Post by blueridgedog on 2009-02-06
You should be able to get mail sent to root with the following.  First, install the command line mail tools:

```
sudo apt-get install mailutils
```

Second, tell the system to send root's mail to you by editing the /etc/aliases file:

```
gksudo gedit /etc/aliases
```

Add an entry at the bottom directing root's mail to your account

```
root: YOURACCOUNT
```

Save, then rebuild the aliases file:

```
sudo /usr/bin/newaliases
```

You should be able to check mail sent to you and root now with the command:

```
mail
```

Note that the mail program is a bit rough around the edges if you are not an ubergeek, so you may want to read about it with:
```

man mail
```

If the command line mail tool is too rough, this link describes how to access these messages with evolution:

[http://ubuntu.wordpress.com/2006/05/25/read-emails-from-your-system-using-evolution/](http://ubuntu.wordpress.com/2006/05/25/read-emails-from-your-system-using-evolution/)

---

### Post by taseedorf on 2009-02-06
read up on the program cron.....  that will do it for you.
it can do locally or remotely.

type mail when logged in too in the terminal

---

### Post by aBitLater on 2009-03-02
thanks!....

mailutils seems to be what I need.  Will check into cron later.

---

### Post by brian_p on 2009-03-02
> **aBitLater said:**
> 

mailutils seems to be what I need.

mailx is an alternative to mailutils. Fewer dependencies, if that matters to you.

---

