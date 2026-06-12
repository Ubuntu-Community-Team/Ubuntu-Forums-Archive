---
title: "Why does chmod do nothing?"
date: 2010-10-06
forum: New to Ubuntu
---

### Post by bubbla on 2010-10-06
Hiya.  I'm logged into a university computer through Putty, trying to familiarize myself with Linux and trying out some commands.  It runs Ubuntu 10.04.1 LTS.  As a student, I get my own directory on the server for storing files.

After typing ls -l, I get 
```
-rwx------  1 [username] domain users 7 2010-04-10 21:32 blah.txt

```I tried out various uses of chmod, including ```
chmod g=rw blah.txt
```  When I do the ls -l again, nothing has changed.  I thought it might be because I don't have permission to change file access, but I googled about that and it turns out the owner of the file has permission to change file access, which is me.  So why wouldn't I be able to change it?

It's really weird because it doesn't give me an error message of any kind.  It just does nothing, which implies that it thinks I've put in a valid command to do something I have permission to do and it thinks it has executed my command.

Any insight and I would be grateful.

---

### Post by mikewhatever on 2010-10-06
It looks like blah.txt is not owned by you, unless of cause 'domain' is your username. Create a file first (with nano) then use chmod on it.

Edit: Just saw you have [username] there. Perhaps students are not allowed to execute chmod at all.

---

### Post by robsoles on 2010-10-06
Welcome to UF.

> **man+chmod][INDENT]A  combination  of the letters ugoa controls which users' access to the
file will be changed: the user who owns it  (u),  other  users  in  the
file's group (g), other users not in the file's group (o), or all users
(a).  If none of these are given, the effect is as if a were given, [B]but
bits that are set in the umask are not affected[/B].[/INDENT][/quote]
I think the administrator of the system you are playing with may have set umask to '700' for their users and this will mean that users cannot make their files available to others.

The command you show is to set group permissions on the file, you may only be able to effect user permissions in the directory you are working in. Read up on umask and ask your administrator if they are using to restrict which permissions you are allowed to set like that.

I've been wrong before, others know more than I do - if I am wrong somebody will point out my error(s) in a post to come.




[QUOTE=mikewhatever said:**
> It looks like blah.txt is not owned by you,  unless of cause 'domain' is your username. Create a file first (with  nano) then use chmod on it.

OP seems to be saying they own the file fairly clearly, I think they modified the output of ls -l to hide their username.

---

### Post by BugBuster on 2010-10-06
> As a student, I get my own directory on the server for storing files.
Is this directory on a linux partition eg ext2/3/4?

---

### Post by bubbla on 2010-10-06
> **robsoles said:**
> Welcome to UF.Thanks! :)


> **robsoles said:**
> I think the administrator of the system you are playing with may have set umask to '700' for their users and this will mean that users cannot make their files available to others.

The command you show is to set group permissions on the file, you may only be able to effect user permissions in the directory you are working in. Read up on umask and ask your administrator if they are using to restrict which permissions you are allowed to set like that.Okay, I read up on it and it seems as though umask is what sets the default settings.  So wouldn't the use of chmod override it?

> **BugBuster said:**
> Is this directory on a linux partition eg ext2/3/4?I don't actually know what that means, but according to [the stickied thread]("http://ubuntuforums.org/showthread.php?t=1422475"), you need sudo access to get hardware information, right?

---

### Post by Morbius1 on 2010-10-06
Maybe I'm missing something here but you are accessing a directory set up by your SysAdmin for your particular use. 

umask ( used in this context ) is a system wide setting and you will in fact have to become root to change it but it's the remote system's root you need to become not your own. Unless your SysAdmin has lost his mind you don't know root's password.

I think mikewhatever and  robsoles have the best guess:
>  Edit: Just saw you have [username] there. Perhaps students are not allowed to execute chmod at all.     > I think the administrator of the system you are playing with may have  set umask to '700' for their users and this will mean that users cannot  make their files available to others.Talk to you SysAdmin about what it is you're trying to do.

---

