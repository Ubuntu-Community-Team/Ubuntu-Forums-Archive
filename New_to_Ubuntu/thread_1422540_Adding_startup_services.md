---
title: "Adding startup services?"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-03-05
Hey, my cups service doesn't start when I log in... Can anyone lead me to the configuration file where start-up services are located? Like, where would I put "/etc/init.d/cups start"?

---

### Post by 2hot6ft2 on 2010-03-05
Have you tried adding it to
System > Preferences > Startup Applications?

Might not be the "right" place to add it but it should work.

---

### Post by ratcheer on 2010-03-05
I think the easiest thing to do would be to install bum (boot up manager) and see if it has a check box for cups. Mine does.

Tim

---

### Post by Ozymandias_117 on 2010-03-05
@2hot6ft2 You need to be root, so it can't be added there.

@ratcheer Alright, I'll try it, thanks

---

