---
title: "Here is a sample Ubuntu set-up"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by cat2005 on 2009-08-15
Here is a sample Ubuntu set-up; I have been thinking about this:

_Users:_

1) Larry:  
Is the only account with root / admin access. He can "sudo". If possible, I would like to disable "sudo do" on this account but doing so is not required. This account will be part of the necessary group to access my virtual box guest OS

2)  Curly:
My regular user account. This account does not have root / admin access. This account will be part of the necessary group to access my virtual box guest OS.

3)  Moe:
A guest account.  This account does not have root / admin access and will not have virtual box access.

_My questions:_
[I]
A)  Is this set-up possible?
B)  If possible, then how difficult to implement?[/I]

Thanks.

---

### Post by credobyte on 2009-08-15
Lary - default account ( sudoer )
Curly - group 1, limited ( access to VirtualBox )
Moe - group 2, limited ( no access to VirtualBox )

This should help you to implement this: [http://www.freesoftwaremagazine.com/articles/users_in_ubuntu](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu)

---

### Post by cat2005 on 2009-08-15
> **credobyte said:**
> Lary - default account ( sudoer )
Curly - group 1, limited ( access to VirtualBox )
Moe - group 2, limited ( no access to VirtualBox )

This should help you to implement this: [http://www.freesoftwaremagazine.com/articles/users_in_ubuntu](http://www.freesoftwaremagazine.com/articles/users_in_ubuntu)



credobyte, et al:

I looked at the website you gave.  However, it is several years old so I have a few questions:

a)  If I understood correctly, only the 1st user created has "root" access.  All subsequently created users do not have "root" access unless specifically given "root" access.  Is this summary correct?

---

### Post by credobyte on 2009-08-15
> **cat2005 said:**
> credobyte, et al:

I looked at the website you gave.  However, it is several years old so I have a few questions:

a)  If I understood correctly, only the 1st user created has "root" access.  All subsequently created users do not have "root" access unless specifically given "root" access.  Is this summary correct?

Yes. Basically, "root access" means that he's on a list of sudo'ers. If you create a new, limited account, they will have no access to system settings and sudo by itself.

---

### Post by cat2005 on 2009-08-15
> **credobyte said:**
> Yes. Basically, "root access" means that he's on a list of sudo'ers. If you create a new, limited account, they will have no access to system settings and sudo by itself.


So I would not have to be concerned about a "limited user" having the ability to "sudo" or otherwise gain "root" access, correct?

---

### Post by theozzlives on 2009-08-15
1. would be able to access users & groups and should add him/her self to the vboxusers group along with #2 but not #3. Therefore #3 will not be able to access the VirtualBox. In 9.04 it's Desktop User, not "Limited".

---

### Post by cat2005 on 2009-08-15
> **theozzlives said:**
> 1. would be able to access users & groups and should add him/her self to the vboxusers group along with #2 but not #3. Therefore #3 will not be able to access the VirtualBox.


But neither #2 nor #3 could "sudo" or otherwise use "root" level unless #1 specifically allows them to do so.  Correct?

---

### Post by theozzlives on 2009-08-15
> **cat2005 said:**
> But neither #2 nor #3 could "sudo" or otherwise use "root" level unless #1 specifically allows them to do so.  Correct?

Only Administrator (#1) can sudo. I had to run upstairs cause I have 9.04 there to see, it's called Desktop User. You have 3, Admin, Desktop, and Underprivileged.

---

### Post by cat2005 on 2009-08-15
> **theozzlives said:**
> Only Administrator (#1) can sudo. I had to run upstairs cause I have 9.04 there to see, it's called Desktop User. You have 3, Admin, Desktop, and Underprivileged.


Thank you!

---

