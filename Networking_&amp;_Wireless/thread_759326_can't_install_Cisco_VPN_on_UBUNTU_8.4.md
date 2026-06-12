---
title: "can't install Cisco VPN on UBUNTU 8.4"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by Jyves on 2008-04-19
HI..there

I'm a newbie to Ubuntu, I love it....But I have to use VPN for my work and i can't seem to get it to work......I have been reading all the forums about it......none worked out ..
Need help .
Here's the message I'm having :
jay@GP-Linux:~/Documents/vpnclient$ make 
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/jay/Documents/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/jay/Documents/vpnclient/linuxcniapi.o
/home/jay/Documents/vpnclient/linuxcniapi.c:589: fatal error: opening dependency file /home/jay/Documents/vpnclient/.linuxcniapi.o.d: Permission denied
compilation terminated.
make[2]: *** [/home/jay/Documents/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/jay/Documents/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
jay@GP-Linux:~/Documents/vpnclient$ sudo make 
[sudo] password for jay: 
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:107:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:108:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:109:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:110:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:111:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:112:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:113:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:114:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from scripts/basic/fixdep.c:115:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:116:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:117:23: error: arpa/inet.h: No such file or directory
scripts/basic/fixdep.c: In function &#8216;usage&#8217;:
scripts/basic/fixdep.c:131: warning: implicit declaration of function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:131: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:131: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:131: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:131: error: for each function it appears in.)
scripts/basic/fixdep.c:132: warning: implicit declaration of function &#8216;exit&#8217;
scripts/basic/fixdep.c:132: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c: In function &#8216;print_cmdline&#8217;:
scripts/basic/fixdep.c:140: warning: implicit declaration of function &#8216;printf&#8217;
scripts/basic/fixdep.c:140: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:143: error: &#8216;NULL&#8217; undeclared here (not in a function)
scripts/basic/fixdep.c: In function &#8216;grow_config&#8217;:
scripts/basic/fixdep.c:156: warning: implicit declaration of function &#8216;realloc&#8217;
scripts/basic/fixdep.c:156: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:158: warning: implicit declaration of function &#8216;perror&#8217;
scripts/basic/fixdep.c:158: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c: In function &#8216;is_defined_config&#8217;:
scripts/basic/fixdep.c:174: warning: implicit declaration of function &#8216;memcmp&#8217;
scripts/basic/fixdep.c: In function &#8216;define_config&#8217;:
scripts/basic/fixdep.c:187: warning: implicit declaration of function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:187: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c: In function &#8216;use_config&#8217;:
scripts/basic/fixdep.c:206: error: &#8216;PATH_MAX&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:214: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:220: warning: implicit declaration of function &#8216;tolower&#8217;
scripts/basic/fixdep.c:222: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c:206: warning: unused variable &#8216;s&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:225: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
scripts/basic/fixdep.c: In function &#8216;parse_config_file&#8217;:
scripts/basic/fixdep.c:227: error: &#8216;len&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:233: warning: implicit declaration of function &#8216;ntohl&#8217;
scripts/basic/fixdep.c:244: warning: implicit declaration of function &#8216;isalnum&#8217;
scripts/basic/fixdep.c: In function &#8216;strrcmp&#8217;:
scripts/basic/fixdep.c:261: warning: implicit declaration of function &#8216;strlen&#8217;
scripts/basic/fixdep.c:261: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
scripts/basic/fixdep.c: In function &#8216;do_config_file&#8217;:
scripts/basic/fixdep.c:272: error: storage size of &#8216;st&#8217; isn&#8217;t known
scripts/basic/fixdep.c:276: warning: implicit declaration of function &#8216;open&#8217;
scripts/basic/fixdep.c:276: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:278: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:278: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:280: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:282: warning: implicit declaration of function &#8216;fstat&#8217;
scripts/basic/fixdep.c:284: warning: implicit declaration of function &#8216;close&#8217;
scripts/basic/fixdep.c:287: warning: implicit declaration of function &#8216;mmap&#8217;
scripts/basic/fixdep.c:287: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:287: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:287: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:294: error: too many arguments to function &#8216;parse_config_file&#8217;
scripts/basic/fixdep.c:296: warning: implicit declaration of function &#8216;munmap&#8217;
scripts/basic/fixdep.c:272: warning: unused variable &#8216;st&#8217;
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:301: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;size_t&#8217;
scripts/basic/fixdep.c: In function &#8216;parse_dep_file&#8217;:
scripts/basic/fixdep.c:304: error: &#8216;len&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:306: error: &#8216;PATH_MAX&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:308: warning: implicit declaration of function &#8216;strchr&#8217;
scripts/basic/fixdep.c:308: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
scripts/basic/fixdep.c:310: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:310: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:311: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:313: warning: incompatible implicit declaration of built-in function &#8216;memcpy&#8217;
scripts/basic/fixdep.c:314: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
scripts/basic/fixdep.c:306: warning: unused variable &#8216;s&#8217;
scripts/basic/fixdep.c: In function &#8216;print_deps&#8217;:
scripts/basic/fixdep.c:343: error: storage size of &#8216;st&#8217; isn&#8217;t known
scripts/basic/fixdep.c:347: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:349: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:349: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:351: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
scripts/basic/fixdep.c:355: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:359: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:359: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:359: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:366: error: too many arguments to function &#8216;parse_dep_file&#8217;
scripts/basic/fixdep.c:343: warning: unused variable &#8216;st&#8217;
scripts/basic/fixdep.c: In function &#8216;traps&#8217;:
scripts/basic/fixdep.c:378: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
scripts/basic/fixdep.c:378: error: &#8216;stderr&#8217; undeclared (first use in this function)
scripts/basic/fixdep.c:380: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
make[2]: *** [scripts/basic/fixdep] Error 1
make[1]: *** [scripts_basic] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2

