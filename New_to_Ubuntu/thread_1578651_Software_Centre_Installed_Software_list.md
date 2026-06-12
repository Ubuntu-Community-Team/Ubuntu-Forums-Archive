---
title: "Software Centre Installed Software list"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by oddentity on 2010-09-20
What's the criteria for deciding whether or not installed software appears in the installed software list?

Because I've installed software from the standard repos both through apt and the software centre itself, and those programs don't necessarily appear in the list. For example, I've just installed get-iplayer, and it's not in the installed software list. It's definitely installed - I just used it. Sun Java plugin is there as is Netbeans, but the jre and jdk I installed are not, etc. My View option is set to show All Software, not just Canonical maintained software.

I realised this software shows up in Synaptic, I'm just trying to "get" the software centre. Showing an arbitrary subset in the way it does doesn't seem helpful.

---

### Post by jtarin on 2010-09-20
Try running th command in a terminal "apt-get check" and see if that updates your view.

---

### Post by oddentity on 2010-09-21
Thanks for the quick response.

That didn't seem to make anything else appear in the list, although I notice that if I type the names of installed (but missing) packages into the search box, they appear under the search results as I would expect. They just don't appear in the installed list normally.

---

