---
title: "Add softwar Source for dummies"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-07
OK - I want to add a software source from my ISP located here:

[ftp://ftp.iinet.net.au/linux/ubuntu/dists/jaunty-updates/](ftp://ftp.iinet.net.au/linux/ubuntu/dists/jaunty-updates/)

When I go to **Software Sources** then **Third Party** then **Add**, do I enter the address above, preceded by **deb** or something else?

When I do try to enter **deb [ftp://ftp.iinet.net.au/linux/ubuntu/dists/jaunty-updates/](ftp://ftp.iinet.net.au/linux/ubuntu/dists/jaunty-updates/)** the **Add source** button remains inactivated, so I assume I'm doing soemthing wrong.

Can anybody tell me what to enter?

**ALSO** - can I keep the other Third Party sources there but just not use them (i.e., only have my iinet one as "active")? Do I just only have the iinet one ticked in Synaptics?

---

### Post by smileyguy on 2009-10-07
Sorry - you might only be able to get to the ftp url linked above if you're signed up with iinet as your isp

---

### Post by OpenGuard on 2009-10-07
```
deb ftp://ftp.iinet.net.au/linux/ubuntu/dists/ jaunty-updates main
```

---

### Post by smileyguy on 2009-10-07
Thanks - it worked:)

What's with the last bit? i guess it's just a protocol we gotta lear right?

Does leaving the other sources unticked mean they won't be checked? I'd like to do that as this new one is unmetered from my isp.

---

### Post by Dougie187 on 2009-10-07
Yes, if you uncheck the third-party sources they are not checked for updates or for software. To then force them to be checked you would have to recheck the boxes and then update your software list (reload in synaptic, or in terminal sudo apt-get update)

---

### Post by MasterOfTheHat on 2009-10-07
[Here's a good guide to adding/managing repositories.]("https://help.ubuntu.com/community/Repositories/Ubuntu") 

[And here's an explanation of the sources.list syntax.]("https://help.ubuntu.com/community/Repositories/CommandLine#Explanation%20of%20the%20Repository%20Format")

---

### Post by smileyguy on 2009-10-07
That all looks great and I look forward to going through it.

Why do you think that there aren't GUIs for dumb Windows users (tautology I know!) like me?

---

### Post by MasterOfTheHat on 2009-10-08
Check that first link I sent you. It walks you through doing it a couple of different ways, including via GUI

---

