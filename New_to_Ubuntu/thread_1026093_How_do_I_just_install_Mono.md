---
title: "How do I just install Mono?"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by HyperHacker on 2008-12-30
> $ ./CTF\ Manager\ v2.0.exe
install the Windows version of Mono to run .NET executables
$ sudo apt-get install mono
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mono is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mono has no installation candidateGoogle gives me all sorts of information on how to install Mono devkits and write programs using Mono... but nobody seems to be able to tell me how to just plain install Mono itself to run a .Net program. I don't want to *make* .Net programs, I just want to run one!

---

### Post by directhex on 2008-12-31
> **HyperHacker said:**
> Google gives me all sorts of information on how to install Mono devkits and write programs using Mono... but nobody seems to be able to tell me how to just plain install Mono itself to run a .Net program. I don't want to *make* .Net programs, I just want to run one!

Mono is made from many parts - compilers, libraries, etc. There's no one package to install everything.

Assuming your CTF Manager is the same one I found on Google, let's take a little look at it, and how to run it.

First, you need the mono-runtime package. This package contains the "mono" command. Next, let's look at which libraries the app need:

```
directhex@mortos:/tmp$ monodis --assemblyref CTF\ Manager.exe 
AssemblyRef Table
1: Version=2.0.0.0
	Name=mscorlib
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
2: Version=8.0.0.0
	Name=Microsoft.VisualBasic
	Flags=0x00000000
	Public Key:
0x00000000: B0 3F 5F 7F 11 D5 0A 3A 
3: Version=2.0.0.0
	Name=System.Windows.Forms
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
4: Version=2.0.0.0
	Name=System
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
5: Version=2.0.0.0
	Name=System.Drawing
	Flags=0x00000000
	Public Key:
0x00000000: B0 3F 5F 7F 11 D5 0A 3A 
```

That's five libraries: mscorlib, Microsoft.VisualBasic, System.Windows.Forms, System, and System.Drawing.

They're contained in the following packages:
libmono-corlib2.0-cil
libmono-microsoft-visualbasic8.0-cil
libmono-winforms2.0-cil
libmono-system2.0-cil
libmono-system2.0-cil

So with all of those, it works, right?
```
directhex@mortos:/tmp$ mono CTF\ Manager.exe 

Unhandled Exception: System.UnauthorizedAccessException: Access to the path "/tmp\DATA" is denied.
```

Apparently, no, it's been programmed by idiots. CLI is designed to deal with cross-platform concerns, but this app's programmers have ignored those abilities (i.e. they've used something like 'tmpdir + "\DATA"' instead of the correct 'System.IO.Path.Combine( tmpdir, "DATA" )'). There's a workaround for this kind of stupid:

```
directhex@mortos:/tmp$ MONO_IOMAP=all mono CTF\ Manager.exe
```

Except, in this instance, it doesn't work either:

```
directhex@mortos:/tmp$ MONO_IOMAP=all mono CTF\ Manager.exe 

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
```

HOWEVER, I did the above using the latest (version 5) of the tool. I tracked down version 2, and..... see attached.

Oh, one little note: libmono-microsoft-visualbasic8.0-cil is only available in Jaunty, but the package ought to work on Intrepid.

---

### Post by HyperHacker on 2009-02-08
[nevermind]

---

### Post by Sir_Sid on 2009-02-16
> **directhex said:**
> Mono is made from many parts - compilers, libraries, etc. There's no one package to install everything.

Assuming your CTF Manager is the same one I found on Google, let's take a little look at it, and how to run it.

First, you need the mono-runtime package. This package contains the "mono" command. Next, let's look at which libraries the app need:

```
directhex@mortos:/tmp$ monodis --assemblyref CTF\ Manager.exe 
AssemblyRef Table
1: Version=2.0.0.0
	Name=mscorlib
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
2: Version=8.0.0.0
	Name=Microsoft.VisualBasic
	Flags=0x00000000
	Public Key:
0x00000000: B0 3F 5F 7F 11 D5 0A 3A 
3: Version=2.0.0.0
	Name=System.Windows.Forms
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
4: Version=2.0.0.0
	Name=System
	Flags=0x00000000
	Public Key:
0x00000000: B7 7A 5C 56 19 34 E0 89 
5: Version=2.0.0.0
	Name=System.Drawing
	Flags=0x00000000
	Public Key:
0x00000000: B0 3F 5F 7F 11 D5 0A 3A 
```

That's five libraries: mscorlib, Microsoft.VisualBasic, System.Windows.Forms, System, and System.Drawing.

They're contained in the following packages:
libmono-corlib2.0-cil
libmono-microsoft-visualbasic8.0-cil
libmono-winforms2.0-cil
libmono-system2.0-cil
libmono-system2.0-cil

So with all of those, it works, right?
```
directhex@mortos:/tmp$ mono CTF\ Manager.exe 

Unhandled Exception: System.UnauthorizedAccessException: Access to the path "/tmp\DATA" is denied.
```

Apparently, no, it's been programmed by idiots. CLI is designed to deal with cross-platform concerns, but this app's programmers have ignored those abilities (i.e. they've used something like 'tmpdir + "\DATA"' instead of the correct 'System.IO.Path.Combine( tmpdir, "DATA" )'). There's a workaround for this kind of stupid:

```
directhex@mortos:/tmp$ MONO_IOMAP=all mono CTF\ Manager.exe
```

Except, in this instance, it doesn't work either:

```
directhex@mortos:/tmp$ MONO_IOMAP=all mono CTF\ Manager.exe 

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
```

HOWEVER, I did the above using the latest (version 5) of the tool. I tracked down version 2, and..... see attached.

Oh, one little note: libmono-microsoft-visualbasic8.0-cil is only available in Jaunty, but the package ought to work on Intrepid.

Thanks hex, but how did you know which packages to get out of that output?

---

### Post by directhex on 2009-02-17
> **Sir_Sid said:**
> Thanks hex, but how did you know which packages to get out of that output?

Generally, use apt-file. If you're told you're missing System.Foo, do an apt-file search System.Foo.dll

Except in my case where I have this stuff memorised :|

---

### Post by cj2003 on 2009-02-17
Don't know if it helps, but there are some [unofficial packages for Intrepid]("http://www.ubuntu-news.net/2008/10/16/mono-20-packages-for-ubuntu-intrepid/")

---

### Post by directhex on 2009-02-17
> **cj2003 said:**
> Don't know if it helps, but there are some [unofficial packages for Intrepid]("http://www.ubuntu-news.net/2008/10/16/mono-20-packages-for-ubuntu-intrepid/")

And don't expect any help when (yes, when) they cause problems for you

---

### Post by Sir_Sid on 2009-02-17
haha thanks

---

