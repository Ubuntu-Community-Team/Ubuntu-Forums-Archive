---
title: "Microsoft .NET framework with Ubuntu 8.10 - Wine"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by mmitt on 2009-02-03
I realize this is a relatively stupid question, but is it possible. I really want Paint.NET on my Ubuntu laptop, but I can't figure out how to without having M$ .NET Framework 3.5, which I don't think is compatable with Wine. Ideas anyone? Thanks.

---

### Post by emarkd on 2009-02-03
Instead of trying to get .net to run under wine, try using mono.  Here's a tutorial the search turned up:
[URL="http://ubuntuforums.org/showthread.php?t=712864"]
http://ubuntuforums.org/showthread.php?t=712864[/URL]

---

### Post by directhex on 2009-02-04
[http://code.google.com/p/paint-mono/](http://code.google.com/p/paint-mono/)

---

### Post by mmitt on 2009-02-04
> **directhex said:**
> [http://code.google.com/p/paint-mono/](http://code.google.com/p/paint-mono/)
Thanks for the advice guys, but how can I install it?

---

### Post by hyper_ch on 2009-02-04
or if mono does not work, try virtualization with vmware or vbox

---

### Post by mmitt on 2009-02-04
> **hyper_ch said:**
> or if mono does not work, try virtualization with vmware or vbox
Ah! That sounds more on my level than source codes. How would I go about this?

---

### Post by directhex on 2009-02-04
paint-mono works, more or less, on Intrepid's Mono. It's not, however, yet of a sufficient quality to package (e.g. it won't quit properly when you try to quit it, so be sure to run it from a console & ctrl-c as needed)

---

### Post by mmitt on 2009-02-04
> **directhex said:**
> paint-mono works, more or less, on Intrepid's Mono. It's not, however, yet of a sufficient quality to package (e.g. it won't quit properly when you try to quit it, so be sure to run it from a console & ctrl-c as needed)
What? I have no clue how to run anything from console. Or quit. But when I have the mono file on my desktop, how can I install it? That is my real problem now.

---

### Post by hyper_ch on 2009-02-04
install vmware or virtualbox and then install a virtual windows there... you then have a fully running virtual windows inside your ubuntu.

---

### Post by directhex on 2009-02-04
> **hyper_ch said:**
> install vmware or virtualbox and then install a virtual windows there... you then have a fully running virtual windows inside your ubuntu.

As long as he pays for a full retail Windows license too, right?

---

### Post by hyper_ch on 2009-02-04
how do you know he hasn't got one already?

---

### Post by directhex on 2009-02-04
> **mmitt said:**
> What? I have no clue how to run anything from console. Or quit. But when I have the mono file on my desktop, how can I install it? That is my real problem now.

cd /tmp
svn checkout [http://paint-mono.googlecode.com/svn/trunk/](http://paint-mono.googlecode.com/svn/trunk/) paint-mono-read-only
cd paint-mono-read-only/src
./configure
make
sudo make install

Will require mono-2.0-devel and possibly some other libraries too. Run with "paintdotnet" in a terminal

---

### Post by directhex on 2009-02-04
> **hyper_ch said:**
> how do you know he hasn't got one already?

Because then he'd be dual-booting to run the apps he needs - and an OEM license isn't valid inside a VM

---

