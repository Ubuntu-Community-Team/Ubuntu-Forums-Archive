---
title: "Connecting 2 networks to one server"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by Geophrum on 2008-05-27
Not sure if there is a "how to" on this but i have been searching for days.. and maybe i over looked it. i am a linux noob but love it so much i dont really use Windows much any more. have to at work 

I have 2 different ISPs. 2 different wireless/wired routers,  my server box is running Ubuntu 8.04 server

and i would like to have my file server be the only link between the two.  i would like to have the File server that has a dedicated FTP server run on the faster ISP and all the personal PCs and Wireless laptops connect to the Second ISP as not to clog Bandwidth. but i still want them to be able to access the File server.

also the Faster ISP i want to use for the FTP server does not allow web hosting and i would like to learn about Web hosting through the other ISP

i was thinking of adding in a wireless nic and having it connect wireless to the other server but i am not sure were to look for information about that type of bridging.  or if it can be done with a wired and a wireless nic.

Can any one point me in the right direction or if this is actually possible

Thanks

---

### Post by SpaceTeddy on 2008-05-28
in general - just install a second network card on your server and plug the cable in... That should work.

But there are a few gotchas that you might run into. For example - how is your network configured at the moment ? do you use network manager, or did you edit the /ect/network/interfaces directly to manage every interface ?

also, how do you obtain IP's ? do dial on, do you set the IP's staticially, do you have a dhcp running and some more routers/servers that do the briding for you ? (a picture of the setup would come in handy here :) )

lastly, i am not sure how to run a specific server on ONE network, and run a different one on the other (server here meaning an application). The only way i am really sure of how to do it is to use a virtual machine... or a NAT on the user-network side to make the server believe that the internet is in the user-network when it comes to www-requests...

i think i need that picture...

hope it helps :)

---

