---
title: "Where to put alias for Conky to see it?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by TideMan on 2009-03-23
I have this alias in my .bashrc file:
```
alias GetNextPerigee="/home/derek/MyProjects/GetNextPerigee/GetNextPerigee"
```

so when I go to a terminal and type GetNextPerigee, it works.

But, when I do this in Conky:
```
${execi 86400 GetNextPerigee}
```
it says it can't find GetNextPerigee, but if I do this:
```
${execi 86400 /home/derek/MyProjects/GetNextPerigee/GetNextPerigee}
```
it works.

Obviously, my personal .bashrc is not the right place for the alias.  It needs to go somewhere higher in hierarchy.
But where?

---

### Post by chuckyp on 2009-03-23
It needs to be in your path. Try typing :
```

echo $PATH

```

To see what directories are in your path. Most people will throw home-made scripts in /usr/local/sbin

Keep in mind that this will be accessible system wide once you put it there though. If you need it specific to just your user you need to adjust your path or the permissions.

---

### Post by TideMan on 2009-03-24
> Most people will throw home-made scripts in /usr/local/sbin

Yes, thank you, this has fixed my problem.

PS I would mark this as solved, but I can't figure out where to do that anymore......

---

