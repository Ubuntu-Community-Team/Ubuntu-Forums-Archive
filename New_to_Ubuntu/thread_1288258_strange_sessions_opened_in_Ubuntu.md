---
title: "strange sessions opened in Ubuntu"
date: 2009-10-11
forum: New to Ubuntu
---

### Post by am65 on 2009-10-11
Hello, the other day when I was to shut down my Ubuntu it showed me a message that if shutted down Ubuntu I would finish also with other sessions that were being executed.

This was a bit upsetting to me becuase I'm the only user of Ubuntu, and while I was connected to the Internet I guessed if some hacker got into my system (I'm a bit paranoid).

I have never get that message again. Is it something I should care about?

Thanks

---

### Post by scorp123 on 2009-10-11
Maybe you had a terminal open somewhere or a program was hanging? Technically this would then count as "another session".

To reproduce:
- Login to GNOME or KDE (or whatever you have)
- Open a terminal
- Press Ctrl+Alt+F2 so you'd switch to your text console #2; login again
- Press Ctrl+Alt+F7 and go back into your GUI

And now into the open terminal type:
```
w
```
... and hit the "Enter" key.

You should see yourself logged in at least three times. Once on ":0", ":0.0" and "tty2"

If you now try to logout you might get the error message again. It's also a possibility that you had a "sudo" session that was still running somewhere... That too would count as "another user" and cause the error message.

---

### Post by tpjk on 2009-10-11
hey there
i don't think you should be too stressed out about what happened, esp since that prompt only came up once. unless you have enemies that you know are into hacking ;) there's no need to believe that someone got into your system somehow just because you were browsing the internet.

check out the following article if you like, it should give you some peace of mind:
[http://bigbolshevik.blog.friendster.com/2008/07/how-do-you-get-down-off-an-elephant/](http://bigbolshevik.blog.friendster.com/2008/07/how-do-you-get-down-off-an-elephant/)

cheers!

---

### Post by am65 on 2009-10-17
I could not reproduce the message of the "other sessions opened" but at that time I was installing software, the printer, etc... I think I will stop worrying about it. Anyway it has never happened again.

Many thanks

---

