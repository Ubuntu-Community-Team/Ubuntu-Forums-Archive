---
title: "how to keep the theme from emerald manager?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by maneesh77 on 2009-01-20
first time to try a theme not given by ubuntu

step 1 installed emerald theme manager

step 2 downloaded and opened theme in emerald

step 3. used command emerald -- replace

now when I close the terminal it goes back to having no theme( something greyish). I logged out tried again same problem.

how to fix and how do i set it up in the sessions so that it will be at start up

---

### Post by Najmudin on 2009-01-20
I Think you should click on System>Prefrences>Sessions
Then select Add , when the Add startup Program appears add the following:
Name : Emerald
Command : /usr/bin/emerald (you can browse to the same directory).
Comment : you can leave it empty it will not effect anything.
Then press Add again.
Done.
I hope that can helps you.

---

### Post by tjwoosta on 2009-01-20
adding the command to the sessions will make emerald start every time you login  (this is probably prefered)


but the original problem that you are having is that you are using the terminal to run emerald


you should not use the terminal to open programs that you want to stay running

if you want programs to stay running you should use the run dialogue instead (alt-f2)

so the command would still be the same except you sould do it from the run dialogue instead of the terminal

---

### Post by maneesh77 on 2009-01-20
got the sessions configured. actually it also solved my problem with starting awn

thanks

---

