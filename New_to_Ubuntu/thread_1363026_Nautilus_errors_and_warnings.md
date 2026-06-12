---
title: "Nautilus errors and warnings"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by jnmjr on 2009-12-23
When I open Nautilus I get the following:

jnmjr@My-Desktop:~$ gksudo nautilus
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

** (nautilus:2238): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2238): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2238): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> l2065
--> inode/directory
--> root
Shutting down nautilus-open-terminal extension
Shutting down nautilus-gdu extension

(nautilus:2238): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:2238): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
jnmjr@My-Desktop:~$ 

Can someone explain and help fix this. THX

---

### Post by Hendronicus on 2009-12-24
It seems as if you are trying to run Nautilus as the super-user. While this might not be the best idea most of the time, sometimes you need to. I do it quite a bit. I've had bad luck with running it with gksudo, so I just use plain sudo. As far as your error messages go, most of them are related to the fact that there is no root user on your system, yet Nautilus is trying to connect to the root account. This is why plain sudo works better with Nautilus. Sudo creates a temporary "fake" root account. I have no idea exactly how gksudo works, but I do know that they are not exactly the same.

---

### Post by jnmjr on 2009-12-24
I tried what you suggested, this what I got:

jnmjr@My-Desktop:~$ sudo nautilus
[sudo] password for jnmjr: 

(nautilus:9087): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension
Initializing nautilus-open-terminal extension

** (nautilus:9087): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:9087): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:9087): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Still no idea what it all means:confused:

---

### Post by Hendronicus on 2009-12-24
Does Nautilus run at all? If so, then just ignore the warnings. One other thing, do you really need to run it as root? If not, then just type "nautilus" (w/o quotes) or choose "File Manager" from the menu.

---

