---
title: "Accessing command line terminal on Ubuntu from WinXP"
date: 2008-03-27
forum: Networking &amp; Wireless
---

### Post by MalcolmCowen on 2008-03-27
I've had to rebuild my Ubuntu system, and I can't get access to Ubuntu command line from WinXP over my internal network using HyperTerminal.

I know it can be done, but I can't remember how and I can't find the documentation page I used last time to set it up.  (Yes I should have made notes!!)

I don't need any secure connection (it's a cabled intranet, not wireless.
Can someone point me at a solution.

---

### Post by Eiríkr on 2008-03-27
I'm not familiar with HyperTerminal, but assuming it's a ssh client like PuTTY, you need to install the ssh package.  Many distros include this by default, but Ubuntu does not.  Once installed, it should be running by default, and all you have to do then is make sure port 22 is open if you have a firewall.  Though it is secure, all you need is your username and login and you've got your command line.  

Cheers,

Eiríkr

---

### Post by MalcolmCowen on 2008-03-27
Thanks, that was it
ssh and PuTTY not Hyperterminal
Cheers

---

### Post by Eiríkr on 2008-03-27
Glad to help.  :D  If that does it for you for this thread, please mark it as SOLVED in the Thread Tools dropdown towards the top of the page.  :)

Thanks,

Eiríkr

---

