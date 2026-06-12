---
title: "Frostwire Help."
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Kafubie on 2010-05-17
It's cool how frostwire is downloadable as a Ubuntu/.deb file format so it can run on debian.

When I downloaded it and used the package installer it gave me the following message.

[COLOR="Red"]Error: Dependency is not satisfiable: sun-java6-jre[/COLOR]

What I do to make frostwire work.... Cause my sister is bugging the poop out of me.

(PLEASE HELP, CONTEMPLATING SUICIDE BECAUSE OF POWER OF SISTER NAGGING ABILITIES lol!)

UPDATE:  Someone said this is a bug, I am running 10.04......  The person said is to force the install...  How would I do that?
[http://forum.frostwire.com/viewtopic.php?f=1&t=7916&p=28897&hilit=Ubuntu#p28897](http://forum.frostwire.com/viewtopic.php?f=1&t=7916&p=28897&hilit=Ubuntu#p28897)

---

### Post by ilovelinux33467 on 2010-05-17
hi all you need to do is enable the partner repo.

instructions are here:
[http://linuxtree.blogspot.com/2010/05/how-to-install-java-runtime-environment.html]("http://linuxtree.blogspot.com/2010/05/how-to-install-java-runtime-environment.html")

---

### Post by Bradtek on 2010-05-17
sun-java6-jre

You need to have java installed

```
sudo apt-get install ubuntu-restricted-extras
```

Should do it

if you already have it installed then the bug could be that frostwire install is not recognising that java is installed.

---

### Post by ilovelinux33467 on 2010-05-17
> **Bradtek said:**
> sun-java6-jre

You need to have java installed

```
sudo apt-get install ubuntu-restricted-extras
```

Should do it

if you already have it installed then the bug could be that frostwire install is not recognising that java is installed.

They have taken out sun-java6-jre in 10.04. To get sun-java6-jre in 10.04 you need to enable the partner repo. Then you should be able to install frostwire

---

### Post by Kafubie on 2010-05-17
Thanks guys!
Didn't fail me like you always do!

I downloaded and installed both of the commands.
[Solved]

---

### Post by cowboy7305 on 2010-05-19
I am having same problem and i do have the restricted extras on my computer 
still frost wire will not work

---

### Post by fooman on 2010-05-19
> **cowboy7305 said:**
> I am having same problem and i do have the restricted extras on my computer 
still frost wire will not work

follow the instructions in the link provided by ilovelinux33467 (first response in this thread)....that should fix it.

[http://ubuntuforums.org/showpost.php?p=9316865&postcount=2](http://ubuntuforums.org/showpost.php?p=9316865&postcount=2)

---

### Post by jocampo on 2010-06-19
> **ilovelinux33467 said:**
> hi all you need to do is enable the partner repo.

instructions are here:
[http://linuxtree.blogspot.com/2010/05/how-to-install-java-runtime-environment.html]("http://linuxtree.blogspot.com/2010/05/how-to-install-java-runtime-environment.html")

Love UBUNTU, Love its community and support! ;-) ... thanks, your advice fixed my issue as well...

---

