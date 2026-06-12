---
title: "Problem in installing gcc"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by sm_here on 2010-01-28
I have gcc-4.4.1. I wish to install gcc-3.3. I have downloaded gcc-3.3.
How do i install it?

---

### Post by Temposs on 2010-01-28
in what format did you download gcc-3.3?

---

### Post by sm_here on 2010-01-28
as .tar.gz

---

### Post by Temposs on 2010-01-28
When you need an older version of a package, you should try to find if Ubuntu has a legacy package put together for the version you want. That will save you the hassle of compiling gcc(that'll take like an hour or something).

It turns out that in Ubuntu 8.04 Hardy Heron, gcc-3.3 was included. So, I found the page to download it: 

[http://packages.ubuntu.com/hardy/devel/gcc-3.3](http://packages.ubuntu.com/hardy/devel/gcc-3.3)

Before you install that package, you should install the following two packages, which are listed as dependencies with strict version requirements(see this for yourself on the gcc-3.3 page for yourself):

[http://packages.ubuntu.com/hardy/gcc-3.3-base](http://packages.ubuntu.com/hardy/gcc-3.3-base)
[http://packages.ubuntu.com/hardy/cpp-3.3](http://packages.ubuntu.com/hardy/cpp-3.3)

In that order. Then the gcc-3.3 package should install.

You can do this kind of package searching for any package Ubuntu might have or ever had. You just go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and start searching for what you need. Everything is in .deb form so it's just click and install.

---

### Post by sm_here on 2010-01-28
> **Temposs said:**
> When you need an older version of a package, you should try to find if Ubuntu has a legacy package put together for the version you want. That will save you the hassle of compiling gcc(that'll take like an hour or something).

It turns out that in Ubuntu 8.04 Hardy Heron, gcc-3.3 was included. So, I found the page to download it: 

[http://packages.ubuntu.com/hardy/devel/gcc-3.3](http://packages.ubuntu.com/hardy/devel/gcc-3.3)

Before you install that package, you should install the following two packages, which are listed as dependencies with strict version requirements(see this for yourself on the gcc-3.3 page for yourself):

[http://packages.ubuntu.com/hardy/gcc-3.3-base](http://packages.ubuntu.com/hardy/gcc-3.3-base)
[http://packages.ubuntu.com/hardy/cpp-3.3](http://packages.ubuntu.com/hardy/cpp-3.3)

In that order. Then the gcc-3.3 package should install.

You can do this kind of package searching for any package Ubuntu might have or ever had. You just go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and start searching for what you need. Everything is in .deb form so it's just click and install.
Please tell me the steps in installing the above three packages

---

### Post by Temposs on 2010-01-28
To install any of the above packages:

1) Go to the page in your browser
2) Determine if you have a 32-bit Ubuntu or a 64-bit Ubuntu.
3) If you have 32-bit Ubuntu, click i386; if you have 64-bit Ubuntu, cick amd64.
4) Click one of the many mirror links on the "Download Page", depending on where you live.
5) When the download is complete, just open the deb file, and click install.

---

### Post by sm_here on 2010-01-28
Thank you...it's installed now.
Can you please also tell me how do the same from command line?

---

### Post by ICEB3AR on 2010-01-28
as Superuser:
```
apt-cache search <package>
apt-get install <package>
apt-get remove <package>

```
use:```

man apt-get 
man apt-cache 
```
to get more information

---

