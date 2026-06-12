---
title: "trying to understand crontab entry for sysstat"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by geppetto1 on 2011-02-11
I'm trying to understand a crontab entry for sysstat.  The entry is from /etc/cron.d/sysstat:

*/10 * * * * root command -v debian-sa1 > /dev/null && debian-sa1 1 1


What I know:

*/10 * * * *     - execute command every 10 minutes
&&                   - we're executing multiple commands consecutively
debian-sa1 1 1  - execute 'debian-sa1 1 1' executes 'sa1' and passes '1 1' to sa1 as options.

also, from the debian-sa1 file -  Debian sa1 helper which is run from cron.d job, not to needlessly fill logs (see Bug#499461).  I'm guessing that the bug is responsible for the existence of 'debian-sa1'

What I don't understand:

root command -v debian-sa1 > /dev/null 

...could be that ' debian-sa1 > /dev/null' is the first command, but then I don't understand 'root command -v'

...more likely that 'root command -v debian-sa1 > /dev/null' is the first command, but then I still don't understand 'root command -v'

maybe what I'm asking is - what is the purpose of  'root command -v' ?

My knowledge is both dated (SVR4) and faded so any help would be appreciated.  Hopefully I picked the proper forum for a question of this type.

Thank you and regards.

---

### Post by gmargo on 2011-02-11
> **geppetto1 said:**
> 
```

*/10 * * * * root command -v debian-sa1 > /dev/null && debian-sa1 1 1

```what is the purpose of  'root command -v' ?

Referencing the **crontab(5)** man page: for a system cron file, the columns are:
```

# m h dom mon dow user    command

```so "root" is the user id under which the command is run.

Referencing the **dash(1)** man page: the shell builtin command named "command" has this syntax for -v:
> 
command [-p] [-v] [-V] command [arg ...]
            Execute the specified command but ignore shell functions when searching for it.  (This is useful when you have a shell function with the same name as a builtin command.)
...
            -v     Do not execute the command but search for the command and print the absolute pathname of utilities, the name for builtins or the expansion of aliases.
So "command -v debian-sa1" says "find the command named 'debian-sa1' on the $PATH (which includes /usr/lib/sysstat) and print the full pathname.  Actually the pathname is ignored ("> /dev/null") and only the return code is checked ("&&"). And if the return code is zero, which means the command was found, then it is run ("debian-sa1 1 1").

---

### Post by geppetto1 on 2011-02-17
Thank you for your reply and detailed explanation of the command!  

The links to the crontab and dash man pages are really appreciated.  I had referenced some web pages describing the crontab (not the man page) and had not seen a reference to the user id. 

I never would have found the dash man page without your assistance and am not sure I would have understood the command without your explanation.

Thank you.

---

