---
title: "Return to bash without closing program when waiting for output"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by afable on 2011-01-29
Hi, 

I'm new to the forums and new to linux and using the terminal.

I've tried googling this and have done a search on 'terminal' in these forums but I can't find an answer when I specifically phrase my question.

So... Is there a way to return to bash without closing a running program when waiting for output? I mean if I didn't run the program with & and I want to leave it running and return to bash (not hitting ^c).

Thanksl
afable

---

### Post by [Snc] on 2011-01-29
> **afable said:**
> Hi, 

I'm new to the forums and new to linux and using the terminal.

I've tried googling this and have done a search on 'terminal' in these forums but I can't find an answer when I specifically phrase my question.

So... Is there a way to return to bash without closing a running program when waiting for output? I mean if I didn't run the program with & and I want to leave it running and return to bash (not hitting ^c).

Thanksl
afable

You can always have multiple terminals running, if you start the program from the terminal, it is going to output information and if you hit Ctrl+c, it will terminate the program and return to shell (as the command is "break")

---

### Post by gmargo on 2011-01-29
> **afable said:**
> So... Is there a way to return to bash without closing a running program when waiting for output? I mean if I didn't run the program with & and I want to leave it running and return to bash (not hitting ^c).


Yes, you can hit a Control-Z, which should stop the program (without killing - it is just suspended), and return control to you at the command line.  If you then type "bg" (for background), the suspended job will resume in the background, as though you had originally typed an ampersand (&).  You can also type "jobs" or "jobs -l" to list all the programs running in the background.

Here is some information on Job Control:
[http://mywiki.wooledge.org/BashGuide/JobControl](http://mywiki.wooledge.org/BashGuide/JobControl)
[http://www.faqs.org/docs/bashman/bashref_77.html](http://www.faqs.org/docs/bashman/bashref_77.html)

---

### Post by afable on 2011-01-29
Thank you both for replying.

gmargo, that was specifically what I was looking for. I knew of the fg (foreground) command but I didn't know that I could do bg as well. Thanks again!

-afable

---

