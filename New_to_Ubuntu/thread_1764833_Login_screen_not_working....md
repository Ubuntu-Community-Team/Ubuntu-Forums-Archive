---
title: "Login screen not working..."
date: 2011-05-22
forum: New to Ubuntu
---

### Post by androssofer on 2011-05-22
Hi, i changed the settings in 10.10 to not ask for password to login. but didnt change the settings to automaticly login as certain user at startup... so the result is that I get the login screen, but when i click on a user, it stalls for a bit as if its about to ask for a password, then shows me the list of users to select from again... and i dont get logged in :-(.

I can login to the cli by pressing ctrl-alt-f1 then enter my details. but wen I go back to the GUI all it does is put a tick beside my name and still wont let me log in to the GUI.. any ideas about how to fix it? its rather annoying...

---

### Post by Gone fishing on 2011-05-22
alt-control-F1 to get to a terminal tty1

Login (which you can do)

then ```
sudo passwd username
```

add a password twice as prompted

If that doesn't work the start up in recovery mode click resume login that will take you to a terminal. Login then run startx and you will be logged into your desktop where you can graphically fix the problem. If the toolbars arn't there click Atl-control-t to get a terminal then ```
unity --replace
```


Personally I think you should login rather than have it auto login and you should have a password - one of the great things about Linux is that it takes security seriously

---

