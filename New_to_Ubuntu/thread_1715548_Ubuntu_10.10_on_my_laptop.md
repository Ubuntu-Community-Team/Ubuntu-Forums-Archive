---
title: "Ubuntu 10.10 on my laptop"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by Davealc on 2011-03-27
Hi,

I installed Ubuntu 10.10 on my laptop today (the desktop version). And I am trying to install the updates but it wont let me. When I click on install updates I get a warning
 'requires installation of untrusted packages' 

There isn't an option to accept it just says close and that takes me back to the update manager. I cannot get past this point. Is there anyway around this?

---

### Post by irw on 2011-03-27
Have you added any other repositories?

---

### Post by Davealc on 2011-03-27
I've not loaded anything apart from 10.10. I have just tried to watch a .mkv file on it. It prompted me to update and I got exactly the same warning message

---

### Post by Dougie187 on 2011-03-27
In the update manager, does it show the potential updates you are told you need to install?

Could you provide a list of these?

It would be prior to you trying to install them.

---

### Post by mikewhatever on 2011-03-27
Run **sudo apt-get update** from a terminal window and post the output.

---

### Post by jfreak_ on 2011-03-27
open synaptic package manager (its in system>administration), click the reload button on the top left. locate the package ubuntu-restricted-extras, if there is a green mark next to it, it means it is installed. If not , right click and select install. Click on the apply button on the top.

---

### Post by Davealc on 2011-03-28
p { margin-bottom: 0.08in; }  jfreak thanks!!! 

Sorted it by following what you said. Thanks for everyone's help with this. This place is brilliant! :D

---

