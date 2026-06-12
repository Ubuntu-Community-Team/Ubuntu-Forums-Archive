---
title: "Can't execute my own shell scripts!"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by Flos Headford on 2010-09-16
I wrote a shell script, made it executable (by anyone).
All it does is cd to the appropriate directory in /home/user,
then start a tcl script.
I put a new icon on the panel, and pointed it to the shell script.
It used to work.
Upgraded to 10.04 - and it doesn't work any more. I get -
"Could not launch application
Failed to execute child process "/home/user/directory/shellscript.sh" (Permission denied)"
I can't execute it from Nautilus, either (Nautilus just opens it in gedit).
The shell script is -rwxrwxrwx 
NOBODY should get that error message though!
What's going on? Can anyone help?

---

### Post by jtarin on 2010-09-16
Make sure you have permission on all levels of directory descent.Right-click and select open with terminal. Check your TLC script also.

---

### Post by utnubuuser on 2010-09-16
are the permissions/ownership of the parent directory ok?

---

### Post by v1ad on 2010-09-16
try executing with sudo and see what it tells you.

---

### Post by Flos Headford on 2010-09-17
Thank you for suggestions, fellows!
jtarin - the tcl script is one I downloaded: it works from terminal - I cd to the appropriate directory, and enter
wish runabc.tcl
and it runs perfectly.
v1ad - no sudo needed.
utnubuuser - containing directory is /home/phil/runabc which has permissions drwxrwxr-x. /home/phil has permissions drwsr-Sr--
Any further ideas?
Phil

---

### Post by CharlesA on 2010-09-17
Try to cd to the directory it is in and run it like so:

```
./script.sh
```

See if it throws back the same error.

EDIT: Also, can you post what is in the script?

---

### Post by Flos Headford on 2010-09-17
Dear CharlesA,
I tried what you suggested. I actually get -

```
me@mycomputer:~/runabc$ ./runabc.sh
bash: ./runabc.sh: Permission denied
```

but, after reading a lengthy discussion elsewhere about getting bitTorrent to work under Linux, I decided, by analogy with a solution there, to try

```
me@mycomputer:~/runabc$ bash runabc.sh
```

It works! - Presumably my terminal is not running bash, as I had assumed, though I'm sure it used to in 9.04, when it  didn't need the "bash" precursor. You'd think they'd tell a chap, wouldn't you?

So, my gnome panel launcher, which used to have the target of 
```
/home/me/runabc/runabc.sh
```
now has a target of 
```
bash /home/me/runabc/runabc.sh
```
and that, too, works perfectly!

Once again, thanks to all who helped in this discussion - you've all helped me to get my thinking cleared on this. If I can find out how to do it, I'll mark this one SOLVED. Congratulations, one and all!
Phil Headford
Shropshire UK

---

### Post by CharlesA on 2010-09-17
Do you have a shebang (example: #!/bin/bash) at the top of the script?

---

### Post by jtarin on 2010-09-17
Run the command ```
ps -p $$
``` to find out what shell your using.

---

### Post by CaptainMark on 2010-09-19
ive always had exactly the same thing, a script would run okay without putting bash first unless you are working from the directory containing the script in which case you have to type bash first, i use bash shells too, i dont know the reason for it

---

