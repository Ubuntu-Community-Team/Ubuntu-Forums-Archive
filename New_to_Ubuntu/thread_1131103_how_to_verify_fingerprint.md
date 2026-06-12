---
title: "how to verify fingerprint"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-20
To Verify a fingerprint do the following:


```
gpg --fingerprint (insert keyid here)
```

An example of fingerprint information is below. The part needed comes after the /:

> pub   1024D/28988BF5 2000-02-27
      Key fingerprint = B117 2656 DFF9 83C3 042B  C699 EB5A 896A 2898 8BF5
uid                  Roger Dingledine <arma@mit.edu>

In this instance, you would enter:
```
gpg --fingerprint 28988BF5
```

btw, I am not Roger Dingledine :)

---

### Post by steve101101 on 2009-04-20
good guide.

---

### Post by Penguin Guy on 2009-04-20
Sorry but you have confused me :confused:. I'll google it.

---

### Post by Didius Falco on 2009-04-20
Just open a shell and type ```
man gpg
```

---

### Post by Penguin Guy on 2009-04-20
> **Didius Falco said:**
> Just open a shell and type ```
man gpg
```
Thanks but it is this part that has confused me:
"An example of fingerprint information is below..."
But how do we find out that information?

---

### Post by yeehi on 2009-04-20
> But how do we find out that information?

Information like this is published by the information owners on, for example, a website.

[Here]("https://www.torproject.org/verifying-signatures.html.en") is the website where I found the information in the example.

If you can trust both the website publishing the information and your connection to that website, then you can compare the published fingerprint with the output of the ```
gpg --fingerprint
``` command.... That is, if I understand correctly :redface:

---

