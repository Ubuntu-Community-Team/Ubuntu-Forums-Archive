---
title: "Newie to Ubuntu - 8.10 - can't upgrade/install packages"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by Kermit524 on 2009-05-22
Hi,
I am trying to upgrade/install new packages using either the Package manager or the terminal (apt - get... ). In either case - I am asked to type my password, and then - nothing. The system seems to react for half a second, but nothing happens, not even an error message.

Problem is, I suspect, with the fact the I don't have password. During Ubuntu installation I was asked if I want to be able to login directly, or use a password, and I chose login directly. So at the moment, I don't have a pssword. Mayb that's the reason for all this?

Even worse: At the moment I can't reset/add/modify my password, When trying to do it I am asked to type my password (..) and then - either I get an error message, or nothing happens.

Any way out of this mess?

Many thanks in advance for any help, 

Michal

---

### Post by nandemonai on 2009-05-22
You still have a password, it'll be whatever you set at installation for your user.

If you need to reset the password then when you start up the machine, hit ESC when it says about loading grub (should be just after the first screen with your BIOS information etc) then from the boot menu select 'Recovery Mode'

Once that's booted up and gives you a menu, pick root - drop to a root shell prompt.

BE CAREFUL HERE! You can severely mess up your system if you mess around in the root prompt.

All you need to do is type this command:

```
passwd USERNAME
```

Where USERNAME is your user account, ie for me, it's passwd nandemonai.

Then it'll ask you to 'Enter new UNIX password'.

Enter it twice (it wont display you're typing but it is registering key strokes) and you should be good to go.

Lastly, type:

```
reboot
```

Password changed. ;)

Edit:

I should note, that this is only necessary when you need to reset the only account on the machine with sudo access. If this wasn't the first created user, or you've added another user with admin access then you can reset the password from that account.

---

### Post by scorp123 on 2009-05-22
EDIT: I didn't read correctly. Sorry. :)

---

### Post by nandemonai on 2009-05-22
> **scorp123 said:**
> Huh???? Where did you take the idea from that a simple password change requires a reboot? This is not the case.

Recovery Mode...

Unless there is a command to resume a normal boot that's what I always do.

If you know a way to resume normal boot after dropping to the root prompt via recovery mode then by all means let me know :)

---

### Post by Kermit524 on 2009-05-22
Thanks, that (booting as singel user - root and changing the password) is what I have done - eventually, and it indeed solved the problem.

Many thanks :-) !

---

### Post by scorp123 on 2009-05-22
> **nandemonai said:**
> Recovery Mode... Uhmm ... as I said: I did not read correctly. My apologies ):P

---

