---
title: "flash issue on chromium"
date: 2010-10-09
forum: New to Ubuntu
---

### Post by learner4ever on 2010-10-09
hey guys..  my flash issue is a weird one. 

flash works normally on chromium(and chrome) and plays for a while. if i start a new tab with flash content after the previous flash files hav buffered, flash displays a gray box and there is no response. when i check the /tmp folder, the previously buffered flash file are present, and they play on any player. but they cannot be accessed from the browser anymore. 

no issues with firefox or opera.

---

### Post by lovinglinux on 2010-10-09
Try the third item on [Flash Issues & Solutions](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html).

---

### Post by learner4ever on 2010-10-10
no improvements yet..:( i tried the step given there. 

when i open the browser through terminal, this is wat happens.. 

[U]~$ chromium-browser youtube.com&

~$ *** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()
*** NSPlugin Viewer  *** WARNING: unhandled variable 18 (<unknown variable>) in NPN_GetValue()

and after a while, this is shown:

*** NSPlugin Wrapper *** ERROR: NPP_Destroy() wait for reply: Connection reset by peer
*** NSPlugin Wrapper *** WARNING:(/build/buildd/nspluginwrapper-1.2.2/src/npw-wrapper.c:1854):invoke_NPP_Destroy: assertion failed: (rpc_method_invoke_possible(plugin->connection))

*** NSPlugin Wrapper *** ERROR: NPObject 0x7f8247612660 is no longer valid!
*** NSPlugin Wrapper *** ERROR: NPObject 0x7f8247612660 is no longer valid!

thanks for replyin!:) 

[/U]

---

### Post by kh1116 on 2010-11-17
i also experience this same problem

---

