---
title: "Command not found as root"
date: 2011-03-21
forum: New to Ubuntu
---

### Post by Dolkar on 2011-03-21
Hello everyone, i have 3 days old ubuntu installation on my computer same as 3 days of linux experience.
I have a little problem with Cuda, but i think its something more general. Google didnt show anything useful, so i came here to ask. Could you please explain this behavior to me and tell me how to run it as root?
```
dolkar@dolkar-NB:~$ nvcc
nvcc fatal   : No input files specified; use option --help for more information
dolkar@dolkar-NB:~$ sudo nvcc
sudo: nvcc: command not found
dolkar@dolkar-NB:~$ sudo su
root@dolkar-NB:/home/dolkar# nvcc
No command 'nvcc' found, did you mean:
 Command 'nvlc' from package 'vlc-nox' (universe)
nvcc: command not found
```It clearly works as an ordinary user, but it cant find the command as root. When i installed it, it couldnt find the command at all, i had to add the binary to the path variable. So, does root have some separate path variable?

---

### Post by synapsys on 2011-03-21
> **Dolkar said:**
> It clearly works as an ordinary user, but it cant find the command as root. When i installed it, it couldnt find the command at all, i had to add the binary to the path variable. So, does root have some separate path variable?

Yes, the user has a separate PATH than root. You should be able to run the command as root by using the absolute path for the command. In other words:

```
/path/to/installation/nvcc
```

You can also add it to the root user's PATH if you so desire.

---

