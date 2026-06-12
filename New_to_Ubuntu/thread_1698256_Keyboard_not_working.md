---
title: "Keyboard not working"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by shankhs on 2011-03-02
Hi,
there seems to be a strange problem with ubuntu 10.10 today, the keyboard is not getting recognised. Earlier during startup it reported some error in /home ( which is another partition in my case) and asked to press 'F' to auto repair and a couple of other keys, I pressed 'F' and got the login screen but after that I was unable to login as the keys were not getting recognised ( the touch pad is working fine) so I used the on screen keyboard to login.

I tried to change the keyboard layout to Dell Inspiron (its my laptop) but nothing worked.

Everything worked fine till the last shut down, I tried to google but it always said about some commands.Since keyboard is not working so the commands cant be entered.

Please help. Thank you

---

### Post by kittkatt on 2011-03-02
For due dilligance try using another keyboard to see if it works.  There's always the freak chance that your thing just happened to die at that moment.

---

### Post by houseworkshy on 2011-03-02
You could try the recovery mode or go backwards to a previous kernal.  I sympathise having had the trying to fix a keyboard issue using a keyboard.  If this is not an isssue with live cd's then you could use one of them to make changes to your system, I lack the knowlage to say what they'd be.

You could also use a live cd/dvd session to backup work prior to a reinstall if all else fails.  Puppy linux is small enough to run in ram, so you can free up your dvd/cd drive and it has a burner included in it's software.

---

### Post by shankhs on 2011-03-02
Thanks guys! The other keyboard is also not getting detected. Is there nothing that i can do like repair using ubuntu live CD or something like that I have some important data that I havent backed up yet?

---

### Post by houseworkshy on 2011-03-02
Well you could try "apropos keyboard" and then dig around in what comes up, "man ( whatever the term is )".   I'm guessing that you are using a live cd session to post, if so that would rule out hardware problems.  As you can copy and paste from the terminal and to the hard drive you may even be able to put a text document together with the commands you wish to use in it and perhaps do some diagnostics or even repairs from the dodgy hd installation.  This would be madly cumbersum, I know, but the last post was an hour ago and what I'm really doing is bumping the thread.

---

### Post by houseworkshy on 2011-03-03
And another.  One can install small programs to ram in live cd sessions as long as they don't require reboots.  So little diagnostic things may glean information.  Sysinfo perhaps.  On information gainable in a live session maybe the log files on your hard drive would be informative too.

---

