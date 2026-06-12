---
title: "Adding domain user to the local admin (root) group?"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by kmille on 2009-06-16
Recently I have been researching how to add a domain user to the root group of the Linux machine I have built with 9.04 Jaunty on it. But to no avail, Can anyone help me with this?

Will greatly appreciate any and all help that i will receive
Thank you

---

### Post by DustyMP on 2009-06-29
Go to system -> administration -> users and groups. Click unlock and enter the password. Select the user you want to promote and click properties. On the last tab, advanced, you can select the users group membership.

EDIT: Just my two cents. Just blindly adding people to the root group may not abide the best practices of least privilege. On the third tab of the user's properties dialog you can add and remove some specific privileges if that would help =)

---

### Post by Tnoty on 2010-02-20
You can also add existing user to existing accounts using the Command Line Interface.
To add a group from the command line, use the *addgroup* utility. 
For example:[FONT=monospace][/FONT]  sudo addgroup accounts

To add an existing user to an existing group:[FONT=monospace]
[/FONT]
[FONT=monospace][/FONT]sudo adduser john accounts

---

### Post by mcduck on 2010-02-20
If you want to give the user same privileges as the normal admin users on Ubuntu have, you don't want to add them to "root" group, but instead to "admin" group.

---

