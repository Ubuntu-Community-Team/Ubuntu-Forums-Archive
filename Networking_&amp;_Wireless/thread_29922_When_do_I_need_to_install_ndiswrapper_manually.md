---
title: "When do I need to install ndiswrapper manually?"
date: 2005-04-26
forum: Networking &amp; Wireless
---

### Post by nanaban on 2005-04-26
I need ndiswrapper for my card, but I am not sure if I need to compile ndiswrapper from source, as instructed on on the wiki site. I don't remember myself compiling ndiswrapper in the past.

---

### Post by az on 2005-04-26
If the versino of ndiswrapper that is installed by default on Hoary is not new enough for you will need to recompile.  You must try it.

---

### Post by jonny on 2005-04-26
ndiswrapper is a fast moving target.  You need to compile it if the snapshot version in Hoary doesn't work (or works badly) with your card.

You'd be daft to compile it unless you need to.  Packaged applications should ALWAYS be your first choice, as they're:

 - easier to install
 - more likely to work
 - less likely to interfere with other packages
 - available as a dependancy for other packages
 - easier to remove
 - most importantly of all, able to be updated automatically - both for security and version update reasons

Having said that, ndiswrapper is an unsupported universe package (incredible, really, considering how important it is) so you don't get all those advantages in this particular case.

If, despite all these problems, you really want the newest, hottest software all the time just because it's there, you should be using Gentoo or Debian Sid, not a release based distro like ubuntu.

Erm, I think.  Anyone agree with me?

---

### Post by elasticwings on 2005-04-26
Ndiswrapper is one package that is best compiled from the most recent source.  It's still in 4 or Development Status on Sourceforge.

---

### Post by az on 2005-04-26
You are both wrong.

"Having said that, ndiswrapper is an unsupported universe package (incredible, really, considering how important it is) so you don't get all those advantages in this particular case."
In Hoary, ndiswrapper in not in universe.  It is on the cd.  You do get the advantages.

If you install from source, the next time your kernel version gets increased due to a security fix, you will have to compile it again.  If you just use the stock version, you will get the compatible version along with the upgrade.

Ndiswrapper is a binary thing.  It either works or it does not.  If it works, there is _no_ reason to try a different version.

---

### Post by jonny on 2005-04-26
[QUOTE=azz]In Hoary, ndiswrapper in not in universe.  It is on the cd.  You do get the advantages.[/QUOTE]Didn't realise that.  Last time I looked for it in Synaptic, it didn't have the little ubuntu symbol beside it - but that was a few months back.

Just goes to show how much better ubuntu's getting - and it was brilliant to start with  :grin:

---

### Post by elasticwings on 2005-04-26
Just out of curiosity, which wireless card are you using?

---

