---
title: "Is kernel.org up"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by alegomaster on 2011-09-05
Hi. Does anybody know if the newest kernel tree for linus is up on kernel.org yet, or is it on github still? If it is still on github, then what version of linux is on kernel.org right now?

Mods: You can move this thread if you dont find this place suitable. I had no clue where to put it. And I am getting into kernel development so I have almost no clue yet about the kernel trees yet so I find this place suitable.

On a side note, where do you find the latest development tree for linux.

---

### Post by andrewthomas on 2011-09-05
Don't really understand.

Always been @ kernel.org as far as I know.


[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=summary)

---

### Post by _d_ on 2011-09-05
3.0.4 is the latest stable kernel, with 3.1-rc4 mainline and 3.1-rc4-git2 as snapshot:

[http://www.kernel.org/](http://www.kernel.org/)

---

### Post by alegomaster on 2011-09-05
> **andrewthomas said:**
> Don't really understand.

Always been @ kernel.org as far as I know.


[http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=summary)

Kernel.org was hacked recently and Linus decided to use github till they got kernel.org working again

_d_ : The latest kernel version is 3.1-rc5 

Here is the email from linus:

```


So it's been another week, and it's time for another -rc.

However, [master.kernel.org]("http://master.kernel.org/") is still down, and there really hasn't been
a ton of development going on, so I considered just skipping a week.
But hey, the whole point (well, *one* of the points) of distributed
development is that no single place is really any different from any
other, so since I did a github account for my divelog thing, why not
see how well it holds up to me just putting my whole kernel repo there
too?

So while [kernel.org]("http://kernel.org/") is down for the count, let's just see how github does:

   [https://github.com/torvalds/linux.git](https://github.com/torvalds/linux.git)

NOTE! One thing to look out for when you see a new random public
hosting place usage like that is to verify that yes, it's really the
person you think it is. So is it?

You can take a few different approaches:

 (a) Heck, it's open source, I don't care who I pull from, I just want
a new kernel, and not having a new update from [kernel.org]("http://kernel.org/") in the last
few days, I *really* need my new kernel fix. I'll take it, because I
need to exercise my CPU's by building randconfig kernels. Besides, I
like living dangerously.

 (b) Yeah, the email looks like it comes from Linus, and we all know
that SMTP cannot possibly be spoofed, so it must be him.

 (c) Ok, I can fetch that tree, and I know that Linus always does
signed tags, and I can verify the 3.1-rc5 tag with Linus known public
GPG key that I have somewhere. If it matches, I don't care who the
person doing the release announcement is, I'll trust that Linus signed
the tree

 (d) I'll just wait for [kernel.org]("http://kernel.org/") to feel better.

Whatever works for you.

One thing to note: If you just do

  git pull [https://github.com/torvalds/linux.git](https://github.com/torvalds/linux.git)

you probably won't get the tags, since it's not your origin branch. So do

  git fetch --tags <...>

too, so that you get not only the actual changes, but the tag that you
can verify too.

And I *would* suggest you just pull into an existing tree, rather than
clone a new copy. I bet the github people will appreciate that.

Anything worth saying about the changes themselves? The appended
shortlog pretty much speaks for itself: there really hasn't been much
excitement on the kernel development front.

Now, if you want to talk to me about dive logging software, that's a
whole different kettle of fish..

                   Linus


```

---

