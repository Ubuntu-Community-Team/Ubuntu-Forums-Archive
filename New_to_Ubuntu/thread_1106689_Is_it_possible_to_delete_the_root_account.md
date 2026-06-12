---
title: "Is it possible to delete the root account?"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Virtualboxbuntu on 2009-03-26
I was just wondering if it's possible to delete the root account. I do not actually intend to do this, I know that it's completely pointless. I just want to know what would happen if you type ```
sudo deluser root
``` or try to delete it in some other way. What would the above command say? Is there any other way to delete the root account if that does not work?

---

### Post by HammerOfDoubt on 2009-03-26
I heard of someone doing that by accident and they had to do a complete reinstall.

Can't remember details.

---

### Post by linuxguymarshall on 2009-03-26
Possible. Yes.  

Do I recommend it? Hell no.

Your system will still work just fine but you will never, ever, be able to run as super user anymore. So you can, but your system will become defunct.

---

### Post by vanadium101 on 2009-03-26
Why on earth would you want to do that? You need the root account, it's what keeps your computer secure.

I don't think anyone will give you the information you want to do that

---

### Post by Virtualboxbuntu on 2009-03-26
As I tried to explain before, I DO NOT intend to do this. I was just curious as to what would happen if you did.

On the other hand, maybe I will try it. In Virtualbox, of course.

---

### Post by CharlieHorse1967 on 2009-03-26
While many things are possible, not all of them are good ideas.  Basically, you could try this to see what happens (it might be fun) but I would avoid doing so on a production machine.

---

### Post by pbpersson on 2009-03-26
> **Virtualboxbuntu said:**
> As I tried to explain before, I DO NOT intend to do this. I was just curious as to what would happen if you did.

On the other hand, maybe I will try it. In Virtualbox, of course.

One would hope the OS would be smart enough not to let you do it.  It sort of sounds like trying to format your system drive in Windows.

Then again, someone said Linux is about freedom - as in the freedom to totally destroy your machine without warning you.  They said if you use sudo the creators of the OS assume you know what you are doing. ;)

Please let us know what happens.  :)

---

### Post by novafluxx on 2009-03-26
:lolflag::popcorn:

Let us know how this goes; sounds interesting!

---

### Post by mhh91 on 2009-03-26
that made me go LOL :D


never thought of it before,but it'd be very harmful :(

---

### Post by CrazyArcher on 2009-03-26
> **pbpersson said:**
> One would hope the OS would be smart enough not to let you do it.  It sort of sounds like trying to format your system drive in Windows.

Then again, someone said Linux is about freedom - as in the freedom to totally destroy your machine without warning you.  They said if you use sudo the creators of the OS assume you know what you are doing. ;)


Actually, it's an interesting issue. At the one hand, the system should protect the user from destroying his machine, but at the other hand should allow doing anything. My opinion is that it should ask twice before performing any potentially catastrophic commands, such as deleting root or the various recursive "rm" commands.

---

### Post by jespdj on 2009-03-26
> **pbpersson said:**
> One would hope the OS would be smart enough not to let you do it.  It sort of sounds like trying to format your system drive in Windows.
Besides this, there are many other dangerous commands that you could think of (I won't mention them here) that would destroy your system in a few seconds.

It would not really be practical to make every possible dangerous command impossible - in fact it would be annoying, because sometimes you do need powerful and potentially dangerous commands (not to destroy your system ofcourse, but for other purposes).

---

### Post by t0p on 2009-03-26
> **CrazyArcher said:**
> [QUOTE=pbpersson;6958924]
Actually, it's an interesting issue. At the one hand, the system should protect the user from destroying his machine, but at the other hand should allow doing anything. My opinion is that it should ask twice before performing any potentially catastrophic commands, such as deleting root or the various recursive "rm" commands.

I fail to see why the system should "protect the user from destroying his machine".  It's the user's machine.  He should be able to do whatever he wants to it.  Just because you or I might not want the root account removed, doesn't mean our (sensible) wishes should be forced on everyone.

I also think your idea that the system "should ask twice before performing any potentially catastrophic commands" would be dreadfully annoying.  I hate it when I get dumb "Are you sure? Are you *really* sure?" messages.  If I issue a command with *sudo*, the computer should just do it.  We have to assume that the use of *sudo* means that the user knows what he's doing.  Against stupidity the Gods themselves contend in vain.  And an OS is not a God.

---

### Post by starcannon on 2009-03-26
> **t0p said:**
> [quote=CrazyArcher;6959278]

I fail to see why the system should "protect the user from destroying his machine".  It's the user's machine.  He should be able to do whatever he wants to it.  Just because you or I might not want the root account removed, doesn't mean our (sensible) wishes should be forced on everyone.

I also think your idea that the system "should ask twice before performing any potentially catastrophic commands" would be dreadfully annoying.  I hate it when I get dumb "Are you sure? Are you *really* sure?" messages.  If I issue a command with *sudo*, the computer should just do it.  We have to assume that the use of *sudo* means that the user knows what he's doing.  Against stupidity the Gods themselves contend in vain.  And an OS is not a God.

I could not agree more.
Leave my ability to control my machine in MY hands; I would also point out that these things are done from the command line, and anyone willing to work at that level must either understand the risks of running commands without knowing the full implication of the commands, or understand fully the implication of the commands they are running. I run linux because I DO NOT want to be baby sat, otherwise I'd have me a Mac.

---

### Post by Virtualboxbuntu on 2009-03-26
Well, there happened to be a Linux Mint CD on my desk, so I put it in Virtualbox. Here's what happened after it was up and running.

```

mint@mint ~ $ sudo deluser root

Deleting the root account is generally not required and can leave your system unusable. If you wish to delete it, use the option --force.

No action has been taken.

$ sudo deluser --force root

Removing account 'root.'

$ sudo aptitude -v moo

No password entry for root!

$ sudo aptitude install emesene

No password entry for root!

$ sudo

No password entry for root!

```

As you can see, you can no longer do anything as root. I suppose it's a good way to prevent hacking if you're absolutely sure that you don't need to do anything as root.

Does anybody know if this command works on Mac OS X? Again, not that I intend to do it, I'm just curious.

---

