---
title: "Running Commands (Previously Exported) As Root"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by Mills00013 on 2010-03-17
Hey all. I have successfully downloaded and installed Google Androids development kit (adb) into my home folder. I have it tucked away in a few more folders for organization sake, and need the commands to run from a tools folder in there. The exact path is as follows:

```
~/Android/Android-SDK/tools/
```

I have edited my .bashrc file with an export command:

```
export PATH=${PATH}:/home/milo/Android/Android-SDK/tools
```

When I call to any of the commands inside the tools folder (the main one being one called "adb" they do work, I get a response so I know the export is working fine.

However, calling to adb starts a server that allows the computer to talk to the phone, and this server must be started as root. If I cd to the tools directory and run "sudo ./adb" and it works fine.

However running "sudo adb" does not work and I get a returned message that "sudo: adb: command not found".

So basically I suppose my issue is that when I run a command through sudo, the export values from my user bashrc file are not carried over? I have also tried editing the root bashrc file but this hasn't seemed to help. Anyone have any ideas?

Is it possible to set permissions on the adb executable to have it always run as root? I don't mind typing in a password, I just do not want to have to cd to the directory every time I want to run it.

---

### Post by lloyd_b on 2010-03-17
Try "sudo -E adb".  For security reasons, 'sudo' is set by default to reset the environment (which includes the PATH).  The "-E" option will override this, so your PATH changes will be carried through to the 'sudo'.

You can also potentially set that program as "suid root", in which case it will always execute as root, but be advised that having any program suid root is a potential security risk - an attacker may be able to use that program as a stepping stone to gain root permissions.

"man chmod" in a terminal window for more info on setting the suid bit.

Lloyd B.

---

### Post by Mills00013 on 2010-03-17
Thanks for the quick reply, unfortunately, neither of those worked. Both just gave me the same not found messages as before. In researching, I did discover what you are talking about with sudo erasing the environmental variables, and I read that this might be able to be changed using visudo. Do you have any insight on how I might go about doing that?

I read that it might be possible to add a line similar to this:

```
Default env_keep=PATH
```

But I dont know exactly how that needs to be formatted. I suppose that "PATH" should work because I have it exported in my user .bashrc or should I change it to "$PATH" or something completely different?

---

### Post by sisco311 on 2010-03-17
Why don't you create an alias to the command:
```
alias adb='sudo ~/Android/Android-SDK/tools/adb'
```
?

Add the above line to the ~/.bashrc file then run:
```
. ~/.bashrc
adb
```

---

### Post by Mills00013 on 2010-03-17
Thats a good idea, and one that I will probably have to do.

I just have always viewed alias commands as a but of a messy solution. The other thing is that there are about 10 other executables inside the tools folder, so I will have to set everyone to be an alias, but again, might be my only option.

---

