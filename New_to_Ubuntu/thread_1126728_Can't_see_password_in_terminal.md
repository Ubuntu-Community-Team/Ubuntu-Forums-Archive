---
title: "Can't see password in terminal"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by AlonzoB on 2009-04-15
after typing in commands in the terminal it asks for password but i cant type it in please help thxs.AlonzoB

---

### Post by Joeb454 on 2009-04-15
This is normal :)

If you type your password correctly, and hit enter, it will work as you expect.

Not showing a password is normal for terminal applications, it's a security thing

---

### Post by llamabr on 2009-04-15
This seems to be confusing or distressing to many beginners.  Perhaps one ought to look into making it an option to output ***'s when the password is typed.

Seems like the sort of thing ubuntu developers would do.

---

### Post by Titan8990 on 2009-04-15
> **llamabr said:**
> This seems to be confusing or distressing to many beginners.  Perhaps one ought to look into making it an option to output ***'s when the password is typed.

Seems like the sort of thing ubuntu developers would do.


And the sort of thing that will push away long time Linux users.

---

### Post by skymera on 2009-04-15
Indeed it will.

Ubuntu doesn't target hard core users anymore it's the laughing stock of all distributions. So they might aswell go ahead and let the characters show.
They've done worse.

---

### Post by llamabr on 2009-04-15
> **skymera said:**
> Indeed it will.

Ubuntu doesn't target hard core users anymore it's the laughing stock of all distributions. So they might aswell go ahead and let the characters show.
They've done worse.

It took me all week to figure out why ctrl-alt-backspace didn't work anymore.  I thought it was a bug -- they call it a feature.

Ubuntu takes away everything confusing or harmful anyway.  I figure we add this one to the bunch.

If ubuntu didn't work so well, I wouldn't use it.

---

### Post by Ms_Angel_D on 2009-04-15
> **skymera said:**
> **ubuntu doesn't target hard core users anymore**

> **skymera said:**
> **so they might aswell go ahead and let the characters show. They've done worse.**

+1

---

### Post by AlonzoB on 2009-04-16
ok lol thxs guys for the help:)

---

### Post by gali98 on 2009-04-16
Just to add my two cents... 
It's one thing to take away ctrl+alt+delete.
It's another thing completely to start hacking away at security.
Kory

---

### Post by FredB on 2009-04-16
> **llamabr said:**
> It took me all week to figure out why ctrl-alt-backspace didn't work anymore.  I thought it was a bug -- they call it a feature.

Ubuntu takes away everything confusing or harmful anyway.  I figure we add this one to the bunch.

If ubuntu didn't work so well, I wouldn't use it.

It is a feature of Xorg itself. Just look at : [http://bgoglin.livejournal.com/16916.html](http://bgoglin.livejournal.com/16916.html)

So ubuntu is not guilty here. It is so simple to bash canonical for every single thing...

---

### Post by Bachstelze on 2009-04-16
> **gali98 said:**
> Just to add my two cents... 
It's one thing to take away ctrl+alt+delete.
It's another thing completely to start hacking away at security.
Kory

+1

*cough*Debian OpenSSL*cough*

---

### Post by lukjad on 2009-04-16
> **skymera said:**
> Indeed it will.

Ubuntu doesn't target hard core users anymore it's the laughing stock of all distributions. So they might aswell go ahead and let the characters show.
They've done worse.
Saying that Ubuntu is the laughingstock of the Linux world is like saying that ice cream is universally hated by the dairy industry. ;)

---

### Post by felinoel on 2009-04-18
> **Titan8990 said:**
> And the sort of thing that will push away long time Linux users.

Why would asterisks push away them? It isn't *that* much of a change nor would it affect anything, except maybe when people copy and past things it will show how many letter their computer's login password is...

---

### Post by juancarlospaco on 2009-04-18
To Restart X :
**sudo apt-get install dontzap && sudo dontzap -d**

**To Restart X without installing nothing ***(there are more options too)*:
sudo /etc/init.d/gdm restart


The "* **** *" can be easy hacked to get back REAL passwords, is NOT safe.

---

### Post by lisati on 2009-04-18
> **AlonzoB said:**
> after typing in commands in the terminal it asks for password but i cant type it in please help thxs.AlonzoB
Don't worry if it doesn't show - that's normal. Just type it in.
> **juancarlospaco said:**
> 
The "* **** *" can be easy hacked to get back REAL passwords, is NOT safe.
Huh? Perhaps I'm missing something here....

---

### Post by Paqman on 2009-04-18
> **skymera said:**
> Indeed it will.

Ubuntu doesn't target hard core users anymore it's the laughing stock of all distributions. So they might aswell go ahead and let the characters show.
They've done worse.

DNFTT, kids.

---

### Post by juancarlospaco on 2009-04-18
**To Restart X without installing nothing (KDE)** *(there are more options too)*:
Alt Gr + Print Screen + K

---

### Post by 3rdalbum on 2009-04-18
The Xorg control-alt-delete change may have come from upstream, but maybe Ubuntu should automatically add the "dontzap: false" option to Xorg.conf.

I'm not sure why the asterisks are such a security problem. All gksudo and kdesudo prompts show asterisks.

---

### Post by Dileeshvar on 2009-04-18
here there is nothing to do with ubuntu.
generally if you take any distribution 
it will not be showing the password you are
typing or event the Astrix.So no harm to ubuntu here.

---

### Post by Ratscallion on 2009-04-18
Ubuntu could make it so that when you copy + pasted the password from the Terminal (when it shows as *** etc) that the pasted item comes out as *** and you can't see what was inputted....

---

### Post by longtom on 2009-04-18
I think this is a prime example, how people, who are obviously bored, try to make an issue were there is none.

Answer the OP, if you like, and tell him, that no characters are showing and he just needs to type away.

@ llamabr

If that confuses beginners, it only shows that they haven't scratched on any documentation concerning Linux or Ubuntu.  
So all that question shows, that most beginners don't bother to read even about the very basics.  That is generally well known and no big deal, really.  If it irritates you - don't answer.

---

