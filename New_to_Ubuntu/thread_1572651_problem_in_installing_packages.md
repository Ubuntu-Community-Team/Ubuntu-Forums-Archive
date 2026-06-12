---
title: "problem in installing packages"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by utkarshjadhav on 2010-09-11
For every installation or even upgrade and update ,there is following error


```
Errors were encountered while processing:
 tex-common
 texlive-binaries
E: Sub-process /usr/bin/dpkg returned an error code (1)
```HELP!!!

---

### Post by sikander3786 on 2010-09-11
First of all try the following commands.

```

sudo apt-get clean

```

```

sudo apt-get install -f

```

```

sudo dpkg --configure -a

```

Also go to Synaptic and in custom filters apply the Broken filter. Try to fix the broken packages.

---

### Post by drpjkurian on 2010-09-11
Hi
You can solve it by removing the offending package
Try ```
sudo aptitude
```

---

### Post by utkarshjadhav on 2010-09-11
@ [sikander3786]("http://ubuntuforums.org/member.php?u=806649") : thank you. but prob isnt solved.


```
sudo apt-get clean
```RUNS 

but remaining command arent running and showing the same prob. 
and about synaptic ... there are no broken packages in the list....  :( :(

@[drpjkurian:]("http://ubuntuforums.org/member.php?u=805294")thank you for response.
i dunno how to use aptitude.i tried to locate offending packages.Plz can you specify more?


can anyone temme whats the EXACT  problem I am facing? :( :(

---

### Post by drpjkurian on 2010-09-12
Hi
The offending softwares are
tex-common
texlive-binaries

Use the command which I have mentioned in the earlier post to remove those programmes

---

### Post by beew on 2010-09-12
Do you mean ```
sudo aptitude remove <offending packages>
```?

It is not clear when you just say "sudo aptitude" when you left out the keyword "remove".

---

### Post by sikander3786 on 2010-09-12
[http://ubuntuforums.org/showthread.php?t=1481877](http://ubuntuforums.org/showthread.php?t=1481877)

The problem is solved in the above mentioned thread and the OP did

```

sudo aptitude remove tex-common

```

```

sudo aptitude remove texlive-binaries

```

See that thread for more details.

Regards.

---

### Post by utkarshjadhav on 2010-09-12
@[sikander3786]("http://ubuntuforums.org/member.php?u=806649"),[ beew]("http://ubuntuforums.org/member.php?u=1090336"),[ drpjkurian ]("http://ubuntuforums.org/member.php?u=805294")
thank you!
it worked !
problem is SOLVED..


Hey can anyone tell me what might had gone wrong...
I mean why did I get this error?when this situation comes??
any guesses,ideas?

---

### Post by drpjkurian on 2010-09-13
hi
You are most welcome

---

### Post by sikander3786 on 2010-09-16
Sometimes it is broken packages, sometimes unmet dependencies, sometimes some other issue. Just let us know when it happens again so we can try to fix it for you. LOL ;-)

Regards.

---

