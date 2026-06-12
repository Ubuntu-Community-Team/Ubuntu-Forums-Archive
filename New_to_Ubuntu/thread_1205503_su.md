---
title: "su"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Wyvernoid on 2009-07-06
How to use this command? When I enter it in a Terminal, it prompts me for a password. I guess that this is the password of the user account I entered during installation, but when I enter it, I get "su: Authentication failure". What should I do?

---

### Post by lisati on 2009-07-06
Just type your password in as normal. It won't show, this is a normal Ubuntu security precaution.

You might also want to have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jman6495 on 2009-07-06
if possible you should use sudo and not su,
may i ask why you are using su?

---

### Post by Wyvernoid on 2009-07-06
First, thanks for the quick reply =]

Yeah, I did enter my own password, and it works for sudo, but not su. Is it because I have an exclamation mark in my password?

Oh and to the above poster, it says so in a software manual (VMware tools).

---

### Post by Zack McCool on 2009-07-06
No.  It's because su is to switch to the user "root", which (by default in Ubuntu) is disabled.  The password it is asking for is root's password, and there isn't one.

There are a few paths you can use.

The preferred is to use ```
sudo -i
``` Which will give the same result as su, but uses your password instead of root's.

The less preferred method (from a security standpoint) is to enable the root account.  I prefer not to give those directions, though they are available all over the place, including in the link given to you above.

---

### Post by frunns on 2009-07-06
AFAIK su doesn't work just like that in Ubuntu, if you really need that functionality you have to
```
sudo su
```

---

### Post by Wyvernoid on 2009-07-06
Oh.. okay, will try that. Thanks for the information.

---

### Post by sadaruwan12 on 2009-07-06
In ubuntu root is disabled and your given user account this account is what you create when you install ubuntu. Unlike most of other distros ubuntu keeps his root hiden for much better security if you really want to get root permissions to run some kind of a command then use "SUDO" for that what "SU" does is turn you in to the root. But root being disabled you want get that accesses but this is not the case to be in fedora or most of other releases.

---

### Post by ad_267 on 2009-07-06
Using "sudo su" isn't recommended, you should use "sudo -i" which will have the same result.

This page is a good resource: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by frunns on 2009-07-06
> **ad_267 said:**
> Using "sudo su" isn't recommended, you should use "sudo -i" which will have the same result.

This page is a good resource: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
Good to know!

---

