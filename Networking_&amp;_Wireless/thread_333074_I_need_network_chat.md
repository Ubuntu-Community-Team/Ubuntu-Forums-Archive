---
title: "I need network chat"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by CameronCalver on 2007-01-06
Hello i would like a chat program for my network like novel that will work on windows and linux and put the base program on my file server and make it admin and all other computers client and when someone sends a message all other computers dont have to have the client open the message just pops up.
Does everyone no what im on about

---

### Post by IYY on 2007-01-07
echo "Hello world!" | sudo wall

---

### Post by CameronCalver on 2007-01-07
cameron@ubuntu:~$ echo "Hello world!" | sudo wall
bash: !": event not found
cameron@ubuntu:~$ 
 and i was thinking more of a program

---

### Post by IYY on 2007-01-07
Sorry, it's the just the ! mark that was a problem.

```
 echo "Hello world" | sudo wall

```

This should work.

---

### Post by CameronCalver on 2007-01-07
and how do i get all other computer to receive that

---

### Post by IYY on 2007-01-07
If the other computers are terminals of this one, they should receive it without any other configuration. But how exactly is your network set up?

---

### Post by CameronCalver on 2007-01-07
that all works fine but i was thinking of something that would just pop up

---

