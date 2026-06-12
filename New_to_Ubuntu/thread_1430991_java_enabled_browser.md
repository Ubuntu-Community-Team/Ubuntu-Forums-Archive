---
title: "java enabled browser"
date: 2010-03-16
forum: New to Ubuntu
---

### Post by quarkhirad on 2010-03-16
When i opened the link below the first line of the page says 

```
Sorry, you need a Java-enabled browser to see the simulation
```

What do i do so that i can see the animation. 

I am using ubuntu 9.10.

[HTML]http://www.falstad.com/circuit/e-555square.html[/HTML]

---

### Post by sikander3786 on 2010-03-16
Have you installed JAVA?

You can install it this way (and of course many other useful plugins like streaming media codecs will be installed)

```

sudo apt-get install ubuntu-restricted-extras

```

Regards.

Sikander.

---

### Post by quarkhirad on 2010-03-16
Thanks man but i have already installed that. 

Any other suggestions????

:-(

---

### Post by sikander3786 on 2010-03-16
Which web browser are you using?

---

### Post by quarkhirad on 2010-03-16
i am using firefox 3.5.8

---

### Post by sikander3786 on 2010-03-16
Type in terminal

```

java -version

```

Does Java Version show up.

If so type in firefox address bar

```

about:plugins

```

If Java Plugin is not listed there you need to follow these steps.

[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

---

### Post by quarkhirad on 2010-03-16
Hey thanks man .

Though i installed sun-java6-plugin using synaptic and it works. Thanks  

again 

:-)  :-)

---

### Post by sikander3786 on 2010-03-16
> **quarkhirad said:**
> Hey thanks man .

Though i installed sun-java6-plugin using synaptic and it works. Thanks  

again 

:-)  :-)

Glad you got it working.

You should also install the sun-java6-fonts package.

Regards.

Sikander.

---

