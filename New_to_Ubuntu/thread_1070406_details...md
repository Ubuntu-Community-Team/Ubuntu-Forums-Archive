---
title: "details.."
date: 2009-02-15
forum: New to Ubuntu
---

### Post by KS1987 on 2009-02-15
I have two minor questions, that are details, but still make me curious.

*****I intiated following command:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```
What does it exactly do?
I didn't do anything else in the terminal with it, is that bad?
Is it stored somewhere?
Anything else to add?

*****My epiphany browser asked if I wanted to save a password for some site, I said "never". Where can I change this? Where is this selection stored?

Thanks in advance.

---

### Post by Xiong Chiamiov on 2009-02-15
Thanks for asking about commands you're not familiar with; too often we tell people to do things without telling them what they're doing, and that can lead to Bad Things(tm).

For future reference, you can find out more information on almost any command with the 'man' command, like so:
```
man wget
```
It'll be a bit terse, however, so don't feel bad if you don't understand what it's saying.

Wget fetches a file from the internets.  The -O flag tells it to store the retrieved file in a different filename than the default.  Specifically, you're putting it in the sources.list.d/ directory, which is where all of the mirror information for APT is stored.

---

### Post by ibizatunes on 2009-02-15
You are install medibuntu repository, it should allow you to install more application ie adobe reader 8, google earth, google picasa, copy right protected DVD's

copy this into the terminal
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list --output-document=/etc/apt/sources.list.d/medibuntu.list
```
then pasted this into the terminal

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Copy the rest of the website pages in your terminal ie x64 for x64 bit or i386 for 32 bit system

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

This will give you a list of new application you can install

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

---

### Post by KS1987 on 2009-02-15
Thank you, this was most helpful. Any information on the epiphany question?

---

