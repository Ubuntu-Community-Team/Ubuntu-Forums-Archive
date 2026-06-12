---
title: "Black screen after hibernating with s2disk - solved with Alt+Sysrq+i"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Anatoliy Kim on 2011-02-24
Hello,

I am a new user for Ubuntu and just started using it few weeks ago.

Today I finally got to fix the suspend/hibernate issues on my Lenovo T500 laptop.

In short, I set itpm=1 following some guide out there, installed uswsusp and made it default program.

Suspend works fine - both itself and resuming from suspend.

Hibernate though resumes to black screen and reacts to nothing.

However, I was trying to do the RSEINUB combination with Alt+Sysrq buttons pressed and after I press "i" key my laptop beeps and ... resumes correctly...

I've looked up what "i" key stands for in here: [http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub) and it says that it sends SIGKILL all processes except init.

As far as I can tell it resumes correctly - all the programs are there and etc. I am unsure currently - is this a correct way to deal with this problem of black screen? Will it have any negative consequences like I dunno burning some hardware or smth?

I am wondering whether to continue looking for some solution to fix it without this magic combination or to leave it like that.

---

