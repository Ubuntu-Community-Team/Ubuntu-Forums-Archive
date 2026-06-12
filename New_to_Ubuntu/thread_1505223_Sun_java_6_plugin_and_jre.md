---
title: "Sun java 6 plugin and jre"
date: 2010-06-08
forum: New to Ubuntu
---

### Post by krippa on 2010-06-08
Why are Sun Java6 JRE and plugin not available in Lucid 64-bit!? This seems like a very very strange move from canonical because a lot of java programs don't run properly with openJDK! Could someone please shine some light on this! It almost makes me lose hope my internet bank will ever run on my ubuntu installation!

---

### Post by pizza-is-good on 2010-06-08
OK. They work for mine. I have programmed in java successfully in 10.04 64bit.
I know that I had some trouble getting jre to work, but eventually I got it. I don't quite remember what I did to get it working, but attached is a screenshot of my synaptic and the jre packages that I have installed.

Hope that helps.

~pizza

---

### Post by garvinrick4 on 2010-06-08
> **krippa said:**
> Why are Sun Java6 JRE and plugin not available in Lucid 64-bit!? This seems like a very very strange move from canonical because a lot of java programs don't run properly with openJDK! Could someone please shine some light on this! It almost makes me lose hope my internet bank will ever run on my ubuntu installation!
If I remember right they are in partners. Go to Software sources and check partners repository. If not there you can add this in Software sources. They were moved in this 10.04 version of Ubuntu to partners repository.

deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by krippa on 2010-06-08
> **garvinrick4 said:**
> If I remember right they are in partners. Go to Software sources and check partners repository. If not there you can add this in Software sources. They were moved in this 10.04 version of Ubuntu to partners repository.

deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

Thanks a lot! With the partner repository I can find it! 

I still think this is handled badly by ubuntu as the "newbie installer" that pops up in firefox only shows an option to install openjdk, which doesnt even let me upload photos to facebook. Also trying to install the java6 plugin in Ubuntu Software Center, I am greeted with a message saying it's not available for 64-bit Ubuntu. How is a newbie ever going to get over this hurdle without going back to windows!?

---

