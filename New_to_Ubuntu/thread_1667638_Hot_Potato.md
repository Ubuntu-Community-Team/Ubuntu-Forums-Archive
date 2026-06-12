---
title: "Hot Potato"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by beanco on 2011-01-15
So, any ideas how to install Hot Potato from the CLI?

I am running Lucid.

Thanks

Robi

---

### Post by bruno9779 on 2011-01-15
If you download binaries version 1.2.0 from softpedia:

[http://linux.softpedia.com/progDownload/Hot-Potato-Online-Download-9502.html](http://linux.softpedia.com/progDownload/Hot-Potato-Online-Download-9502.html)

just unpack it in your home folder, cd to the right directory and execute HotPotato

---

### Post by beanco on 2011-01-15
Thanks,

I will give it a try later... being all new to this stuff I am not quite sure I understand what you are saying, but I will try it.

thanks

robi

---

### Post by bruno9779 on 2011-01-15
There are several HotPotato on the net. Post back with a link, if it is something else you are trying to run.

---

### Post by beanco on 2011-01-16
I used the link you provided for the binaries...

I do not know how to unpack it from the CLI so I just used the gui and tried that... it shows up in my desktop... but I cannot launch it...

So, what are the exact steps to do this at the CLI?

thanks for the help.

Robi

---

### Post by beanco on 2011-01-16
I used the link you provided for the binaries...

I do not know how to unpack it from the CLI so I just used the gui and tried that... it shows up in my desktop... but I cannot launch it...

So, what are the exact steps to do this at the CLI?

thanks for the help.

Robi

---

### Post by beanco on 2011-01-16
I used the link you provided for the binaries...

I do not know how to unpack it from the CLI so I just used the gui and tried that... it shows up in my desktop... but I cannot launch it...

So, what are the exact steps to do this at the CLI?

thanks for the help.

Robi

---

### Post by bruno9779 on 2011-01-16
First you unpack the .tar.gz file (after moving it to your home folder):

```
tar xvfz HotPotatoOnlineBinary-v1.2.0.tar.gz
```

then go to the folder created by unpacking:

```
cd HotPotatoOnlineBinary-v1.2.0
```

Then just execute the binary:

```
./HotPotato
```

---

### Post by bruno9779 on 2011-01-16
First you unpack the .tar.gz file (after moving it to your home folder):

```
tar xvfz HotPotatoOnlineBinary-v1.2.0.tar.gz
```

then go to the folder created by unpacking:

```
cd HotPotatoOnlineBinary-v1.2.0
```

Then just execute the binary:

```
./HotPotato
```

---

### Post by beanco on 2011-01-17
I Thanks for the help.... I really want to learn all this CLI code stuff, it is cool..

I did get an error msg. though..



> rob@rob-laptop:~$ cd HotPotatoOnlineBinary-v1.2.0
rob@rob-laptop:~/HotPotatoOnlineBinary-v1.2.0$ ./HotPotato
./HotPotato: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

---

