---
title: "Nautilus doesn't like my smb connection"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by pokapeski on 2005-09-05
I am trying to configure a network share on an xp machine. So, I've shared a folder on windows and defined a workgroup. Now I've configured smb.conf with the given workgroup and netbios name of the windows machine.
Now I go to Compueter>network places>Connect to server "servername" ; "sharename" ; "user" and a folder for the share is created. Fine.
I now double click on the folder, a password is requested (I give it) and then I get this message:

Nautilus cannot display "smb://alvaro@ack102/c/Mis%20Documentos".

 :roll: 

Does anyone know what I am doing wrong?

Thanks in advance

---

### Post by s_p_a_r_k_y on 2005-09-05
try browsing to it manually type into smb://host
then browsing to the share...
I also think it shouldn just be
smb://user@host/share
no path after your /c/

also try smbclient -L host -U user
from the command line
Stefan

---

### Post by pokapeski on 2005-09-05
[QUOTE=s_p_a_r_k_y]try browsing to it manually type into smb://host
then browsing to the share...
I also think it shouldn just be
smb://user@host/share
no path after your /c/

also try smbclient -L host -U user
from the command line
Stefan[/QUOTE]

got it!  \\:D/  bad password, no permissions on the folder.  ](*,) 
anyway I didn't know about the CLI smbclient. it can be very useful. thanks.

---

### Post by s_p_a_r_k_y on 2005-09-05
for debugging lean to love the console and the tools : )

---

