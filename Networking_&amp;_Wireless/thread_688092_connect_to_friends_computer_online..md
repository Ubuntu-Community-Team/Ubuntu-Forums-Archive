---
title: "connect to friends computer online."
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by Masterj15 on 2008-02-05
how can you do this? I want to connect to my friends computer through my copmuter. How can I do this. 

Thanks in advance.

---

### Post by lsmobrian on 2008-02-05
Depends on what you want to do, command line through ssh i think would be the easiest.  Is your friends computer running linux or windows(or osx)

---

### Post by Masterj15 on 2008-02-05
> **lsmobrian said:**
> Depends on what you want to do, command line through ssh i think would be the easiest.  Is your friends computer running linux or windows(or osx)

she is running windows and I am running Ubuntu gusty gibbon. I thought of some type of ftp server thingy. Where I can search through her stuff in a file broswer thingy.

---

### Post by lsmobrian on 2008-02-05
I'm on a hardy box at the moment and network on nautilus isnt working for me  

you might be able to connect with smb ( smb://Server IP/ShareName/ )

your friend would have to set file and print sharing on, and then set directories to sharing
most likely they will also have to setup port forwarding on their home router


another option would be like you said ftp ... there are some easy ftp client/servers out there   
FileZilla has both... again would probably need to setup port forwarding

---

