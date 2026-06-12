---
title: "ubuntu natively run other binary packages"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by psorincatalin on 2010-09-15
hey there,
as you can see this is my first post on this forum, i'm new to this and linux in general but i'm learning fast.

i had the chance to read alot of stuff on linux (or should i say gnu/linux [IMG]http://kubuntuforums.net/forums/Smileys/classic/tongue.gif[/IMG]),  but i could't find any topic on (i don't know if it even possible)  running other binary packages on ubuntu. i also know that there's a  program called alien that can convert between formats but that's not my  point

like for example installing an .rpm just like you would normally install a .deb on my ubuntu sistem

as  far as i understand open source software can be shared and modified by  everyone so there must be a way of taking the files from opensuse for  example that have to do with reading .rpm's and implement them to ubuntu. now my question is....can that be done by a complete newbie  like me or does it require a techie ?

the reason i'm asking u  this is that i found and extremely light distro of linux that works  flawlessly with my very old pc, tiny core linux and it would be sooooo  sweet if i could make it run and read .deb files (curently it's using  .tcz)

i'm waiting forward for your responses

---

### Post by snowpine on 2010-09-15
Sounds like a question for the Tiny Core Linux forums. :)

I would recommend learning how to compile source code. That is the best way to develop an application that can be installed on any Linux distro. (You've heard the expression "open source"?)

Here is a tutorial to get you started: [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by solar george on 2010-09-15
Unlikely, although the source code can be compiled on any distro the actual binary packages will be linked to specific versions of libraries and expect certain conventions of file system layout which varies between distributions.
Things like alien only work on very simple packages, are not recommended unless you really know what you are doing since a broken package could destroy your entire system.

---

