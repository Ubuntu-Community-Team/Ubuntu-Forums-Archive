---
title: "Setting environment variables in launchers"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by mmasroorali on 2011-08-25
Dear All,
i thought that this will be very easy, but it is not.

In a launcher button, I am trying to set an environment variable (please do not ask me why) before the command is invoked. So, I tried something like this,

export ENVVAR=value; command

But when the launcher is clicked, I get the following,

```
Could not launch application
Failed to execute child process "export" (No such file or directory)

```

I also tried using set, with similar results.

Missing shell in launcher? Or some such? But how then PATH works?

Could you please tell me how I can make the above work? 

Setting environment variable in .bashrc does not work. And for some reason I want to avoid global environment variable (/etc/bash.bashrc).

Thanks in advance.

---

### Post by androssofer on 2011-08-25
> **mmasroorali said:**
> Dear All,
i thought that this will be very easy, but it is not.

In a launcher button, I am trying to set an environment variable (please do not ask me why) before the command is invoked. So, I tried something like this,

export ENVVAR=value; command

But when the launcher is clicked, I get the following,

```
Could not launch application
Failed to execute child process "export" (No such file or directory)

```

I also tried using set, with similar results.

Missing shell in launcher? Or some such? But how then PATH works?

Could you please tell me how I can make the above work? 

Setting environment variable in .bashrc does not work. And for some reason I want to avoid global environment variable (/etc/bash.bashrc).

Thanks in advance.

seems very hush hush.. however! ask no questions hear no lies ;)

did u do:

```
source .bashrc
```

after adding it in to bashrc? (gotta check this sorta thing 1st...)

or how about:

```
PATH=$PATH:value && export PATH && command
```

tht work?

---

### Post by kerry_s on 2011-08-25
launchers are very basic, they run 1 command.
so if you put your command in a script, then just point to it in the launcher, it should work.

---

### Post by mmasroorali on 2011-08-25
> **kerry_s said:**
> launchers are very basic, they run 1 command.
so if you put your command in a script, then just point to it in the launcher, it should work.

It was so simple, but escaped me. Thanks a lot.

Anyway, why can not the launchers run more than one command? You said that it is very basic. Would you mind elaborating a little more?

---

### Post by kerry_s on 2011-08-25
> **mmasroorali said:**
> It was so simple, but escaped me. Thanks a lot.

Anyway, why can not the launchers run more than one command? You said that it is very basic. Would you mind elaborating a little more?

not sure how to explain it. never bothered to really look into it. :confused:

---

### Post by Azdour on 2011-08-25
Hi,

A little bit more info about the launcher restrictions can be found here:

[https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)

"Unfortunately launchers do not have access to the Bash environment so you cannot just include the needed commands."

---

