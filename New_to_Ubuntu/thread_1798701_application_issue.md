---
title: "application issue"
date: 2011-07-06
forum: New to Ubuntu
---

### Post by azhar_kashif2k on 2011-07-06
When i login with domain user the installed application in administrator or root account will not appear in all login's

---

### Post by ajgreeny on 2011-07-06
> **azhar_kashif2k said:**
> When i login with domain user the installed application in administrator or root account will not appear in all login's
??

I do not understand your question, if it was a question!

---

### Post by Perkins on 2011-07-06
I'm not sure if I understand, but I think you might be asking why you can't run administrative applications when logged in with a domain account...

The answer is that the domain account is different from the local account with the same name.  If you want the domain account to have admin rights, you'll need to add it to the list of admin users.

---

### Post by azhar_kashif2k on 2011-07-07
> **Perkins said:**
> I'm not sure if I understand, but I think you might be asking why you can't run administrative applications when logged in with a domain account...

The answer is that the domain account is different from the local account with the same name.  If you want the domain account to have admin rights, you'll need to add it to the list of admin users.

Can you please help me how to add domain users to admin account

---

### Post by Perkins on 2011-07-07
Unfortunately I am no longer running a machine on a domain, and my memory is a bit fuzzy.  However, the first thing to do is to figure out the name the account is using to identify itself to the system.  The whoami command should work, I think.  Then edit /etc/group and add the name to the admin group.  The names are separated by commas.  You may have to use \\ in place of \ in the name as \ is an escape character.  Or maybe not...  I don't remember for certain which way it worked out.  It *is*, however, case sensitive.

Alternatively, or as a time saver if you have more than one account that needs privileges,  domain groups such as the domain administrator group will show up with the groups command.  You can then use the visudo command to add an entry to the sudoers file allowing members of particular domain groups root privileges.  You can either duplicate the entry for the admin group, changing the name to match the domain group name, or see "man sudoers" for a more precise description of what you can do with it.  There are a lot of possibilities, including only allowing certain commands to be run, not needing to enter a password, changing the user they can pretend to be to something other than root, et cetra.

---

