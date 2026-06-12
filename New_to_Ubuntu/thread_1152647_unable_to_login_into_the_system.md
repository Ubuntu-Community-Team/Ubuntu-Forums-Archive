---
title: "unable to login into the system"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by anuragccsu on 2009-05-08
Hi All,

I've installd kubuntu 8.10 in my laptop. everything was fine but since yesterday i am unable to login into the system. As i start my laptop and select the ubuntu boot option given by grub, it boots silently but in the credential(login) window when i enter my user name and password it doesn't login and returns me to the same login window. my password is correct as if i type some junk password it says login failed.

i've tried all the session types (Default, KDE, and failsafe) provided by kubuntu. same problem. and

i've tried in the "recovery mode" all the options more importantly "try to fix the xserver" but this was also not helpful.

i can do only console login by the option provided on the login window or by pressing ALT+CTRL+F1. and there if i try to open any file(text) using gedit i get GTK+ warning and it doesn't open or if i open by kate(text editor in kubuntu) it says "unable to connect to xserver".

plz help me!
:confused:

---

### Post by Marvin666 on 2009-05-08
I don't know how to help but try using alt+ctrl+f2. The f1 shell is mostly used for debugging, etc.

---

### Post by anuragccsu on 2009-05-08
Hi All,

I've installd kubuntu 8.10 in my laptop. everything was fine but since yesterday i am unable to login into the system. As i start my laptop and select the ubuntu boot option given by grub, it boots silently but in the credential(login) window when i enter my user name and password it doesn't login and returns me to the same login window. my password is correct as if i type some junk password it says login failed.

i've tried all the session types (Default, KDE, and failsafe) provided by kubuntu. same problem. and

i've tried in the "recovery mode" all the options more importantly "try to fix the xserver" but this was also not helpful.

i can do only console login by the option provided on the login window or by pressing ALT+CTRL+F1. and there if i try to open any file(text) using gedit i get GTK+ warning and it doesn't open or if i open by kate(text editor in kubuntu) it says "unable to connect to xserver".

plz help me!:confused:

---

### Post by atomizer on 2009-05-08
strange problem.


In the console you can't use Kate or Gedit. you should use nano as your text editor. (or vi if you like the challenge)



Can you change the password in "recovery mode (drop to root shell)" with 
```
passwd <username>
```

---

### Post by Didius Falco on 2009-05-08
Try the steps outlined here:

[http://nixcraft.com/linux-software/491-start-x-server-ubuntu-linux.html](http://nixcraft.com/linux-software/491-start-x-server-ubuntu-linux.html)


I hope it helps...


Regards,

Didius

---

### Post by scheuri on 2009-05-08
I had those symptoms ages ago as well. It turned out that my /home was completely full.

What I could do was changing from X-Login to CLI (ctrl-alt-f1) and login there. Then I deleted some files, restarted the computer and voila...it worked again.

But I do not know if that works in your situation.
The CLI command "df -h" shows the usage of your partitions.

---

### Post by anuragccsu on 2009-05-11
:guitar:Thank you very very much Scheuri...it has worked for me also...:guitar:
but couldn't get the reason behind it..anyway cool...it's working...

---

