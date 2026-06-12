---
title: "vb.net linux IDE"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by simple24061986 on 2011-03-23
Hi guys. I am a huge ubuntu fan and suggest it as the first choice to try out linux. I am an engineering student and I know that linux really holds its own when it comes to programming. So it surprised me when I didnt find a software/package for using VB and other .NET languages. 
 
A good free tool is SharpDevelop ( [COLOR=#0e774a][www.icsharpcode.net/opensource/sd/]("http://www.icsharpcode.net/opensource/sd/") [/COLOR]). But then again it works for Windows only. Its not that I havent tried Wine. I just want to include it in the livecd that I have created using Ubuntu 10.04. Any idea on how to do this ? Or will I have to go the windows way ( download/copy and install everytime ) ??
 
I've just been so far as to create and use various components like command buttons , checkboxes , text boxes etc. Could you suggest me a linux equivalent software on which I can do this ? 
 
Thanks in advance to all.
 
Sid

---

### Post by cariboo on 2011-03-24
VB.net is Microsoft only, you could try mono-devel which is similar to and licensed by Microsoft.

---

### Post by directhex on 2011-03-24
> **cariboo907 said:**
> VB.net is Microsoft only,

The VB.NET compiler package is [mono-vbnc](apt:mono-vbnc)

> you could try mono-devel

[mono-devel](apt:mono-devel) is a default build environment for the Mono C# compiler, and pulls in everything needed to build against the core framework. Perhaps you're thinking of the [monodevelop](apt:monodevelop) IDE?

> which is similar to and licensed by Microsoft.

MonoDevelop is not written by Microsoft, therefore has nothing for them to license.

MonoDevelop can be used as an IDE for several languages, both .NET languages and otherwise (it's originally based on SharpDevelop), but the GUI designer is for C# projects only.

---

