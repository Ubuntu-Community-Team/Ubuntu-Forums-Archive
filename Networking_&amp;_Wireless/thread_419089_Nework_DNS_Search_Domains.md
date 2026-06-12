---
title: "Nework DNS Search Domains"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by krisrmgua on 2007-04-22
Every time i start my computer i have to go to System >> Administration >> Network and then click the DNS tab and add in my entries for Search Domain. I have created a Location for it. But would like to know if theres a way to add the Search domain Entires i have to default that loads for it. Any ideas?

---

### Post by krisrmgua on 2007-04-24
anyone?

---

### Post by eentonig on 2007-04-24
Do you get a DHCP address?

In that case, you should have your dhcp server giving you the DNS addresses.

In case of fixed addressing, I have no idea. I never had a problem with it.

---

### Post by branbuntu on 2008-06-05
Hello,

I'm having the same problem, I'm trying to research a solution.
This is what I have so far, but it's not working as expected.
--

Open a root terminal or prefix "sudo" for each of these commands:

Ensure you've installed VI (apt-get install vim-runtime)

```

0. Assumptions:
Wired connection is set to Roaming mode enabled
1. apt-get install resolvconf
2. vi /etc/resolvconf/resolv.conf.d/head
(the vi editor commands are here: http://www.cs.colostate.edu/helpdocs/vi.html)
(use :w to save and :q to quit without saving your changes)
(type "A" to add a line to the file, type in the domain name(s))
3. disable the dynamic retrieval of the search domains
4. gedit /etc/resolv.conf
(add search entries, example:)
nameserver x.x.x.x
search example.domain.com
search primary.domain.com
(Save file)


```



Ubuntu 7.04 (Hardy)

---

