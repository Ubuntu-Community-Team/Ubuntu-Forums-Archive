---
title: "Breaking symlinks"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by DarkerStar on 2009-07-17
Is there a built-in command to break a symbolic (or even hard) link? i don't mean **deleting** the link (or the linked file/directory), i mean replacing the link with the linked content.

For example, let's say i have a file FILE_A that has the text "Hello", and i create a link with ln -s FILE_A FILE_B.

```
dstar@space:~$ ln -s FILE_A FILE_B
dstar@space:~$ cat FILE_A
Hello
dstar@space:~$ cat FILE_B
Hello
dstar@space:~$ file FILE_A FILE_B
FILE_A: ASCII text
FILE_B: symbolic link to `FILE_A'
```

Now I want to break the link, leaving FILE_B, except now it is a copy of FILE_A:

```
dstar@space:~$ ??? FILE_B
dstar@space:~$ cat FILE_A
Hello
dstar@space:~$ cat FILE_B
Hello
dstar@space:~$ file FILE_A FILE_B
FILE_A: ASCII text
FILE_B: ASCII text
dstar@space:~$ 
```

Is there a simple command that does what ??? does? A single command that does "cp FILE_B xxx && rm FILE_B && mv xxx FILE_B"?

---

### Post by cariboo on 2009-07-17
You could try:

```
ln -i
```

From man ln:

> -i, --interactive
              prompt whether to remove destinations

---

### Post by jerome1232 on 2009-07-17
Well hard links will act like that by default.

For example
```
jeremy@psion:~/test$ ln -s fileA fileB
jeremy@psion:~/test$ ln fileA fileC
jeremy@psion:~/test$ ls -l
total 8
-rw-r--r-- 2 jeremy jeremy 6 2009-07-17 11:16 fileA
lrwxrwxrwx 1 jeremy jeremy 5 2009-07-17 11:16 fileB -> fileA
-rw-r--r-- 2 jeremy jeremy 6 2009-07-17 11:16 fileC
jeremy@psion:~/test$ rm fileA
jeremy@psion:~/test$ ls -l
total 4
lrwxrwxrwx 1 jeremy jeremy 5 2009-07-17 11:16 fileB -> fileA
-rw-r--r-- 1 jeremy jeremy 6 2009-07-17 11:16 fileC
jeremy@psion:~/test$ cat fileC      # the hard link still works
hello
jeremy@psion:~/test$ cat fileB      # while the symlink doesn't
cat: fileB: No such file or directory

```

---

### Post by DarkerStar on 2009-07-17
No, i guess i didn't explain it clearly enough. i don't want to remove the link target. i want to replace the link with a copy of the target.

If fileA has the contents "Hello", and then i created links like this:

```
dstar@space:~$ ln -s fileA fileB
dstar@space:~$ ln fileA fileC
dstar@space:~$ ls -l
... fileA
... fileB -> fileA
... fileC
dstar@space:~$ 
```

Then i did *something*:

```
dstar@space:~$ something fileB
dstar@space:~$ something fileC
dstar@space:~$ ls -l
... fileA
... fileB
... fileC
dstar@space:~$ 
```

See that fileB is no longer a link. And then if i edit fileA to say "Goodbye", neither fileB nor fileC are affected, because they're not links anymore:

```
dstar@space:~$ cat fileA
Goodbye
dstar@space:~$ cat fileB
Hello
dstar@space:~$ cat fileC
Hello
dstar@space:~$ 
```

i want to know what that "something" command would be. Whatever it is, "[COLOR="Red"]something <file>[/COLOR]" is functionally the same as "[COLOR="Red"]cp <file> xxx && rm <file> && mv xxx <file>[/COLOR]". Not "rm <whatever file links to>".

---

### Post by Paddy Landau on 2011-08-28
To the best of my knowledge, there is no such command. Whether the link is hard or soft, the link needs to be severed and the file copied.

Therefore, the only option is
```
rm fileB && cp fileA fileB
```You can, of course, create your own command to do this.

---

