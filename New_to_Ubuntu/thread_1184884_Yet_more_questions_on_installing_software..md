---
title: "Yet more questions on installing software."
date: 2009-06-11
forum: New to Ubuntu
---

### Post by Deathfrost on 2009-06-11
Hello all, 

Trying to install NAMD on Ubuntu here. The download doesnt come with a configuration file, which I have used for all other software to specify were the paths are.

Basically I have a namd2 executable and all the associated files to run a program in a folder, I can run it in that directory through the terminal, but I want to invoke the executable when I am in other paths in the terminal, as I can do with anything else I installed.

I guess im a little confused on what files  need to be where in the hierarchy. 

Thanks

---

### Post by Azrael3000 on 2009-06-11
I don't know namd so please excuse me if my answer is entirely wrong :)

So lets say you have namd in ~/namd-dir and call the program via
```
cd ~/namd-dir
namd
```

Then you can call it from every directory via 
```
~/namd-dir/namd
```

Now alternatively you can also edit your Path variable, as can be seen here: [http://lowfatlinux.com/linux-environment-variables.html](http://lowfatlinux.com/linux-environment-variables.html)

So you would do the following:
```
 PATH = $PATH:$HOME/namd-dir
```

and then you can execute namd in every directory by simply typing
```
 namd
```

HTH
Arno

---

### Post by Deathfrost on 2009-06-12
Thank you Thank you!
This is exactly what I was looking for.

---

