---
title: "I'm curious..how are updates and such ... vetted?"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by s1baker on 2010-12-18
Don't get me wrong, I firmly believe that our operating system software should be open and for examination for all to see, and I do truelly appreciate the Ubuntu family that provides this great OS for us, but just exactly how are the updates to the system OS that are regularly posited for download vetted?

---

### Post by iponeverything on 2010-12-18
To get an idea regarding the who, how, why and other mysteries and magic with package updates - bug fixes - and the controlled mayhem that happens behind the scenes --

sign up for launchpad account

when you see an interesting update in the update manager, click on it so that you see the notes associated with it. Note launch pad bug reference #.

Go into launchpad read though progression of the bug, noting and following upstream references.

Note the reoccurring names and find bugs seem to seem attract them. Soon, it will all become clear, that there is not a simple or "exact" answer to you question. It is very dynamic process that is not perfect but works pretty well. 

I don't update as soon as the updates show up, I wait a few weeks and to the throngs of enthusiastic updater's out there do vetting for me and I don't do kernel updates unless find something compelling in the notes for update.

---

### Post by s1baker on 2010-12-18
That does not answer my question. Quite simply, when upgrades/updates are offered to Ubuntu users, who exactly are the the people who verify that the executable code that people are downloading has been vetted?

---

### Post by QLee on 2010-12-18
[QUOTE=s1baker]That does not answer my question. Quite simply, when upgrades/updates are offered to Ubuntu users, who exactly are the the people who verify that the executable code that people are downloading has been vetted?[/QUOTE]

That would be the maintainer(s) of the specific package. Not just anybody can upload packages to the official repositories, that's why a recommendation to only download software from trusted sources. Of course, if you have the knowledge and experience you could download source from anywhere and examine it before installing.

If you want to see the maintainer, you could use the Synaptic GUI by selecting the package and checking its properties from the menu.

If you prefer the command line approach, you could use,
 dpkg-query -W -f='${Package} ${Version}\t${Maintainer}\n' [B](insert the name of the package you are interested in here)
[/B]

---

