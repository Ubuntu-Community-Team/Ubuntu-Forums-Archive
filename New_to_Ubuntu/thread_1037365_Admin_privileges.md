---
title: "Admin privileges"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by Merkyor on 2009-01-11
[http://img407.imageshack.us/img407/622/adminsf4.png](http://img407.imageshack.us/img407/622/adminsf4.png)

do I have to run it as root? how do I do that?

I tried logging in as root but I don't even know what the password is. I don't remember being asked to give one and if it did ask me, the pass I would have given doesn't work.

---

### Post by igknighted on 2009-01-11
Need more information... what command did you run to get that output?

---

### Post by avtolle on 2009-01-11
Try running the command you ran which gave you the output you posted prefaced by sudo, which will give you temporary root privileges. It will ask for your password, which should be the same as the one with which you log on, and when you type it in, nothing will show on the screen, just press Enter after typing the password.

---

### Post by Carl Hamlin on 2009-01-11
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Righto. In order to run commands as root, prepend them with 'sudo'. When it asks for a password, it's the one you use to login.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklqf9YACgkQyLm4ydrABvfiZQCfQj/BwRP5/u58ldrYvQ7QnsE8
lnAAoKr5fVtwZWq09zYt0nofgWafvX6t
=BrWW
-----END PGP SIGNATURE-----

---

### Post by jimmy the saint on 2009-01-11
preface the command with "sudo"
for example
```
sudo <command>
```

---

### Post by Merkyor on 2009-01-11
ok in virtualbox i clicked "install guest additions" in the menu which mounts an iso

in the iso the only file i see in there that i think would work in ubuntu is "VBoxLinuxAdditions-x86.run"

i double click that and it gives me 4 options

- run in terminal
- display
- cancel
- run

when I pick run i get what you see in the pic i posted above

the others dont seem to do anything useful

terminal seems to do the same but auto quits
cancel is obvious
and display just displays the file as plain text

---

### Post by Merkyor on 2009-01-11
hmm ok im not really running a command tho?

---

### Post by jimmy the saint on 2009-01-11
Ok, so you want to install the guest additions in an Ubuntu guest then.  That requires some work in the terminal, where you will be running the appropriate commands.  Don't worry, it is pretty simple.  I will get you a good tutorial if you tell me two things
1) what version of Ubuntu are you running in VirtualBox?
2) What version of VirtualBox are you running?

---

### Post by minsf on 2009-01-11
in the terminal, change to the directory that has this .run file, then run ```
sudo sh VBoxLinuxAdditions-x86.run
```
I think this should work, though i have no idea what virtual box is :)

---

### Post by Merkyor on 2009-01-11
nevermind i found the solution in another thread

[http://moxiefoxtrot.com/2009/01/05/installing-ubuntu-810-in-virtualbox/](http://moxiefoxtrot.com/2009/01/05/installing-ubuntu-810-in-virtualbox/)

thanks anyway

---

### Post by albinootje on 2009-01-11
> **Merkyor said:**
> ok in virtualbox i clicked "install guest additions" in the menu which mounts an iso

in the iso the only file i see in there that i think would work in ubuntu is "VBoxLinuxAdditions-x86.run"

i double click that and it gives me 4 options

This works for me :
0) Make sure the GuestAdditions cdrom is (still) mounted.
1) Open a terminal.
2) Enter this :
```

cd /media/cdrom0
sudo sh ./VBoxLinuxAdditions-x86.run

```

---

### Post by iqtedar on 2010-02-11
I have two cdrom directories (one inside 'media') and I tried sudo with and without the sh and ./ portions but I get the same reply "Can't open ..."

Update:
No need to reply to this now. I figured it out. You need to first navigate to the directory that contains the 'VBoxLinuxAdditions-x86.run' file. For me this was in '/media/VBOXADDITIONS_3.' It is then that I typed 'sudo sh VBoxLinuxAdditions-x86.run' and it installed.

---

