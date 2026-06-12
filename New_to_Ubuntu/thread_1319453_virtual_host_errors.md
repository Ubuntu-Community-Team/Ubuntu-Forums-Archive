---
title: "virtual host errors"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by dougie_boy on 2009-11-08
hi everyone

i am trying to setup a series of virtual servers on my webserver but i am having some difficulty working out what needs to be put where.

i know that i need a series of virtual host parameters but i am not sure where to put them. i have read that they need to go into the httpd.conf but its empty, the apache2.conf seems to be the place to put the info but i cant be sure.

i have left my apache2.conf file as it was when i was running a single site, i have just added another site-available file for the new website with the information pointing in the correct locations.

when i restart the web server with both sites enabled i get the following error

* Restarting web server apache2                                                                                                                            [Sun Nov 08 17:32:41 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Nov 08 17:32:41 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
[Sun Nov 08 17:32:41 2009] [error] VirtualHost *:80 -- mixing * ports and non-* ports with a NameVirtualHost address is not supported, proceeding with undefined results
[Sun Nov 08 17:32:41 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
                                                                                                                                                     [ OK ]


bit lost now so i am thinking about wiping the lost back to square one, but this still leaves me with no idea how to enable a virtual server which is name based. anyone got a good tutorial or advice?

cheers

---

