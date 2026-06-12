---
title: "Save local file to network drive via command line"
date: 2011-09-02
forum: New to Ubuntu
---

### Post by niko123 on 2011-09-02
Hello Everyone - 

I have a shared drive on windows i map to it by \\drive\folder and i have a local file on my ubuntu machine - is there any way using the terminal i can securely copy that file over to the network? 

I know i can do it via a gui...but i want to experiment with the terminal. 

Please let me know 

Thanks!

---

### Post by e79 on 2011-09-02
Best way to securely copy files over the network, is to install SSH and then use SCP to copy it:

```
scp /folder/file user@machine:/folder/file
```

> SCP uses [Secure Shell]("http://en.wikipedia.org/wiki/Secure_Shell") (SSH) for data transfer and utilizes the same mechanisms for authentication, thereby ensuring the [authenticity]("http://en.wikipedia.org/wiki/Information_security#Authenticity") and [confidentiality]("http://en.wikipedia.org/wiki/Confidentiality") of the data in transit.

[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)

[http://en.wikipedia.org/wiki/Secure_copy](http://en.wikipedia.org/wiki/Secure_copy)

Hope this helps

---

### Post by niko123 on 2011-09-02
> **e79 said:**
> Best way to securely copy files over the network, is to install SSH and then use SCP to copy it:

```
scp /folder/file user@machine:/folder/file
```



[http://en.wikipedia.org/wiki/Secure_Shell](http://en.wikipedia.org/wiki/Secure_Shell)

[http://en.wikipedia.org/wiki/Secure_copy](http://en.wikipedia.org/wiki/Secure_copy)

Hope this helps


Thanks! That worked like a charm! Gonna read up on Secure shell & copy!

---

### Post by e79 on 2011-09-03
I'm glad I could be of some help !

Cheers

---

