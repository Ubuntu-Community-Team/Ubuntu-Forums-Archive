---
title: "NM applet and Feisty"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by eg-maverick on 2007-04-23
I upgraded from 6.10 to 7.04. Am I supposed to remove the NM Applet and use what comes with Ubuntu now? I have the wireless interface commented out in the /etc/network/interfaces file. Do I need to uncomment that? Will wireless now work without having to enter keyring every time?
Thanks,
Craig

---

### Post by eg-maverick on 2007-04-24
[tap tap tap] Is this thing on?

---

### Post by Floppyjoe on 2007-04-24
> **eg-maverick said:**
> I upgraded from 6.10 to 7.04. Am I supposed to remove the NM Applet and use what comes with Ubuntu now? I have the wireless interface commented out in the /etc/network/interfaces file. Do I need to uncomment that? Will wireless now work without having to enter keyring every time?
Thanks,
Craig
There is a way to get around the keyring issue I think. If you search the forum for Pam keyring you should be able to find something of use.

---

### Post by eg-maverick on 2007-04-24
> **Floppyjoe said:**
> There is a way to get around the keyring issue I think. If you search the forum for Pam keyring you should be able to find something of use.

I tried the solution presented in [http://ubuntuforums.org/showthread.php?t=316927&highlight=network+manager+keyring](http://ubuntuforums.org/showthread.php?t=316927&highlight=network+manager+keyring)
but it doesn't change anything. I still have to enter the keyring password each time I change wireless networks.

---

### Post by Floppyjoe on 2007-04-24
> **eg-maverick said:**
> I tried the solution presented in [http://ubuntuforums.org/showthread.php?t=316927&highlight=network+manager+keyring](http://ubuntuforums.org/showthread.php?t=316927&highlight=network+manager+keyring)
but it doesn't change anything. I still have to enter the keyring password each time I change wireless networks.
Are you using the same keyring password and User password? They both have to be the same or it won't work.

---

### Post by eg-maverick on 2007-04-25
> **Floppyjoe said:**
> Are you using the same keyring password and User password? They both have to be the same or it won't work.

I'm confused. Line 4-6 says that it is for when the password is different. My keyring password is different than my login. If I do want to change my keyring password, how do I do that?

---

### Post by eg-maverick on 2007-05-02
I'm still without a solution. I have done extensive searches on the ubuntuforums and the web. Some solutions claim to be applicable only if the login and keyring passwords are the same. If so, how do I change the keyring password? 
Craig

---

### Post by tbc on 2008-04-21
eg-maverick, I was looking for a solution to this tonight. I think I found one. Does the "[Stop having to enter keyring over and over again]("http://ubuntuforums.org/showpost.php?p=2776815&postcount=1")" thread help you?

---

