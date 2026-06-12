---
title: "How to change the Audacious Skin at school?"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by honeybear on 2010-11-20
Hello,

I downloaded some skin themes for audacious, however it is said that to install them one need to be root, but at school, it is not possible. 

Isnt there some folder such as .fonts or .themes, : like .audaciousskins? 

I tried many thigns like creating skins folder but no way :(

---

### Post by Rex Bouwense on 2010-11-20
This may sound simple so excuse me.  Have you tried sudo?  That does give you root access for a limited time.

---

### Post by yetiman64 on 2010-11-20
> **Rex Bouwense said:**
> This may sound simple so excuse me. Have you tried sudo? That does give you root access for a limited time.

It is unlikely being a school computer that you will be in the sudoers file anyway OP.

Have you tried asking whoever administers the computers there to do the install for you (as they will have the required root access) ?

> I tried many thigns like creating skins folder but no way :-(Looking for a simple way to bypass the need for root access on someone else's computer to install skins doesn't sound like a particularly good idea, and in fact may land you in trouble with the school (depending on how strict their policies are). 

My advice is to think carefully about what you are doing, and preferably ask permission as it is not your computer.

---

### Post by honeybear on 2010-11-21
> **Rex Bouwense said:**
> This may sound simple so excuse me.  Have you tried sudo?  That does give you root access for a limited time.

school admin does not give root pwd , nor enable sudo in any situations. no chances, well I understand , you know wargames movie

> **yetiman64 said:**
> It is unlikely being a school computer that you will be in the sudoers file anyway OP.

Have you tried asking whoever administers the computers there to do the install for you (as they will have the required root access) ?


Forget guys to get the password , it is a school, they wont give the passwd. it is written on the whole thread.. :( Nor wont proceed under sudo, even, in whatsoever...

---

### Post by mcduck on 2010-11-21
Audacious manual gives three different locations for themes, two of which are in user's home directory. Try these:

~/.audacious/Skins
~/.share/audacious/Skins

---

### Post by gandaran on 2010-11-21
you can put the skins in your user directory /home/'user'/.local/share/audacious/Skins

---

### Post by honeybear on 2010-11-21
not working :(
> 

~/.audacious/Skins$ ls
Audacious grey theme  BlubuntuBlue      new_wave_audacious
Audacious Lite        Cyanian_2010.wal



 .local/share/audacious/Skins
works but man, skins are all blue
instaead of what is displayed 

it is a bug very certainly again :(

---

### Post by gandaran on 2010-11-22
which interface are you using the old winamp or the new gkt and the skins are for which one?
I'm using winamp and xmms skins and no problem with them here.

---

### Post by julio_cortez on 2010-11-22
> **honeybear said:**
> school admin does not give root pwd , nor enable sudo in any situations. no chances, well I understand
Of course, if I were the sysadmin of the school I wouldn't really want to spend all the day fixing/reinstalling machines broken by people who don't know what they do.

It seems strange to me anyway that you cannot load your themes under your /home directory, I don't see any reason not to let you do so!

---

### Post by mastablasta on 2010-11-22
then again is **Audacious **really needed in school? you should learn not listen to music or play games.

---

