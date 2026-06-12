---
title: "Can not instal pidgin 2.6.2 in ubuntu 9.04"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by legolas_w on 2009-09-09
Hi
Thank you for reading my question
I am trying to install latest version of pidgin downloaded from [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin) in ubuntu 9.04 but I am getting the following error. Any clue what should I do?

Thanks.

```


sudo dpkg -i *.dev
dpkg: status database area is locked by another process
legolas@HAL10000:~$ sudo dpkg -i *.deb
dpkg: status database area is locked by another process
legolas@HAL10000:~$ sudo dpkg -i *.deb
(Reading database ... 229009 files and directories currently installed.)
Preparing to replace libpurple0 1:2.6.2-1~getdeb1 (using libpurple0_2.6.2-1~getdeb1_i386(2).deb) ...
Unpacking replacement libpurple0 ...
Selecting previously deselected package libpurple-bin.
Unpacking libpurple-bin (from libpurple-bin_2.6.2-1~getdeb1_all.deb) ...
Selecting previously deselected package pidgin.
Unpacking pidgin (from pidgin_2.6.2-1~getdeb1_i386.deb) ...
dpkg-deb: `pidgin-data_2.6.2-1~getdeb1_all.deb' is not a debian format archive
dpkg: error processing pidgin-data_2.6.2-1~getdeb1_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Setting up libpurple0 (1:2.6.2-1~getdeb1) ...

Setting up libpurple-bin (1:2.6.2-1~getdeb1) ...
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on pidgin-data (>= 1:2.6.2); however:
  Package pidgin-data is not installed.
 pidgin depends on pidgin-data (<< 1:2.6.2-z); however:
  Package pidgin-data is not installed.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 pidgin-data_2.6.2-1~getdeb1_all.deb
 pidgin



```

---

### Post by SpinningAround on 2009-09-09
I don't understand the error message but would it not be easier to add pidgin PPA, but you maybe already did know this, anyway here is the link 
[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)
general info
[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

---

### Post by nivl4 on 2009-09-18
use your package manager to change the repository to karmic, and then upgrade to pidgin 2.6.2. Once that's done change the repository back to jaunty. (make sure you don't upgrade anything other than those required for pidgin 2.6.2 to work.)

you can also change jaunty to karmic in your /etc/apt/sources.list
(just remember to change it back once the pidgin is upgraded.)

works for me, now gmail audio/video chat works.

---

### Post by Kronhjort on 2009-10-06
Hey
   
  First of all thank you for reading this tread.
   
  I am relatively new to ubuntu so don’t kill me for being stupid. 
  I am trying to upgrade pidgin 2.6.1 to 2.6.2 but I simply can’t figure out how. 
  My system is 9.04 
   
  I already tried many thinks but none of them work so fare.
   
  Installing via PPA [https://launchpad.net/~pidgin-developers/+archive/ppa]("https://launchpad.net/%7Epidgin-developers/+archive/ppa")


  After doing that the software should be available from synaptics package manager but I only find 2.6.1
   
  I downloaded many deferent deb’s and get all sorts of errors: Tube is broken, You are trying to install an old version, pidgin-data is not installed and so on.
   
  Can somebody give me an easy to use guide or just terminal lines that I can copy paste?  
   
  I’m very frustrated right now and hope that a friendly person will help me.

---

### Post by zeroseven0183 on 2009-10-06
Hi guys!

Here's how I installed Pidgin 2.6.2

1. removed the currently installed Pidgin from Add/Remove.../Synaptics

2. downloaded all .deb files from [http://www.getdeb.net](http://www.getdeb.net)
particularly at [http://www.getdeb.net/release/4743](http://www.getdeb.net/release/4743) (Link for Pidgin 2.6.2)

3. installed all the dependencies: **pidgin-data,** **libpurple**,** libpurple-bin**

4. installed [B]pidgin


[/B]Enjoy!

---

### Post by Milossh on 2009-10-06
> **zeroseven0183 said:**
> Hi guys!

Here's how I installed Pidgin 2.6.2

1. removed the currently installed Pidgin from Add/Remove.../Synaptics

2. downloaded all .deb files from [http://www.getdeb.net](http://www.getdeb.net)
particularly at [http://www.getdeb.net/release/4743](http://www.getdeb.net/release/4743) (Link for Pidgin 2.6.2)

3. installed all the dependencies: **pidgin-data,** **libpurple**,** libpurple-bin**

4. installed [B]pidgin


[/B]Enjoy!

You should get a medal for this! Thank you sire!

---

### Post by zeroseven0183 on 2009-10-06
> **Milossh said:**
> You should get a medal for this! Thank you sire!

flattered :oops:

Sure, you're welcome!

---

### Post by Kronhjort on 2009-10-06
Thank you!!! 

I had to install in this ordre to make it work: **libpurple**,** libpurple-bin, ****pidgin-data and finaly ** [B]pidgin

Now I just need to figur out how to video chat via google talk:)


[/B]

---

### Post by Kronhjort on 2009-10-07
Hmmm! I might need a little more help from you. After installing from the .deb above I do not know how to make Gtalk voice and video chat work. Normal Gtalk text chat work just fine. Is ther some plug-in I am missing or am I just plain stupid:confused:

---

