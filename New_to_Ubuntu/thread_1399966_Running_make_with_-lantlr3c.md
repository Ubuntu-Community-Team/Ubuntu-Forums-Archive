---
title: "Running make with -lantlr3c"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Ram- on 2010-02-06
Hello,

I building a project which uses AnTLR for grammar and parsing. I am running make for the AnTLR files with -lantlr3c option. It doesn't work because I don't have libantlr3c-dev installed. But libantlr3c-dev does not exit.. and I suppose libantlr-dev is different... I need to use AnTLR for C and not for Java.

Any suggestions?

Thanks in advance.

---

### Post by Bachstelze on 2010-02-06
[font=monospace]libantir-dev[/font] is what you want.

*EDIT: sorry, misread your post. This library apparently doesn't exist in the Ubuntu repositories. You will probably need to build it from source.*

---

