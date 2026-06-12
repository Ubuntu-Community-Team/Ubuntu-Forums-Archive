---
title: "System hangs on 'shutdown -f'"
date: 2008-12-31
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-31
Recently, I've started to turn my computer off at night. I do the following command:

```

sudo rm -fr ~/.local/share/Trash/files/*; sudo apt-get update --yes && sudo apt-get upgrade --yes; sudo apt-get autoremove --yes && sudo apt-get clean --yes; sudo shutdown -f now

```

So, basically, delete my trash; update computer; remove irrelevant files; shutdown. Everything works fine until the unloading screen of Linux Mint comes up, and it gets to the end of the bar, and just sits there. I've let it stay overnight, but nothing happened.

Any ideas?

---

### Post by adult swim on 2008-12-31
try the -P flag to power off the machine
```
sudo shutdown -P now
```

---

### Post by adobrakic on 2009-01-01
No one has a solution on fixing the '-f'?
:x

---

### Post by Sprut1 on 2009-01-01
> **adobrakic said:**
> No one has a solution on fixing the '-f'?
:x

Shutdown command have no option -f. -P will power off, -H will halt, and -h will either power off or halt after system been brought down.

---

### Post by alan34 on 2009-01-01
A "man shutdown" does not show a -f option? Only these

OPTIONS
       -r     Requests  that  the system be rebooted after it has been brought
              down.

       -h     Requests that the system be either halted or powered  off  after
              it has been brought down, with the choice as to which left up to
              the system.

       -H     Requests that the system be halted after  it  has  been  brought
              down.

       -P     Requests  that  the  system  be  powered  off  after it has been
              brought down.

       -c     Cancels a running shutdown.  TIME is  not  specified  with  this
              option, the first argument is MESSAGE.

       -k     Only  send  out  the warning messages and disable logins, do not
              actually bring the system down.


Don't see a -f there.

halt and poweroff have a -f options.

---

### Post by adobrakic on 2009-01-01
Thought adding -f will search for broken dependencies, etc.?
When I did that command, the terminal said something about 'shutting down for maintenence'

---

### Post by adult swim on 2009-01-01
```
sudo apt-get -f install
``` fixes broken packages

---

### Post by snova on 2009-01-01
> **adobrakic said:**
> Recently, I've started to turn my computer off at night. I do the following command:

```

sudo rm -fr ~/.local/share/Trash/files/*; sudo apt-get update --yes && sudo apt-get upgrade --yes; sudo apt-get autoremove --yes && sudo apt-get clean --yes; sudo shutdown -f now

```

Not really related to your question, but I suggest you also empty out the "~/.local/share/Trash/info" folder, where information about the trash files are stored.

---

### Post by adobrakic on 2009-01-01
> **adult swim said:**
> ```
sudo apt-get -f install
``` fixes broken packages

Is it recommended that I not do this?

---

### Post by ajcham on 2009-01-01
> **adobrakic said:**
> When I did that command, the terminal said something about 'shutting down for maintenence'

That's part of the shutdown process - it's so that other people on your system* get some advance warning that the system is going to become unavailable.  The shutdown command doesn't necessarily power off the machine, either. It can do, but depending on the setup it just changes the current runlevel (for example, when I ran 'sudo shutdown now ' while using the ClamAV live disc I was dropped onto a root terminal).

[SIZE="1"]*(not as relevant in a desktop scenario, but crucial in a good old-fashioned *nix setup)[/SIZE]

---

### Post by adult swim on 2009-01-01
if you had broken packages, youd probably know it or would find out very soon.  i dont see a need to run it every shutdown.  with that being said, if it is in a script it couldnt hurt.  if there arent any broken packages, nothing is done when the command is run.

---

### Post by snova on 2009-01-01
> **adobrakic said:**
> Is it recommended that I not do this?

Not necessarily. But there's little reason for it unless you habitually break packages on your system. :P

And as for the shutdown command and its options, why not just use "sudo halt"? Less confusing...

---

### Post by nemilar on 2009-01-01
```
poweroff
```

is what I usually use.  Apparently, from the man page, it looks like it's just a frontend for shutdown -h

---

### Post by adobrakic on 2009-01-02
> 
if you had broken packages, youd probably know it or would find out very soon. i dont see a need to run it every shutdown. with that being said, if it is in a script it couldnt hurt. if there arent any broken packages, nothing is done when the command is run.


Oh, I thought it was for more than just broken packages.
I'm kind of crazy about space on my computer (even though I have about 40gb+ left, which is more than enough for me), I like to keep everything nice and tidy. 

Well thanks for clearing that up, everyone who posted!

---

