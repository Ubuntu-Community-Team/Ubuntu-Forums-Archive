---
title: "Suddenlt cannot connect to wireless anymore"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by woodyg on 2009-10-27
My acer aspire one with UNR (9.04 Jaunty) has worked nicely so far. Today I had some problem with my internet connection, being slow and a bit on and off... being a problem with my provider as I had the same problem with my other lappie that is running windows.

My UNR was grinding to a halt more or less... terribly slow. I tried to disconnect from network and then connect again. However, it refused to connect again. It just tries on and on and on. A reboot makes no difference. Still cannot connect (Network is no fine. My other windows lappie is now ok, having no problem using the same network). 

What can be the problem? How can I diagnose any problem? I'm clueless...

---

### Post by jbrown96 on 2009-10-27
We need some info about your system. I need you to run some commands, so we can get an idea about what's happening with your system. Since you don't have any internet connection, we are going to run these commands and save the output to a file, then you can copy that file to your other laptop and upload it here. 
1) I haven't used the UNR, so I don't know how to find a terminal, but it would probably be easier if you can. It will probably be somewhere in applications-->accessories. If you can't find it, do step A.
A) Ctrl+Alt+F2 This should take you to a console login. Login
2) Run these commands
```
lspci >> output.txt && sudo lshw -c network >> output.txt && iwconfig >> output.txt && lsb_release -a >> output.txt && uname -a >> output.txt
```
B) If in console mode, switch back to the desktop. ```
exit
``` then Ctrl+Alt+F7 (or maybe F1).
3) Open up your home directory and you should find a file called output.txt Copy that over with a flash drive, then upload here.

---

### Post by woodyg on 2009-10-28
thanks a lot for the reply... however, today it suddenly works like a charm. how weird is that? Have you seen issues like this with ubuntu? I mean, is this one can expect to happen once in a while?

---

