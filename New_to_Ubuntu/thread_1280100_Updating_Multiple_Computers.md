---
title: "Updating Multiple Computers"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2009-10-01
Hi

Just checking how one should go about if you want several computers to update from one computer when packages becomes available instead of all of them updating the same packages from the repositories.

The computers are in a peer-to-peer network.

Any pointers will be appreciated.

Thanks

---

### Post by yanceypd on 2009-10-01
Well if they were identical  you could use clonzilla.  If they have different Motherboards and cards Probably would be issues.:(

---

### Post by CatKiller on 2009-10-01
A search for "Ubuntu local repository" will probably get you what you want. Basically, you set one machine's /var/cache/apt/archives (or a mirror of the whole repository) to be accessible to the other computers, and then add a line in each of those computers' sources.list to point to the one machine.

---

### Post by markbuntu on 2009-10-01
I was just reading how to do that in Linux Pro Magazine a few days/weeks ago. It did not seem to difficult or especially easy either, I think you need to set up one machine to be a local repository server and point update manager on the others to that machine by changing the apt sources list. I think there is also a how to around here somewhere, maybe in tips and tutorials or at the ubuntu or debian wiki.

---

### Post by boblemur on 2009-10-01
i think that you should try one of the following things:

1) mount the main servers /usr/cache/apt from all the clients and then when they run apt-get upgrade it will look from that directory which is actually the servers and then any other computers that request it will find it already in there cache.

2) apt-cacher-ng is a program written to do pretty much what you are trying to do there is a tutorial here:
 [http://ubuntuforums.org/archive/index.php/t-981085.html]("http://ubuntuforums.org/archive/index.php/t-981085.html") 

i think apt-cacher-ng is probably your better option. then the computers can simply update as normal.

hope this helps :)

---

### Post by arnold.pietersen on 2009-10-02
Hi Everyone

I went to bed and received all these pointers this morning. 

Thanks for all your advice, I will try it out and give you feedback.

Regards

---