---

### Post by fain on 2008-04-19
Do you have libstdc++ installed? Make sure all the dependency's are installed that are listed on the site where you got the program.

---

### Post by Jyves on 2008-04-19
How do i check this?????

---

### Post by fain on 2008-04-19
just open up synaptic 
"System>Administration>Synaptic Package Manager" 
and search for the package you need. In this case libstdc++ theres going to be a few different ones so you'll need to refer to the softwares installation instructions for dependency's.

There are also a few vpn packages in Synaptic in case you could maybe use a alternative.

---

### Post by fain on 2008-04-19
I just found this. seems like theres some trouble with newer kernels and the cisco program.
Check this link out maybe it will help you.
[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/]("http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/")

---

### Post by Jyves on 2008-04-19
Flain!!!
 I was on that site, actually i have downloaded everything from that site. It just didn't work out the way they say it should . I have applied all the patches.

I couldn't find libstdc++  in there !!!!! I have seen a bunch of library in...but nothing like libstdc++ 
I don't know what to do at that point..

---

### Post by fain on 2008-04-19
I was thumbing through the instructions and it appears you dont use make to compile you use ```
./vpn_install
``` 
im on gutsy not sure about hardy but im sure libstd is somewhere maybe renamed. try searching "std"

---

### Post by stuart brogan on 2008-04-19
suggestion

build-essential might solve some of the missing lib problems.

can you use OpenVPN? (I realize you probably have to use the companies software.)

apt-get install build-essential

---

### Post by Jyves on 2008-04-20
I did  that already ...

Here's the info i'm getting :
Making module
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/jay/Documents/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/jay/Documents/vpnclient/linuxcniapi.o
In file included from /home/jay/Documents/vpnclient/Cniapi.h:15,
                 from /home/jay/Documents/vpnclient/linuxcniapi.c:31:
