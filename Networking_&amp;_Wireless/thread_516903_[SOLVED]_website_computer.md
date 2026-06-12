---
title: "[SOLVED] website computer"
date: 2007-08-03
forum: Networking &amp; Wireless
---

### Post by charlier653 on 2007-08-03
I have recently been given another computer, and I want to put our website on it. Before I do, I need to know the best way to do this.

I have read somewhere in the forums about "headless" installs, but I have concerns about doing this (I still feel like a noob).

I am thinking about purchasing a KVM switch, so if I do a "headed" install I won't have an extra monitor etc to deal with.

My question is how easy is it to administer a headless web server over our home LAN?

I'm not sure of myself yet using the CLI.....as an example, I've killed X several times trying to edit the xorg.conf file to get my graphics card working better.

If I go with the KVM, does anyone have any recommendations for a fairly inexpensive one?

Any ideas how best to proceed?

---

### Post by splintercellguy on 2007-08-03
I guess you could use Apache, and remote administer with SSH? I'm no sys admin :(.

---

### Post by az on 2007-08-03
Installing a GUI on a web server will not help you administer the web server.  There are no GUI tools (that work) anyway,

Just run it over ssh.

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by charlier653 on 2007-08-03
Ok, Thanks!!

---

