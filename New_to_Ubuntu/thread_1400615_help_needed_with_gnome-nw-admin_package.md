---
title: "help needed with gnome-n/w-admin package"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by aneesha on 2010-02-07
i am new to the forum .. and started using ubuntu only a cpl of weeks ago..i hv ubuntu 9.04 installed .. i need help with configuring network connection.i installed the gnome-network-admin package .. i am not sure about its dependencies .. everytime i find and install a dependency they ask for a new one .. can any1 plz tell me which all dependencies i'll need .. the same problem is with compizconfig-settings-manager package.

---

### Post by ks07 on 2010-02-07
How are you trying to install gnome-network-admin?
If you install with synaptic or apt-get, the dependencies should be solved for you. Try:
```
sudo apt-get install gnome-network-admin
``` on a command line.

If you really want a .deb or just the dependency list, [look here]("http://packages.ubuntu.com/jaunty/gnome-network-admin").

---

### Post by aneesha on 2010-02-07
i tried that ... but it shows "Couldn't find gnome-network-admin package" .. i have the package file in my home folder ..

---

### Post by ks07 on 2010-02-07
Go to System>Administration>Software sources and make sure on the 'Ubuntu Software' tab that the universe repo is ticked (enabled). Then re-try the install command.

---

### Post by oldos2er on 2010-02-07
> **aneesha said:**
> i tried that ... but it shows "Couldn't find gnome-network-admin package" .. i have the package file in my home folder ..

Double-click the package.

---

### Post by aneesha on 2010-02-08
> **oldos2er said:**
> Double-click the package.


i did that already .. they are asking for dependencies

---

### Post by ks07 on 2010-02-08
Could you copy and paste/screenshot the error message you're getting. It may help us find the source of the problem.

---

### Post by aneesha on 2010-02-08
> **ks07 said:**
> Could you copy and paste/screenshot the error message you're getting. It may help us find the source of the problem.

this is what i get now when i run the sudo command..

"Reading package lists... Done

Building dependency tree 

Reading state information... Done

Package gnome-network-admin is not available, but is referred to by another package.

This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package gnome-network-admin has no installation candidate"

---

### Post by ks07 on 2010-02-08
Did you check you have the universe repo enabled? Paste the output of ```
cat /etc/apt/sources.list
``` so we can see. If it's enabled, the package should have been found...

---

### Post by aneesha on 2010-02-08
> **ks07 said:**
> Did you check you have the universe repo enabled? Paste the output of ```
cat /etc/apt/sources.list
``` so we can see. If it's enabled, the package should have been found...

universe repo is enabled .. i checked the s/w sources

---

### Post by ks07 on 2010-02-08
Strange... Ok, let's see if apt can find the package a different way. Run:
```
sudo apt-get update

```
Then run
```
apt-cache search gnome-network-admin
``` and see if it finds the package now.

If it still doesnt find the package, you'll have to install it manually by downloading it from the link I posted before (unless you already have a copy, ofc). Gdebi should automatically download any dependencies.

---

### Post by oldos2er on 2010-02-08
> **aneesha said:**
> i did that already .. they are asking for dependencies

gdebi (the installer that opens when you double-click a package) should be able to install any needed dependencies. If it's not doing that, can you please post any error messages it shows?

---

### Post by aneesha on 2010-02-09
> **ks07 said:**
> Strange... Ok, let's see if apt can find the package a different way. Run:
```
sudo apt-get update

```Then run
```
apt-cache search gnome-network-admin
``` and see if it finds the package now.

If it still doesnt find the package, you'll have to install it manually by downloading it from the link I posted before (unless you already have a copy, ofc). Gdebi should automatically download any dependencies.


i tried both codes but no use .. i tried installing with gdebi .. but it doesnt download dependencies automatically .. it shows error messages ..

---

### Post by aneesha on 2010-02-09
this is the error msg that i get when i try to install using gdebi

"Error: Dependency is not satisfiable: libpolkit-dbus2 (>= 0.7)"

---

### Post by ks07 on 2010-02-09
> **aneesha said:**
> this is the error msg that i get when i try to install using gdebi

"Error: Dependency is not satisfiable: libpolkit-dbus2 (>= 0.7)"
Haven't got that exact package in the repositories, but have similar. Where did you download the .deb from? It's possible that package was built for another version of ubuntu or debian, where that package exists.

---

### Post by achase79 on 2010-02-09
If you are using a local repository server, you may try selecting a different server in software sources.

---

### Post by aneesha on 2010-02-11
> **ks07 said:**
> Haven't got that exact package in the repositories, but have similar. Where did you download the .deb from? It's possible that package was built for another version of ubuntu or debian, where that package exists.

i downloaded the .deb file from the link you gave me ..from NA server

---

### Post by ks07 on 2010-02-11
Well... Honestly this now has me stumped. I suggest you try changing to a different apt server using software sources like achase suggested. Other than that, I'm out of ideas. :(

---

### Post by aneesha on 2010-02-13
> **ks07 said:**
> Well... Honestly this now has me stumped. I suggest you try changing to a different apt server using software sources like achase suggested. Other than that, I'm out of ideas. :(

i tried downloading the same stuff from other servers but no use .. thanx anywas for ur patience and help :)

---

