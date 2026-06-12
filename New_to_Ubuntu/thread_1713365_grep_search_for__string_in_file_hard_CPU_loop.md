---
title: "grep search for  string in file hard CPU loop"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by wrtell on 2011-03-24
Hi,

I am trying to find all instances  of the string "update-manager" in the Ubuntu Server 10.10 file ssytem

I have tried various grep command

The result of issuing 


grep -irsI "update-manager" /


is one line of output

/etc/update-motd.d/91-release-upgrade:exec /usr/lib/update-manager/release-upgrade-motd


Grep is in a hard CPU loop consuming 40% of the VBOX VM I run Ubuntu in. . Theer is no file activity based on both system monitor and VBOX tools and noting else happens.

I would appreciate any help .

Thanks

William

---

### Post by Paddy Landau on 2011-03-24
There are a couple of possibilities.

Try adding sudo and -F:
```
sudo grep -irsIF 'update-manager' /
```The problem is if you have a large filesystem mounted, grep might be going down that route. If you do not wish to search the home partition, try this modification:
```
sudo grep -irsIF --exclude='/home' 'update-manager' /
```Let us know what happens.

---

### Post by gmargo on 2011-03-24
I would recommend using **find(1)** to traverse the filesystem, instead of **grep(1)**, since find has the "-xdev" option to avoid descending into different filesystems.  This will keep you out of naughty places like **/proc** and **/sys**.

```

$ find / -xdev -type f -print0 | xargs -0 grep -isInH "update-manager"

```You'll have to run one for each mount point you're interested in (like /home).

---

### Post by wrtell on 2011-03-24
Hi,

I wish to thank you for the quick replies.

I tried both approaches.

sudo grep -irsIF 'update-manager' /

results in the same hard CPU loop


find / -xdev -type f -print0 | xargs -0 grep -isInH "update-manager"


does not produce  the loop. it  results in quite a few lines of output. Lots of chrome cache hits ( from my internet searches), various hits in python scripts and so on and so forth. So for now I consider this issue solved.

Once again . I wish to thank both of you for taking the time to replay to me

Regards


William

---

### Post by Paddy Landau on 2011-03-25
@gmargo: +1 for the *find* solution.

I think *grep* goes into that intensive CPU usage because it's going down the path of one or more virtual filesystems. *find* with *-xdev* solves that problem.

---

### Post by wrtell on 2011-03-25
Once again Thanks for the info. I will examine the -xdev parameter.

William

---

