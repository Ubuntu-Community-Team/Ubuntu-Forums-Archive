---
title: "Update Manager Error"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by twinaxel on 2009-09-09
Hi can anyone kindly help with this error message.


An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Type ‘sudo’ is not known on line 1 in source list /etc/apt/sources.list.d/abiword-stable.list, E:The list of sources could not be read.'

                         Thanks

---

### Post by Perfect Storm on 2009-09-09
Seems something that should not be in the sourcelist.

```
cat /etc/apt/sources.list.d
```

---

### Post by twinaxel on 2009-09-09
Hi tried that I get david@david-desktop:~$ cat /etc/apt/sources.list.d
cat: /etc/apt/sources.list.d: Is a directory
david@david-desktop:~$ cat /etc/apt/sources.list.d

---

### Post by Perfect Storm on 2009-09-09
sorry, my mistake;

```
cat /etc/apt/sources.list.d/abiword-stable.list
```

---

### Post by twinaxel on 2009-09-09
This is the output 
david@david-desktop:~$ cat /etc/apt/sources.list.d/abiword-stable.list
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2382D57E

echo "deb [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu)

sudo tee /etc/apt/sources.list.d/abiword-stable.list
david@david-desktop:~$

---

### Post by Excedio on 2009-09-09
It looks like the line
> echo "deb [[COLOR=#000000][URL="http://ppa.launchpad.net/abiword-stable/ppa/ubuntu"]http://ppa.launchpad.net/abiword-stable/ppa/ubuntu[/COLOR]]("http://ppa.launchpad.net/abiword-stable/ppa/ubuntu")[/URL]
Is missing something. Should it also have the name of the Ubuntu distro in it?

---

### Post by Perfect Storm on 2009-09-09
I guess it this guide you used; [http://www.abisource.com/wiki/Install_on_Ubuntu](http://www.abisource.com/wiki/Install_on_Ubuntu)

I can't get to working atm. (timeout). But it shouldn't look like that.

You can either remove it completly or wait.

---

### Post by Excedio on 2009-09-09
You could use [this]("http://www.abisource.com/wiki/Install_on_Ubuntu"). Seems pretty simple and straight forward to me.

---

### Post by Perfect Storm on 2009-09-09
Yep, but it won't connect (may be temporary). So I can't test it.

---

### Post by mc4man on 2009-09-09
the line in /etc/apt/sources.list.d/abiword-stable.list should look like this

```
deb [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu) hardy main
```
or 
```
deb [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu) intrepid main
```
or 
```
deb [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu) jaunty main

```
not
[COLOR="Red"]echo[/COLOR] "deb [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu)

lose the echo " and add to the end <release> main

---

### Post by NESFreak on 2009-09-09
> **mc4man said:**
> the line in /etc/apt/sources.list.d/abiword-stable.list should look like this

```
deb [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu) hardy main
```
or 
```
deb [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu) intrepid main
```
or 
```
deb [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu) jaunty main

```
not
[COLOR="Red"]echo[/COLOR] "deb [http://ppa.launchpad.net/abiword-stable/ppa/ubuntu](http://ppa.launchpad.net/abiword-stable/ppa/ubuntu)

lose the echo " and add to the end <release> main

indeed, however don't forget to start up the commandline and run:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2382D57E
```
so you wont get any key errors

---

### Post by twinaxel on 2009-09-10
Problem solved thank you

---

