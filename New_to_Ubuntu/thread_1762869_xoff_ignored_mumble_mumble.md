---
title: "xoff ignored mumble mumble"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by tjhans on 2011-05-19
I have been looking all over to figure this out.  A common noob mistake is to type ^s in nano to save rather than the proper ^o.  however, long after I learned the proper way to save my work, I still have not found where anyone explains what the message you get from that mistake means:

[ XOFF ignored, mumble mumble ]

I would really like to know that that means.

---

### Post by Irihapeti on 2011-05-19
XON and XOFF are flow control signals, used on serial communications (e.g. modems and some printers), so probably not in much use these days. The key commands are Ctrl-Q and Ctrl-S respectively.

More details: [http://whatis.techtarget.com/definition/0,,sid9_gci213406,00.html](http://whatis.techtarget.com/definition/0,,sid9_gci213406,00.html)

As for that message, I take it that one of the nano developers is having a little joke.

---

