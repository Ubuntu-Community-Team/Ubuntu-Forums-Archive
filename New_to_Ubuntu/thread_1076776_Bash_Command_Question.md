---
title: "Bash Command Question"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-02-21
i want to use feh to display the current amarok album art, which is given when i run the command ```
dcop amarok player coverImage
```
how do i tell feh to open that?
here's what i tried, but it didnt work:
```

mike@mike-laptop:~$ feh -g 40x40 "dcop amarok player coverImage"
feh WARNING: dcop amarok player coverImage does not exist - skipping
feh - No loadable images specified.
Use feh --help for detailed usage information

```
thanks in advance for any and all help!

---

### Post by karlr42 on 2009-02-21
I'm not sure what dcop does, but does
```
feh -g 40x40 < dcop amarok player coverImage
```
do anything?

---

### Post by snova on 2009-02-21
> **mjheagle8 said:**
> ```

mike@mike-laptop:~$ feh -g 40x40 "dcop amarok player coverImage"
feh WARNING: dcop amarok player coverImage does not exist - skipping
feh - No loadable images specified.
Use feh --help for detailed usage information

```

Try using backticks. It substitutes the output of one command as a parameter to another.

```
feh -g 40x40 `dcop amarok player coverImage`
```

---

### Post by mjheagle8 on 2009-02-21
okay, that works. how would i be able to execute that command every 15-30 seconds or so?  i'm trying watch and that's not working.

---

### Post by snova on 2009-02-21
Hmm... this seems to work:

[PHP]
while true; do
    feh -g 40x40 `dcop amarok player coverImage` &
    pid=$!
    sleep 20 # Or however many seconds you want it to run
    kill $pid
done
[/PHP]

---

