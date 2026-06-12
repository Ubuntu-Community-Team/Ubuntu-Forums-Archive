---
title: "A few questions"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by takiama on 2009-10-21
Two main things:
1. Regarding video driver: I have noticed that my video is not working at optimum efficiency, so I was wondering if there was a better driver for my card.  The result of lspci|grep VGA is
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
```

2. I prefer managing my software through the terminal, however I have not found a way to find the name of the software I want so I can plug it into ```
sudo apt-get install NAMEHERE
```  Is there any apt-get command that lists available packages?

Any help would be greatly appreciated:)

---

### Post by fooman on 2009-10-21
for #2....to list all available packages, try:

```
apt-cache pkgnames
```

and to list installed packages, try:

```
 dpkg -l
```

---

### Post by martrn on 2009-10-21
1. ```
sudo apt-get install xserver-xorg-video-intel
```
Warning can cause problems, but can clear up problems also.

2. [..]sudo apt-get install [NAMEHERE] [..] Is there any apt-get command that lists available packages?

Try:
```
sudo apt-get install apt-cache

sudo apt-cache serch NAMEHERE
sudo apt-cache search firefox
```

[...etc...]

---

### Post by alphaniner on 2009-10-21
You can use aptitude to get information about packages:

```
aptitude search *keyword*
```

At least I think that's how it works.  The syntax is pretty complex and I only used it once or twice... you should check the man page.

If you have the name of a package and want to get a description, use

```
aptitude show *package_name*
```

Can't help with the video issue.

---

