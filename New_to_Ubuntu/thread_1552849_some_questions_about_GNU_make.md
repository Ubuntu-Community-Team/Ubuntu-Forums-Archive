---
title: "some questions about GNU make"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by logicman112 on 2010-08-14
3.7 How Make&#64257;les Are Remade
Sometimes make&#64257;les can be remade from other &#64257;les, such as RCS or SCCS &#64257;les. If a make&#64257;le can be remade from other &#64257;les, you probably want make to get an up-to-date version of the make&#64257;le to read in.
To this end, after reading in all make&#64257;les, make will consider each as a goal target and
attempt to update it. If a make&#64257;le has a rule which says how to update it (found either
in that very make&#64257;le or in another one) or if an implicit rule applies to it (see Chapter 10
[Using Implicit Rules], page 101), it will be updated if necessary. After all make&#64257;les have been checked, if any have actually been changed, make starts with a clean slate and reads all the make&#64257;les over again. (It will also attempt to update each of them over again, but normally this will not change them again, since they are already up to date.)
--------------------------------------------------------------------------------------------
I have copied some lines from the manual GNU make and have some questions. What are RCS and SCCS files? Where are they?
make will consider each Makefile as a goal target? What makefiles is it talking about? the makefiles that have been included? 
Would you please clarify it by an example?

Thank you to read my message.

---

