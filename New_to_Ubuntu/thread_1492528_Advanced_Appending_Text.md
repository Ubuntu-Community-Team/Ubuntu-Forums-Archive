---
title: "Advanced Appending Text"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by DivinusVox on 2010-05-24
I've run into a situation where I figured I would seek the more experienced. I've had a hard time finding information on the subject via google/yahoo searches.

I have a configuration file that I need to write custom data into for each installation of Drupal. Specifically, the database connectivity information.

The line is:
$db_url = 'mysql://$user:$pass@$host/$database';

The line itself is defining a variable, so I need the line to ignore the part of the string ($db_url). I've found I can do this by using the ' markings around the variable. Unfortunately, I'm having trouble with the existing ' marks around the second being read as taking the rest literally as well. The configuration needs to have the single quotes to be read properly, but I need the rest of the string to insert user defined values.

Any ideas?



Thanks,

DV

---

### Post by anarchywolf46 on 2010-05-24
I'm not too familiar with what you are doing, but my guess would be change the single quotes originally there to double quotes or use \' to do it. That's just my guess though.

---

### Post by DivinusVox on 2010-05-24
There we go, backslash solves what ails. Figured it was something silly that I wasn't thinking of. ;)

Thanks much.

---

### Post by anarchywolf46 on 2010-05-25
Wow, glad it helped. It's always the simple things we all overlook.  :KS

---

