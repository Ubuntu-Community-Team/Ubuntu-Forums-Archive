---
title: "bored of passwords"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by timmy86 on 2011-06-08
hi,

is there an easy way to turn off being asked for a password every time i install?

---

### Post by wolfen69 on 2011-06-08
..................

---

### Post by jerrrys on 2011-06-08
never tried it

[http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-password-prompts-in-ubuntu.html)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+password&sa=Search&cof=FORID:9#941](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+password&sa=Search&cof=FORID:9#941)

---

### Post by crispy_420 on 2011-06-08
Wouldn't this just make you wide open to any threat?

---

### Post by jerrrys on 2011-06-08
thus, my second link crispy

---

### Post by nzjethro on 2011-06-08
Yeah, I'll add a warning to my howto. It's not recommended. The root password (i.e. the sudo command) is in place for a reason.
But then again, we're not here to tell you how to use your computer. :)

---

### Post by Lateralis on 2011-06-08
There are ways, yes.  For information on Sudo, see this community wiki page: [RootSudo]("https://help.ubuntu.com/community/RootSudo").

Before you do anything with your security setup, I would like to say, in the strongest possible terms, that turning off this kind of authentication is a really ***_bad_*** idea.  There are a few reasons mentioned in the above link as to why sudo is your friend, the biggest ones simply being security and stability.  If you disable the password request for your account then anything can be done to any directory at anytime and at will.  This essentially leaves your computer wide open to both attacks and accidental damage.  This may render your computer either unstable or entirely broken, where the only recourse is a complete reinstall.

One other point.  During normal operation, I hardly ever have to type in my sudo password.  Maybe once a day when doing package updates, or when I'm editing configuration files in /etc - which is very rare.  Otherwise, everything I do is within my home directory which doesn't require password.  If you have just installed a fresh system then you may have a lot of installing of packages to do, but once that is over with you really won't need to use your password that much.  


If I haven't convinced you just yet that sudo is useful, you may enjoy the following partial workaround.  If you are using the Software Centre to install programs, you may want to start doing them from the command line from within a root shell environment:

```

sudo -i

```

This command, described in the RootSudo link above, gives you a shell with root access.  You can install whatever programs you like without ever being asked for your password.  But, I still do not recommend leaving a logged in root shell for any length of time, nor using one as a habbit, as the same problems surrounding security and accidental catastrophic damage apply.  


If you still wish to go ahead and disable sudo for your account then you will find the instructions in the link but I will not give the instructions here.  I stress again that doing what you intend, purely out of sheer laziness, is really not a bright idea and is strongly discouraged.

---

### Post by Lateralis on 2011-06-08
Enabling the root account is in some ways a *worse* idea than simply removing your need for a sudo password. I think there are reasons for this contained in the RootSudo link posted several times in this thread already. Again, if the OP wants to do that they can do, but l personally strongly discourage this.

Edit: 

@nos09 That situation you describe is one of the reasons why you really shouldn't disable sudo passwords. You only get asked for it if your actions will make a change to anywhere outside of your user account. Thus, when you are asked for a password unexpectedly, you can at least pause and ask "why does this want to change my filesystem?" Or more importantly "What *is* this script/thing doing?" Blindly hitting "go" when you are effectively root (or actually root) is asking for trouble. And this one of a number of reasons I so strongly recommend against the use of such methods.

---

### Post by nos09 on 2011-06-08
> **Lateralis said:**
> Enabling the root account is in some ways a *worse* idea than simply removing your need for a sudo password. I think there are easons for this contained in the RootSudo link posted several times in this thread already. Again, if the OP wants to do that they can do, but l personally strongly discourage this.

i agree. but as a newbies people gets lazy sometimes came form our old friend - WinDos ! but its really important that users learn the importance of sudo and root accounts .. i still uses the root account when i have to do some stuff but not being lazy about it, being careful enough to read scripts and doing administrative task watchfully..

develop the habit of using sudo for the most time.

and for newbies there's another thing i'd like to add as many people will tell you here ... DO NOT download any scripts and if then don't run them with root account (or aka sudo), and even if you know something at least try to read it first !

---

### Post by SteveHillier on 2011-06-08
> **nzjethro said:**
> But then again, we're not here to tell you how to use your computer. :)
I agree but if someone posts on this forum "Guys my system is in an awful mess can you help me.  By the way I turned off all password checking." What might our response be?
[-X

---

### Post by jerrrys on 2011-06-08
> **SteveHillier said:**
> I agree but if someone posts on this forum "Guys my system is in an awful mess can you help me.  By the way I turned off all password checking." What might our response be?
[-X

so true, but where would we be if people didn't try questionable things? a windows only world?

---

### Post by timmy86 on 2011-06-09
Alright i get the idea... as mentioned, i guess its just 'cos this is my first go at a non-M$ OS and as you say - lots of installing at the moment.
You've won me over. i'll leave it there...
Thanks for your words of wisdom

---

### Post by jtarin on 2011-06-09
I know Board of Education,Board of Equalization,Board of Registered Nursing,Board of Directors,Board of Certification,Board of Investments,Board of Trade ,Board of Regents,Board of Medical Specialties and Board of Behavioral Sciences, but I've never encountered the Bored of Passwords......so I'm no help, but count on me for moral support.:P

---

### Post by Legendary_Bibo on 2011-06-09
> **timmy86 said:**
> Alright i get the idea... as mentioned, i guess its just 'cos this is my first go at a non-M$ OS and as you say - lots of installing at the moment.
You've won me over. i'll leave it there...
Thanks for your words of wisdom

Most users don't read scripts anyways so that makes sudo kind of moot.

You'll only have to use sudo for a while, and you may only have to use it once if you download all the programs you want in one go.

I personally think the Software Center shouldn't need sudo (synaptic should though), but Canonical just watches the packages.

---

### Post by nzjethro on 2011-06-09
> I agree but if someone posts on this forum "Guys my system is in an awful mess can you help me. By the way I turned off all password checking." What might our response be?

Something along the lines of told-you-so. Which would be somewhat satisfying. Or else something along the lines of OK, good on you for breaking it, let's fix it and you'll know for next time what not to do.

---

### Post by Mariane on 2011-06-09
> **Legendary_Bibo said:**
> 
Most users don't read scripts anyways so that makes sudo kind of moot.


As if everybody could read them! A few lines with comments and meaninful variable names might give a clue - though the variables could refer to something completely different than what their name suggest if the script is malicious. Most of the time scripts are completely unreadable if you don't already know the scripting language they are written in. And even if you know it sometimes. 

As for the sudo + password issue, I don't so much mind giving my password once when I'm attempting to troubleshoot something but I resent having to type "sudo" each time. I'll look into the root shell option next time. 

Mariane

---

