---
title: "Unknown Compiz Effect? Please help"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-06
Hi,
in this video [http://www.youtube.com/watch?v=V_XXuEPqErk](http://www.youtube.com/watch?v=V_XXuEPqErk)

at 2:04, there is a desktop effect.

What is it? How do I get it?

Anyone know? Thnx.

---

### Post by skymera on 2009-03-06
Still asking this question a Gp.? :P

I'm not sure what plugin. I've seen it before.

Perhaps It's experimental and not included in the repositories due to stability issues.

I'll hunt around, looks like a great plugin.

List of pllugins:
[http://wiki.compiz-fusion.org/Plugins](http://wiki.compiz-fusion.org/Plugins)

---

### Post by binbash on 2009-03-06
It is at compiz git, i was using it, it's name is like blabla stack plugin.You have to install it from compiz git.

---

### Post by ibuclaw on 2009-03-06
Alternately you can pull the version from the Jaunty Source repository.

```
dget http://archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.7.9+git20090211-0ubuntu6.dsc
```
Then cd into the compiz directory and type in:
```
dpkg-buildpackage -rfakeroot
```
If you get any error messages (most notably xyz is not installed), then install those packages to meet the dependencies of the build-deps.

Once the build has finished, **cd** up a directory and all deb packages are there to install.

NOTE: This is only one step in the process. You will more than likely get dependency problems.
If so, the problem may be solved by get more sources from here: [http://packages.ubuntu.com/search?suite=jaunty&searchon=names&keywords=compiz](http://packages.ubuntu.com/search?suite=jaunty&searchon=names&keywords=compiz)

Regards
Iain

---

### Post by Gp. on 2009-03-06
I'm still confused on exactly what I should be doing from the last two posters (Thanks btw).

Care to explain it in "noob" lol

---

