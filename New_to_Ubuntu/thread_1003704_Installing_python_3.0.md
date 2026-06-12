---
title: "Installing python 3.0?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by jmauster on 2008-12-06
Hi, I am sure I'm just missing something simple, but....

Do do I upgrade to python 3.0? I'm running 8.10, if that helps. I got the python3 package from synaptic and it appeared to install correctly. However, it looks like python 2.5.2 is still running. 

```
evan@evan-laptop:~$ python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.

```

Also- will I need to get a newer version of idle?

Thanks!

---

### Post by lovelyvik293 on 2008-12-06
You can install python 3.0 from the synaptic.

---

### Post by jmauster on 2008-12-06
I've installed python3.0 from synaptic

However I still get that response on the command line (running 2.5.2 or whatever)

Is there a problem in that?  Shouldn't it say 3.0?

---

### Post by lovelyvik293 on 2008-12-06
Yes it's same 2.5.2;)

---

### Post by snova on 2008-12-06
The default Python interpreter is 2.5, and I suggest you do not change it.

Run 'python3.0' instead of 'python', and use '#!/usr/bin/python3.0' in your scripts (or equivalent /usr/bin/env).

---

### Post by jmauster on 2008-12-06
Thanks for your helpful post. It's cool that I'll be able to play around with the features of 3.0 without getting stuck with it. 

I have just one more question - do you think I should try to use 2.6? From what I've read, in the future, it will be easier to go to 3.x from 2.6

---

### Post by snova on 2008-12-06
> The major theme of Python 2.6 is preparing the migration path to Python 3.0, a major redesign of the language. Whenever possible, Python 2.6 incorporates new features and syntax from 3.0 while remaining compatible with existing code by not removing older features or syntax. When it&#8217;s not possible to do that, Python 2.6 tries to do what it can, adding compatibility functions in a future_builtins module and a -3 switch to warn about usages that will become unsupported in 3.0.

If you like. Unfortunately it isn't in the repos, so you'll have to compile it yourself, but that isn't hard.

I don't think it's that hard to port, although I haven't tried it with anything very large... There is a tool to automate some of it, but it won't be perfect.

---

