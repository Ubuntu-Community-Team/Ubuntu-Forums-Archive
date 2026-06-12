---
title: "Finger Command"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by Swenghk on 2009-12-21
When i use the finger command on my e-mail, it starts, but then comes to a stall and doesn't do anything... Am I doing something wrong?

```
seth@SETH-LAPTOP:~$ finger sethrobert94@gmail.com
[gmail.com]


```

And it just sits like that until I push <CTRL-C> to quit. Help! :]

---

### Post by Dougie187 on 2009-12-21
Well, I don't think you have permissions to finger on gmail.com.

When it says user@host, it means user=username, host=computer that you have permissions on.

Like for example. If you had a laptop and a desktop, and your laptop had an ip of 192.168.0.2 and your laptop was 192.168.0.3, and you were using your laptop. You wanted to finger the user testuser on your desktop, you could enter

```
finger testuser@192.168.0.2
```

from your laptop.

---

### Post by Swenghk on 2009-12-21
So there is no way I can use the finger command unless I have 2 computers? Ah. I really want to learn how to use it

---

