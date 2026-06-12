---
title: "cpan install"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by dvdljns on 2009-09-03
I tried to install apache::asp. went to the page and decided I needed to install cpan first. It asked me a lot of questions which I answered and thought I did all right but when I ran the command to install apache asp I got the longest list of errors I have ever seen. I uploaded the error files.
one is everything from the start of the cpan install to the end. The second is the attempt to install apache::asp. Can someone look and tell me what went wrong I either need to fix this or reinstall.

---

### Post by Shig on 2009-09-03
Hi There

Under Ubuntu and Debian it is not really worthwhile configuring CPAN and updating it, as most perl packages are packaged in Deb files and available using APT.

At a console the following command will install the module you are after:
```
sudo apt-get install libapache-asp-perl
```

---

### Post by Mornedhel on 2009-09-03
As Shig says, when available, always use the packages in your repository.

When unavailable, run
```
sudo cpan
```

and in the cpan shell, run install Your::Module.

Note that the cpan install may result in the installation of lots of dependencies without oversight by your package manager, which is problematic. Optimally, you should first check the dependencies of the module you want to install, then try to install as many as possible from APT.

---

### Post by dvdljns on 2009-09-03
> **Mornedhel said:**
> As Shig says, when available, always use the packages in your repository.

When unavailable, run
```
sudo cpan
```

and in the cpan shell, run install Your::Module.

Note that the cpan install may result in the installation of lots of dependencies without oversight by your package manager, which is problematic. Optimally, you should first check the dependencies of the module you want to install, then try to install as many as possible from APT.

Thanks, I should have asked before I messed with it.

---

### Post by Gen2ly on 2009-09-03
dvdljns, I do it like you do but I've seen people also use 'pear' to do this.  For example:

```
pear upgrade-all
pear install Numbers_Roman
```

Haven't tried this though.

---

### Post by dvdljns on 2009-09-04
> **Gen2ly said:**
> dvdljns, I do it like you do but I've seen people also use 'pear' to do this.  For example:

```
pear upgrade-all
pear install Numbers_Roman
```

Haven't tried this though.

This is the first time I did it but when I ran a search I found cpan. sounded easy and I thought may be it might be good to have cpan, but apt-get is better. The last thing I need is something messing with dependencies. At least till I lean how to fix them.

---

### Post by Gen2ly on 2009-09-04
Oh, yeah, Shig's approach is better.  Just thought I'd mention it in case sometime in the future if you need a module that isn't in the repositories.

---

### Post by Mornedhel on 2009-09-04
> **Gen2ly said:**
> dvdljns, I do it like you do but I've seen people also use 'pear' to do this.  For example:

```
pear upgrade-all
pear install Numbers_Roman
```

Haven't tried this though.

I think pear is a PHP utility.

---

### Post by dvdljns on 2009-09-04
should I see something in modules letting me see pearl is there.

---

### Post by Mornedhel on 2009-09-04
> **dvdljns said:**
> should I see something in modules letting me see pearl is there.

I'm not sure what module you mean.

If you want to check if pear (the PHP utility) is installed, type "dpkg -s php-pear" in a terminal.

Perl is always installed, Linux distributions rely heavily on it.

If you want to check if a Perl module is installed, type "perl -mYour::Module -e '1'". If you get a compilation error message, the module is not installed.  If you get no output, the module is installed.  Note that there is no space between -m and the module name, and that -e '1' (one, not lowercase L) is an empty script that just loads whatever is needed, and returns successfully.

---

### Post by dvdljns on 2009-09-04
No I mean once I install apache::asp,should there be some type module in apache? Its going to take a while for me to learn how to config this so I would like to check the install first.

---

