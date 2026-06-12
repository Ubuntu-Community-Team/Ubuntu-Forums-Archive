---
title: "Install Gyachi"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by nimishalex on 2011-01-01
How to install Gyachi in Ubuntu 10.04.. I tried 

[COLOR=Black]sudo add-apt-repository ppa:baudm
[/COLOR]  [COLOR=Black]sudo apt-get update
[/COLOR]  [COLOR=Black]sudo apt-get install gyachi[/COLOR]


[COLOR=#008000][COLOR=Black]and  [/COLOR]
[/COLOR]
deb [http://ppa.launchpad.net/baudm/ppa/ubuntu](http://ppa.launchpad.net/baudm/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/baudm/ppa/ubuntu](http://ppa.launchpad.net/baudm/ppa/ubuntu) lucid main 

But these both are not working for me. Plz help me to find a solution

---

### Post by gandaran on 2011-01-01
this is the correct PPA gyachi
[https://launchpad.net/~loell/+archive/ppa](https://launchpad.net/~loell/+archive/ppa)
```
sudo add-apt-repository ppa:loell/ppa
```

---

### Post by nimishalex on 2011-01-01
> **gandaran said:**
> this is the correct PPA gyachi
[https://launchpad.net/~loell/+archive/ppa]("https://launchpad.net/%7Eloell/+archive/ppa")
```
sudo add-apt-repository ppa:loell/ppa
```

Hi, this ppa is also not working for me ..

```
sudo add-apt-repository ppa:loell/ppa
sudo apt-get update
sudo apt-get install gyachi

```[
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gyachi


. Plz help to find a solution.. thanks ..

---

### Post by gandaran on 2011-01-01
what version of ubuntu do you have installed?

update
did you get any errors running 
> sudo apt-get update
I did and looks like that server is down for the moment so try maybe tomorrow

---

### Post by nimishalex on 2011-01-01
Ubuntu 10.04 ... I didnt get any errors ..   , i will try it tomorrow.
thanks............

---

### Post by loell on 2011-01-01
try

[https://launchpad.net/~adilson/+archive/experimental](https://launchpad.net/~adilson/+archive/experimental)

---

### Post by nimishalex on 2011-01-02
Thanks..........Its works......................

---

### Post by Ravenshade on 2011-01-02
that was the most doubt ridden thanks I've ever seen on these forums. Make sure to mark the topic as solved once those doubts have been erased.

---

### Post by nimishalex on 2011-01-02
[COLOR=Black]Hi ravenshade 

Where i can find the sloved prefix.I just add a tag "solved" into this.. I dont know it's the exact way of doing this.Thanks
[/COLOR]

---

### Post by Czvp on 2011-02-04
Originally Posted by **gigelb** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9952238#post9952238") 				
 				[I]Found a solution that works for me on Ubuntu 10.10

type in terminal

sudo add-apt-repository ppa:adilson/experimental
sudo apt-get update
sudo apt-get install gyachi

Hope it works for you.[/I]



that worked for me man. check it out
voice chat doesnt though, im looking for a solution now.

---

### Post by finisdiem on 2011-02-23
> **Czvp said:**
> Originally Posted by **gigelb** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9952238#post9952238") 				
 				[I]Found a solution that works for me on Ubuntu 10.10

type in terminal

sudo add-apt-repository ppa:adilson/experimental
sudo apt-get update
sudo apt-get install gyachi

Hope it works for you.[/I]



that worked for me man. check it out
voice chat doesnt though, im looking for a solution now.

that code worked for me too. but i also cant use voice chat. when i click the button it say "voice chat enabled" but cant get passed that.

did they stop working on this package?

---

