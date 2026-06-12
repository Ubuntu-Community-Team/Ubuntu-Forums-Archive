---
title: "Script for killing a program and starting it again"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by asdir on 2007-10-05
The script I intend to write should kill an old instance of vpnc-connect and start a new one. However, to kill it (sudo kill pid) I need to know the pid, which I cannot extract so that a script could take it and use it (or can I? For now I do ps -A and extract it from the list manually). Starting the new instance after that would be straight forward I guess.

Is there a possibility to write a script, so that I simply click an icon and it happens? I have to do these steps a dozen times a (work-)day which really bums me out.

Thanks guys.

---

### Post by bubbalouie on 2007-10-07
you could **ps-e|grep vpnc-connect** then parse the results using sed then build a command, finally you can execute the command, all using a 5 line bash script, it could easily be made to be quite poweful.

Alternatively:

**killall vpnc-connect && vpnc-connect**

Hope this helps :)

Ryan

---

### Post by sonicx on 2007-10-07
you can use any command as a variable in bash shell skripts, like the pidof command, to get a pid:
```
$(pidof vpnc-connect)
```
regards,jonas

---

