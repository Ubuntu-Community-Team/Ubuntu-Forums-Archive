---
title: "monodevelop 2.0 mcs.exe"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by cwmoser on 2009-05-02
Running Monodevelop 2.0 on Ubuntu 9.04 64 bit version.

Where is mcs.exe?

When I compile I get this error:
Cannot open assembly '/usr/lib/mono/1.0/mcs.exe': No such file or directory.


Any help appreciated.

Carl

---

### Post by cwmoser on 2009-05-02
I found mcs.exe -- its in mono-mcs package.

Now I get no errors when I build, but now I get:
** (c5:6928): WARNING **: Missing method .ctor in assembly /usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll, type System.Runtime.CompilerServices.RuntimeCompatibilityAttribute

** (c5:6928): WARNING **: The class System.Runtime.CompilerServices.RuntimeCompatibilityAttribute could not be loaded, used in gtk-sharp

Any ideas?

Thanks

Carl

---

### Post by Didius Falco on 2009-05-02
I can't help with  the mcs.exe question, but I did see a link to an apt get for it right on the Monodevelop site.

I also found this web page:

[http://streebgreebling.blogspot.com/2009/04/ubuntu-904-installation.html](http://streebgreebling.blogspot.com/2009/04/ubuntu-904-installation.html)

 > One big improvement from my point of view is that MonoDevelop version 2.0 is now supported, which provides an integrated debugger. However, just selecting MonoDevelop from Add/Remove is not enough to get all the functionality. Go to System/Administration/Synaptic and search for all packages related to *Nunit* and *monodevelop-debugger*, select them, then apply. On running the IDE a new toolbar button appears called "Debug", which can be used to interactively debug after setting some breakpoints.

I hope this helps...

---

### Post by directhex on 2009-05-03
All libraries on Jaunty have been moved to support CLI 2.0 only, including GTK#.

You cannot compile GTK# apps with mcs anymore. Use gmcs - switch your project to target CLI 2.0 in Project Options/Build/General

---

### Post by cwmoser on 2009-05-03
I went to Project -> Options -> Build -> General
Changed Runtime version to:  Mono / .NET 2.0

and now I get an executable that works -- [COLOR="DarkRed"]thanks much Direct-Hex[/COLOR]:)

My executable works and I get no errors -- just this warning:

**Reference 'pango-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' not found on system. Using 'pango-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f instead.]**

What does this mean?  Not sure what "pango-sharp" is all about.

Thanks

Carl

---

### Post by directhex on 2009-05-03
> **cwmoser said:**
> I went to Project -> Options -> Build -> General
Changed Runtime version to:  Mono / .NET 2.0

and now I get an executable that works -- [COLOR="DarkRed"]thanks much Direct-Hex[/COLOR]:)

My executable works and I get no errors -- just this warning:

**Reference 'pango-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' not found on system. Using 'pango-sharp, Version=2.12.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f instead.]**

What does this mean?  Not sure what "pango-sharp" is all about.

Thanks

Carl

Pango is a font rendering engine. It's used in GTK+. The message means that your app is compiled against Pango-sharp 2.10, but is being executed by Pango-sharp 2.12 (which is the version included in Jaunty) as there is a policy file redirecting 2.10 requests to 2.12. If you're curious, take a peek in /usr/lib/mono/gtk-sharp-2.0/

---

### Post by cwmoser on 2009-05-03
DirectHex, thanks for the great help with MonoDevelop.
I can tell by your response to my questions this time and those in the past that you have quite extensive knowledge of MonDevelop.

Thanks again.

Carl

---

