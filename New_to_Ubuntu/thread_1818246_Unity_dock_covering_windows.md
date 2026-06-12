---
title: "Unity dock covering windows"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by DSn0wMan on 2011-08-04
My Unity dock is set to auto hide, but sometimes it gets stuck up/out covering the left edge of open windows.

Is there some way to fix the auto hide, or at least not let windows go under the dock?

Here is a screenshot with the dock not hiding, and it's set to auto hide I get the same behavior from dodge windows.

[http://i.imgur.com/OuVy1.png]("http://i.imgur.com/OuVy1.png")

---

### Post by wastvedt on 2011-08-06
I also have this issue. I am running Natty on a ThinkPad W520.

---

### Post by linuxman94 on 2011-08-06
What programs are you using when this occurs?
I could be [bug #769703]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/769703")

---

### Post by DSn0wMan on 2011-08-06
> **linuxman94 said:**
> What programs are you using when this occurs?
I could be [bug #769703]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/769703")

That's pretty interesting.. I guess it's related to to using SQLDeveloper(Java Program) I'll have to try it when I get back to my work machine.

---

### Post by wastvedt on 2011-08-06
> **linuxman94 said:**
> What programs are you using when this occurs?
I could be [bug #769703]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/769703")

Ahah. Thanks! I do indeed have this bug. In my case it was showing up dragging something in digikam. As #39 suggests in that bug report, any supported dragging (i.e., I think, any dragging in a non-qt app.) causes the launcher to re-hide. I'll be waiting for 10/11 to install 11.10, but hopefully it is fixed there, as that bug also suggests. Thanks for the tip!

---

