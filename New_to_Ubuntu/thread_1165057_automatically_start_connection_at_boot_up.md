---
title: "automatically start connection at boot up"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by J.K on 2009-05-20
[FONT=Verdana]Hi,

When using xubuntu 9.04, I set up the Internet connection via pppoeconf. After being set up, it would automatically connect when booting the system.

Now with ubuntu 9.04, I've tried the same thing, but still have to run [/FONT]  [FONT=Verdana]sudo pon dsl-provider [/FONT]each time I boot up. Is there a way around this?

J.K

---

### Post by stephanvaningen on 2009-05-20
You can always at that to the services or in your .profile script I believe? If you don't know exaclty how to - give a sign, I'll try to be more concrete...

---

### Post by ashmew2 on 2009-05-20
The best way in my opinion is to make a shell script and set it to execute every boot , you could do something like :

```
cd ~
touch Connect.sh
chmod +x Connect.sh
nano Connect.sh

```

After that copy this into the file : 
```

echo "<password>" | sudo -S pon dsl-provider
```


Replace <password> with your actual password (Dont remove the quotes"").

Click on System > Preferences > Startup Applications.
Click Add.

Name : Whatever you want.
Command : ~/Connect.sh
Comment : Whatever you want.

This should fix you up. You can try rebooting and ask if something doesnt work! :D

---

