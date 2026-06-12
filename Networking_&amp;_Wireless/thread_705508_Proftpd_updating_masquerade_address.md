---
title: "Proftpd updating masquerade address"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by tsikis on 2008-02-23
Hello there i have a problem found another post about the same thing but no one has asnwered so i will it another try.
I have a dynamic ip to my router i have setup proftpd with dyndns so on ... But every time my ip changes the proftpd is running with the old ip so my Question: is there any way the ip of the proftpd which i have already setup to listen on the dyndns host to listen on the new ip instead of the old one?
The restart Proftpd is not the answer cause i could be away from the server so i will have a problem to restart proftpd.
Making a script to restart isnt the question because from the time the router gets the new ip till the time the proftpd restarts i will have no Ftp server.
(Other ftp server that could offer me this are welcomed)
Any help would be appreciated Thanks
Well after some more search i found the answer there is a module mod_dynmasq that i read does the job but now i have a problem when i try to load the module i get a permission denied after i added the mod_dynmasq.c to the modules.conf and the Include....... to the proftpd.conf

---

