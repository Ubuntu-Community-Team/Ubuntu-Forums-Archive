---
title: "Can't install build essential"
date: 2009-04-16
forum: New to Ubuntu
---

### Post by Captain_Glen on 2009-04-16
When I try to install build essential I get an error:

```
glen@glen-desktop:~$ sudo apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
E: Broken packages
glen@glen-desktop:~$ 

```

I have tried clicking Edit > Fix broken packages in synaptic package manager but it doesn't fix it.

---

### Post by nandemonai on 2009-04-16
Hmm odd. This is Intrepid yes?

Try and apt-get update then apt-get install build-essential.

build-essential will bring down the kernel headers regardless.

Otherwise perhaps try a different mirror? (Are you using an ISP mirror?)

---

### Post by Captain_Glen on 2009-04-16
Actually this is on my other ubuntu machine, which is running hardy heron.

---

### Post by Captain_Glen on 2009-04-16
I solved it!

I had the intrepid cd ticked as a repository under third party software in software sources.

---

