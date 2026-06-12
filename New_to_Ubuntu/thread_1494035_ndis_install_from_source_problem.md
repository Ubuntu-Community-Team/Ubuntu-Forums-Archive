---
title: "ndis install from source problem"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by nibblet5109 on 2010-05-26
Howdy all,

I'm a new user to Ubuntu, and just loaded up the Lynx software on a Toshiba Satellite laptop that's about four years old.  I'm trying to figure out how to install the 3 ndis pieces from source, as nothing else I've found has worked.  Any help would be greatly appreciated.

The wireless card I'm trying to run is a Linksys WPC54G v1.0 (I know, its old).  I've managed the ndis install before, but I just reinstalled the ubuntu software, and can't find the code again.  I didn't have to do much - if I recall correctly it was about 3-5 command lines.  Thanks!

---

### Post by jerome1232 on 2010-05-26
From source? Or you just need the package from the repositories?

If you just wanted the package in the repositories

```
sudo apt-get install ndiswrapper
sudo ndiswrapper -i /path/to/your/inf\ file/here
sudo modprobe ndiswrapper

```

Then you need to add "ndiswrapper" to /etc/modules with out the quotes
```
gksu gedit /etc/modules
```

From source you probably just need to download the source extract it then

```
sudo apt-get build-dep ndiswrapper
cd /path/to/source/code
./configure
make
sudo make install

```

Then do the steps listed above minus the apt-get install line.

---

### Post by nibblet5109 on 2010-05-26
Honestly I don't know the proper terminology yet.  I'm gonna give that a go and see how it works - thanks for the help, and I'll post the result.

---

### Post by nibblet5109 on 2010-05-26
From the repository steps I keep getting the message E: Couldn't find package ndiswrapper

---

### Post by jerome1232 on 2010-05-26
my bad, do ndisgtk, that will even give you a gui to use under System-Administration-Windows Drivers I think it is called.

```
sudo apt-get install ndisgtk
```

---

### Post by nibblet5109 on 2010-05-26
So good news - I got the ndiswrapper installed, and even got my wireless card driver installed.  However, it's not seeing a network.  How would one proceed to find something? (And I know there is a network, b/c I'm on it right now with my 2nd cpu)

Thanks again

---

### Post by jerome1232 on 2010-05-26
32 bit or 64 bit intall?

if you don't know, this command will tell, i386, i486, i586, i686 = 32 bit, x86_64 = 64 bit.

```
uname -m
```

That driver for 32 bit windows or 64 bit windows? You need to have the same architecture of driver to match your install, ie 32 bit driver for 32 bit Ubuntu, 64 bit driver for 64 bit Ubuntu. Other than that I would try a different version of the driver (ie if your download is ver 5.04, try 4.86 etc...)

---

### Post by nibblet5109 on 2010-06-09
So, I found a way to cheat.  Its not nearly as satisfying as being able to do this from the command line, but it worked.  I simply opened the cd in the GUI, and searched NDIS.  Three boxes show up in the NDIS folder - they install in a specific order (they won't work unless the previous one is in place).  Then I clicked on system/administration/windows wireless at the bottom.  I directed the installer to the .inf file I needed, (in my case it was LSBCMNDS) and it installed properly.  I rebooted the cpu to finish the install and viola!!! I have wireless.  So... moral of the story - I cheated a wee bit, it worked, and I hope it saves someone else the three days it took me to figure this out.  And yes, I felt like a moron after the fact.  Many thanks to Jerome1232 for all the advice and assistance.

---