/home/jay/Documents/vpnclient/GenDefs.h:113: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
make[2]: *** [/home/jay/Documents/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/jay/Documents/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

At that point ..... what do you think I'm doing wrong???????
What do you mean company software???? can you explain?
 I used Cisco VPN Client for Linux: v4.8.01.0640-k9 I don't know if its compatible with ubuntu 8.4 .

---

### Post by stuart brogan on 2008-04-20
I have no idea, however, I am very interested in your problem. I was merely trying to keep this thread alive, I guess it wasn't a very relevant suggestion.

As far as company software, what I meant was are you required to use this specific VPN? Because I have found that OpenVPN is very well documented and works well with Linux.

Best of Luck.

---

### Post by Jyves on 2008-04-20
Well, I'm stuck.funny thing is it did work on Ubuntu 7.10.  
I have upgraded to 8.4. I can't get VPN it to work. I keep looking around to see if i can find help. Ubuntu 8.4 is too fresh out there...I'm surprise people haven't got into bugs yet.\

Anyway if you find anything let me know.

---

### Post by Drakkn on 2008-04-20
> **Jyves said:**
> Well, I'm stuck.funny thing is it did work on Ubuntu 7.10.  
I have upgraded to 8.4. I can't get VPN it to work. I keep looking around to see if i can find help. Ubuntu 8.4 is too fresh out there...I'm surprise people haven't got into bugs yet.\

Anyway if you find anything let me know.


Do you have vmware installed? I am getting the same error but I noticed while searching that this error comes up in vmware installations too. I had this working in Gutsy too. The pcf file I have to use has settings in it not yet supported by the open version so I have to use this.

---

### Post by Drakkn on 2008-04-20
Well I got it to install by following this:
[http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/]("http://www.lamnk.com/blog/vpn/with-kernel-2624-you-will-need-a-patch-to-install-cisco-vpn-client/")
Seems to be working fine.

---

### Post by catfacts on 2008-05-15
Cant you install "vpnc" through Synaptic, the install worked fine for me, havent tried to connect yet tho.

---

### Post by navy pilot 26734 on 2008-05-16
I was having similar problems trying to get the Cisco VPN client to work and finally just gave up.  I decided to try vpnc last night and for whatever reason it wasn't working.  I shutdown my computer for the night and when I rebooted it today and tried it I was able to get it to work.  To do this you'll need to have the profile file (.pcf file) you would use for the Cisco client. Then do the following:

1.  Click on your network connections > vpn connections > configure vpn  and add a new connection.  

2.  On screen 1 of 2 make sure that where it says Connect to:  Compatible Cisco VPN client (vnpnc).

3.  On screen 2 of 2 click on the import saved configuration button in the lower right and select the .pcf file that you got from your work/school.  This will import the connection name, gateway and group name you need to connect to the VPN.  

4.  Then in the optional tab, check the box that says override user name and enter the user name for the network you are tying to vpn into and finish the process of setting up the connection. 

5.  Finally, in order to connect, you are going to need the group password, which unfortunately isn't imported from the .pcf file.  You can either ask your IT people and see if they will give it to you, or you can open up the .pcf file and find the encoded group password and go to this address [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode]("http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode")to decode it so you can then enter it when prompted. 

6.  You should now be able to connect to your VPN.  I hope this works for you like it did for me. 

Cheers!

---

### Post by lamnk on 2008-05-17
> **Jyves said:**
> I did  that already ...

Here's the info i'm getting :
Making module
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/jay/Documents/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/jay/Documents/vpnclient/linuxcniapi.o
In file included from /home/jay/Documents/vpnclient/Cniapi.h:15,
                 from /home/jay/Documents/vpnclient/linuxcniapi.c:31:
/home/jay/Documents/vpnclient/GenDefs.h:113: error: conflicting types for &#8216;uintptr_t&#8217;
include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was here
make[2]: *** [/home/jay/Documents/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/jay/Documents/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

At that point ..... what do you think I'm doing wrong???????
What do you mean company software???? can you explain?
 I used Cisco VPN Client for Linux: v4.8.01.0640-k9 I don't know if its compatible with ubuntu 8.4 .
FYI it does work with Hardy Heron 8.04, you just need to patch the client before install.

It worked OOTB with Feisty Fawn because Feisty used the old kernel 2.6.22

---

### Post by lamnk on 2008-05-17
> **navy pilot 26734 said:**
> 
5.  Finally, in order to connect, you are going to need the group password, which unfortunately isn't imported from the .pcf file.  You can either ask your IT people and see if they will give it to you, or you can open up the .pcf file and find the encoded group password and go to this address [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode]("http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode")to decode it so you can then enter it when prompted. 

vpnc includes a tool called pcf2vpnc in the package, it can decipher the group password from the pcf files.

---

### Post by joslinar on 2008-05-18
I installed it on hardy but I don't have the bookmarks here with me right now. Let me know if you still need it.
Meanwhile check [http://projects.tuxx-home.at/?id=cisco_vpn_client](http://projects.tuxx-home.at/?id=cisco_vpn_client) it looks very similar to what I did.

---

### Post by joslinar on 2008-05-18
By it I mean Cisco VPN Client

---

### Post by joslinar on 2008-05-19
&#65279;Ok, now I'm back home and have the bookmarks with me.
This is how I solved it:
I went to [[COLOR="Navy"] this website[/COLOR] ]("http://projects.tuxx-home.at/ciscovpn/") and donwnloaded the latest vpnclient and patch version. Note that there are 2 files that you need to download. First is the client, in my case [[COLOR="Navy"]this file[/COLOR]]("http://projects.tuxx-home.at/ciscovpn/clients/linux/4.8.01/vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz") and then the patch, in my case [[COLOR="Navy"]this file[/COLOR]]("http://projects.tuxx-home.at/ciscovpn/patches/vpnclient-linux-2.6.24-final.diff").

The first thing you have to do is use the patch command to apply the patch to the  file.

```
 tar -xvzf vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz
```

This will uncompress the file and create a folder called vpnclient. Go to that folder and copy the patch file ( vpnclient-linux-2.6.24-final.diff in my case) that you downloaded and update the client with the following command:

```
 patch < ./vpnclient-linux-2.6.24-final.diff
```

Then

```
sudo ./vpn_install
```

you should be all set with the installation part
now you need to get the profile, ".pcf" file provided by your company and save it int he  /etc/opt/cisco-vpnclient folder. You invoke the to start the daemon if you haven't rebooted type

```
 sudo  /etc/init.d/vpnclient_init start
```

go with the defaults. 

and to connect you type

```
 sudo vpnclient connect <profile> 
```

**[COLOR="Red"]Important:[/COLOR]** Use the name of the profile file without the extension pcf.

---

### Post by jkilgrow on 2008-05-22
Yep. I tried all of that. Still no love. My problem (well...my problem with the Cisco VPN Client...) is that I'm running 64-bit. I don't think the patch is built for 64-bit. Everything I've read about this Cisco VPN Client problem is that if you patch it correctly you can get it to work...unless you are using the 64-bit 8.04.

If anyone running 64-bit Hardy has gotten Cisco VPN Client to work, I'll give you a dollar.  :KS

---

### Post by jkilgrow on 2008-05-22
Hold the phone kids! I just found the following:

[http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/](http://www.lamnk.com/blog/domain/how-to-install-cisco-vpn-client-on-ubuntu-hardy-heron-804/)

I'm going to try it....I'll let y'all know!

---

### Post by jkilgrow on 2008-05-22
bah!
i got vpnc to work just fine. well....sort of. it doesn't seem to be able to connect via wireless and it kills my routing when i'm connected. maybe the two problems are related. i don't know. stupid network voodoo....i'm going to bed.

---

