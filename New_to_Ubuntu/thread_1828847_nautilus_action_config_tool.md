---
title: "nautilus action config tool"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by vagelism on 2011-08-19
Hello again.
I try to configure WIPE through nautilus but I come in one problem.
It can not handle files that dont have solid name...
For example it will wipe a file called 123.txt but not a file that named 123_123.
How can I overcome this problem?
thank you!

---

### Post by vagelism on 2011-08-19
> **vagelism said:**
> Hello again.
I try to configure WIPE through nautilus but I come in one problem.
It can not handle files that dont have solid name...
For example it will wipe a file called 123.txt but not a file that named 123_123.
How can I overcome this problem?
thank you!

Well, I solved the problem by reverting to the old Maverick version.

The steps: 

Code:
sudo apt-get purge nautilus-actions
I then downloaded the old deb from here (choose the appropriate mirror):
[http://packages.ubuntu.com/maverick/...tions/download](http://packages.ubuntu.com/maverick/...tions/download)

then:

Code:
sudo dpkg -i /path/to/nautilus-actions_2.30.2-1_i386.deb
Now open synaptic to lock down the version of nautilus-actions in order to avoid updating it to the new one on your next upgrade:

Code:
sudo synaptic
(or use the menu)

On synaptic, look for nautilus-actions, select the package and go to the menu Package > Lock Version.

And you're done.

---

