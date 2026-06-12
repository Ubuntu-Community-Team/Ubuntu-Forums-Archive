---
title: "Bash script symlink gvfs"
date: 2010-08-19
forum: New to Ubuntu
---

### Post by jblaty on 2010-08-19
Having an issue with a shell script using bash.

Here's the command I'm trying to execute, which works just fine at the command line (logged on as a user):
```
ln -s "/home/user/.gvfs/sharename on 192.168.0.100" /home/user/linkname
```

I'm trying to automate this in a startup script.  I'm assembling components of this command using environment variables, remote IP addresses, etc.  For simplicity, I have stripped this down to the bare minimum to illustrate the issue.

The following **_doesn't work_**:
```
#!/bin/bash
cms='ln -s "/home/user/.gvfs/sharename on 192.168.0.100" /home/user/linkname'
`$cms`

```

This leads to the following result:
ls: cannot access linkname: No such file or directory

The following **_works_**:
```
#!/bin/bash
`ln -s "/home/user/.gvfs/sharename on 192.168.0.100" /home/user/linkname`

```

In other words if I simply hard code the command, and I don't execute it using a variable, the command works.

Any ideas of what I'm doing wrong?

---

### Post by Rushyang on 2010-08-19
As far as my concepts, there is little difference using ` ` and $. 

1) Use of ` `
When you use any binary or executable file or let's say a command. Which is available in one of your PATH. You need to use ` ` if you want to assign those final values to any other variable. 

For example..
> 
echo `date +%d%m%Y`
or
today=`date +%d%m%Y`
and then
echo $today

Where "date" is command, being accessed from one of your PATH... /bin/.
> which date

2) Use of $
As far as I know, you can't use ` ` for any of your created variable.

When you create a variable let's say

> myvar=100when you say echo `myvar` it will say command not found. 

when you're creating any variable it is stored into 'set' for that particular terminal. 
>  set | grep myvarand which are your variables, can be used by $... and not ` `.

---

### Post by jblaty on 2010-08-19
Thanks for the response.  Still have the same issue.

Remove the backticks:
```
#!/bin/bash
cms='ln -s "/home/user/.gvfs/sharename on 192.168.0.100" /home/user/linkname'
$cms
```

==> ln: target `/home/user/linkname' is not a directory

```
#!/bin/bash
ln -s "/home/user/.gvfs/sharename on 192.168.0.100" /home/user/linkname
```

==> WORKS

I need to properly assemble the command into a variable, and pass that command to the shell for processing.  Quite apparently, it's not working the way I'm doing it.

---

### Post by jblaty on 2010-08-20
...Any other suggestions?

---

### Post by Rushyang on 2010-08-20
I don't understand that if the direct command is working then why do you want to use a variable?

---

### Post by jblaty on 2010-08-20
I am assembling the syntax in a variable.  Certain components of the command line come from different places (and variables).  I'm only hard coding the entire command line to illustrate my issue.  I can't hard code the command line into the script.  I need to assemble it into the variable, and then pass it for execution to bash.

---

### Post by David Andersson on 2010-08-20
> **jblaty said:**
> 
The following **_doesn't work_**:
```
#!/bin/bash
cms='ln -s "/home/user/.gvfs/sharename on 192.168.0.100" /home/user/linkname'
`$cms`

```

This leads to the following result:
ls: cannot access linkname: No such file or directory


One of the problems is that the quotes ("") around the filename is not removed when $cms is expanded by the shell. The link will point to a non-existent file. I think eval will work better in this case:

```
eval $cms
```

There might be other problems. E.g. I don't understand why the error message seems to be from "ls". Are you hiding something from us?

---

### Post by jblaty on 2010-08-20
I'll give eval a shot, thanks.

Nope, that's exactly the error message.

---

### Post by jblaty on 2010-08-20
THANK YOU!

eval WORKED just fine.:KS

---

