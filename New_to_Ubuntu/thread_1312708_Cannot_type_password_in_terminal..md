---
title: "Cannot type password in terminal."
date: 2009-11-03
forum: New to Ubuntu
---

### Post by Cruvenium on 2009-11-03
Hi,

I'm having this problem, I cannot type my password in terminal when requested.

[IMG]http://h.imagehost.org/0708/Screenshot-1.png[/IMG]

In the line 

```
[sudo] password for cruvenium: 
```

I cannot enter anything. What's the problem here? I only can press ENTER once and go to the next line, but if I type my password it is not valid and gives me

```
Sorry, try again.
```

EDIT: And yes I know I forgotten the word 'install'. But that isn't important. It happens even if I type 'sudo apt-get install tomboy' anyway.

---

### Post by aysiu on 2009-11-03
Not displaying feedback when you type the password is normal (and **not** a security measure, despite what some people will tell you):
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

Maybe also make sure you don't have caps lock on?

Worst-case scenario, reset your password to a new one:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by sisco311 on 2009-11-03
*Your password is being accepted in the terminal. You just aren't getting any visual feedback. Go ahead and type your password and hit Enter afterwards. If you typed your password correctly, there should be no problems.*

[http://psychocats.net/ubuntu/passwordinterminal]("http://psychocats.net/ubuntu/passwordinterminal")

---

### Post by Cruvenium on 2009-11-03
OHHH.

I didn't know there was such feature. I'm a complete beginner here. Thanks anyway, problem solved!

---

