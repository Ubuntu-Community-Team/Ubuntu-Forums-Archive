---
title: "Apt-get clarification please"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by executorvs on 2009-07-09
so as of late I've been using the command line a lot more to build MYbuntu from minimal install. well last night, in the midst of reOSing a toshiba satellite 1905-s301, I noticed apt-get using a markup of some sort that I haven't been able to identify.

so what does it mean when you say:
apt-get install  googleearth*

as opposed to

apt-get install googleearth

the closest I could find was 

dpkg -l *packagename*

sorry if this seems stupid, I just don't like not knowing what is being said on my screen during un/installs

---

### Post by CatKiller on 2009-07-09
It's a [regular expression]("http://en.wikipedia.org/wiki/Regular_expression") (regexp)

From man **apt-get**:
> 
           If no package matches the given expression and the expression
           contains one of ´.´, ´?´ or ´*´ then it is assumed to be a POSIX
           regular expression, and it is applied to all package names in the
           database. Any matches are then installed (or removed). Note that
           matching is done by substring so ´lo.*´ matches ´how-lo´ and
           ´lowest´. If this is undesired, anchor the regular expression with
           a ´^´ or ´$´ character, or create a more specific regular
           expression.

---

### Post by executorvs on 2009-07-09
thank you, I suddenly feel dumb for not thinking about the manpages.

---

