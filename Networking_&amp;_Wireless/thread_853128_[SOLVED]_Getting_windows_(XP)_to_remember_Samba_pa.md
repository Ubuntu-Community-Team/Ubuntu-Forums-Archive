---
title: "[SOLVED] Getting windows (XP) to remember Samba password"
date: 2008-07-08
forum: Networking &amp; Wireless
---

### Post by masterdam79 on 2008-07-08
Hiya everyone,

Just something that's busting my nuts is the following..

[SETUP]

Ubuntu 7.10 desktop server with Samba server and smb user "ina" with setup password with
```
smbpasswd -a ina
``` 
and smb user "masterdam79" with setup password with
```
smbpasswd -a masterdam79
``` 

Windows Vista (Home Premium) desktop with windows user "masterdam79"

Windows XP (Home) Laptop with windows user "ina"

[PROBLEMS SOLVED]

Am now able to access the Samba shares from my Windows Vista machine WITHOUT entering username/password for my Samba user because I made a Samba user equal to my Vista windows user "masterdam79".

I WAS able to select the "Remember my password" checkbox on my Vista machine, first time I logged on into the Ubuntu server and now I never have to type in the credentials again on that machine.

[PROBLEMS NOT SOLVED]

Am able to access the Samba shares from my Windows XP machine WITH entering username/password for my Samba user which I made equal to my XP windows user "Ina"

I was NOT able to select the "Remember my password" checkbox on my XP machine, which brings me to the target set out on the subject of this post.

How do I make Windows XP remember my Samba password and why is Vista remembering it without a problem?

Where is my "Remember my password" checkbox on XP?


Much thanks!!

P.s. I have already tried with another XP Home machine and there WAS a "Remember my password" check option when connecting to the Linux share. (Some people claim this to be a disfunctionality of the "Home" version of XP, which I here declare as a load of ____.

P.s.P.s. Also It has nothing to do with the Linux machine as both my Vista machine and (the other) XP machine were able to remember passwords. Clearly something went wrong on the first XP machine that disabled the "Remember my password" checkbox on network login.


In Vista I can add servers manually and it remembers the passwords without problems.
[SCREENSHOTS]
[http://masterdamonline.nl/Vista-remembered-password.JPG](http://masterdamonline.nl/Vista-remembered-password.JPG)
[http://masterdamonline.nl/Vista-remembered-password-001.jpg](http://masterdamonline.nl/Vista-remembered-password-001.jpg)

In XP (virtualized) Home I am able to add servers, but it doesn't remember the passwords
[SCREENSHOTS]
[http://masterdamonline.nl/XP-Virtualized-001.JPG](http://masterdamonline.nl/XP-Virtualized-001.JPG)
[http://masterdamonline.nl/XP-Virtualized-002.JPG](http://masterdamonline.nl/XP-Virtualized-002.JPG)
[http://masterdamonline.nl/XP-Virtualized-003.JPG](http://masterdamonline.nl/XP-Virtualized-003.JPG)

and in the XP Home laptop I can't even add servers manually, let alone get it to remember my passwords.
[SCREENSHOT]
[http://masterdamonline.nl/XP-Laptop.JPG](http://masterdamonline.nl/XP-Laptop.JPG)
[http://masterdamonline.nl/XP-Laptop-001.JPG](http://masterdamonline.nl/XP-Laptop-001.JPG)

---

### Post by df6269 on 2008-07-08
Please use "control userpasswords2" command in windows xp.
It will display user account for local and network and .Net passport.
You can add user in advance --> manager password

---

### Post by masterdam79 on 2008-07-09
Thanks heaps!!

It was not the actual solution (but it lead to an acceptable one):

[I could add useraccounts]
[http://masterdamonline.nl/XP-Laptop-User-Accounts-001.JPG](http://masterdamonline.nl/XP-Laptop-User-Accounts-001.JPG)

I checked the "Users must enter a ...", but I don't think this was such a mayor difference.

Then I mounted a network drive and selected the option for "log on using a different user"

[http://masterdamonline.nl/XP-Laptop-Map-Network-Drive.JPG](http://masterdamonline.nl/XP-Laptop-Map-Network-Drive.JPG)
Connect using a _different user name_
filled in my (same) credentials and BINGO!!:guitar:

The earlier mentioned checkbox has not returned, but became obsolete.

---

