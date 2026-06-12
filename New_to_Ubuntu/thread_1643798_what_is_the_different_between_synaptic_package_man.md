---
title: "what is the different between synaptic package manager and ubuntu software centre"
date: 2010-12-12
forum: New to Ubuntu
---

### Post by Pollyanna1 on 2010-12-12
Some times when I need to install program I use Synaptic and some times I use Ubuntu software centre, but really I don't know what is the different between both and when should I use that and when should I use this???? Are they both existing to do the same functions? Any explanation?

---

### Post by tesex167 on 2010-12-12
they should both do the same thing - unfortunately in my case at the moment neither is wanting to open....

---

### Post by I'mGeorge on 2010-12-12
the software center it's more simple to use and organised. There you can only find the available softwares defined by their genre, Games, Networking, Multimedia and so on.

Synaptic on the other hand shows everything, including available libraries, auxiliary packages, transitional packages, basically everything that's available from your repos. If you have a little experience with linux, and you already know what do you need, you can uninstall the software center 'cause it will be meaningless to keep it around.

---

### Post by rburkartjo on 2010-12-12
i use both. as a rule of thumb i always use the software center first. easy to install something and remove it. the spm takes a little more thought and care. you could remove something that shouldnt be removed if you arent careful. linux assumes you always know what your doing.

---

### Post by beew on 2010-12-12
Synaptic is amazing. It allows you to sort things in different categories, it supports smart search, you can easily add or delete repositories, you can fix broken packages, downgrade packages or lock package versions. Basically it gives you the power that is otherwise only available in the command line but the search and browse function is even better than the command line tool.

In short, Synaptic is the best. Tried other software packagers like kpackagekit (which is a piece of junk for KDE) or yumex (for Fedora) ,there is nothing quite amazing.

I just keep the Software Center for the pretty icons and to check once in a while what software is for purchase. Just out of curiosity, not that I am planning to buy any software.

P.S. I think the purchase option is only in the Software Center, so if you are planning to buy something you would need to keep SC, otherwise there is no harm in uninstalling it.

---

### Post by beew on 2010-12-12
> **I'mGeorge said:**
> the software center it's more simple to use and organised. There you can only find the available softwares defined by their genre, Games, Networking, Multimedia and so on.


You have that in Synaptic as well, just choose your sort option from the side panel.

---

### Post by uriel1998 on 2010-12-13
Okay, so if they're the same entity (essentially), why can I get Synaptic to run just fine using Openbox (not GNOME/Openbox, just Openbox over Ubuntu) but not the Software Center?   It all runs just fine when I'm running straight GNOME...

---

### Post by Perfect Storm on 2010-12-13
> **uriel1998 said:**
> Okay, so if they're the same entity (essentially), why can I get Synaptic to run just fine using Openbox (not GNOME/Openbox, just Openbox over Ubuntu) but not the Software Center?   It all runs just fine when I'm running straight GNOME...

Try open it via the terminal;
```
gksudo synaptic
```

---

### Post by uriel1998 on 2010-12-13
> Okay, so if they're the same entity (essentially), why can I get  Synaptic to run just fine using Openbox (not GNOME/Openbox, just Openbox  over Ubuntu) but not the Software Center?   It all runs just fine when  I'm running straight GNOME...

Sorry, I wasn't clear.   Synaptic runs splendidly.  The Software Center will show me everything, but when I click "install" (or "remove") it does nothing.  It's an annoyance, but... well, it's an annoyance.  ;)

---

### Post by amjjawad on 2010-12-13
Synaptic, Software Center and Terminal are different name that serve or do the same function.

To be clear: I mean when you want to use the terminal to "install/remove" something. Synaptic and Software Center are GUI tools.

---

### Post by mcduck on 2010-12-13
> **uriel1998 said:**
> Sorry, I wasn't clear.   Synaptic runs splendidly.  The Software Center will show me everything, but when I click "install" (or "remove") it does nothing.  It's an annoyance, but... well, it's an annoyance.  ;)

You are probably missing PolicyKit that is used to handle authentication for the Software Center (and some other admin tools used on the Gnome desktop). Synaptic on the other hand simply launches as root user with gksudo.

---

### Post by uriel1998 on 2010-12-13
> **amjjawad said:**
> Synaptic, Software Center and Terminal are different name that serve or do the same function.

To be clear: I mean when you want to use the terminal to "install/remove" something. Synaptic and Software Center are GUI tools.

Right, I *know* that.  When I'm running Openbox (with an Ubuntu install) Apt-get works fine from the command line.  Synaptic works just fine.  The Software Center lets me **browse** its contents, but not interact with it at all.

That's *why* I'm confused that one GUI tool (and the CLI tool) work just fine, but the other (very similar) tool does not.  :)

---

