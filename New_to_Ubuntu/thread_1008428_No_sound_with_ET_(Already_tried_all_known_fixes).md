---
title: "No sound with ET (Already tried all known fixes)"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-11
Hi guys,

I am using Intrepid and I have downloaded Wolfenstein ET. 2.6

I can't seem to get sound to run.

I have tried installing "esound" and nothing happens.

I have also tried this command "killall esd; et; esd"

and this "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss"
note: with this command I get permissions denied error so I tried to run as sudo and get the same permissions denied error so the only way I found to execute it was first doing "sudo su"

But I still am having no luck

any help would be great.

I have already looked at [https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory) still did not help.

---

### Post by LowSky on 2008-12-11
have you treid the other two methods, they talk about in the link you provided.
[https://help.ubuntu.com/community/EnemyTerritory#Method%202](https://help.ubuntu.com/community/EnemyTerritory#Method%202)
[https://help.ubuntu.com/community/EnemyTerritory#Method%203](https://help.ubuntu.com/community/EnemyTerritory#Method%203)
[https://help.ubuntu.com/community/EnemyTerritory#Making%20Startup%20Scripts%20More%20Friendly](https://help.ubuntu.com/community/EnemyTerritory#Making%20Startup%20Scripts%20More%20Friendly)

---

### Post by Nepherte on 2008-12-11
Try this:
```
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
```

Explanation: You will become root in the shell and add the specified text into the corresponding files. Afterwards you close your root session.

---

### Post by nakama85 on 2008-12-11
> **LowSky said:**
> have you treid the other two methods, they talk about in the link you provided.
[https://help.ubuntu.com/community/EnemyTerritory#Method%202](https://help.ubuntu.com/community/EnemyTerritory#Method%202)
[https://help.ubuntu.com/community/EnemyTerritory#Method%203](https://help.ubuntu.com/community/EnemyTerritory#Method%203)
[https://help.ubuntu.com/community/EnemyTerritory#Making%20Startup%20Scripts%20More%20Friendly](https://help.ubuntu.com/community/EnemyTerritory#Making%20Startup%20Scripts%20More%20Friendly)

as for method 2  I did not see any input/output errors so I did not try it.

as for method 3 was the echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss command noted above.

Thanks for the reply

---

### Post by nakama85 on 2008-12-11
thanks I gave that a try but I still have no sound.
> **Nepherte said:**
> Try this:
```
sudo -i
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
```

Explanation: You will become root in the shell and add the specified text into the corresponding files. Afterwards you close your root session.

---

### Post by nakama85 on 2008-12-11
```
------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/nakama/.etwolf/etmain/ui.mp.i386.so)... 
Sys_LoadDll(/home/nakama/.etwolf/etmain/ui.mp.i386.so) failed:
"/home/nakama/.etwolf/etmain/ui.mp.i386.so: cannot open shared object file: No such file or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/etmain/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xa926af40  
Sys_LoadDll(ui) succeeded!

```

Ok this is the error I see. Does anyone know how to fix this?

---

### Post by vastus on 2008-12-11
Do u have any other sound programs running when u get this? Like teamspeak, ventrilo or music players. Anyway This worked for me.

do:
```
sudo sh -c "echo 'et.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss"
sudo sh -c "echo 'et.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss"

```

start et and see if it helped. If it did help here is how u make it permanent.

1. Open file /etc/rc.local:
```
sudo gedit /etc/rc.local
```

2. Add following lines to the file:
```
echo 'et.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
echo 'et.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss
```
*before* the last line:

```
exit 0
```

3. Save the file and close it.

---

