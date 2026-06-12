---
title: "how often is ''apt-get update' needed?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by egalvan on 2009-01-29
I haven't found any postings or info on the following...

how often is the following needed, or recommended?

either in a terminal

```
sudo apt-get update
```


or in Synaptics

"Reload"

.

I tend to reload every time I fire up Synaptic.. 
and I run 'apt-get update' every time I use apt-get

Is this needed so often?

---

### Post by OutOfReach on 2009-01-29
Update Manager should take care of updating every so often (I forgot the default setting, I don't use Ubuntu), I think that it is daily.
So you don't even need to execute that command, Update Manager should take care of that for you.

---

### Post by damis648 on 2009-01-29
I believe Ubuntu does this automatically every day or every two days. I never reload manually unless I modify my repos.

EDIT: Dang! Beat to it!

---

### Post by HittingSmoke on 2009-01-29
> **egalvan said:**
> I haven't found any postings or info on the following...

how often is the following needed, or recommended?

either in a terminal

```
sudo apt-get update
```


or in Synaptics

"Reload"

.

I tend to reload every time I fire up Synaptic.. 
and I run 'apt-get update' every time I use apt-get

Is this needed so often?

You only need to do this when you add or change repositories. If you update them via Synaptic, you will be prompted to reload. If you add repos via gedit or another txt editor you have to run apt-get update before installing any software from that repo.

---

