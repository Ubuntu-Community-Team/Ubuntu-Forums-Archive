---
title: "&quot;sudo: shell: command not found&quot;"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by watchpocket on 2010-02-02
Doing a 

sudo -s

I get:

sudo: shell: command not found.

According to the "Rootsudo" Community Ubunt Documentation, "sudo -s" is used "to start a *root shell*, but keep the current shell's environment".

I realize this command isn't supported by the developers, and I don't plan to use it a lot, but I'd at least like to have it working right.

How can I get sudo -s to find my user shell (which is zsh)?

---

### Post by ubudog on 2010-02-02
Did you type this into a "gnome-terminal"?

---

### Post by watchpocket on 2010-02-02
Yes, I did.  Where my user shell is zsh.

---

### Post by bodhi.zazen on 2010-02-02
> **watchpocket said:**
> Doing a 

sudo -s

I get:

sudo: shell: command not found.

According to the "Rootsudo" Community Ubunt Documentation, "sudo -s" is used "to start a *root shell*, but keep the current shell's environment".

I realize this command isn't supported by the developers, and I don't plan to use it a lot, but I'd at least like to have it working right.

How can I get sudo -s to find my user shell (which is zsh)?

I advise you use sudo -i rather then sudo -s

At any rate ...

I use zsh as my default shell and have never seen this error message. Did you change your root shell ? How did you set your user's shell ?

You can look at /etc/passwd and see what shells are listed .

---

### Post by watchpocket on 2010-02-02
> **bodhi.zazen said:**
> I advise you use sudo -i rather then sudo -s

I really only want to use plain old ***sudo*** when necessary, but I hate being yanked out of my zsh environment (suddenly I can't even tell in a listing if I'm looking at a file, a directory, an executable file or a symlink.  Ugh!).

Then I saw that ***sudo -s*** keeps my current shell's environment.  It seemed the logical choice.  Things will look and feel like they do in zsh. (Except for the small problem of ***sudo -s*** not working right now.)

> Did you change your root shell ?I may have, but I don't think so.  In **/root** I have right now a leftover .zcompdump file, because I briefly had zsh config files in **/root**, but I took them out.  I should probably remove the .zcompdump file as well (I'm not at home now.)  

By the way, is the default root shell ***sh***?  Or ***bash***?  (Or ***dash***?)  

 > How did you set your user's shell ?I honestly don't remember.  I have zsh config files in my homedir, and zsh is working as my user shell.  

Maybe all I really need to do is configure the system .bashrc as closely as possible to my zsh configs. 

I don't want to muck with /bin/sh.  I know enouh not to touch that. But I'd still like to have the ***sudo -s*** command functioning correctly.

---

### Post by watchpocket on 2010-02-02
Btw, if you use zsh as your user shell, how do you deal with the constant change of environment every time you run sudo?  

Doesn't going back & forth form a fully configured and customized shell to a raw, minimally-config'd shell prove to be an annoyance?

---

### Post by bodhi.zazen on 2010-02-02
> **watchpocket said:**
> Btw, if you use zsh as your user shell, how do you deal with the constant change of environment every time you run sudo?  

Doesn't going back & forth form a fully configured and customized shell to a raw, minimally-config'd shell prove to be an annoyance?

I use a .bashrc or .zshrc for root as well. I keep a separate set of options for each.

It may be easiest if you simply set root's shell as zsh and use sudo -i

My guess is something in your environment is not agreeing with bash, either your $PATH or one of a few .zsh files.

---

### Post by watchpocket on 2010-02-02
> **bodhi.zazen said:**
> It may be easiest if you simply set root's shell as zsh. . . .

How does one normally do that in Ubuntu?  

And should I put the config files in /etc/ ?

or is it okay to have them in an /etc/zsh/ subdir ?
(I have a .zprofile, a .zshenv and a .zshrc)

I appreciate your responses.

---

### Post by bodhi.zazen on 2010-02-02
```
sudo chsh root -s /bin/zsh
```

You can move your .zsh* to /root and chown then to root.root

---

### Post by watchpocket on 2010-02-02
So I should put the zsh config files in /root, and take them ***out***  of /etc/ ?

Or have them in both?

---

### Post by bodhi.zazen on 2010-02-02
It depends on what you want.

/etc is global, so applies to all users.

/root is for root

On small systems, with a single user, go for /root

On larger systems with multiple users, go for /etc

Again, I use different environmental variables, especially $PATH for users and root  with only a small number of alises for all users, for example,

cp="cp -i"

---

### Post by watchpocket on 2010-02-03
> **ubudog said:**
> did you type this into a "gnome-terminal"?

yhbt hand?

---

