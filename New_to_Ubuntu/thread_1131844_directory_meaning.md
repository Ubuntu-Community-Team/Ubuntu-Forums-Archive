---
title: "directory meaning"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by new_kubunto on 2009-04-21
Hello, I'm really new on Linux like environnement and I'm tring to figure aout the basic concept of the File directory environnement and user roles.
Files and directory:
1) etc
on the root directory I find /etc directory, what can we say about this directory, since now I used it for networking configuration..
...
2) Program file
When I install a application, where should I install it, can I find a realtion with window program file directory
....
3) Home & usr
on home directory I find peronal folder like Music, Desktop etc... what do I find on usr, is this directory related to users ?

---

### Post by 3rdalbum on 2009-04-21
> **new_kubunto said:**
> Hello, I'm really new on Linux like environnement and I'm tring to figure aout the basic concept of the File directory environnement and user roles.
Files and directory:
1) etc
on the root directory I find /etc directory, what can we say about this directory, since now I used it for networking configuration..


It's mainly for configuration files that don't belong anywhere else.

> 2) Program file
When I install a application, where should I install it, can I find a realtion with window program file directory

No, there's no relation to Program Files on Windows. Nobody has ever needed to worry about where to install a program on Linux - they ALWAYS get installed into an appropriate location where they can be run by typing the name of the program.

If you must know, usually they get installed into /usr/bin. Just the executable. You'll never need to know this though.

> 3) Home & usr
on home directory I find peronal folder like Music, Desktop etc... what do I find on usr, is this directory related to users ?

/usr contains software and resources (fonts, themes, documentation and more) that will be used by the users of the computer, rather than the administrator. This is only a general guideline, not a rule - as such, administrators can do what they like with /usr and users are not limited to software in /usr/bin or /usr/local/bin.

---

### Post by nandemonai on 2009-04-21
> **new_kubunto said:**
> Hello, I'm really new on Linux like environnement and I'm tring to figure aout the basic concept of the File directory environnement and user roles.
Files and directory:
1) etc
on the root directory I find /etc directory, what can we say about this directory, since now I used it for networking configuration..
...
2) Program file
When I install a application, where should I install it, can I find a realtion with window program file directory
....
3) Home & usr
on home directory I find peronal folder like Music, Desktop etc... what do I find on usr, is this directory related to users ?

Hello and welcome :)

I'll make this quick cause I'm having a late dinner but..

1. /etc is generally where configuration files are stored

2. A little trickier. /bin is essential binaries /usr/bin most user installed applications, /sbin system binaries /usr/sbin user installed system binaries.

3. /home is where user files are stores (also specific user configurations as .application-name files) /usr is for general user programs, libraries and documentation.

A great doc on the subject can be found here: [http://tldp.org/LDP/intro-linux/html/sect_03_01.html](http://tldp.org/LDP/intro-linux/html/sect_03_01.html)

Hope that helps explain things.

---

### Post by gn2 on 2009-04-21
[Use Synaptic to install]("https://help.ubuntu.com/community/SynapticHowto") and you won't need to think about where it installs to ;)
Or [Adept]("https://wiki.ubuntu.com/AdeptHowto") if it's Kubuntu.

[File structure explained]("http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html")

[Diagram of file structure]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html")

Hope that's all useful.

---

### Post by nandemonai on 2009-04-21
> **gn2 said:**
> [Use Synaptic to install]("https://help.ubuntu.com/community/SynapticHowto") and you won't need to think about where it installs to ;)
Or [Adept]("https://wiki.ubuntu.com/AdeptHowto") if it's Kubuntu.

[File structure explained]("http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html")

[Diagram of file structure]("http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html")

Hope that's all useful.

Need to know? No. Wise to know? Yes.

---

### Post by ibuclaw on 2009-04-21
> **new_kubunto said:**
> 
2) Program file
When I install a application, where should I install it, can I find a realtion with window program file directory
....

When you install the application, you shouldn't be asked the location of where you want to install it if you are installing software through the Add/Remove programs utility.

Unless of course you are trying to install something else...?

Regards
Iain

---

### Post by netJackDaw on 2009-04-21
Check out this site on preffered ways of installing applications i Ubuntu. It can be confusing for new users but it is a revelation when you get the hang of it...

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by gn2 on 2009-04-21
> **nandemonai said:**
> Need to know? No. Wise to know? Yes.

Depends on one's understanding of wisdom.
Is it wise to fill your brain with stuff you don't need to know?

---

