---
title: "Gdesklets not working. Help!!!"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by nyxm on 2010-06-07
> Starting gdesklets-daemon...
Connecting to daemon [  ###        ]
==========================================================[06/07/10-06:11:47]===
Could not import tiling module!


Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.
This is what happens when I try to start gdesklets. If anyone know where the log file would be I would gladly post it.

---

### Post by 3ar1 on 2010-06-10
If got the same problem here :(

Invoking gdesklets check results in: 

```
gdesklets check
Checking requirements:
 - sys ... found
 - xml.parsers.expat ... found
 - xml.sax ... found
 - gtk ... found
**
ERROR:/build/buildd/pyorbit-2.24.0/src/pyorbit-utils.c:39:_pyorbit_escape_name: assertion failed: (keyword_mod != NULL)
 - ORBit ...Aborted
```

Seems to be a problem with pyorbit.

---

### Post by picarune on 2010-06-10
Me too.  Same errors, same fault in pyorbit.  

Solution anyone?  Is there an earlier version we can fall back to?

Is it possible to insert a value instead of null in:

ERROR:/build/buildd/pyorbit-2.24.0/src/pyorbit-utils.c:39:_pyorbit_escape_name: assertion failed: (keyword_mod != NULL)
 - ORBit ...Aborted

---

### Post by shinzo on 2010-07-22
gdesklets not running because "Could not import tiling module!"? Solution and explanation can be found [_here_]("http://forum.linuxmint.com/viewtopic.php?f=90&t=32554#p187551").

You only have to edit one line in the file "/usr/lib/gdesklets/utils/ErrorFormatter.py". But don't forget to make a security save before!


Look for the following line in the file:
[PHP]def _new_imp(name, globs = {}, locls = {}, fromlist = []):[/PHP]

and replace it by the following
[PHP]def _new_imp(name, globs = {}, locls = {}, fromlist = [], test = []):[/PHP]

That's all (To save the changes you have to set up the appropriate rights for this file, of course). 

It's recommended to save the edited line within the file instead of deleting it. For doing so enter a " # " at the beginning of the original line that it looks like this
[PHP]# def _new_imp(name, globs = {}, locls = {}, fromlist = []):[/PHP]
Now this line woun't be executed but is still there if it's needed to undo the changes.


Hope this helps.

---

### Post by kfrancist on 2010-08-09
thank you! this worked!

i had the same problem as the first 3.

is the original poster the only one who can tag this as solved?

---

### Post by 29732 on 2010-08-09
and there's a similar program with compiz called screenlets 
you should try it out

---

### Post by dinesh2n on 2010-08-21
thank you this code works great....

dinesh

---

### Post by musashi39 on 2010-08-31
> **shinzo said:**
> gdesklets not running because "Could not import tiling module!"? Solution and explanation can be found [_here_]("http://forum.linuxmint.com/viewtopic.php?f=90&t=32554#p187551").

You only have to edit one line in the file "/usr/lib/gdesklets/utils/ErrorFormatter.py". But don't forget to make a security save before!


Look for the following line in the file:
[PHP]def _new_imp(name, globs = {}, locls = {}, fromlist = []):[/PHP]

and replace it by the following
[PHP]def _new_imp(name, globs = {}, locls = {}, fromlist = [], test = []):[/PHP]

That's all (To save the changes you have to set up the appropriate rights for this file, of course). 

It's recommended to save the edited line within the file instead of deleting it. For doing so enter a " # " at the beginning of the original line that it looks like this
[PHP]# def _new_imp(name, globs = {}, locls = {}, fromlist = []):[/PHP]
Now this line woun't be executed but is still there if it's needed to undo the changes.


Hope this helps.

Has this been reported to Google or somebody???

---

### Post by jtarin on 2010-08-31
> **musashi39 said:**
> Has this been reported to Google or somebody???How do you think the answer is found......GOOGLE? Most difficulties a person encounters with anything a solution can be found with the right search parameters in GOOGLE. ```
google |grep answers to linux problems
```

---

### Post by kathleenhenri on 2010-12-12
Just encountered this problem with Jolicloud 1.1 running on my Fujitsu U810.

The fix worked!

Thanks so much for posting the solution!

---

### Post by Jetro on 2011-05-21
Yup, just got the same error and #4 fixed it. :D
Thanks, shinzo!

---

