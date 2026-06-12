---
title: "Terminal Server Client"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by chris.tkd on 2008-06-21
Hello,

I am running 8.04 and attempting to use the Terminal Server Client to remote desktop into a computer i have running in the next room, its running 7.10.

Ive input the ip of the machine in the 'Computer:' box and the user name and password of the machine in the relevant fields.

When i hit connect i get the error

ERROR: channel_register
WARNING: Initializing sound-support failed!
ERROR: connect: Connection refused.

Does anyone know whats wrong?

Thanks.

---

### Post by chris.tkd on 2008-06-21
I usually dont do this...bump.

---

### Post by zeronothing on 2008-06-21
in order to use the terminal server client to connect to another linux box you would need to change the protocol connection to vnc. I'm pretty sure the RDP protocol is only for windows. Their might be away to connect using that protocol but I haven't needed to use it to connect to another linux box. If you cant select VNC as the protocol that would mean you need to install it by using synaptic or another means. then you will be able to select VNC as the protocol. I on the other hand I would use another terminal server and client called "nxmachine". it is completely free and really easy to install (it comes in .deb packages so its a double click install). go to the nxmachine [[COLOR="Blue"]website[/COLOR]]("http://www.nomachine.com/").You will have to download 3 packages for either 32 bit edition or 64 bit edition. you have to install the packages in order of dependency, just try to install one package and if you cant install that package try the others (you will eventually get it installed its only 3 packages). if you want to connect to the linux box via a windows machine they do make a windows client as well. after you get it install, the application should be located in you menu with all of the other applications you have installed. oh and one more thing make sure you have "openssh server" installed first before installing the nxmachine application. just use synaptic to install openssh server. have fun....

---

