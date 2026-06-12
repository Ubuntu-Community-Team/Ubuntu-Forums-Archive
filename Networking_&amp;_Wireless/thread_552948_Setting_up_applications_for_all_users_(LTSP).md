---
title: "Setting up applications for all users (LTSP)"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by stephenwalder on 2007-09-17
Hi,
I have a small query that I think somebody will have a simple answer for.

We've setup LTSP in our primary school. I have created user accounts for 40 or so children.

When I log in as a child I am required to setup flash in the web browser. Does this mean that each user would have to individually setup flash for their user profile? It would make much more sense if I could just setup flash for all the users in one fell swoop. Is this possible?

I would be very grateful if somebody could point me in the right direction here.l I can also forsee the same problem happening when I want each user to have Java, Acrobat Reader, etc, etc.

Your kind help would be much appreciated!

Thanks in advance,

Stephen Walder
Holmfirth Junior, Infant and Nursery School, Huddersfield

---

### Post by SpiritIsReality on 2007-10-26
howdy
I'm thinkin' that the package
flashplugin-nonfree 
installed on the servers environment would allow all clients flash in the browser?
correct me if I'm wrong, but I think the chroot /opt/ltsp/i386 environment is used to boot the clients,
and the clients log in to the server /home. Packages are added to the server / , not added to the
chroot /opt/ltsp/i386 environment.
trails

helps
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ltsp&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=ltsp&titlesearch=Titles)
[https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring)

[http://www.edubuntu.org/Documentation](http://www.edubuntu.org/Documentation)
[http://www.edubuntu.org/GettingStarted](http://www.edubuntu.org/GettingStarted)
[http://doc.ubuntu.com/edubuntu/handbook/C/](http://doc.ubuntu.com/edubuntu/handbook/C/)
[http://doc.ubuntu.com/edubuntu/handb...sp-theory.html](http://doc.ubuntu.com/edubuntu/handb...sp-theory.html)
[http://doc.ubuntu.com/edubuntu/handb...sp-client.html](http://doc.ubuntu.com/edubuntu/handb...sp-client.html)
and the motherload here !!!
[http://wiki.ltsp.org/twiki/bin/view/Ltsp/Debian](http://wiki.ltsp.org/twiki/bin/view/Ltsp/Debian)

---

