---
title: "Vista Sidebar Gadgets in Ubuntu"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Andy06 on 2009-06-18
Is there any way to run vista sidebar gadgets in ubuntu?

Perhaps running some of the XP sidebar programs under wine? Or using a compatibility layer? I vaguely remember I once saw some months ago a google code converter to convert gadgets/widgets from one form to another but cannot find it anymore.

The most promising cross platform gadget app seems to be the kludgets project but it does not have native linux support yet.

Anyone else have any success in running vista gadgets in Ubuntu?
To be honest I really only am desperate for one gadget that I cannot do without: SFkilla's Multimeter 2.10 to be precise. Can I somehow make it a .exe and run it under wine?

---

### Post by marshall.robert on 2009-06-18
The closest thing you are going to find is Screenlets. You can install it from Add/Remove... and then search places like Gnome-Look.org to get extras for it.

---

### Post by mikechant on 2009-06-18
> To be honest I really only am desperate for one gadget that I cannot do without: SFkilla's Multimeter 2.10 to be precise. Can I somehow make it a .exe and run it under wine?

Looking at this application I would guess it is very windows specific and very unlikely to run satisfactorially under Wine; but you might as well try it, shouldn't do any harm.

However, assuming it doesn't work you might like to look at the 'Graphical Process and System Management Tools' in the following article: [http://www.informit.com/articles/article.aspx?p=770644](http://www.informit.com/articles/article.aspx?p=770644)
xosview looks as if it might provide at least some of what you want.

---

### Post by Andy06 on 2009-06-18
I had a look at screenlets, gdesklets and adesklets but none of them can satisfactorily re-create the functionality. Plus they sorely lack features and polish in comparison to the above mentioned gadget.

Mikechant,
I checked out your recommendation. I also checked out conky. Looks very hard to do to be honest and for little gain, the info we get back is quite basic.

Perhaps there is some third party gadget for screenlets, gdesklets or adesklets not included in the default set that I do not know about? Anyone using anything like it?

---

### Post by Tibuda on 2009-06-18
I found [this site]("http://sfkilla.com/index.php?option=com_content&task=view&id=24&Itemid=63") by googling, and I do think SFKilla Multi Meter looks more like Conky. There are no screenshots, so I'm not sure.

Another widgets application that runs in Linux is Google Gadgets.

---

### Post by PureLoneWolf on 2009-06-18
Maybe Conky could do what you are after?  It's highly customisable

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by OffAxis on 2009-06-18
I've never used SFKilla's Multimeter program, but isn't that just Conky?

[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

It's in the repos, and there's a HUGE thread on different customizations.

[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

---

### Post by Cheesemill on 2009-06-18
Check out the June screenshots thread for some inspiration and to see what conky can do:
[http://ubuntuforums.org/showthread.php?t=1175016](http://ubuntuforums.org/showthread.php?t=1175016)

---

### Post by Mark Phelps on 2009-06-18
> **Andy06 said:**
> Is there any way to run vista sidebar gadgets in ubuntu?
Basically -- no.  Even in Windows 7, although MS claims it has eliminated the sidebar program, the desktop gadgets still rely on the sidebar program to execute.

You could try it in Wine, but unless you're already using Wine for other things, it's probably not worth the trouble.

As others have said, there are similar features in the various "xxx-lets".

Also, Google stuff might work -- if they have a Linux port.

---

### Post by Tibuda on 2009-06-18
> **Mark Phelps said:**
> Also, Google stuff might work -- if they have a Linux port.

Yes they have both a deb package and a repository.
[http://desktop.google.com/linux/](http://desktop.google.com/linux/)

---

