---
title: "Here is my database plan... any input?"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-08-13
Hello:

I plan to create a database program in ubuntu. I want to use FireBird, freepascal and lazarus.

Are there any known problems with the installation processes for these programs?

I ask this because I doubt that I will know how to resolve any problems. Then I will become frustrated and begin to doubt lnux and then go back to Windows, again.

Any input would be appreciated.

Rob.

---

### Post by lykeion on 2010-08-13
Maybe I am not the right person to answer this, since I haven't coded in Pascal and try to do my best to avoid databases ;-)

Anyway, the installation should be straightforward since all the packages you mention is in the Ubuntu repository:
```
sudo apt-get install fpc fpc-source fp-docs lazarus firebird2.1-classic
```

Some links of interest:

Firebird Documentation
[http://www.firebirdsql.org/index.php?op=doc](http://www.firebirdsql.org/index.php?op=doc)

Pascal Game Development Forum: Lazarus and Ubuntu
[http://www.pascalgamedevelopment.com/forum/index.php?topic=5772.0](http://www.pascalgamedevelopment.com/forum/index.php?topic=5772.0)

Free Pascal Interface to Interbase/Firebird
[http://www.freepascal.org/packages/ibase.html](http://www.freepascal.org/packages/ibase.html)

Hope this helps...

---

### Post by Robert.Thompson on 2010-08-13
Thanks!

I copied the code to the terminal prompt and pressed enter.

Things began to install but then the process seemed to stall. I wainted about 20 minutes and tried to close the terminal. It said that it was still doing something so I waited another 20 minutes and then closed it anyway. Here is what it was doing when I terminated:
<snip>


Setting up firebird2.1-common-doc (2.1.3.18185-0.ds1-6build1) ...
Setting up firebird2.1-common (2.1.3.18185-0.ds1-6build1) ...
Setting up firebird2.1-server-common (2.1.3.18185-0.ds1-6build1) ...
adduser: Warning: The home directory `/var/lib/firebird' does not belong to the user you are currently creating.

Setting up libfbembed2.1 (2.1.3.18185-0.ds1-6build1) ...

Setting up openbsd-inetd (0.20080125-4ubuntu2) ...
 * Stopping internet superserver inetd       ############################[ OK ] 
 * Not starting internet superserver: no services enabled

Setting up firebird2.1-classic (2.1.3.18185-0.ds1-6build1) ...
Created default security.fdb
 * Preparing /var/run/firebird/2.1...       #############################[ OK ] 


<snip>


So, how do I know if Firebird was installed correctly or at all?

Lazarus appears in a menu.

I don't see anything about freepascal or Firebird in any menu.

Thanks for any advice,

Rob.

---

### Post by lykeion on 2010-08-14
That doesn't sound like a smooth installation of freebird.
After you've successfully installed firebird, you'd see something like this in the terminal:

Starting Firebird server: server has been successfully started

My advice is that you should start Synaptic and check for broken packages. 
If there are any broken you can try to fix them with Edit > Fix broken packages 

And apparently you need to configure the package after installation:```
sudo dpkg-reconfigure firebird2.1-classic
```

But like I mentioned before I've no experience with this, so the best I can do is give you links where you could get the info you're after:

Ubuntu Documentation: FireBird2.1
**_[https://help.ubuntu.com/community/Firebird2.1](https://help.ubuntu.com/community/Firebird2.1)_**

Setting up Firebird on Ubuntu Linux
**_[http://www.firebirdsql.org/manual/ubusetup.html](http://www.firebirdsql.org/manual/ubusetup.html)_**
(at the moment firebirdsql.org seem to be unresponsive, 
maybe try google "Setting up Firebird on Ubuntu Linux" and select the cached).

[edit]
About freepascal, you've installed the compiler (fpc), source and docs.
The compiler is used from the command-line (try: man fpc) 
or used in an IDE like Lazarus

---

### Post by Robert.Thompson on 2010-08-27
Thanks for the links - I re-installed and all is well!

---

### Post by mariuz on 2010-12-09
you can use the full RAD ide to build gui applications in ubuntu 

I have wrote a miniguide :Lazarus + Firebird 

[http://mapopa.blogspot.com/2010/04/using-lazarus-ide-with-firebird-in.html](http://mapopa.blogspot.com/2010/04/using-lazarus-ide-with-firebird-in.html)

---

