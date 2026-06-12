---
title: "Can't install g++ :("
date: 2009-04-20
forum: New to Ubuntu
---

### Post by lobo-tuerto on 2009-04-20
Hi guys, I'm on Ubuntu 8.10 and I'm getting this message when doing a:

sudo apt-get install g++

```

g++: Depende: cpp (>= 4:4.3.3-1ubuntu1) pero 4:4.3.1-1ubuntu2 va a ser instalado
       Depende: gcc (>= 4:4.3.3-1ubuntu1) pero 4:4.3.1-1ubuntu2 va a ser instalado
       Depende: g++-4.3 (>= 4.3.3-1) pero no va a instalarse
       Depende: gcc-4.3 (>= 4.3.3-1) pero 4.3.2-1ubuntu12 va a ser instalado

```

Sorry it's in Spanish, but I think most of you will understand what's going on... I don't. :(

---

### Post by whitethorn on 2009-04-20
Try this,

```
sudo apt-get install build-essential
```

It installs pretty everything you need to compile stuff with.  gcc, g++, cpp.  I'm guessing g++ needs some dependencies.

---

### Post by steve101101 on 2009-04-20
> **whitethorn said:**
> try this,

```
sudo apt-get install build-essential
```

it installs pretty everything you need to compile stuff with.  Gcc, g++, cpp.  I'm guessing g++ needs some dependencies.

+1

---

### Post by lobo-tuerto on 2009-04-20
Thank you guys, but I got this message instead:

```

  build-essential: Depende: g++ (>= 4:4.3.1) pero no va a instalarse
E: Paquetes rotos

```

Paquetes rotos = Broken packages

---

### Post by DGortze380 on 2009-04-20
> **whitethorn said:**
> Try this,

```
sudo apt-get install build-essential
```

It installs pretty everything you need to compile stuff with.  gcc, g++, cpp.  I'm guessing g++ needs some dependencies.

yup, build-essential is what you're looking for.

---

### Post by Dougie187 on 2009-04-20
try this.

```
sudo apt-get install -f
```

---

### Post by lobo-tuerto on 2009-04-20
Got same message:

```

~$ sudo apt-get install -f build-essential
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
No se pudieron instalar algunos paquetes. Esto puede significar que
usted pidió una situación imposible o, si está usando la distribución
inestable, que algunos paquetes necesarios no han sido creados o han
sido movidos fuera de Incoming.

Como sólo solicito una única operación, es extremadamente posible que el
paquete simplemente no sea instalable y debería de rellenar un informe de
error contra ese paquete.
La siguiente información puede ayudar a resolver la situación:

Los siguientes paquetes tienen dependencias incumplidas:
  build-essential: Depende: g++ (>= 4:4.3.1) pero no va a instalarse
E: Paquetes rotos


```

Maybe the admins are moving things around preparing for the new release?

---

### Post by Cypher on 2009-04-20
Nothing the admins do in preparation of Januty being released should mess up any of the previous repository, that'd be quite trauamatic to people who are happily using the old releases.

However, it does look like you're trying to pull different version of GCC/CPP/G++. Intrepid has GCC-4.3.1 and Januty has GCC-4.3.3. 

What are the contents of your /etc/apt/sources.list?

---

### Post by leandromartinez98 on 2009-04-20
sudo apt-get --reinstall -f g++ build-essentials

This will try to both reinstall these packages and solve package problems,
so it may help.

---

### Post by stchman on 2009-04-20
> **lobo-tuerto said:**
> Hi guys, I'm on Ubuntu 8.10 and I'm getting this message when doing a:

sudo apt-get install g++

```

g++: Depende: cpp (>= 4:4.3.3-1ubuntu1) pero 4:4.3.1-1ubuntu2 va a ser instalado
       Depende: gcc (>= 4:4.3.3-1ubuntu1) pero 4:4.3.1-1ubuntu2 va a ser instalado
       Depende: g++-4.3 (>= 4.3.3-1) pero no va a instalarse
       Depende: gcc-4.3 (>= 4.3.3-1) pero 4.3.2-1ubuntu12 va a ser instalado

```

Sorry it's in Spanish, but I think most of you will understand what's going on... I don't. :(

The packages gcc and g++ are installed by default, but the appropriate header files are not!!!!!  The package build-essential is what you need.

---

### Post by lobo-tuerto on 2009-04-20
Thank you but it seems that line has something wrong with it:

```

~$ sudo apt-get reinstall g++ build-essentials
E: Operación inválida: reinstall

```

Operación inválidad = Invalid operation
Tried to switch the -f around, but couldn't make it work.


@Cypher:
You are right, just checked out that file and this line was enabled:
```
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release Candidate i386 (20090414.2)]/ jaunty main restricted
```
While this one was commented:
```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
```

Thank you for the help you all! :)

---

### Post by Cypher on 2009-04-20
Hehe, bingo..glad you got it figured out.

---

### Post by stchman on 2009-04-20
> **lobo-tuerto said:**
> Thank you but it seems that line has something wrong with it:

```

~$ sudo apt-get reinstall g++ build-essentials
E: Operación inválida: reinstall

```

Operación inválidad = Invalid operation
Tried to switch the -f around, but couldn't make it work.


@Cypher:
You are right, just checked out that file and this line was enabled:
```
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release Candidate i386 (20090414.2)]/ jaunty main restricted
```
While this one was commented:
```
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
```

Thank you for the help you all! :)

The packages build-essential and gcc, g++ are in the Jaunty repos.

[http://packages.ubuntu.com/jaunty/build-essential](http://packages.ubuntu.com/jaunty/build-essential)
[http://packages.ubuntu.com/jaunty/gcc](http://packages.ubuntu.com/jaunty/gcc)
[http://packages.ubuntu.com/jaunty/g++](http://packages.ubuntu.com/jaunty/g++)

---

