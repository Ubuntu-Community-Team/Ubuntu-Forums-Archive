---
title: "880514 - my privilege"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by hamidi on 2009-08-04
hi
i installed vmware workstation on my Windows. for this purpose after downloading and installing ubuntu-9.04-desktop-amd64.iso, i need to install vmware tools for my virtual ubuntu machine.
running vmware-install.pl made the following error:
```
Please re-run this program as the super user.
Execution Aborted.

```
when installing it asked me one username and password which i'm currently login with. if i'm not the super user what user may be? i thought, like Windows, the users which are asked to be entered during installation of the OS, they get admin. but it seems that they don't.
in another hand, i didn't enter any password for user root. it didn't ask me to enter. so i don't know what's the password of root.
su - also didn't help. it says Authentication failure.
i enter right password for the username i created while installing (hamidi). otherwise i couldn't enable some locked features.
in another hand, i selected not to have to enter my password to login while there's no other user.
thanx for any idea

---

### Post by llamabr on 2009-08-04
Hi.  to run things as super user in ubuntu, you issue 

```
sudo
```

before the command (to get SU to DO it).  So if I want su to open, e.g., firefox, I'd do:

```
sudo firefox
```

This applies to the error you're receiving, too

---

### Post by hamidi on 2009-08-05
thx it worked :)
but why the prompt is not '#' by default?!

---

### Post by DrDevice on 2009-08-05
> **hamidi said:**
> but why the prompt is not '#' by default?!
Linux is based off of Unix, which was originally a mainframe computer OS meant to have multiple users on different terminals running at the same time.  The "#" prompt indicates you are currently logged in as **root**, which for all intents and purposes is God for that system.  Root can do anything, change anything, delete anything.

Of course, you don't want your regular users to have that ability.  Ya never know, student X might want more space for a project, and deletes files that the computer needs to run.  Not only has he borked himself, he's borked all the other users as well.  So normal users get only a certain amount of permissions, depending on what they're doing and where in the computer they're doing it.

Ubuntu & other Linux distros keep that idea, requiring system changes to be run by root or a user given those permissions.  You _*can*_ make your normal account have those permissions, but then anyone who sits at your computer could accidentally delete or change something very important.  By requiring the extra action of going through the superuser, it drastically improves security & safety of the system.  Unless you're an obsessive tweaker (like me!), once you have your system all set up the way you want you'll rarely have to use **su** or its GUI equivalent **gksu** to get things done.

Hope this answers your question. =)

---

### Post by tarps87 on 2009-08-05
> **llamabr said:**
> Hi.  to run things as super user in ubuntu, you issue 

```
sudo
```

before the command (to get SU to DO it).  So if I want su to open, e.g., firefox, I'd do:

```
sudo firefox
```

This applies to the error you're receiving, too

Just a quick point sudo firefox is a bad idea, so is running any program with super user privileges unless it is necessary

---

### Post by hamidi on 2009-08-05
sure, thank u for such a complete description :)

---

