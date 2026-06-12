---
title: "LogMein.msi and Wine"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by diasje on 2008-02-19
Hello, i am new here, and new to Ubuntu, i have a dsl network and a router at home, so i can easely use remote desktop outside to enter in my home computers, the problem is that at my work, i do not have the privelegies to access with remote desktop and TightVNC or radmin.

What i use now is logmein, its not great but it will do.

Now  i have one Ubuntu box, and i what to access it with logmein, i have read a lot of posts, about this but nothing abou the error that i am having.

I have installed Ubuntu 7.10, and installed Wine with Wine-Doors, i have installed all lib and dll&#347; from wine doors, and when i do this: sudo wine start LogMein.msi, the app installer starts well, all goes right until the app starts to copy files to Virtual c:\Program Files, after 5 or 6 secound i get this error message: **LogeMein Setup Wizard ended premature**ly, and at the console i get this lines:

```
err:msi:ACTION_InstallFiles compressed file wasn't extracted (L"c:\\Program Files\\LogMeIn\\x86\\lmimirr.cat")
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603

```

Is there any way of installing this app? Has anyone done it?

The guys at LogMein, say that they cannot suport Linux at the moment.

Help Please.......

PS- Sorry for my poor english :lolflag:

---

### Post by diasje on 2008-02-19
Hello again, i have installed it to a pen drive, with XP, and on the Ubuntu box, i put all the files to the wine virtual drive C:/Program Files/LogMein, but it wont work, so i copy all the files to wine C:/Windows System32/, on the console o used sudo wine start LogMein.exe.

but i get the app to start, and when i try to enable it:

[[IMG]http://img512.imageshack.us/img512/7600/logmeineg0.th.png[/IMG]](http://img512.imageshack.us/my.php?image=logmeineg0.png)

---

### Post by vahnx on 2008-02-24
I also tried WINE to install LogMeIn, but I get the 
```
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
```

Anyone help?

---

### Post by diasje on 2008-03-05
No one to help us? :confused:

---

### Post by vahnx on 2008-03-05
I started using the vncviewer command on a LAN and it works great. You can use it on ubuntu/xp/vista to controll either. Never tested it outside of a LAN though. I like it better than logmein now.

---

### Post by diasje on 2008-04-04
Ok friends, i now that VNC its better then logmein, but when you are on a company thar has 3 proxy servers, what can you do?

I have used other combination, that consists in having ubuntu on a xp box in virtual pc, the problem is that you can see, but you cant enter that virtual machine.

:confused:

---

### Post by sands on 2008-05-17
check this
[https://secure.logmein.com/products/hamachi/vpn.asp?lang=en](https://secure.logmein.com/products/hamachi/vpn.asp?lang=en)
you can create a personal lan network in the internet. and then use vnc in your internal lan...

I am looking for a simpler solution than this.

---

