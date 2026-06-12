---
title: "What is a networking keyring? and what to do about it."
date: 2011-06-14
forum: New to Ubuntu
---

### Post by nash black on 2011-06-14
Hi all,
 
I am setting up a login on my Ubuntu laptop for my mom to use while she is visiting a friend. 
 
When she tries to access the wireless network, it asks for a wireless keyring password (forgive me for not knowing the exact message, I am not there with her). 
 
Could someone explain to me what a wireless keyring is and why it is asking for it? It appears to be asking for a password other that the wireless network password... Correct?
 
When she logs in to my account, it doesn't ask for the keyring password. At this point both accounts are administrators, but I had her change her's to administrator from a custom user to see if that would help the problem. No such luck.
 
Thanks,
Nash

---

### Post by wolfen69 on 2011-06-14
All I know is that when I initially set up my wireless connection, it asks for my user password after I input the encryption key. I leave it blank, and then it says "are you sure you want unsafe storage?" I say yes, and it never bothers me again, and the wireless connects automatically every time.

---

### Post by doas777 on 2011-06-14
ok, heres the skinny.

at some point you asked ubuntu (Network-Manager probably) to store a password.

since storing passwords in plain text is a no-no, ubuntu encrypts them, and places them on a "keyring". a keyring is nothing more than a set of keys (passwords) that are administered by a single application (in this case seahorse, but thats beside teh point).

so since the passwords are encrypted, you need to decrypt them before they can be used. 

usually,  when a ubuntu user logs in, their keyring is automatically unlocked, and their keys are accessible. however if you enable auto-login to your desktop, your keyring will not be unlocked until you attempt to access a password. when this happens you will be asked for your keyring password. 

your default keyring password should be the same as your desktop password, but if it isn;t you can set it to be:
[http://www.ubun2.com/question/392/how_change_default_keyring_password_ubuntu](http://www.ubun2.com/question/392/how_change_default_keyring_password_ubuntu)

---

### Post by nash black on 2011-06-15
Thanks, that makes sense. Do you know why it might show up without auto-login enabled. It doesn't automatically log in to that or any other account. Her account just doesn't have a password... Or does that count as auto-login?

---

### Post by JohnBonne on 2011-06-15
> **nash black said:**
> Thanks, that makes sense. Do you know why it might show up without auto-login enabled. It doesn't automatically log in to that or any other account. Her account just doesn't have a password... Or does that count as auto-login?

Log out and log back in using her password if you don't want to configure your logon to _always_ contain her information. Otherwise go Control Center  >Login Screen and set up the logon information to be shown.

To Set up a different logon for yourself, Go to Users and Groups in Control Center. You may need Administrative privileges.

Login using a guest account. You still have to log out. and log back in. Go to the log out button at the top right and enter Guest Session.

Regards,

---

### Post by doas777 on 2011-06-15
> **nash black said:**
> Thanks, that makes sense. Do you know why it might show up without auto-login enabled. It doesn't automatically log in to that or any other account. Her account just doesn't have a password... Or does that count as auto-login?
yeah, an empty password won't work.
when you use an empty password, seahorse should default to "unsafe storage" mode, where it does not encrypt the passwords when they are at rest. check the link above, and set your default keyring to blank, just like the password. it will prevent the promtps, but will allow anyone who can get access to the laptop to get access to all the passwords on the keyring. not great, but is often secure enough, as long as you control who has access to the box.

---

