---
title: "Can't log in Empathy"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by colau on 2009-08-15
Hi,
If i put the password of yahoo id and click the close button, it prompts /usr/bin/empathy locked ,give the password.
If i give the password, nothing happens.
It prompts me again and again.
Nothing to do.

---

### Post by philinux on 2009-08-15
Try log out then in and use empathy again.

---

### Post by colau on 2009-08-15
> **philinux said:**
> Try log out then in and use empathy again.
```

"**Enter password for default keyring to unlock"**

```
This is the message i'm getting.
And the password for yahoo account is automatically reset to seven digits.
```

Empathy 2.26.1

```

---

### Post by colau on 2009-08-15
Authentication failed.
Do I have to type like "example@yahoo.com" of "example" for yahoo id?

---

### Post by colau on 2009-08-15
> **philinux said:**
> Try log out then in and use empathy again.
May be , it's a bug for older version.

---

### Post by colau on 2009-08-15
Bump.
What's the reason?Can't login in empathy.
Authentication failed.

---

### Post by philinux on 2009-08-15
For yahoo it's just example, not example@yahoo....

---

### Post by colau on 2009-08-15
> **philinux said:**
> For yahoo it's just example, not example@yahoo....
Yes,but it's not working.

---

### Post by peakshysteria on 2009-08-17
Same problem with my **hotmail** account. I where prompted to add the password to a keyring. I added the password and then: Authentication failed. Only option is to edit account. Which give me the same problem. Iget:

```
Allow application access to keyring?

The application 'Application' (/usr/lib/telepathy/mission-control) wants to access the password for'Password for account msn3' in the default keyring

Deny Allow Once Always Allow
```

Anyone?

---

### Post by juanoleso on 2009-08-17
just for the sake of clarity, when it asks for the keyring password, are you putting in the yahoo password or your ubuntu password?  You should try your ubuntu user password if you haven't already.

I don't know what empathy is, but I do use the keyring manager program...

---

### Post by peakshysteria on 2009-08-18
*bump*

---

### Post by inpxfx on 2009-10-15
::heres the fix ::

Go to EDIT /Accounts/ there should be an account called "PEOPLE NEAR BY" to the Right of this is a little trash icon click it and get rid of that account and it shouldnt ask for the password to the keyring anymore. thats how i fixed it.

---

### Post by hangnguyen on 2009-12-11
I have same proplem

I found that issue because Guarddog firewall . I can add accounts when I turned off the Guarddog firewall , after add accounts you may turn on firewall and using Empathy normaly .

hope this help .

---

### Post by jarbiscuit on 2010-04-02
as for me, i had the same problem with authentication failed.

at username, instead of putting [email]xxx@yahoo.com[/email], i put xxx
and password is as my yahoo password.

hope that's help!

---

### Post by @rizz on 2010-04-02
Yipeee

 Guys i know this one (had the same problem)

 Heres the fix:

 1. Delete the default keyrings:p


either use terminal:

```
rm ~/.gnome2/keyrings/default.keyring
```

**Or **

For GUI

go to 

**Navigate to Places > Home.  Press ctrl-h for "hidden files".  Navigate to .gnome2 > keyrings.  Delete default.keyring file.   **

then try to login again

**Remember**

[COLOR=Red]it will ask you for the new keyring, just put anything u want but remember it![/COLOR]

---

### Post by kishorr on 2010-04-27
im able to log in wit my google account but when i log in with my yahoo it says, network error... :-(

---

