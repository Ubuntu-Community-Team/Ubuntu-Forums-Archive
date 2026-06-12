---
title: "Unison version numbers Windows and Ubuntu"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by exup1000 on 2010-03-09
Hi

I am trying to use Unison between Ubuntu and Windows XP. I understand that the version numbers need to be the same.

Except I can only see version 2.27.57 for Ubuntu within the application manager and for windows the only one that will execute properly is 2.32.94. I have tried other versions but they come up with the error, "This application has failed to start because  the application configuration is incorrect. Please try reinstalling the application."

When I run the gui version it starts the gui and I can enter in values, then enter in my password within the command prompt to connect to the sever  but then it comes up with 
[INDENT]Received unexpected header from the server:
 expected "Unison 2.32\n" but received "Unison 2.27\n\000\000\000\000", 
which differs at "Unison 2.2".
This can happen because you have different versions of Unison
installed on the client and server machines, or because
your connection is failing and somebody is printing an error
message, or because your remote login shell is printing
something itself before starting Unison.[/INDENT]

So assume its the miss match, but I am stuck trying to find a version of unison that matches the windows one. I can find a tar.gz file but reading the content of install readme file show how to install it for Linux (except for a complex build your own application process)?

PS I have installed openssh on the windows box and it looks like it can succesfully connect ok.

Any advice?

Cheers

---

### Post by thatguruguy on 2010-03-09
My advice is to go to [http://www.seas.upenn.edu/~bcpierce/unison//download/releases/stable/]("http://www.seas.upenn.edu/%7Ebcpierce/unison//download/releases/stable/") and grab the source code for the current stable program. Then, you can compile it yourself for both your ubuntu and windows boxes.  They provide fairly thorough documentation to help with compiling the program.

Good luck!

---

### Post by exup1000 on 2010-03-09
Hi, thanks, I had been following that guide but found it a bit unclear in terms of the install process for Linux, it looks like I will have to build the software using OCAML. (Which for a neubie is a steep learning curve)

I was surprised to find that there are no pre-built versions of Unison that you could install (with out having to build them) seeing as its relatively popular. (Except for the one version in Synaptic)

Is it common to have to build software so that it can be installed on linux systems.

cheers

---

### Post by xtho on 2010-04-18
If you're willing to take risks, you could also add a personal build from launchpad, e.g.:
[https://launchpad.net/~abelcheung/+ppa-packages]("https://launchpad.net/%7Eabelcheung/+ppa-packages")

From [http://wiki.ubuntuusers.de/Launchpad/PPA](http://wiki.ubuntuusers.de/Launchpad/PPA) (in German):
sudo add-apt-repository ppa:user/ppa-name[FONT=Verdana]

[/FONT]

---

### Post by clive littlewood on 2010-04-18
Hi

```
Is it common to have to build software so that it can be installed on linux systems.
```


No

99% of add software is available through the software center or synaptic.

Clive

---

