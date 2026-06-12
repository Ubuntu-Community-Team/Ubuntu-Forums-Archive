---
title: "update manager keeps saying need to authenticate"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by kapi on 2011-05-01
I've had this problem for over a week now and and stuck. A pop up states that it needs to authenticate software but does nothing else. I select the authenticate button but it does nothing.

Any ideas please?

---

### Post by oldos2er on 2011-05-01
Can you run **sudo apt-get update** in a terminal, and if there are any errors copy and paste them in full here?

---

### Post by kapi on 2011-05-02
Hi, thanks for replying. Ran input as request and no errors occurred but update manager still gives me this output via a pop up.see screen dumpl please.

---

### Post by kapi on 2011-05-02
actually I've just realised that when you select the authenticate button a user input box should appear so I am able to input my password, but this is the problem, no such input box appears and so it just hangs

---

### Post by kapi on 2011-05-02
SOLVED!

I should have known - WINE, it's really buggy and once I went to synaptic package manager and un-installed all the wine packages and re booted the laptop then the update manager works fine (so far :-))

---

