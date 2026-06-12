---
title: "Installing 32bit applications on 64bit installation"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by bpowell2005 on 2009-01-31
Hi All,

I'm not having much luck with researching this, and could use some help. I recently got a laptop with a 64bit processor; so I went crazy and installed the 64bit version of Jaunty. 

However, there are a few applications I'd like to install that I can only find in 32bit version.

It seems like I sometimes read about folks installing and running 32bit applications on their 64bit Ubuntu installation...how is this done? Every time I try, the installer fails with a "Wrong architecture" failure.

Any ideas?

Thanks!

---

### Post by oldos2er on 2009-01-31
> **bpowell2005 said:**
>  there are a few applications I'd like to install that I can only find in 32bit version.
  

 Which ones?

 To install a 32-bit *.deb file on 64-bit Ubuntu, use the command
```
sudo dpkg -i --force-architecture filename.deb
```

---

### Post by bpowell2005 on 2009-01-31
> **oldos2er said:**
> Which ones?

 To install a 32-bit *.deb file on 64-bit Ubuntu, use the command
```
sudo dpkg -i --force-architecture filename.deb
```

oldos2er: Thanks for the command line tip! I intentionally didn't specify which programs because people would no doubt be helpful, and tell me how to install those specific programs, but I was looking for a more general command exactly like what you have posted.

FWIW: I'm trying to install AngryIP Scanner....There is a Java version that works okay, but I was just trying to get the .deb to install...using the command you provided, it installed, but will not run. I'll have to keep poking around.

Thank you very much for the help though! I'm looking for the "Thanks" button, but can't find it...what happened there?

---

### Post by Muffinabus on 2009-01-31
> **bpowell2005 said:**
> oldos2er: Thanks for the command line tip! I intentionally didn't specify which programs because people would no doubt be helpful, and tell me how to install those specific programs, but I was looking for a more general command exactly like what you have posted.

FWIW: I'm trying to install AngryIP Scanner....There is a Java version that works okay, but I was just trying to get the .deb to install...using the command you provided, it installed, but will not run. I'll have to keep poking around.

Thank you very much for the help though! I'm looking for the "Thanks" button, but can't find it...what happened there?

The thanks and thread solved functions are disabled right now.

---

### Post by bpowell2005 on 2009-01-31
> **Muffinabus said:**
> The thanks and thread solved functions are disabled right now.

I thought I was going crazy there for a moment! I've been looking for the "Mark as solved" option for 5 minutes!

Thanks for the update.

Oh well, this one is solved, and thanks to all for the help!

---

