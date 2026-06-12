---
title: "Where is my new installed program?"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by David4 on 2008-12-12
Sorry for this question, been searching for threads but no luck.
Just installed Avast antivirus for Linux.
Synaptic Package Manager shows the program Avast4Workgroup as installed, I thought after installing will see a new Icon as in Windows, but no such a thing, check on Places, computer,files,etc,perhaps am looking for a folder/programs but no.
Where should I look?
David

---

### Post by neu2buntu on 2008-12-12
this happens with some programs that are not native in linux   you could try opening the terminal and type in the name of the program and maybe go to computer -filesystem then search for "avast" and in view make sure you tick show hidden files

---

### Post by billgoldberg on 2008-12-12
> **David4 said:**
> Sorry for this question, been searching for threads but no luck.
Just installed Avast antivirus for Linux.
Synaptic Package Manager shows the program Avast4Workgroup as installed, I thought after installing will see a new Icon as in Windows, but no such a thing, check on Places, computer,files,etc,perhaps am looking for a folder/programs but no.
Where should I look?
David

Unless you run a mail server or something, remove it.

---

### Post by theevilhamster on 2008-12-12
try looking for it with the other binarys in the following folders.

/bin
/usr/bin
/usr/local/bin
/usr/sbin
/usr/local/sbin

maybe its installed but just hasn't come up in the menus

---

### Post by David4 on 2008-12-12
no luck
David

---

### Post by theevilhamster on 2008-12-16
hummm... strange... i dont think it installed properly, or it installed in a very strange place. sorry, i dont think there is much else i can think off at the moment.

---

### Post by nandemonai on 2008-12-16
> **billgoldberg said:**
> Unless you run a mail server or something, remove it.

^

You don't need it unless you wish to scan for windows viruses via a email server or something along those lines.

---

### Post by grazed on 2008-12-16
> **nandemonai said:**
> ^

You don't need it unless you wish to scan for windows viruses via a email server or something along those lines.

this is incorrect. the linux edition of avast scans for native linux malware, in addition to known windows malware.

that said, it is very difficult to infect your machine with said malware. typically, for it to penetrate your system, you would need to authorize it yourself. (entering root password) entering the root password itself is not easily done in ubuntu due to the fact that the system is designed not to require it, thus, the user not knowing it.

---

### Post by grazed on 2008-12-16
> **David4 said:**
> Sorry for this question, been searching for threads but no luck.
Just installed Avast antivirus for Linux.
Synaptic Package Manager shows the program Avast4Workgroup as installed, I thought after installing will see a new Icon as in Windows, but no such a thing, check on Places, computer,files,etc,perhaps am looking for a folder/programs but no.
Where should I look?
David

which version of the download did you install? rpm, deb, etc..?

---

### Post by nandemonai on 2008-12-16
> **grazed said:**
> this is incorrect. the linux edition of avast scans for native linux malware, in addition to known windows malware.

that said, it is very difficult to infect your machine with said malware. typically, for it to penetrate your system, you would need to authorize it yourself. (entering root password) entering the root password itself is not easily done in ubuntu due to the fact that the system is designed not to require it, thus, the user not knowing it.

Oh reallly? I should have looked into it more. Apologies. I'd assumed it was another email attachment scanner type thing.

Learn something new everyday ;)

---

### Post by Tatty on 2008-12-16
> **grazed said:**
> this is incorrect. the linux edition of avast scans for native linux malware, in addition to known windows malware.

Whilst true, there are very few linux viruses in the wild.  Although it may have changed by now. Last time I checked (about a year ago) most reputable sources said there were no known linux viruses in the wild which could still infect a modern linux system.
The fact is that most linux viruses get patched out of existance almost as soon as they are discovered.

It takes time once a virus is identified for an anti-virus company to dissect it, put an entry and fix in their databases and distribute it to users.  Often the community has dealt with any vulnerabilities itself by then.  So the most common advice given to linux users is to simply keep their systems updated, and to keep an ear in the community to hear of any new threats which emerge.

All that said, I would never discourage someone from installing anti-virus software if they wanted to.  As the linux desktop market increases, so will the number of viruses and exploits, and so due vigilance should always be adhered to.  As to whether this will ever get to the extreme levels seen in Windows remains to be seen, although past precident certainly gives hope that it can at least be contained to a more manageable level.

Personally I dont use anti-virus software on my linux machines.  However, I am prepared to install it one day, if things change.

@the OP:

try:
```
whereis Avast4Workgroup
```

---

