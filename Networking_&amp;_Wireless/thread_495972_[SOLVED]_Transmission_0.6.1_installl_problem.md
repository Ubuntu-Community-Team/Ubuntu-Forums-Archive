---
title: "[SOLVED] Transmission 0.6.1 installl problem"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by neburzaragoza on 2007-07-08
Hi,


I've downloaded *transmission 0.6.1* for my *dapper drake* from the official [site]("http://download.m0k.org/transmission/files/"). Now I'm trying to install it, but without the expected succes.

that's what i've done:
- I have decompress the .tar.gz
- cd in the new folder
- ```
xx@xx-laptop:~/Desktop/Transmission-0.6.1$ ./configure
System:  Linux
OpenSSL: missing, using built-in SHA1 implementation
GTK+:    no

Now use GNU make to build Transmission.
It may be called 'make' or 'gmake' depending on your system.

```

- ```
xx@xx-laptop:~/Desktop/Transmission-0.6.1$ make
Checking SVN revision...
* Building libtransmission
Checking dependencies...
Cc transmission.o
Cc bencode.o
Cc net.o
Cc tracker.o
Cc peer.o
Cc inout.o
Cc metainfo.o
Cc sha1.o
Cc utils.o
Cc fdlimit.o
Cc clients.o
Cc completion.o
Cc platform.o
Cc ratecontrol.o
Cc choking.o
Library libtransmission.a
* Building Transmission CLI client
Checking dependencies...
Cc transmissioncli.o
Link transmissioncli
  
```

- then to meake sure I did it again with sudo and install as following:
```

xx@xx-laptop:~/Desktop/Transmission-0.6.1$ sudo make install
Checking SVN revision...
* Building libtransmission
make[2]: `libtransmission.a' is updated.
* Building Transmission CLI client
make[2]: `transmissioncli' is updated.
* Installing Transmission CLI client
Install transmissioncli
Install transmissioncli.1

```

*****

now the problem is that my transmission-gtk does not start, apparently, I've only installed the transmissioncli, wich is actually working.

```

xx@xx-laptop:~/Desktop/Transmission-0.6.1$ transmission-gtk
bash: transmission-gtk: not found

```

in my *applications -> internet*  I don't have any Transmission program.

any idea or suggestions?

Thank for your help.

---

### Post by taurus on 2007-07-08
It says from the first message that you don't have GTK+ library on your machine so it will only build a terminal base.  Therefore, you can run it as

```
transmission filename.torrent
```
If you want to GUI, then you need to start up synaptic and install libgtk+-dev package first before you build transmission again.

---

### Post by neburzaragoza on 2007-07-08
Hello and thank you for your quick answer,

I actually cannot start my .torrent as you said.

```
xx@xx-laptop:~/Desktop/torrents$ transmission John\ Scofield\ -\ Hand\ Jive\ \[1994\]\ -_mininova.org_-.torrent
bash: transmission: orden no encontrada

``` 

and the last thing:

what I want to try install what you told me, but you sais it'd be better before I build it again, does it mean I need to remove what i've installed -> installe the new lib -> reinstall tranmission.
and if yes. How do I remove waht i've installed?

thank you for your patience, these are myabe nexbie questions xD

---

### Post by neburzaragoza on 2007-07-08
it seems that it works now.

I've installed some libgtk+ and its dependences and then I've tried again the 
- ./configure
- make
- sudo make install

and now in my shell I can luch transmission with:
- transmission-gtk

but I don't have yet any transmission in my applications -> internet, is this normal?

thanks so much for your advices *Taurus*

---

### Post by taurus on 2007-07-08
Well, you can always create a shortcut or an icon on the top panel so all you need is to double-click it to run it.

---

