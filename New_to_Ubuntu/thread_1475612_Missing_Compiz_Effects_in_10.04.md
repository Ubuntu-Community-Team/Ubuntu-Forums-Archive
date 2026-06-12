---
title: "Missing Compiz Effects in 10.04"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2010-05-07
After updating to Ubuntu 10.04 I noticed that a lot of compiz effects that I had in 9.10 are missing. (Too many to list). Is there any way to get back all the missing compiz effects and options?

---

### Post by Mustard on 2010-05-07
To manually choose all the options you could install the settings manager...

```
sudo aptitude install compizconfig-settings-manager
```

---

### Post by Captainflowers91 on 2010-05-07
No, what happens is when I go into Compiz settings, many options are missing. Show Mouse, The Grid, Cube Deformation, Extra Window Animations, the list goes on

---

### Post by buntudawg on 2010-05-07
Have you tried the advanced search just above the close button?

---

### Post by Mustard on 2010-05-07
> **Captainflowers91 said:**
> No, what happens is when I go into Compiz settings, many options are missing. Show Mouse, The Grid, Cube Deformation, Extra Window Animations, the list goes on

You could do a search for compiz packages in the repository

```
aptitude search compiz
#this will list all packages with the keyword 'compiz'

```

The packages in the list this will generate with an 'i' next to them are installed already.  Look for packages that arent installed yet and use aptitude to install them.

```
sudo aptitude install SomePackageName
#substitute the package name you want to install for SomePackageName

```

I suspect the package you are looking for might be 
```
p   compiz-fusion-plugins-extra  - Collection of extra plugins from OpenCompositing for Compiz
```

---

### Post by Captainflowers91 on 2010-05-07
yea, all that does is allow me to search for compiz options I already have. What I need is a way to install the missing options

---

### Post by buntudawg on 2010-05-07
I think the packages are  compiz-fusion-plugins-main  and  compiz-fusion-plugins-extra

---

### Post by Captainflowers91 on 2010-05-07
Yup. that did it. Thanks for all the help. Works great now

---

### Post by KdotJ on 2010-05-07
I also had this same problem. I wonder why installing the compiz manager and the top desktop effects didn't get the extra plugins automatically like it did in karmic...

---

### Post by topet2k12001 on 2010-05-19
Issue [SOLVED]!

> **Mustard said:**
> You could do a search for compiz packages in the repository

```
aptitude search compiz
#this will list all packages with the keyword 'compiz'

```

The packages in the list this will generate with an 'i' next to them are installed already.  Look for packages that arent installed yet and use aptitude to install them.

```
sudo aptitude install SomePackageName
#substitute the package name you want to install for SomePackageName

```

I suspect the package you are looking for might be 
```
p   compiz-fusion-plugins-extra  - Collection of extra plugins from OpenCompositing for Compiz
```

Hi, I'm new to using Linux (Ubuntu). Just like to say that I'm excited using this and I'm hoping to learn more (currently running dual-boot with Windows 7). I particularly quoted this message because it helped me solving the same problem. Thanks!

---

### Post by lpanebr on 2010-09-22
Thanks! Installing the compiz-fusion-plugins-extra then loging out and logging in again restored my plugins.


Luciano

---

