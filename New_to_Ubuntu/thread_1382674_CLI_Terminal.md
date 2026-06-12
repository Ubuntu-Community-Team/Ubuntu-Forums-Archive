---
title: "CLI Terminal"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by luckdezzy on 2010-01-16
I'm a real novice to the Linux CLI commands so my ? is a very simple one is their a difference between sh or  bash terminal or is it just a matter of what u are comfortable with?

---

### Post by mcduck on 2010-01-16
Yes, there is a difference. Bash has more features than the original Sh does. Ubuntu doesn't actually have Sh, /bin/sh links to Dash which is a new shell compatible with Sh but with better performance.

Ubuntu uses Bash as the default shell for users, and Dash as the system shell. So when you log into CLI you use Bash by default, but /bin/sh is actually linked to /bin/dash.

Different shells have different features, and sometimes even completely different syntax. If you write shell scripts you shuld either keep them compatible with Sh and not use any shell-specific features (like stuff that works in Bash but not in sh), or specify the shell that should be used in the beginning of your script.

Being new to shells you should probably stick to Bash, at least until you get more comfortable working with CLI. Most of the guides and tutorials you find in the web and in the forums use Bash as the shell.

---

### Post by daschel on 2010-01-16
Bash has more features, and I've found it to be more comfortable.

On the other hand, the Bourne shell (and dash and busybox) can run in computers with less memory or cpu.

The bash reference manual has more details about the differences.
[http://www.faqs.org/docs/bashman/bashref_122.html](http://www.faqs.org/docs/bashman/bashref_122.html)

---

### Post by Captain_tux on 2010-01-16
Bash is also the default shell on many Linux distros today...

---

### Post by audiomick on 2010-01-16
There is a wikipedia article here
[http://en.wikipedia.org/wiki/Shell_%28computing%29](http://en.wikipedia.org/wiki/Shell_%28computing%29)
that goes into it a bit, and has links to various shells.

---

### Post by Tnoty on 2010-01-16
This also a good article about CLI commands. 
[https://help](https://help).**ubuntu**.com/community/UsingThe**Terminal**
I[I]m new to CLI commands also and this article help a little.  Hope it can help you also.

Tnoty
[/I]

---

