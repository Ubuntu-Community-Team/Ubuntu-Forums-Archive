---
title: "Moving, copying and removing multiple files at once in terminal"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by niteling on 2011-01-02
Hi I'm relatively new to ubuntu and i was wondering how i would go about removing multiple files/folders in a folder at once. What do i use to separate the names. I would like to know this for copying and moving aswell.

Thanks

---

### Post by theozzlives on 2011-01-02
you could use wildcards like
```
rm /path/to/file/*.jpg
```

copy = cp

move = mv

to rename you go
```
mv oldname newname
```

Be careful with rm. Used incorrectly can be very dangerous! You're safer if you use Nautilus.

---

### Post by Miter_J on 2011-01-02
> **theozzlives said:**
> you could use wildcards like
```
rm /path/to/file/*.jpg
```

copy = cp

move = mv

to rename you go
```
mv oldname newname
```

Be careful with rm. Used incorrectly can be very dangerous! You're safer if you use Nautilus.
It seems to be quite easy to use "*.jpg" to achieve this. But how to operate files that cannot be bound together by "*"? For example, I wanna move files abc and def to another folder, is there a command that could work? 
Just like ```
mv abc&def anotherFolder
```though this command could not work. I wonder if there're commands that are similar like that

---

### Post by bikodog on 2011-01-02
> **theozzlives said:**
> you could use wildcards like
```
rm /path/to/file/*.jpg
```

copy = cp

move = mv

to rename you go
```
mv oldname newname
```

Be careful with rm. Used incorrectly can be very dangerous! You're safer if you use Nautilus.

use these parameters on the commands listed above for safety:

-v  = verbose output - displays the files as they are being moved
-i  = prompt - prompts before overwriting existing files

these can be combined as -vi

example:

```
mv -vi /path/to/oldfile /path/to/newfile
```

---

### Post by bikodog on 2011-01-02
> **Miter_J said:**
> It seems to be quite easy to use "*.jpg" to achieve this. But how to operate files that cannot be bound together by "*"? For example, I wanna move files abc and def to another folder, is there a command that could work? 
Just like ```
mv abc&def anotherFolder
```though this command could not work. I wonder if there're commands that are similar like that

like this:

```
mv -vi abc def /path/to/anotherfolder
```

---

### Post by fabricator4 on 2011-01-02
> **niteling said:**
> Hi I'm relatively new to ubuntu and i was wondering how i would go about removing multiple files/folders in a folder at once. What do i use to separate the names. I would like to know this for copying and moving aswell.

The command is rm (for remove), and the only separator is <space>. eg:

```
rm file1 file2 file3 file4
```

You can remove directories with the recursive option:

```
rm -r dir1 dir2 dir3 dir4
```

This also works for a mix of files and directories:

```
rm -r file1 file2 dir1 dir2
```

Copy (cp) and move (mv) are a little more complicated, but they will both assume that the _last_ name is the destination directory. eg

```
cp file1 file2 file3 directory1
```

For more information than you possibly wanted to know, try:

```
info coreutils 'mv invocation'
```

Remember that Linux uses / instead of \ as used in DOS to denote root and subsequent directories.

Chris

---

### Post by niteling on 2011-01-04
> **fabricator4 said:**
> The command is rm (for remove), and the only separator is <space>. eg:

```
rm file1 file2 file3 file4
```

You can remove directories with the recursive option:

```
rm -r dir1 dir2 dir3 dir4
```

This also works for a mix of files and directories:

```
rm -r file1 file2 dir1 dir2
```

Copy (cp) and move (mv) are a little more complicated, but they will both assume that the _last_ name is the destination directory. eg

```
cp file1 file2 file3 directory1
```

For more information than you possibly wanted to know, try:

```
info coreutils 'mv invocation'
```

Remember that Linux uses / instead of \ as used in DOS to denote root and subsequent directories.

Chris

Thank you guys for your help!! I spent a fair bit of time looking on google for the answer and didn't find anything.

Its funny how you said be careful with the rm command "theozzlives" because I was mucking around trying to work it out in a folder of my home directory and managed to delete all the folders under my user... but it wasn't to bad coz I didn't have much stuff in them.

---

### Post by digitography on 2011-02-25
Sorry to jump on someone elses thread, but I think it's relevant.

I read somewhere you can use the mv command to also leave the original files in place, ie it works like cp but copying all files and folders if used with *

---

### Post by Vaphell on 2011-02-25
where is the difference? you can cp files and folders with *

---

