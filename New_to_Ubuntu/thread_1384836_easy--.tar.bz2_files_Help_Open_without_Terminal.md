---
title: "easy--.tar.bz2 files Help Open without Terminal"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by hollowtd on 2010-01-18
I can't get it to open in terminal, so what else can I do to open and install a newly downloaded tar.bz2 file? This has got to be easy...but I know me and can't figure it out.

---

### Post by cbabbage on 2010-01-18
Right click on the folder in Nautilus, and select the option which says Extract Here.

---

### Post by hollowtd on 2010-01-18
I got it to extract on the desktop. It's a driver for a ralink usb wifi adapter. What do I do now, there are all kinds of files in there? Im using karmic by the way.

---

### Post by hollowtd on 2010-01-18
Sorry I'm a newbie. Got about 10 min till my gf kicks me off. Anyone know what I do after I extract the .tar.bz2 file? Thanks

---

### Post by cbabbage on 2010-01-19
See if there is a README file amongst the files. It should tell you what to do.

---

### Post by sandyd on 2010-01-19
or an INSTALL file.
it usually is as simple (this is generic through!)
```

./configure
make
sudo make install
```
provided you have the propper dependencies of course.

---

### Post by PenguinInside on 2010-01-19
Why don't you go ahead and start up a new thread regarding the particular program you're installing?

Also, please mark this thread as SOLVED. Thanks.

---

### Post by hollowtd on 2010-01-19
I get into the directory, which is on my desktop and then try to do the ./configure and it doesn't work. I'm trying to get this driver to install but I can't seem t get past this error message. 

terry@terry-laptop:~/Desktop/RT2870_LinuxSTA_V2.3.0.0$ ./configure
bash: ./configure: No such file or directory
terry@terry-laptop:~/Desktop/RT2870_LinuxSTA_V2.3.0.0$ make
make -C tools
make[1]: Entering directory `/home/terry/Desktop/RT2870_LinuxSTA_V2.3.0.0/tools'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/terry/Desktop/RT2870_LinuxSTA_V2.3.0.0/tools'
make: *** [build_tools] Error 2
terry@terry-laptop:~/Desktop/RT2870_LinuxSTA_V2.3.0.0$ sudo make
[sudo] password for terry: 
make -C tools
make[1]: Entering directory `/home/terry/Desktop/RT2870_LinuxSTA_V2.3.0.0/tools'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/terry/Desktop/RT2870_LinuxSTA_V2.3.0.0/tools'
make: *** [build_tools] Error 2
terry@terry-laptop:~/Desktop/RT2870_LinuxSTA_V2.3.0.0$

---

### Post by steveneddy on 2010-01-19
OK - is this a Windows driver that you would like to use on your Ubuntu machine to get your wireless working?

Post the link where you got the file.

Explain exactly what you are trying to accomplish.

Why are you trying to install this driver?

I think we all need a few more details to completely resolve your issue.

---

### Post by hollowtd on 2010-01-19
> **steveneddy said:**
> OK - is this a Windows driver that you would like to use on your Ubuntu machine to get your wireless working?

Post the link where you got the file.

Explain exactly what you are trying to accomplish.

Why are you trying to install this driver?

I think we all need a few more details to completely resolve your issue.

This is a linux driver. 

I got the file from [http://www.opendrivers.com/company/2159/ralink-free-driver-download.html](http://www.opendrivers.com/company/2159/ralink-free-driver-download.html)

I'm trying to get my Ralink USB wireless adapter to work with ubuntu 9.10

I'm installing so that the Ralink USB adapter will work. It actually works and picks up the wifi signal but I can't get it to load the webpage. 

:D

---

### Post by 3rdalbum on 2010-01-19
> **hollowtd said:**
> This is a linux driver. 

I got the file from [http://www.opendrivers.com/company/2159/ralink-free-driver-download.html](http://www.opendrivers.com/company/2159/ralink-free-driver-download.html)

I'm trying to get my Ralink USB wireless adapter to work with ubuntu 9.10

I'm installing so that the Ralink USB adapter will work. It actually works and picks up the wifi signal but I can't get it to load the webpage. 

:D

If it can pick up the signal then you've got a driver already.

Can you:

```
ping 66.102.11.104
```

If you get the pings sent back to you ("64 bytes from syd01s01-in-f104.1e100.net" gets returned, or something similar) then you need to check your DNS settings. Right-click on the Network Manager applet and go to Edit Connections, choose your wireless connection and hit Edit, then go to IPv4 Settings. Change the method type to "Automatic (DHCP) Addresses Only" and put in the following for DNS:

208.67.220.220

Disconnect and reconnect and see how you go.

---

### Post by hollowtd on 2010-01-19
Give me a minute and I'll see if I can do this. Thanks

---

### Post by hollowtd on 2010-01-19
> **3rdalbum said:**
> If it can pick up the signal then you've got a driver already.

Can you:

```
ping 66.102.11.104
```

If you get the pings sent back to you ("64 bytes from syd01s01-in-f104.1e100.net" gets returned, or something similar) then you need to check your DNS settings. Right-click on the Network Manager applet and go to Edit Connections, choose your wireless connection and hit Edit, then go to IPv4 Settings. Change the method type to "Automatic (DHCP) Addresses Only" and put in the following for DNS:

208.67.220.220

Disconnect and reconnect and see how you go.

The terminal said exaclty as you said. I changed the IPv4 settings and it worked for about a minute, loaded the forum and google. Now, It's going slow and waiting or searching and won't load the webpage. Strange. Any more ideas as we are so close here. 

Cheers

---

### Post by hollowtd on 2010-01-19
I can even get on Google and do searches but when I click a link for a webpage, like NYtimes for example, it takes forever and won't load, but the Google search is quick. Makes me think that a "large" webpage won't load or somthing. It's working sometimes though.

---

### Post by hollowtd on 2010-01-19
It works for a bit and then doesn't load webpages. Any ideas? Cheers

---

