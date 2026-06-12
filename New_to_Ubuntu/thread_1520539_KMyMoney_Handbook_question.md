---
title: "KMyMoney Handbook question"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by ParadoxBlue on 2010-06-29
First let me apologize if I haven't researched this enough and am wasting forum bandwith. 

I'm running Ubuntu 9.10 and I installed KMyMoney about a week ago and all works fine (I like it better than Quicken). The problem I have is when I try to run the KMyMoney Handbook from the help menu I get the error: (thumbnail attached). Upon looking at the KMyMoney faq I find the following:

     **14. Will KMymoney work on my X/Ubuntu desktop?**
      [B]It will work, but you will have to install the basic KDE libraries first, as Xubuntu comes with Gnome libraries by default. If you want to install from CVS, you should install these packages:
[/B]        

[LIST]
[*]**build-essential**
[*]**kdelibs4-dev (this one will install a ton of other KDE-related packages)**
[*]**kcontrol (this one will allow you to change KDE-related settings)**
[/LIST]
        
Build-essential is installed on my system, kdelibs4-dev is not installed and kcontrol isn't listed anywhere in Synaptic Pkg Mgr. that I can find. Do I need to install kdelibs4-dev to run the help file and if so what about the kcontrol that I can't seem to find anywhere?

Any help is appreciated and let me know if I need to clarify or provide more info in any way.  This is my first formal post to the forums and it may not come out looking quite as I intended. I've been running Windows since 1991 and am a total noob when it comes to Linux and Ubuntu but I like what I've seen so far.

Thanks in advance

---

### Post by -humanaut- on 2010-06-29
Yes, you'll need to install the kdelibs

---

### Post by Hei Ku on 2010-06-29
The easy way is to install KMyMoney from this PPA:


[https://edge.launchpad.net/~claydoh/+archive](https://edge.launchpad.net/~claydoh/+archive)

Uninstall kmymoney2, then update and install from here.

---

