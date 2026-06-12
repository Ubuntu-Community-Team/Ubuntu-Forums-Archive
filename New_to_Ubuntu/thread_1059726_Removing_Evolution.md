---
title: "Removing Evolution"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2009-02-04
Hi,

    Having successfully installed Thunderbird,  I thought I'd like to tidy up by removing Evolution,  but Add/Remove Applications won't let me do that because of dependencies,  and tells me to go to Synaptic Package Manager instead.  :arrow:

A search for Evolution in Synaptic Package Manager though,  brings up lots of packages with Evolution in their name,  many of which either I don't recognise or I don't properly understand what their function is from their description.#-o

My question is whether it would be safe to proceed and remove all these,   or might some of them be needed to support Thunderbird?   An example would be evolution-data-server which says it manages mail, calendar, addressbook, tasks and memo information.  I'm not clear whether Thunderbird has its own data server and address book etc, or whether it relies on some common packages that have Evolution in their name. :?:   

Or am I perhaps worrying unnecessarily here?   Can I rely on being warned if I try to remove some common program that another of my installed programs is dependent on :?:

---

### Post by 7mkgw7q on 2009-02-04
When I cleaned mine up, I erased them all. I have yet to witness any negative affects from it.

---

### Post by mikewhatever on 2009-02-04
You can safely remove evolution and evolution-common, evolution-data-server-common is the problematic one since it removes gnome-panels and gnome-applets. It shouldn't be a problem if you have a replacement for those or use xfce instead of gnome. You get to review the list of packages to be removed, but synaptic wouldn't know whether or not you need gnome-panel etc, and will remove everything you choose to.

---

### Post by Sleepy-zz-John on 2009-02-04
Thanks folks.    So you think it would be safe to also remove evolution-exchange,  libedataserverui,  evolution-webcal. and evolution-plugins,  do you?
How about evolution-data-server (without the common) ?

---

