---
title: "Problem Installing Java in Ubuntu 10.04"
date: 2010-11-28
forum: New to Ubuntu
---

### Post by patch953 on 2010-11-28
Ubuntu 10.04

Was trying to install java. Acceptance screen came up in the terminal. I could not get by it. Like an idiot I get PO'ed and closed the terminal window.

Tried running it again.  
I run this: sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

I get this:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What now?

---

### Post by howefield on 2010-11-28
You may only have one instance of apt-get running, so close software centre, synaptic, update manager, ect, ect and try again.

If you are installing in terminal, and are struggling with the license agreement, try using the tab key to highlight the ok button and move on.

---

### Post by patch953 on 2010-11-28
Thanks for your help

Closed everything and rebooted. Tried running the command line as before.

Now I get this:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (>= 6.22-0ubuntu1~10.04) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.22-0ubuntu1~10.04) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (>= 6.22-0ubuntu1~10.04) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I've still got something screwed up.

---

### Post by Wobblybob on 2010-11-28
Try entering 
sudo apt-get -f install
in a Terminal, then your original command

---

### Post by patch953 on 2010-11-28
Problem Solved.

Thanks

---

