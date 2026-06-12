---
title: "question about coding"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Achilles124 on 2009-01-05
I have tried several times to install openoffice 3 on my computer, but I get an errormessage when trying to open it:

**terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'**

Now i have found two pages on this issue:
[http://ubuntuforums.org/showthread.php?t=173566]("http://ubuntuforums.org/showthread.php?t=173566")
[http://ubuntuforums.org/archive/index.php/t-216522.html]("http://ubuntuforums.org/archive/index.php/t-216522.html")

But the codes in the solution is not the same.
**sudo chown -vR <user>:<group> /home/<user>/.openoffice.org2**
Or 
**sudo chown -R andrew.andrew ~/.openoffice.org2/**

What is the right code to fix the problem?

---

### Post by Gwasanaethau on 2009-01-05
Hi there!

Believe it or not, the two commands are actually identical - they just use different 'shorthand'. The ~ symbol at the beginning of a file name is the same as using /home/<user>

Also, where the first command has <user>:<group> they're just generic terms - the second command uses a very specific version for 'andrew'. Assuming your username on your system is 'achilles124', the command you need is:
```
sudo chown -vR achilles124:achilles124 /home/achilles124/.openoffice.org2
```
or
```
sudo chown -vR achilles124:achilles124 ~/.openoffice.org2
```
whichever you prefer.

---

### Post by RomeReactor on 2009-01-05
Hi. Both would be correct; however, there's a typo in the second command. It should read:
```
sudo chown -R andrew:andrew ~/.openoffice.org2
```
(notice the colon between the two "andrew").

The **-v** option just tells chown be verbose; the **-R** is to act recursively, working on however many folders and files are inside the openoffice2 directory. Try:
```
man chown
```
for more on that command.

Important: remember to change both <user> and <group> for your own user name in the first command, or in both "andrew" instances in the second command.

---

### Post by Achilles124 on 2009-01-06
Thank you, Gwasanaethau and RomeReactor.

---

### Post by Gwasanaethau on 2009-01-09
You're welcome! ;)

---

