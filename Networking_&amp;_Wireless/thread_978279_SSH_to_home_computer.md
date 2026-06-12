---
title: "SSH to home computer"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by sdlyr8 on 2008-11-11
So I'm away at school and I'm looking for a way to ssh home to my family computer (running mac os x). I have enabled ssh on the mac a while ago back when I was home, but now that I'm away at school I can't due to the router. I wont be home again until christmas to get in and change the settings on the router to allow the port forwarding to the computer. I do know the router login and password and the home IP address. Is there any way I can either trick the router or get a way to log in and find my way into the computer? Thanks for any help!

---

### Post by pdwerryhouse on 2008-11-11
My guess is that the router doesn't allow logins from its external interface, so what you will need to do is get someone from your house to ssh outwards from the Mac, to some server that you have an account on, and then forward the ssh port so that you can get back into the Mac.

eg. imagine you have access to an external server on address 1.2.3.4.

Get someone from your family to ssh from the Mac to that server and forward the port back:

```
ssh -R 8022:localhost:22 username@1.2.3.4
```

Once they have done that, you can then log into your Mac remotely, from the server on 1.2.3.4, with:

```
ssh -p 8022 localhost
```

---

