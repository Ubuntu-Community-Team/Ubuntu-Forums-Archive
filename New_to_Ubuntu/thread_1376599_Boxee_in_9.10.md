---
title: "Boxee in 9.10???"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by GonZo1323 on 2010-01-09
I can't seem to get it working any advice?
It installed fine just everytime i try to start it loads and then never opens.
Any Ideas?

---

### Post by Roger E Critchlow Jr on 2010-01-09
> **GonZo1323 said:**
> I can't seem to get it working any advice?
It installed fine just everytime i try to start it loads and then never opens.
Any Ideas?

I just tried installing boxee-0.9.20.10263.i486.deb in a 64bit system.  After using getlibs to install the needed 32bit libraries, I get the following error when launching:
[INDENT]rec@elf11:~$ /opt/boxee/Boxee
10/01/10 03:18:38#DEBUG#bxbgprocess.cpp:180(Start)#bg process initialized. [m_lazy=1] so m_maxNumOfWorkingThreads was set to [2]
10/01/10 03:18:38#DEBUG#bxbgprocess.cpp:180(Start)#bg process initialized. [m_lazy=1] so m_maxNumOfWorkingThreads was set to [1]
10/01/10 03:18:38#DEBUG#bxcurl.cpp:93(Initialize)#curl initialized. version <7.19.5>

Running Boxee test...
And the log goes to... /tmp/rec-boxee.log
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  21
  Current serial number in output stream:  21
Boxee: asked to stop
Boxee: already stopped[/INDENT]
You might try starting from a command line and seeing if you get a similar error. Don't know exactly what to do about it.

-- rec --

---

### Post by tom.swartz07 on 2010-01-10
> **GonZo1323 said:**
> I can't seem to get it working any advice?
It installed fine just everytime i try to start it loads and then never opens.
Any Ideas?

I might be mistaken, but the current version of Boxee doesnt work in 9.10.

I was just reading a week or two ago on Lifehacker about how to set it up on a 9.04 machine.

If this is the case, The new version should fix problems- perhaps you could get a beta build and use that?

---

### Post by Howie Spitz on 2010-01-10
I'm using Boxee with 9.10 . Once I created an account it just works. Boxee version 0.9.14.6992.
[http://techdrivein.blogspot.com/2009/12/install-boxee-in-ubuntu-910-karmic.html]("http://techdrivein.blogspot.com/2009/12/install-boxee-in-ubuntu-910-karmic.html")
This worked for me , whether it's the right thing to do, can't say.

---

