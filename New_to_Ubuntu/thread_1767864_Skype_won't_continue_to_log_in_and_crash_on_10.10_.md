---
title: "Skype won't continue to log in and crash on 10.10 Netbook"
date: 2011-05-26
forum: New to Ubuntu
---

### Post by iamchichi on 2011-05-26
Hello! Does anyone know why and how to fix skype when it crashes and won't launch after an update? 

I'm using an Eee PC 1001P running on an Ubuntu 10.10 Netbook Edition. 


Please help. 

Really need skype to run for work. :confused::confused::confused:

Thanks in advance.

---

### Post by kaldor on 2011-05-26
Possible temporary fix is to delete the .Skype directory.

Graphical way:
Bring up your home folder. In the menu, click View > Show Hidden Files. Scroll down, find and delete ".Skype". 

Terminal way:
```
rm -rf .Skype
```

Try relaunching Skype then. If that doesn't work, remove Skype through the Software Centre or with this Command:
```
sudo apt-get remove skype
```

After that, delete the .Skype folder as shown above again. Re install Skype.

Seems like a few people have this issue today :(

---

### Post by iamchichi on 2011-05-26
> **kaldor said:**
> Possible temporary fix is to delete the .Skype directory.

Graphical way:
Bring up your home folder. In the menu, click View > Show Hidden Files. Scroll down, find and delete ".Skype". 

Terminal way:
```
rm -rf .Skype
```

Try relaunching Skype then. If that doesn't work, remove Skype through the Software Centre or with this Command:
```
sudo apt-get remove skype
```

After that, delete the .Skype folder as shown above again. Re install Skype.

Seems like a few people have this issue today :(


Thanks for the solution. we were able to fix it by following the steps from [http://heartbeat.skype.com/](http://heartbeat.skype.com/)


1. home folder 
2. ctrl+h 
3. searched for .skype folder. 
4. delete the shared.xml file 
5. relaunch skype 
6. login and accept the skype license agreement. 



hope this helped others having the same problem.
^_^

---

