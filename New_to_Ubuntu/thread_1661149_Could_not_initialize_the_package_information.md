---
title: "Could not initialize the package information"
date: 2011-01-06
forum: New to Ubuntu
---

### Post by dee_exlusive on 2011-01-06
Hello, please help me I'm having this problem "Could not initialize the package information" after installing wine, but it didn't become successful.. :( now i can't open my synaptic. It states like this:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'src' is not known on line 1 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list'

---

### Post by oldos2er on 2011-01-06
Can you run this command in a terminal, and post the output here? ```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
```

---

### Post by dee_exlusive on 2011-01-06
rutchell@rutchell-Satellite-L500:~$ cat /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main
rutchell@rutchell-Satellite-L500:~$

---

### Post by oldos2er on 2011-01-06
Open the file in gedit with root privileges: ```
gksu gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-maverick.list
```
Change the first line to 

deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main

Save and exit the file, run ```
sudo apt-get update
```

---

### Post by dee_exlusive on 2011-01-07
Hello --Ann

So helpful!

Thank you so much!!! I am now able to open my synaptic as well as my software center..

I love ubuntu10.10~

---

### Post by oldos2er on 2011-01-07
You're welcome. Glad it's working!

---

