---
title: "BASH - Checking if files exist with wildcards"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by kazza765 on 2009-03-25
Hi, I have a script, and I'd like to check if any files exist with the extension .out. I've been searching and can only find people suggesting.

if [[ -e "filename" ]]

which doesn't seem to accept wildcards. Can anyone tell me the correct syntax for this? What I'm after is something like

if [[ -e "*.out" ]]

(but that actually works).



John

---

### Post by lovinglinux on 2009-03-26
I'm not an expert, but I think you could do this:

```

FILTER=$(find $HOME -type f \( -name "*.out" \) )

if [ -z ${FILTER} ]; then
```

This will basically search for files with .out extension in the home directory, use the results as a variable, then check if the variable has a value. If there aren't any files with the .out extension in the home directory, then the variable will be null and the condition will be satisfied.

The condition is satisfied if there aren't any files. I know is the opposite of checking if the files exists, but I couldn't make it work with -n option.

---

### Post by kazza765 on 2009-03-26
That works perfectly. Thanks for the help.

---

