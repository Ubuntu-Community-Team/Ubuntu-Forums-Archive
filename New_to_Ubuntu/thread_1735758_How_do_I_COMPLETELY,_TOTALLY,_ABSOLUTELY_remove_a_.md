---
title: "How do I COMPLETELY, TOTALLY, ABSOLUTELY remove a program?!?!"
date: 2011-04-21
forum: New to Ubuntu
---

### Post by Longstreet on 2011-04-21
Here's the situation. I've been playing with Cairo and AWN, and finally decided I wanted to stick with AWN. I uninstalled (I thought) AWN before I installed Cairo. When I reinstalled AWN, it brought it back with the same configuration I had when I uninstalled. Apparently there is some config file deep in the system that saved my settings when I deleted AWN. I don't like the way it looked, and would rather delete and start from scratch. How can I know that I have completely deleted everything about AWN, so that it is as if AWN was never there at all?

---

### Post by uRock on 2011-04-21
Mark for complete Removal via Synaptic Package Manager. Or you can just delete the corresponding configuration file in your /Home, then restart awn.

---

### Post by oldos2er on 2011-04-21
```
sudo aptitude purge avant-window-navigator
``` has the same function as 'Completely remove' in Synaptic.

---

### Post by Frogs Hair on 2011-04-21
The Awn folder is located in File System usr/share/in the A section , also make sure the Awn theme is removed in appearance preferences . It shows up in Customize > Icons.

---

### Post by Telengard C64 on 2011-04-21
Did you install from the package manager?

There may be configuration files remaining in your home directory related to the package named something like **.PACKAGENAME**.

```
sudo apt-get purge PACKAGENAME # purges configuration files.
sudo apt-get --purge autoremove # purges dependencies
find / -iname '*PACKAGENAME*' # finds any stragglers
```

The **find** command will take a long time. Manually removing files outside your home directory may be risky, and requires root. Be careful!

HTH

---

### Post by bodhi.zazen on 2011-04-21
You have to purge the package.

apt-get remove foo

^^ removes the package, but leaves the system config files (in case you customized them and later wish to re-install)

apt-get purge foo

^^ removes the package (and dependencies), and system config files, but leaves the config (. or dot) files in your user(s) home directory. You have to manually delete then (or use an application such as bleachbit.

The dot files are hidden by default so use the command line options -A (or a) to list them

ls -Al

or configure your file manager to show hidden files.

Update: There are occasional orphaned packages that can be removed as above, see my post below).

---

### Post by bodhi.zazen on 2011-04-21
> **Telengard C64 said:**
> Did you install from the package manager?

There may be configuration files remaining in your home directory related to the package named something like **.PACKAGENAME**.

```
sudo apt-get purge PACKAGENAME # purges configuration files.
sudo apt-get --purge autoremove # purges dependencies
find / -iname '*PACKAGENAME*' # finds any stragglers
```

The **find** command will take a long time. Manually removing files outside your home directory may be risky, and requires root. Be careful!

HTH

Close. 

The remove option will remove dependencies as well

Autoclean is more for orphaned packages, packages that were once installed as dependencies, but are no longer needed. This can occur for a variety of reasons.

see man apt-get

[http://manpages.ubuntu.com/manpages/natty/man8/apt-get.8.html](http://manpages.ubuntu.com/manpages/natty/man8/apt-get.8.html)

>        clean
           clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When APT is used as a dselect(1) method, clean is run automatically. Those who do not use dselect will likely want to run apt-get clean from time to time to free up disk space.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless. This allows a cache to be maintained over a long period without it growing out of control. The configuration option APT::Clean-Installed will prevent installed packages from being erased if it is set to off.

       autoremove
           autoremove is used to remove packages that were **automatically installed to satisfy dependencies for some package and that are no more needed.**

I know, it is a subtle difference.

:twisted:

---

### Post by Longstreet on 2011-04-23
SOLVED!

I guess I should have mentioned the things I'd already tried...

1. "Remove" and "Remove Completely" in Synaptics tried, no dice.
2. "sudo aptitude purge avant-window-navigator" tried, also no dice.
3. "...purge auto-remove..." tried, again, no dice.

However, this:
> Or you can just delete the corresponding configuration file in your /Home, then restart awn.

and this:
> find / -iname '*PACKAGENAME*' #

along with some help from my ubuntu-savvy son, put me on the right track, and got rid of the offending files.

Opened /Home, searched for anything AWN. Found and deleted a lot, more than I thought I would find. Ran / find, found a few more, deleted same, ran it again and found nothing. About this time my 18 y/o, whom I introduced to Ubuntu over a year ago, wandered by. He's not quite an expert, but he is pretty knowledgeable.

18 y/o: "Whatcha doing?"
Me: "Still trying to rid this machine of my broken AWN install. I think I've just about got it, but I can't remember how to look for hidden files." (I was offline at the time, and couldn't access this thread).
18 y/o: "Oh. I always use Nautilus. Open a terminal, run Nautilus, then hit Ctrl+H"

Bingo. Up popped several more AWN files, all of which were killed with extreme prejudice.

Reinstalled AWN, and everything worked, like it was the first time.

Thanks for all the advice. Got the problem solved, and even managed to show my son a thing or two from the thread.

---

