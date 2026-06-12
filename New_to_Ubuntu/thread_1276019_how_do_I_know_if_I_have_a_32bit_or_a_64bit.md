---
title: "how do I know if I have a 32bit or a 64bit"
date: 2009-09-26
forum: New to Ubuntu
---

### Post by ernie101 on 2009-09-26
I'm trying to install all of the stuff I need to get movie streams to work. The last than they are asking me to do is :

[COLOR=Red][B]For Windows, Real Networks, Quick Time and other codecs add one line depending of your Ubuntu version:

Ubuntu 9.04 32bit
[/B][/COLOR][INDENT][COLOR=Red]**sudo apt-get install w32codecs**[/COLOR][/INDENT][COLOR=Red][B]Ubuntu 9.04 64bit
[/B][/COLOR][INDENT][COLOR=Red][B]sudo apt-get install w64codecs

[/B][COLOR=Black]

[/COLOR][/COLOR][/INDENT]How do I know the type I have?

thanks,  ernie

---

### Post by howefield on 2009-09-26
Open a terminal and type

```
uname -a
```

If the returned output has x86_64 in it, you have 64 bit, if not... you don't.

---

### Post by mfernando on 2009-09-26
Go to **System > Administration > System Monitor** and click on the first tab. It will state what CPU you have under **Hardware**. You can google that to find if it is 32 or 64 bit.

---

### Post by howefield on 2009-09-26
> **mfernando said:**
> Go to **System > Administration > System Monitor** and click on the first tab. It will state what CPU you have under **Hardware**. You can google that to find if it is 32 or 64 bit.

How will that tell the OP whether the install is 32 bit or not ?

He is asking about the software, not the hardware.

---

### Post by mlentink on 2009-09-26
I don't think he/she is.

The OP wants to know which version to install. which is dependent on his/her hardware.
howefield's response is quite to the point.

---

### Post by howefield on 2009-09-26
> **mlentink said:**
> I don't think he/she is.

The OP wants to know which version to install. which is dependent on his/her hardware.
howefield's response is quite to the point.

The OP has Ubuntu already installed, and is at the point of installing the multimedia codecs, he wants to know if he has installed a 32 or 64 bit version in order to install the correct codecs.

The capability of the hardware is irrelevant.

---

### Post by slakkie on 2009-09-26
```

getconf LONG_BIT

```

That will help you.

---

### Post by bodhi.zazen on 2009-09-26
> **howefield said:**
> The OP has Ubuntu already installed, and is at the point of installing the multimedia codecs, he wants to know if he has installed a 32 or 64 bit version in order to install the correct codecs.

The capability of the hardware is irrelevant.

+1

The OP is asking how to determine if he or she needs to install the 32 or 64 bit codics.

One can run 32 bit Ubuntu on 32 bit Arch so it is probably best to use

```
uname -a
```

If the OP wanted to know if he or she had a 64 bit CPU the other answers would be more appropriate for the same reason (uname -a does not identify the hardware).

For that I use :

```
grep --color=always ' lm ' /proc/cpuinfo
```

Output in red [color=red]lm[/color] = a 64 bit CPU.

---

