---
title: "notify-send from commandline without x"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-01-07
how do you use notify-send from commandline without x? I tried it use it the normal way but i get an error about their being no x. If notify-send can not be used from the command line without x is their another program that will work?

---

### Post by ibuclaw on 2010-01-07
```
export DISPLAY=:0
```
Then try it.

FYI - there needs to be at least **one** display running.
The first display is :0, the second :1, the third :2, etc...

Regards
Iain

---

### Post by lance bermudez on 2010-01-08
what would the command look like?

notify-send export DISPLAY=:0 "text"

---

### Post by juancarlospaco on 2010-01-08
ssh -X $USER@127.0.0.1 notify-send "LOL" "test"

*This works for me but uses an SSH magic* :)

---

### Post by lance bermudez on 2010-01-08
i get 
ssh: connect to host 127.0.0.1 port 22: Connection refused

also i still can not get the 

export DISPLAY=:0

to work either

---

### Post by chewearn on 2010-01-08
```

export DISPLAY=:0; notify-send "LOL" "test"

```

---

### Post by ibuclaw on 2010-01-08
> **lance bermudez said:**
> i get 
ssh: connect to host 127.0.0.1 port 22: Connection refused

also i still can not get the 

export DISPLAY=:0

to work either

Not much to explain really.

To set a variable in a shell, you would do.
```
variable=value
```
But this is only defined locally, so any applications forked from the shell will not be able to access this variable.

The shell built-in **export** makes it global.
```
export DISPLAY=:0
```
Is a separate command to set the DISPLAY variable, which is used by X applications to determine which server to run on.
You can ensure it is set by echo'ing the variable:
```
echo $DISPLAY
```
and ":0" will be outputted.

With that ensured, you are all set. You can run whatever X app you were wanting to run.

Regards
Iain

---

### Post by juancarlospaco on 2010-01-08
> **lance bermudez said:**
> i get 
ssh: connect to host 127.0.0.1 port 22: Connection refused


because you need to istall [ssh server]("apt:/openssh-server")

---

