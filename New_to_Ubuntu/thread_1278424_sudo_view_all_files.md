---
title: "sudo view all files"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by whizzle on 2009-09-29
Hi ya gang, first post here! :)

I log in as a user and then I want to sudo as root so I can view ALL users on the system. For example, when I type *ls /home*. I'd expect to see ALL user's home directory and not just mine when I sudo. But sadly I can only see mine. Can anyone give me some pointers?

Cheers
\w/

---

### Post by sloggerkhan on 2009-09-29
Maybe you're the only user?
OTB you don't even need root perms to ls /home/

---

### Post by whizzle on 2009-09-29
Oh no...I'm positive I'm not the only user. If I login as root I can see many users. I just can't see them when I sudo.

---

### Post by Darkwing-Duck on 2009-09-29
If you want to view *all* files in a folder to include hidden ones you can use this flag on the ls command.
 
```
ls -a
```
 
For a list of flags that can be added you can type.
 
```
ls --help
```
 
Hope this helps you out a bit.
 
EDIT: Here is a good online list of what each thing does with the ls command.
 
[http://www.computerhope.com/unix/uls.htm](http://www.computerhope.com/unix/uls.htm)

---

### Post by slakkie on 2009-09-29
sudo find /home -type f -exec less {} + 

that is to see the contents of all files.
Remove the '-exec less {} +' if you only want to see what files are present.

Best of luck.

---

### Post by whizzle on 2009-09-29
nah....still not giving me what I need. Here's the scenario. 

There are 2 user's on the sytem: whizzle and fudcake. whizzle can sudo fudcake can't.
whizzle logs into the system and sudo's.
whizzle tries to change directory to /home/fudcake
system gives an error saying "No such file or directory"
root logs into the system and types /home/fudcake everything is fine.

How can whizzle login and sudo and get to fudcake without having to manually login as user root?
make sense? thanks guys :)

---

### Post by bwallum on 2009-09-29
how about> gksudo nautilus

---

### Post by hotstovejer on 2009-09-29
Check and see if whizzle is a member of the admin group. Also, file permissions on the folder might be restrictive. Unprivlidged users can hardly see anything.

---

### Post by lswb on 2009-09-29
I think "sudo -i", which will open a root shell, is what you want.

---

### Post by whizzle on 2009-09-29
> **hotstovejer said:**
> Check and see if whizzle is a member of the admin group. Also, file permissions on the folder might be restrictive. Unprivlidged users can hardly see anything.

hmm....how do I see if whizzle is a member of the admin group? whizzle is in the sudoers file with privileges of ALL just like root. 

as for gksudo...yea I think that would give me everything I need....however, i also kind of need a solution for my webserver online which is a distro of red hat without any GUI on in. But yeah, when on my home box gksudo gives me everything I need. :)

---

### Post by slakkie on 2009-09-29
I'm convinced that sudo find command should give you what you need... 

If it is not working, could you paste the output of the command?

---

### Post by sloggerkhan on 2009-09-29
it sounds like your permissions aren't default.

---

### Post by A_Fiachra on 2009-09-29
```


sudo cat /etc/sudoers


```

You probably don't have sufficient permissions to sudo *everything*.  Which makes sense almost all of the time except when you own the machine.

---

### Post by whizzle on 2009-09-29
> **slakkie said:**
> I'm convinced that sudo find command should give you what you need... 
If it is not working, could you paste the output of the command?
sure
```

joshm@----.com [~]# sudo ls /home/joshuamu
Password:
ls: /home/joshuamu: No such file or directory
joshm@-----.com [~]#

```visudo
```

joshm ALL=(ALL) PASSWD:ALL

```

---

### Post by cranecreek on 2009-09-29
Do what [lswb]("http://ubuntuforums.org/member.php?u=210286") said:

```
sudo -i
```That will make you root then you can do as you wish

---

### Post by whizzle on 2009-09-29
i've been wanting to avoid that as I've read it isn't a preferred thing to do so....If it's the only option so be it. 

i do appreciate the help so far guys! Today is around my 4th day of running Linux (Ubuntu) and I don't see myself switching back to M$ anytime soon...only for stuff linux doesn't have like Adobe CS products. Cheers :)

---

### Post by Miljet on 2009-09-29
> .however, i also kind of need a solution for my webserver online which is a distro of red hat without any GUI on in

Perhaps the above quote offers the answer. It is my understanding that sudo only works for Ubuntu, and derivatives.

---

### Post by sloggerkhan on 2009-09-29
> **Miljet said:**
> Perhaps the above quote offers the answer. It is my understanding that sudo only works for Ubuntu, and derivatives.

Sudo can be set up to work on other distros. However, it is not OTB configured on most red hat set ups.

---

### Post by whizzle on 2009-09-30
ok...all the solutions here work great for my Ubuntu set up. Thanks guys! And here is a quote from my web host, it doesn't look like something I'll pursue too much....sigh.
>   [FONT=&quot]Since multiple users will need permissions to multiple directories, the best way would be to create a group and add the users to the group. However, we'll still need to change the group-ownership and group permissions on every file and directory you'd like them to have access to. Depending on your Apache setup, this might interfere with running your domain's software- particularly PHP scripts[/FONT]

---

### Post by starcannon on 2009-09-30
When adding a new user using the:
System>Administration>Users and Groups 
widget, the default is to make all new users **Desktop Users**. The easiest solution is, to log in with the current sudo capable *Administrator* account, open up the Users and Groups application, unlock the application, select the user that needs Administrator privileges, click on **Properties**, click on the **User Privileges** tab, tick all the boxes, click **Okay**, close the Users and Groups window, Log out, Log into the user you just escalated permissions for, and sudo should now be working.

GL and HF

---

### Post by slakkie on 2009-09-30
> **whizzle said:**
> sure
```

joshm@----.com [~]# sudo ls /home/joshuamu
Password:
ls: /home/joshuamu: No such file or directory
joshm@-----.com [~]#

```visudo
```

joshm ALL=(ALL) PASSWD:ALL

```

Sir, that is not sudo **find**.

---

### Post by whizzle on 2009-10-07
turns out the user was in a "jailshell." put him in a regular shell and everything is fine now.

cheers

---

