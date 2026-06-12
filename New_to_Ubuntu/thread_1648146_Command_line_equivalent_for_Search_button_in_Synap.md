---
title: "Command line equivalent for Search button in Synaptic"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by mmasroorali on 2010-12-18
There is a search button at the right side of Synaptic Package Manager. 

[IMG]http://teacher.buet.ac.bd/mmasroorali/spm.png[/IMG]


What will be command line equivalent for this Search button?

Thanks in advance.

---

### Post by amauk on 2010-12-18
```
apt-cache search search_term
```

---

### Post by karthick87 on 2010-12-18
```
aptitude search <package name>
```

---

### Post by mmasroorali on 2010-12-18
> **karthick87 said:**
> ```
aptitude search <package name>
```

Thanks for the reply.

Is there any way to select the searched packages in command line the way we click the check boxes? Or am I asking to too much?

---

### Post by CharlesA on 2010-12-18
Might be able to use aptitude, but I don't know, as I just install stuff with apt-get.

---

### Post by sikander3786 on 2010-12-18
As a side note, aptitude is not installed by default on 10.10 and later. Need to install it yourself.

Software Center is going to replace everything including aptitude, Gdebi and might be apt-get also. Who knows :-)

---

### Post by mmasroorali on 2010-12-18
> **sikander3786 said:**
> As a side note, aptitude is not installed by default on 10.10 and later. Need to install it yourself.

Software Center is going to replace everything including aptitude, Gdebi and might be apt-get also. Who knows :-)

If apt-get is replaced, what will happen to command line version?

---

### Post by Joeb454 on 2010-12-18
I don't think the software center is going to replace apt-get, I have a funny feeling it could be dependent on apt-get. Not 100% sure on that last part though

---

### Post by sikander3786 on 2010-12-18
I also feel like apt-get would be there till the very end. And not sure if Software Center depends on apt-get but I don't think so. I think SC is independent of any other package manager.

Regarding the imporvements in SC:
[http://www.omgubuntu.co.uk/2010/09/ubuntu-software-centre-handles-now-deb-installations-in-maverick/](http://www.omgubuntu.co.uk/2010/09/ubuntu-software-centre-handles-now-deb-installations-in-maverick/)

---

### Post by mmasroorali on 2010-12-18
> **sikander3786 said:**
> I also feel like apt-get would be there till the very end. And not sure if Software Center depends on apt-get but I don't think so. I think SC is independent of any other package manager.

Regarding the imporvements in SC:
[http://www.omgubuntu.co.uk/2010/09/ubuntu-software-centre-handles-now-deb-installations-in-maverick/](http://www.omgubuntu.co.uk/2010/09/ubuntu-software-centre-handles-now-deb-installations-in-maverick/)

Somehow failed to like SC. So, it was not a love at first sight.

---

### Post by nothingspecial on 2010-12-18
You can use the -n option to only search the names with apt-cache, rather than the description as well.

For example
```

$ apt-cache search music | wc -l
507
$ apt-cache search -n music | wc -l
44

```
So if you search for music you get 507 results, but if you search just the package names you get 44.

Narrows things down a little.

---

### Post by oldos2er on 2010-12-18
> **mmasroorali said:**
> Somehow failed to like SC. So, it was not a love at first sight.

I agree. I installed aptitude, removed Software Center.

---

