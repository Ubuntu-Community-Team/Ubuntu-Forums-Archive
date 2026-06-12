---
title: "GUI not loading (ruined in a weird way)"
date: 2009-11-24
forum: New to Ubuntu
---

### Post by poisn on 2009-11-24
[FONT=Verdana][COLOR=Red][SIZE=2]update:
[/SIZE][/COLOR][/FONT][COLOR=Red]reinstalling ubuntu. Thank you for all the support though![/COLOR]
[FONT=Verdana][SIZE=2]
Hi everyone, im not an ubuntu geek and I only have some experiences with it, please bear with me!

edit: if I forgot to give any information you want, please tell me since im not aware if this is enough. Thanks

**My system**. Ubunto 9.04 Desktop Edition

**What I did (short version below)**
I was trying to install slapd and I got:
[/SIZE][/FONT]    *[FONT=Verdana][SIZE=2]Depends: libldap-2.4-2 (=2.4.9-0ubuntu0.8.04.1) but 2.4.9-0ubuntu0.8.04.2 is to be installed[/SIZE][/FONT]*
[FONT=Verdana][SIZE=2]so I was searching for a solution on the internet. Trying to update my ubuntu didn't help at all, nor the other "solutions" I found. I was becoming desperate, so I tried installing libldap and whatever else it wanted (which might be totally stupid...). Eventual I ended up deinstalling the packages my system wanted to depend on, but which he couldn'nt install.[/SIZE][/FONT]


[FONT=Verdana][SIZE=2]**In short**
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]I deinstalled some ldaplib and some perllib (not sure about this one) packages. From that time on, my GUI was already behaving weird, so i decided to reboot. When it booted I ended up in the console.[/SIZE][/FONT].
[SIZE=2][FONT=Verdana]
[/FONT][/SIZE]
[FONT=Verdana]**[SIZE=2]Things i tried[/SIZE]**[/FONT]
[FONT=Verdana][SIZE=2]- startx[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]- several apt-get clean, autoclean, update[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]- apt-get install several packages (gdm, ubuntu-desktop)[/SIZE][/FONT]
    => resulted in a long list of errors all saying: depends xxxx but it will not be installed and a long list of recommendations what to install..
[FONT=Verdana][SIZE=2]- xfix in the recovery mode
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]If anyone can help me in any way, I would be damn grateful. I don't know how I was able to mess it up this way ):[/SIZE][/FONT]



[FONT=Verdana][SIZE=2]p.s. if you know an answer to my slapd problem as well, I would greatly appreciate it.[/SIZE][/FONT]


[FONT=Verdana][SIZE=2]Thanks in advance for any help!!
[/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]
[/SIZE][/FONT]

---

### Post by JDShu on 2009-11-25
Hmmm, what does it say when you try "sudo /etc/init.d/gdm start"?

---

### Post by jacobs444 on 2009-11-25
try installing what it recommends, and if that doesn't work, then i have no idea. Good luck

---

### Post by poisn on 2009-11-25
> **JDShu said:**
> Hmmm, what does it say when you try "sudo /etc/init.d/gdm start"?
It's doing nothing at all. No output either.

@jacobs
I tried installing the things it recommended. I'm just getting other errors saying something like:  depend xxx .... but it will not be installed

---

### Post by poisn on 2009-11-25
Well. Thanks for the effort trying, but I need to get this fixed soon because my ldap work needs to be done until friday. I guess I will just have to reinstall ubuntu :/
If u have any hints how I can save some configurations I made, like Themes, Login settings etc. so i don't need to re-set them, I would be glad to hear.

So um. I'm gonna wait some hours before I reinstall ubuntu hoping for some replies.
Thanks~

---

### Post by Sealbhach on 2009-11-25
> **poisn said:**
> Well. Thanks for the effort trying, but I need to get this fixed soon because my ldap work needs to be done until friday. I guess I will just have to reinstall ubuntu :/
If u have any hints how I can save some configurations I made, like Themes, Login settings etc. so i don't need to re-set them, I would be glad to hear.

So um. I'm gonna wait some hours before I reinstall ubuntu hoping for some replies.
Thanks~

Try this
```


sudo apt-get update
sudo apt-get --reinstall install ubuntu-desktop

```

.

---

### Post by poisn on 2009-11-25
Thanks for the quick reply.
I tried it out, it was loading for a while. When it was done it gave me:
E: Sub-process /usr/bin/dpkg returned an error code(1)

I rebooted and unfortunately I can't even get into the Console now.
After the Ubuntu loading screen I get some error about undefined symbol and
init terminated with status 127

I get the same error if I try the recovery mode.

Is it time to reinstall or is there some way out?

---

### Post by ikacer on 2009-11-25
If you look in

/var/log/apt/term.log

there should be a record of changes you have made. You could try these steps:

```
sudo nano var/log/apt/term.log
```
in this file look for the changes you have made when you problems occured

then switch to a different console with ctl-alt-f1
in this console you should open up aptitude
```
sudo aptitude
```

now you can switch back and forth between the log (f7) and aptitude (f1), and try and undo the changes you have made.

edit:
also, here are some basic instructions on using aptitude (from wikipedia):

aptitude does not require root privileges to run, and shows prompts to "Become Root" only when such rights are required.

Once opened, aptitude proposes a threaded list of packages that can be navigated with arrow keys and enter to open and collapse nodes. Pressing Ctrl-T gives access to the menus that list all the features and the shortcuts of the program. The most important are:

    * u to update package listings (requires root)
    * shift-u to mark all upgradeable packages for upgrade
    * + to mark the selected package for installation
    * - to mark the selected package for removal
    * / to search the listings (use n and shift-n to cycle between the results)
    * g to preview changes
    * g again to apply changes (requires root)
    * q to quit

---

### Post by poisn on 2009-11-25
> **ikacer said:**
> If you look in

/var/log/apt/term.log

there should be a record of changes you have made. You could try these steps:

```
sudo nano var/log/apt/term.log
```in this file look for the changes you have made when you problems occured

then switch to a different console with ctl-alt-f1
in this console you should open up aptitude
```
sudo aptitude
```now you can switch back and forth between the log (f7) and aptitude (f1), and try and undo the changes you have made.

I'm not able to get into the console if u read my last post, unless you can help me out there. Thanks for your effort though

---

### Post by ikacer on 2009-11-25
> **poisn said:**
> I'm not able to get into the console if u read my last post, unless you can help me out there. Thanks for your effort though

do none of the consoles work? try ctrl-alt-F1.

If you can't get to the console at all, then its time boot up a live cd, salvage any important files, and reinstall Ubuntu :(

---

### Post by poisn on 2009-11-25
Yea. It's not even reaching the console.

UPDATE. laptop is running again through miracle SIGH.. I dont know. I will reinstall ubuntu asap i finished my backup..

Thanks again for the help, i greatly appreciated it :)

---

