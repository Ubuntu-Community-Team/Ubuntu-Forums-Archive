---
title: "Bash-completion not working as expected for directories"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by Fabdog on 2009-01-29
Hi Forum,

I have a problem with the bash-completion for directories.
I am running Ubuntu 8.10, bash 3.2.39 and bash_completion 1.872

When I tab-expand a cd command I do not get the trailing slash
e.g.
cd Down
<Tab>
-> cd Downloads 
I would expect -> cd Downloads/

The same holds for environment variables
cd $HOM
<Tab>
-> cd $HOME
instead of $HOME/

Furthermore, I have a directroy with a space in the name, the Tab Completion doesn't work.
Directory A B is expended not like "A\ B", but "A B".

Does anyone have an idea how to solve these problem? Is this a known issue? I found some similar links, but not the exact problem. Does anyone have a suggestions how I should edit my bash_completion or what I should do?

Cheers,
Fabdog

---

### Post by anoxi on 2011-04-16
found one solution here [http://ubuntuforums.org/showpost.php?p=10636255&postcount=6](http://ubuntuforums.org/showpost.php?p=10636255&postcount=6)

---

### Post by TeoBigusGeekus on 2011-04-16
This isn't a problem at all
```
cd Desktop
```
is the same as
```
cd Desktop/
```
and 
```
cd A\ B
```
is the same as
```
cd "A B"
```

---

### Post by hmonteiro on 2011-11-14
That IS a problem.

Of course
```
cd Desktop
```

is the same as
```
cd Desktop/

```

But the problem only appears when you want to go deeper in the directory some more levels.
If you issue ```
cd Desk<tab>
```, it will do ```
"cd Desktop "
``` (notice the extra space). Now try to append something more to that path. It won't work.
The decision of using completion that way was just wrong.

anoxi's solution solves it.

---

### Post by hmonteiro on 2011-11-14
Actually the problem lies elsewhere.

See

[http://forums.adobe.com/thread/745833](http://forums.adobe.com/thread/745833)

and

[https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/716008](https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/716008)

Just remove /etc/bash_completion.d/acroread.sh and it'll all be fine. Although it's a temporary solution, it's the least intrusive i've seen so far.

Cheers.

---

### Post by Normalex on 2012-03-04
Confirmed, that was acroread, i.e. from Adobbe's site
adobrereader-enu:i386, v 9.4.7

---

