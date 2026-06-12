---
title: "HOWTO: Install UMTSMon (GUI for 3g/HSDPA connections)"
date: 2008-07-24
forum: Networking &amp; Wireless
---

### Post by motin on 2008-07-24
[UMTSMon]("http://umtsmon.sourceforge.net/") is currently [missing in the repos]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/186364"), and I have not found a .deb so far, but: You can either:

1. Download [an rpm-package]("http://download.opensuse.org/repositories/home:/seife/Fedora_8/i386/umtsmon-0.8-1.1.i386.rpm") from [http://download.opensuse.org/repositories/home:/seife/Fedora_8/i386/](http://download.opensuse.org/repositories/home:/seife/Fedora_8/i386/) and use "alien" to convert it into a .deb package:
```

sudo apt-get install alien
sudo alien umtsmon-0.8-1.1.i386.rpm
sudo chown $USER umtsmon_0.8-2.1_i386.deb # To easily being able to  (re)move this .deb later
gdebi-gtk umtsmon_0.8-2.1_i386.deb

```

or...
2. (For i386 users) Download a [compiled version]("http://downloads.sourceforge.net/umtsmon/umtsmon-0.8.i386.tar.gz?modtime=1205316487&big_mirror=0") from 
 download the sources from [http://sourceforge.net/project/showfiles.php?group_id=159777](http://sourceforge.net/project/showfiles.php?group_id=159777) and run umtsmon directly:
```

tar -xvf umtsmon-0.8.i386.tar.gz
./umtsmon-0.8/umtsmon

```

...or:
3. Download [the source]("http://downloads.sourceforge.net/umtsmon/umtsmon-0.8.src.tar.gz?modtime=1205316505&big_mirror=0") from [http://sourceforge.net/project/showfiles.php?group_id=159777](http://sourceforge.net/project/showfiles.php?group_id=159777) and compile + install it:
```

tar -xvf umtsmon-0.8.src.tar.gz
cd umtsmon-0.8
make
sudo make install

```
Note: I haven't done this myself so I don't know what packages are needed to have in order to finish the compilation...

Note: Only the first option will provide you with a menu item for UMTSMon... For the 2nd and 3rd option you need to manually install the "libqt3-mt" package before running the application. Also - I have personally only tested the 2nd option above - please report back if the others are not working. 

Happy 3G surfing! Cheers!

---

### Post by Sleepy-zz-John on 2008-08-26
> **motin said:**
> 
... Only the first option will provide you with a menu item for UMTSMon... For the 2nd and 3rd option you need to manually install the "libqt3-mt" package before running the application. Also - I have personally only tested the 2nd option above - please report back if the others are not working. 



Thanks for the instructions.  

As I'm very much a beginner,  I decided your first alternative would probably be the simplest to try.  

Your first three lines of code for went in OK,  and umtsmon_0.8-2.1_i386.deb was generated.  

Your 4th line produced some warnings and a long string of SSS like this:

/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.5/site-packages/GDebi/GDebi.py:93: GtkWarning: gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed
  self.window_main.set_sensitive(False)
/usr/lib/python2.5/site-packages/GDebi/GDebi.py:93: GtkWarning: gdk_window_set_cursor: assertion `GDK_IS_WINDOW (window)' failed
  self.window_main.set_sensitive(False)
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS 

However the installation did complete, so I then tried the umtsmon command,  but it was not successful:

umtsmon: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

So do you think you could explain (in beginner's language please:)) what libqt-mt.so.3 actually is, what was it made you think that only options 2 and 3 would need the package,  where I could find a copy, and what I should do to install it?

   Many thanks,
      S-zz-J   :-?

---

### Post by aasche on 2008-08-27
> **Sleepy-zz-John said:**
> However the installation did complete, so I then tried the umtsmon command,  but it was not successful:

umtsmon: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

So do you think you could explain (in beginner's language please:)) what libqt-mt.so.3 actually is, what was it made you think that only options 2 and 3 would need the package,  where I could find a copy, and what I should do to install it?
Fastest way to install the missing library *libqt-mt.so.3*:

```
sudo apt-get install libqt3-mt
```

Option 1 should have installed the missing lib as a dependency - if not, see above.

---

### Post by TekNullOG on 2008-08-27
Will this work with a mobile phone plugged via USB?

I have a Nokia E71 and would love to get the internet to work on my laptop.

Sorry, I didn't see if it was for devices that already support 3G natively.

---

### Post by lightxx on 2009-02-19
sorry to bring up this thread from the past, but no matter what i try i can't figure out how to get UMTSmon to bring up a PPP connection.

i downloaded the latest source files and compiled them, and umtsmon runs, but fails when creating a PPP connection.

i would really appreciate any help i can get, as the UMTS/HSDPA support in ubuntu 8.10 really sucks w/o umtsmon :(

[IMG]http://kraxn.t-h.cc/umtsmon/umtsmon_ss1[/IMG]

[IMG]http://kraxn.t-h.cc/umtsmon/umtsmon_ss2.png[/IMG]

[IMG]http://kraxn.t-h.cc/umtsmon/umtsmon_ss3.png[/IMG]

debug-log: [http://kraxn.t-h.cc/debug.log]("http://kraxn.t-h.cc/umtsmon/debug.log")

funny thing, however, is that when UMTSmon runs i can _STILL_ dial up using NetworkManager, and monitor the signal strength in UMTSmon.

---

### Post by TekNullOG on 2009-02-19
OK I will try to help you out but I am at work and am sadly running a Windows computer.

Ubuntu 8.10 is the BEST for configuring this type of connection. It is finally built into the OSS so I don't see why you would need to compile anything.

When you right click on your network icon on the top right, you can configure a new connection. Off the top of my head I can't remember what the exact option is but you should be able to add a mobile device or phone. It asks you what country you're in, then what provider you're with and voila... It's done!

I might be forgetting 1 or 2 little things because I am going by memory but it worked with my Nokia E71 in Canada on Fido and Rogers networks.

Let me know how it goes. I can maybe check it out when I get home.

---

### Post by lightxx on 2009-02-19
erm ... thanks alot for your quick reply. i'm afraid i haven't made my point clear ;)

i regard the built-in UMTS support of ubuntu 8.10 as insufficient, and i'm having a number of reasons why.

1.) there's no way to check whether your modem handshaked using GSM/GPRS/EDGE/UMTS/HSDPA, which i need and want to know.
2.) there's no built-in way to show the signal-strength, another piece of info i really want to know
3.) there's no built-in SMS support, another feature UMTSmon has and NetworkManager lacks.

so, what i want to do is using UMTSmon for UMTS/HSDPA PPP connections instead of NetworkManager. what i'm doing now is using UMTSmon just for monitoring purposes, and let NetworkManager do the dial up, which works, but i'd rather do both things with UMTSmon ;)

Thanks,
Tom

---

### Post by TekNullOG on 2009-02-19
Ahhh, I see...

I wish I could help but I use the network manager. I haven't had a need for all these features yet but I admit that they'd be cool if they were installed natively in the next Ubuntu.

---

### Post by lightxx on 2009-02-20
hm. you never need to know your current signal strength? 

> **TekNullOG said:**
> Ahhh, I see...

I wish I could help but I use the network manager. I haven't had a need for all these features yet but I admit that they'd be cool if they were installed natively in the next Ubuntu.

---

### Post by TekNullOG on 2009-02-20
Well it's shown on the phone so I guess the answer is no, I have never needed to know my signal strength from Ubuntu.

---

### Post by beamish68 on 2009-04-29
> **lightxx said:**
> hm. you never need to know your current signal strength?

Hello lightxx,
 did you solve your problem?
 
 I have the same problem, getting an error when I try to connect via umtsmon.
 
 So I tried to start umtsmon but connect via NetworkManager.
 Then umtsmon shows me all the informations as if he did the connect.
 
 Maybe this will help you.
 
 Regards
 beamish
 
 PS: please apologize my english :rolleyes:

---

### Post by stedevil on 2009-07-10
Thanks for the guide :)

It's so sad networkmanager misses basic functionality like connection strength and handshake info.

PS Times pass, the links to the rpms is nowdays

[http://download.opensuse.org/repositories/home:/seife/Fedora_9/i386/](http://download.opensuse.org/repositories/home:/seife/Fedora_9/i386/)
and the package currently is 0.9.72

---

### Post by stedevil on 2009-07-10
It's so sad networkmanager misses basic functionality like connection strength and handshake info. When you have a HSDPA modem, there is no connection LCD screen to look at, so these features needs to be in the network manager.

PS Times pass, the links to the rpms is nowdays

[http://download.opensuse.org/repositories/home:/seife/Fedora_9/i386/](http://download.opensuse.org/repositories/home:/seife/Fedora_9/i386/)
and the package currently is 0.9.72

Also option 1 needs you to install libqt3-mt (at least on xubuntu 9.04) so suggest the tutorial is updated to be
sudo apt-get install alien libqt3-mt

---

### Post by stedevil on 2009-07-10
Sorry about the double/tripple post. Forum seems broken, can neither edit nor delete a message.

---

### Post by ~Las~ on 2010-01-30
Got .deb from this site.[http://people.debian.org/~winnie/umtsmon/](http://people.debian.org/~winnie/umtsmon/) .Everything works allmost well (sig strength ,sms,network selection etc.But firefox works offline :-(

---

### Post by yasir.elsharif on 2010-04-05
Thanks for the hard work guys and this valuable act of sharing information.
Sadly I have tried almost all the provided various ways and still couldn't get umtsmon to work with me at all.
I always get the same error:

*umtsmon: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory*

I even googled this error, where I found many people got the same error but I could see no solution at all.

I am desperate to such a program, my ISP requires sending an activation sms every day, where I unplug the device, replace the sim in an ordinary mobile and send the sms and reinsert the sim in the device and reconnect.
help!

---

### Post by pdc on 2010-04-05
> apt-get install libqt3-mt 

eg post #3 here

[http://www.linuxforums.org/forum/debian-linux-help/74426-missing-libqt-mt-so-3-a.html](http://www.linuxforums.org/forum/debian-linux-help/74426-missing-libqt-mt-so-3-a.html)

---

### Post by yasir.elsharif on 2010-04-06
Thanks for responding.
libqt3-mt is already installed.
so, what is it, and why the this program can't see this library?
I am confused.

---

### Post by am.kh on 2010-04-06
[SIZE=7][SIZE=5]I think it may be the problem of utmsmon version architecture(i386,i586,...) be sure you use your processor's architecture version. [/SIZE][/SIZE]

---

### Post by yasir.elsharif on 2010-04-12
I have tried both architectures and none worked with me I still have the same error :(

---

### Post by yasir.elsharif on 2010-04-15
Finally I have got it to work. I learned a hard lesson, i.e. Ishould have uninstall the installation that I tried 1st fromsource......:(
anyhow now it's working :P. but I still miss certain features like service com. editor where you send credit requests to the network and got an immediate notifications on screen.

---

### Post by sportsdude81 on 2010-11-01
This thread might be dead. Thought I'd give a shot.  Trying to install umtsmon on a 64bit Lucid CPU i keep getting 

```
umtsmon: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory
```

now matter how i try to install it or what architecture I use.  Any body know of a 64 bit deb or binary?

---

### Post by sprockin on 2011-06-07
Get a pclinuxos live cd, it's installed by default on that distro :lolflag:

---

