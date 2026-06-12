---
title: "Shell Scripting"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by Bofill82 on 2010-05-21
How can I determine if my script has run sucessfully

---

### Post by Kafubie on 2010-05-21
If it works...
This is hard to actually answer, but if it does what you intended it to do...  Then I would guess the Script worked.

---

### Post by ryan858 on 2010-05-21
Umm... That depends greatly on the script... It depends on what is in the script and it depends how you mean 'determine' and 'successfully'... It's not so black and white when it comes to that... More like Technicolor.

You can post a copy of the script here and maybe we'll be able to help you out...

But either way we kinda need a little more to go on... More info, please.

---

### Post by geerm on 2010-05-21
Taking in to consideration the previous posts.... if you run this on the terminal

echo $?

and you see anything other than 0, then it something went wrong

13:41:12  $ mkdir test
13:41:17  $ echo $?
0
13:41:23  $ mkdir test
mkdir: cannot create directory `test': File exists
13:41:28  $ echo $?
1

---

### Post by BoneKracker on 2010-05-21
Run the script with the -x option (debugging mode), like so:
```
bash -x myscript.sh
```

Or you can make it stick for the whole time you're working on the script by adding "-x" to the hash-bang line:
```
#!/bin/bash -x

statements
.
.
.
```

That will display each statement and it's result, as the script executes.  Try it with a very simple script first to understand what it's doing.

You can also turn this on or off for an entire script or a portion of it:
```

statements

statements

# now we reach the part you want to debug
set -x

statements you want to debug

statements you want to debug

# now we're past the part you wanted to debug
set +x

statements

statements
```

---

