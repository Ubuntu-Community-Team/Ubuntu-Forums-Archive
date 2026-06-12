---
title: "Changing default keyring pasword"
date: 2009-06-14
forum: New to Ubuntu
---

### Post by pablo66 on 2009-06-14
When I first login and attempt to connect to my wireless network I'm prompted for a default keyring password by the network manger, how do I change this password and is there a way to login to the network automaticly without compromising security?

---

### Post by lovinglinux on 2009-06-14
Follow this:

> **mcduck said:**
> 
Changing/removing the keyring password is quite easy to do (no need to remove the current keyring or mess with user accounts):

1. open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Edit/Preferences

3. On the Password Keyrings-tab select the "login"-keyring & click "Change Unlock Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password is to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

Since you are apparently new here, I would like to give you a tip. This subject is very common and there are tons of posts about it in the forums. To search for them you can use Google Site Search. This type of search, which includes a string for the web site you want to search, gives you only results related to the chosen site. For example you could search for "keyring password site:ubuntuforums.org". It will give [these results](http://www.google.com/search?q=keyring password+site:ubuntuforums.org&hl=en&sourceid=mozilla-search&num=20&start=0&start=0).

---

