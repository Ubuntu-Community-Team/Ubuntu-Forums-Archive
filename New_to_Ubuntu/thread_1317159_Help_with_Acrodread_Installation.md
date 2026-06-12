---
title: "Help with Acrodread Installation"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by leonidg on 2009-11-06
Hey Guys

So I run the acroread installation command and I get this error, any suggestion.

Thanks,
Lenny 


[I]leonid@leonid-laptop:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  acroread: Depends: libldap2 but it is not installable
            Depends: libstdc++5 but it is not installable
E: Broken packages[/I]

---

### Post by rustutzman on 2009-11-06
Go to [http://get.adobe.com/reader/otherversions/](http://get.adobe.com/reader/otherversions/) and grab the linux x86 deb and install that.

Russ

---

### Post by XCan on 2009-11-06
Which version of Ubuntu are you using? If you're using >= Jaunty, have you enabled the partner repos in "Software Sources"?

---

### Post by treesurf on 2009-11-14
> **XCan said:**
> Which version of Ubuntu are you using? If you're using >= Jaunty, have you enabled the partner repos in "Software Sources"?


Thanks, that did the trick for me!

---

