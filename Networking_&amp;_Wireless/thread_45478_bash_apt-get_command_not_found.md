---
title: "bash: apt-get: command not found"
date: 2005-06-30
forum: Networking &amp; Wireless
---

### Post by podrik0 on 2005-06-30
I required my internet to work, which I have to install drivers for seperetly... 
 
 I go to ./configure and then: 
 
 checking how to run the C preprocessor... /lib/cpp 
 configure: error: C preprocessor "/lib/cpp" fails sanity check 
 
 So assume I need to build essential then get: 
 lib/cpp" fails sanity check 
 bash: apt-get: command not found 
 
 What is going on? I urgently need to resolve this for internet access!!! 
 THANK YOU!

---

### Post by Seti on 2005-06-30
Are you trying to run apt as regular user? Would ```
sudo apt-get xxx
``` 
help?

---

### Post by podrik0 on 2005-06-30
I have tried as root as well! Still says its not found  :-?

---

### Post by spanishwasabi on 2005-06-30
Are you sure the command is in your path?
If your program searchs in your path and apt-get is not in your path... is gonna never find it.

which apt-get

If it does not work

sudo which apt-get

or in last ressort

sudo find / -name "apt-get" -print

If none give an answer... well, you do not have apt-get. And that's one of the weirdest errors for a debian based distribution!

G

---

### Post by arosct on 2005-07-02
[QUOTE=spanishwasabi]Are you sure the command is in your path?
If your program searchs in your path and apt-get is not in your path... is gonna never find it.

which apt-get

If it does not work

sudo which apt-get

or in last ressort

sudo find / -name "apt-get" -print

If none give an answer... well, you do not have apt-get. And that's one of the weirdest errors for a debian based distribution!

G[/QUOTE]
 try this
sudo /usr/bin/apt-get
It is installed there.
Otherwise try '/usr/sbin/synaptic' which is a gui tool when you're not familiar with the command line.

---

### Post by philostik on 2008-02-06
Greetings:

I do notice that this thread has died long back but holds the error that I am getting. I tried looking for apt-get at all the places but couldn't locate it anywhere. Can anyone please help me know how do I get the apt-get running on my gutsy gibbon...

Regards,
Manish

---

