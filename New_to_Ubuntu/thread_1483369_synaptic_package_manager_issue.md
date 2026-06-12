---
title: "synaptic package manager issue"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by georgian on 2010-05-14
**[COLOR=Black]can't open syn pac[/COLOR]****[COLOR=Black]aptic[/COLOR]****[COLOR=Black]kage manager [/COLOR]**

I am using ubuntu 9.04, from past few days i am unable to open synaptic package manager , evrytime i try to open it i get message : 

[B][COLOR=DarkSlateBlue][I]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/I][/COLOR][/B]


I will be waiting for your help!! 
Thanks!!!!
bye :)

---

### Post by -humanaut- on 2010-05-14
A program failed to install properly. You'll have to open a terminal and run "sudo dpkg --reconfigure -a" to regain control of synaptic post the results here if that fails to unlock synaptic.

---

### Post by georgian on 2010-05-19
I typed in the above command in terminal and got following output:

[COLOR=Indigo][COLOR=Navy]dpkg: unknown option --reconfigure

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' ![/COLOR]
[/COLOR]
Thnx

---

### Post by apjone on 2010-05-19
there is no space between dpkg and -reconfigure

```
dpkg-reconfigure -a
```

---

### Post by Soul-Sing on 2010-05-19
```
sudo dpkg --reconfigure -a
```
in the terminal (afaik)

---

### Post by CompyTheInsane on 2010-05-19
It seems that the above posters meant:
```

sudo dpkg --configure -a

```

---

### Post by georgian on 2010-05-20
Yipeee !! I typed in 
[COLOR=Navy]sudo dpkg --configure -a[/COLOR]  and it's working fine now.

Thanks to everyone for helping me out.  

:)

---

### Post by Paqman on 2010-05-20
> **georgian said:**
> Yipeee !! I typed in 
[COLOR=Navy]sudo dpkg --configure -a[/COLOR]  and it's working fine now.

Thanks to everyone for helping me out.  

:)

For terminal commands it's probably easier just to copy and paste to prevent spelling errors.

You can also use tab auto-completion, which is really handy for long directory names. Just hit the first couple of letters then TAB.

---

