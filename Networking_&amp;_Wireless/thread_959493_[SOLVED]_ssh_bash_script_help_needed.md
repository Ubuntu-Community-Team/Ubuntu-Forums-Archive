---
title: "[SOLVED] ssh bash script help needed"
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by ctsdownloads on 2008-10-26
So I am using ssh with a ssh key file (not password) and it is working well.

I can do the following:

[INDENT]*ssh -X me@target-pc *[/INDENT]

and it logs me in just fine to the terminal. And being I am able to execute evolution at near native speeds, but actually using the installation on the server machine by simply typing in evolution actually creates a process called ssh-evolution, makes ssh all the better.

This allows me to run my email *on the server box* instead of the local install of evolution. Cool, but I want to make this automatic.

Basically I need a script that will:

(execute) ssh -X matt@desktop-pc
(then run) evolution (which runs the client on the remote machine using X to show it on the local box)

Again, this works doing it manually. It's a little slow, but functional. Please, surely there is an argument in the script that will echo/run evolution after ssh has logged into the remote machine.

Thanks:KS

---

### Post by nixscripter on 2008-10-26
You can pass a command to ssh directly and it will execute it (not in a shell, though):

```
ssh -X user@host 'run-this-command'
```

Also, look into the -f (fork into background) flag if you don't want to leave your terminal window hanging open.

Hope this helps.

---

### Post by ctsdownloads on 2008-10-26
> **nixscripter said:**
> You can pass a command to ssh directly and it will execute it (not in a shell, though):

```
ssh -X user@host 'run-this-command'
```

Also, look into the -f (fork into background) flag if you don't want to leave your terminal window hanging open.

Hope this helps.

Yeah, that did it - thanks! :guitar:

However I did not have any luck with the -f flag. Must be my placement?

```
ssh -X user@host 'run-this-command -f'
```

and

```
ssh -X user@host 'run-this-command' -f
```


did not work for implementing the fork flag.

---

### Post by ctsdownloads on 2008-10-27
Figured it out. Using GNOME has its advantages. Just make the sh file executable and then double click, hit Run instead of run in terminal. :)

---

### Post by nixscripter on 2008-10-27
Great. Please mark the thread solved (under the thread tools menu).

---

