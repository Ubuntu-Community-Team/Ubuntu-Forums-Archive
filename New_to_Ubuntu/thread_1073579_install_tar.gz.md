---
title: "install tar.gz"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by kimikrishna on 2009-02-18
i am some old to ubuntu [1 month]

but still, i dont really understand how to install contents of tar compressed file.. 

i downloaded this  and extracted

```
http://estudiantes.univalle.edu.co/~juanjmed/gtklxsplit/packages/gtklxsplit-0.1.1.tar.gz
```

but i do not know how to install ..

i read install file 
and entered make, make install ... no use, it says some errrs.. help me with this

---

### Post by baizon on 2009-02-18
What are the errors?

---

### Post by hyper_ch on 2009-02-18
well, first yo need to have compiling tools:

```

sudo apt-get install build-essential

```

Then you should read what libraries you need. Very likely that tar.gz file has a file containing all those infos. Then once you have everything you normally have to:

```

./configure
make
sudo make install

```

However the steps might be differnet. Again, there should be a howto relted to that package.

And if you encounter errors, you should post them here.

---

### Post by halitech on 2009-02-18
according to the INSTALL file
```

INSTALLATION:  

REQUIREMENTS:

GTK+, developed on 1.2 version (version 2.0 untested)  
  
Process of Compilation  
For a quick beginning, type in the prompt of the shell:  
  
          
        make  
  
to install the binaries type:  
        
        make install  
          
For uninstall process:  
  
       make uninstall  
```

did you install build-essential prior to trying to install?

what errors are you getting when you try to install?

---

### Post by mikewu on 2009-02-18
This was the error:
> gcc -g -Wall `pkg-config --cflags --libs gtk+-1.2` -c join.c
Package gtk+-1.2 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-1.2.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-1.2' found


You need to install libgtk1.2-dev

```
sudo apt-get install libgtk1.2-dev
make

```

That should let everything compile.

---

### Post by kimikrishna on 2009-02-20
> **mikewu said:**
> This was the error:


You need to install libgtk1.2-dev

```
sudo apt-get install libgtk1.2-dev
make

```

That should let everything compile.

:popcorn: this solved ..

thanksssss

---

