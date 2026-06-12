---
title: "Back up all parts of Evolution"
date: 2009-07-25
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-07-25
I wish to be sure that I'm backing up all parts of Evolution.

[LIST]
[*]Emails
[*]Email accounts
[*]Settings
[*]Calendar
[*]Contacts
[*]Memos
[*]Tasks
[/LIST]
Am I correct in thinking that I merely have to back up ~/.evolution? Or are there files somewhere else that need backing up?

---

### Post by llamabr on 2009-07-25
Depends on your setup.  Are you running a mail server?

---

### Post by wojox on 2009-07-25
1. ~/.evolution/
2. ~/.gconf/apps/evolution/
3. ~/.gnome2_private/Evolution

```
$tar -cvzf evolution-backup.tar.gz .evolution .gconf/apps/evolution .gnome2_private/Evolution
```

---

### Post by Paddy Landau on 2009-07-25
> **llamabr said:**
> Depends on your setup.  Are you running a mail server?
No, just a standard Jaunty Remix single-user setup with standard POP emails.

---

### Post by Paddy Landau on 2009-07-25
> **wojox said:**
> 1. ~/.evolution/
2. ~/.gconf/apps/evolution/
3. ~/.gnome2_private/Evolution
Thanks, I'd never have guessed the second two!

I don't have the third one, though; there's no Evolution in .gnome2_private.

---

### Post by CatsRninja on 2009-08-05
Actualy the Evolution backup pulgin only backsup .evolution,

but in the evolution faq (at [http://www.go-evolution.org/FAQ#How_can_I_completely_backup_evolution.3F](http://www.go-evolution.org/FAQ#How_can_I_completely_backup_evolution.3F)) it says for evolution <2.22 to backup all those 3.

thats why im a bit confused.

I guess config files and stuff like the rules you create doesn`t pass in just .evolution.

---

### Post by Paddy Landau on 2009-08-06
> **CatsRninja said:**
> Actualy the Evolution backup pulgin only backsup .evolution
Thanks for the link.

You're right. For Evolution later than 2.2, you only need ~/.evolution.

But it seems important to shut down Evolution before doing the backup.

---

### Post by CatsRninja on 2009-08-06
> **Paddy Landau said:**
> Thanks for the link.

You're right. For Evolution later than 2.2, you only need ~/.evolution.

But it seems important to shut down Evolution before doing the backup.

I ansered this post because i was seartching for a way to backup evolution without the gui.
If you, like me, wanted to make a shell script just for evolution something like this would work i think:
```

#! /bin/bash
evolution --force-shutdown;
tar -czf $HOME/evolution-backup.tar.gz $HOME/.evolution;

```

and i think with anacron you can schedul it for the time you want(i did not do this yet)

---

### Post by Little John on 2009-09-28
THANKS! Bu how to restore it in a new installation ( Karmic ) ?

Regards from Sweden!

LJ

---

