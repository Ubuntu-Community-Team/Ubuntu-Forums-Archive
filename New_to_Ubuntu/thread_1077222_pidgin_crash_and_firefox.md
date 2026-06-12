---
title: "pidgin crash and firefox"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by sonicatu on 2009-02-22
Hi everyone. I`m new here so excuse me if i`m not posting where i should.

I`m using ubuntu 8.10 for 2 weeks or so and after i fiddled with it and installed applications like any other user.
Today when i started the PC and ran ubuntu, i tried to open pidgin and it won`t start. Then i wanted to lunch firefox to search for this problem and all my bookmarks and history disappeared. I tried restarting the PC but no result. I then uninstalled a plugin from firefox and restarted the PC and now it works fine. I don`t know if that was the problem, but is there anyway i can find out exactly what caused it?

UPDATE: pidgin still crashes when i try to open it.

---

### Post by yeats on 2009-02-22
Regarding these crashes:

- is Firefox working fine now that you've removed the add-on?

- are there error messages that happen when they're crashing?

Sometimes this sort of thing is related to compiz, the program that provides all the eyecandy effects.

---

### Post by sonicatu on 2009-02-22
firefox seams to work fine now, but pidgin still doesn`t work. no error message, no nothing. I just doesn`t start.

---

### Post by Limerick on 2009-02-22
I'd like to add to this and say that Pidgin occasionally dies for no apparent reason. It isn't permanent and does no damage but it gets annoying.

---

### Post by superprash2003 on 2009-02-22
go to the terminal and type pidin and incase you see any error message..post it.. did you install any add-on to pidgin recently??

---

### Post by sonicatu on 2009-02-23
I`m very confused. Today when I started the PC pidgin is working fine, but firefox is the problem. as described in my first post, the bookmarks are gone and all the history. it`s just like in safe mode.

I don`t know what to think. maybe if i restart my PC, pidgin won`t work but firefox will.

---

### Post by shredder12 on 2009-02-23
I am not sure about pidgin but i once had the same problem with firefox..
and the problem was some file permissions in the .mozilla folder.
so jst change the permissions and ownership..
```
sudo chown -R user:user  ~/.mozilla/
```
Hope this helps..

---

