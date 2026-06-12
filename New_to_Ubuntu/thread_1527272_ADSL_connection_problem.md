---
title: "ADSL connection problem"
date: 2010-07-09
forum: New to Ubuntu
---

### Post by Punkbyz on 2010-07-09
Yeaterday when i installed ubuntu i could not connect to internet( i use ADSL) at first but later i used:

sudo pppoeconf

and it was connected. but again the same problem arised and no matter what i do i dont seem to connect to internet.

---

### Post by dineshs on 2010-07-09
pleasem try post #5 here
[http://ubuntuforums.org/showthread.php?t=1525054](http://ubuntuforums.org/showthread.php?t=1525054)

---

### Post by Punkbyz on 2010-07-09
> **dineshs said:**
> pleasem try post #5 here
[http://ubuntuforums.org/showthread.php?t=1525054](http://ubuntuforums.org/showthread.php?t=1525054)
I am still not getting connection icon. I tried #5 post but still no use.

---

### Post by dineshs on 2010-07-09
Are you using 10.04?Did you restart after editing the files?

---

### Post by Punkbyz on 2010-07-09
yes i am using 10.04. I did restart.

---

### Post by dineshs on 2010-07-09
pl post the result of
```
cat /etc/NetworkManager/nm-system-settings.conf 
```
and
```
cat /etc/network/interfaces
```

---

### Post by Punkbyz on 2010-07-09
Both code generates, No such file or directory message

---

### Post by dineshs on 2010-07-09
instaed of [COLOR="Blue"]cat[/COLOR] pl use [COLOR="Blue"] sudo gedit[/COLOR]

---

### Post by Punkbyz on 2010-07-09
Results

---

### Post by dineshs on 2010-07-09
pl try to copy and paste the command because you have typed /etc/network/interface
it is interface[COLOR="Blue"]s[/COLOR]

---

### Post by Punkbyz on 2010-07-09
Interfaces Result:

---

### Post by dineshs on 2010-07-09
pl try this
```
sudo gedit /etc/network/interfaces
```
delete the whole contents.Then copy and paste the following
```
auto lo
iface lo inet loopback
```
I mean the file should contain only the above two lines.
Now restart and configure the connection via the DSL tab in NM following the link I mentioned earlier

---

### Post by Punkbyz on 2010-07-09
This is it right!!
So now how to connect it? coz i have to dial it to connect to the internet? if i can get back the connection icon(you know the up and down arrow) in the task bar i could connect like before.

---

### Post by dineshs on 2010-07-09
Right click on the NM icon (double arrow) and click adsl 36667 (hope this is listed).

Hope you clicked the apply button after configuring

---

### Post by Punkbyz on 2010-07-09
Yes i could do that but i dont have that icon any where.. on the task bar..

---

### Post by dineshs on 2010-07-09
right click on the taskbar click add to panel - select notification area and ADD

---

### Post by Punkbyz on 2010-07-09
I got some thing but i am not really sure what it is. its just three tiny horizontal lines. I tried other options as well but could not get connection icon.

---

### Post by dineshs on 2010-07-09
i still suspect your /etc/network/interfaces.PL once again post the contents
```
sudo gedit /etc/network/interfaces
```

---

### Post by Punkbyz on 2010-07-09
Its fine.. Still i dont get connection icon

---

### Post by dineshs on 2010-07-09
did you restart after adding notification area?
pl try this
[http://ubuntuforums.org/showpost.php?p=5132230&postcount=3](http://ubuntuforums.org/showpost.php?p=5132230&postcount=3)

---

### Post by Punkbyz on 2010-07-09
Hey Thanks man it solved the problem. Thanks a lot dude..

---

### Post by dineshs on 2010-07-11
Happy to hear your problem is solved

---

