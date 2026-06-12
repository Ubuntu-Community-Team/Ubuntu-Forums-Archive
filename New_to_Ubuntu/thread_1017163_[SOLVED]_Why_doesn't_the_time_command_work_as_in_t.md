---
title: "[SOLVED] Why doesn't the time command work as in the man page examples?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by tnek on 2008-12-20
Hi,

The man page for time says (under EXAMPLES)
> To  run  the command ‘ls -Fs’ and show just the user, system, and total
       time:
            time -f "%E real,%U user,%S sys" ls -Fs
However when I do execute this line it says:

```
kent@rat:~$ time -f "%E real,%U user,%S sys" ls -Fs
bash: -f: command not found

real    0m0.162s
user    0m0.124s
sys    0m0.032s
kent@rat:~$ 

```I find this strange, is it a bug? In fact time does not seem to take any parameters, not even this works:
```
kent@rat:~$ time --help
bash: --help: command not found

real    0m0.162s
user    0m0.124s
sys    0m0.028s
kent@rat:~$ 

```Any ideas?

---

### Post by Morpheun on 2008-12-20
```
time(ls -Fs)
```

That works fine for me.

---

### Post by snova on 2008-12-20
Because the man page describes an actual command, however Bash has a built in version of time that overrides this one. So the 'time' you're reading about was never run.

---

### Post by tnek on 2008-12-21
Morpheun: Well what you wrote has nothing to do with what I wrote. [U][U]:confused:
[/U][/U]__> **snova said:**
> Because the man page describes an actual command, however Bash has a built in version of time that overrides this one. So the 'time' you're reading about was never run.
Ah! Thank you! I didn't notice the hint ( bash: <error message) until know. What confused me was that there was a man page for time, and I kind of used that way to check if a command was built in or not. I stand corrected!

I added [FONT=Courier New]alias time='/usr/bin/time'[/FONT] to my [FONT=Courier New]~/.bashrc[/FONT] so that I may use the separate time application in the future.

---

