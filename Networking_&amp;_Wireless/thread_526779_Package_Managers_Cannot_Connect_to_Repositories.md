---
title: "Package Managers Cannot Connect to Repositories"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by caspersghosts on 2007-08-15
Update manager can fetch the updated packages, but not the list of changes
Synaptic can browse for installables, but cannot download them

Cannot connect to any repositories.

My internet connection is otherwise functioning normally.
I was experimenting with proxy settings, but reverted to a direct connection, and now the package managers are trying to connect to the localhost when I try to access the repositories.

Is there a command to change how the package managers access the internet?

this post describes the situation, evidently there is a solution...
but what?
[http://ubuntuforums.org/showthread.php?p=3197088#post3197088](http://ubuntuforums.org/showthread.php?p=3197088#post3197088)

---

### Post by imdano on 2007-08-15
In Synaptic, navigate to Settings->Preferences->Network, and make sure you're set to directly connect to the internet.

---

### Post by caspersghosts on 2007-08-16
doublechecked, it was set that way.

still gives me could not connect to localhost errors, for every repository

is there a setting somewhere else that could be dictating that it try to connect to the localhost, instead of the wireless?

---

### Post by imdano on 2007-08-17
Can you connect using apt-get?

---

### Post by caspersghosts on 2007-08-17
oh did I not make that apt-get joke in this thread? :-p

yep, tries to connect to the localhost as well 127.0.0.1:4001, I´ve seen it sooo many times.

---

