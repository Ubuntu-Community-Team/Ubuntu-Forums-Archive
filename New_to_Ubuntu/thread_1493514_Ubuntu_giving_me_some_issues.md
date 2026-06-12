---
title: "Ubuntu giving me some issues"
date: 2010-05-25
forum: New to Ubuntu
---

### Post by guitardennison on 2010-05-25
After getting frustrated with my tearing start up and shut town graphics issues I chose to just live with it.  Until i was on youtube this afternoon watching loose change and i was unable to click on the video to alter volume or the time bar.  I also experienced similar tearing glitches with scrolling down op on the video.
  
  I Would like to completely get rid of my windows 7 partition completely but there are so many graphical issues that i cam still having.

  Does anyone know of some helpful information that can relieve my stress?

Currently  
-Nvidia graphics card

-Mozilla 

-Hp dv7t quad edition

I did install the recommended drives under the systems tab with little to no change.

---

### Post by Talon2 on 2010-05-25
System > Administration > Hardware Drivers

See if there is a driver for your card.  If there is, activate it.

---

### Post by Babuloseo on 2010-05-25
If its Nvidia, ther will probably be drivers for it, on the other hand AMD needs to improve their drivers ASAP.

Never mind, will not happen will have to switch to my NVIDIA linux computer or get a new system.

---

### Post by nhasian on 2010-05-25
can you tell us which nvidia driver your using?

```
lshw -C display
```


also which flashplayer and version it is?  in firefox type:

```
about:plugins
```

finally, are you using ubuntu 32 bit or 64 bit?

```
uname -a
```

---

### Post by guitardennison on 2010-05-28
> **nhasian said:**
> can you tell us which nvidia driver your using?

```
lshw -C display
```
also which flashplayer and version it is?  in firefox type:

```
about:plugins
```finally, are you using ubuntu 32 bit or 64 bit?

```
uname -a
```

got this boss.

matt@matt-laptop:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d2000000-d2ffffff memory:c0000000-cfffffff(prefetchable) memory:d0000000-d1ffffff(prefetchable) ioport:6000(size=128) memory:d3080000-d30fffff(prefetchable)
matt@matt-laptop:~$ about:plugins
about:plugins: command not found
matt@matt-laptop:~$ uname -a
Linux matt-laptop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

---

### Post by nhasian on 2010-05-29
your supposed to type:

```
about:plugins
```

inside of firefox :)

---

### Post by guitardennison on 2010-05-30
[SIZE=2]> **nhasian said:**
> your supposed to type:```
about
```[/SIZE]> **nhasian said:**
> ```
 [SIZE=2]:plugins[/SIZE]
```[SIZE=2]inside of firefox :)[/SIZE][SIZE=2]
  
Oh durr...

[B]I got a page with these items:

[/B]  [/SIZE]**[SIZE=1][B]VLC Multimedia Plugin (compatible Totem 2.30.0)**[/SIZE]

[SIZE=1]Windows Media Player Plug-in 10 (compatible; Totem)[/SIZE][/B]  [B][SIZE=1]
[/SIZE][SIZE=1]DivX® Web Player[/SIZE]

[SIZE=1]QuickTime Plug-in 7.6.6[/SIZE][/B]  [SIZE=2]
[/SIZE]**[SIZE=1]Shockwave Flash[/SIZE]**

-----------------------------------------------------------------------

---

### Post by nhasian on 2010-05-30
Okay your running 64bit ubuntu.  you should uninstall any flash plugins you've installed since the ones from the repository are all 32bit and use a wrapper to make them work in 64bit.

grab the 64bit adobe flash plugin [here]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz")

extract it, then copy the file to /usr/lib/mozilla/plugins/libflashplayer.so

make sure that is the only libflashplayer.so and that it doesn't conflict with any other ones with this command:

```
sudo updatedb && locate libflashplayer.so
```

then your flash support should look like this in firefox:
> 
Shockwave Flash

    File: libflashplayer.so
    Version: Shockwave Flash 10.0 r45

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by guitardennison on 2010-06-01
I was unable to copy the libflashplayer.so into the folder you specified.  an error occurred stating that i did not have permission to preform the task. 

I was able to download the item and unwrap it with ease.  

When you said delete any conflicting flash players which ones would i have to get rid of?

I was able to get this upon typing the code in terminal 
/home/matt/libflashplayer.so
/home/matt/Desktop/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

---

### Post by acrazyplayer on 2010-06-01
You want to go into synaptic and type in flash in the search bar then find any that you have installed and un-install them completely, Then to put the libflashplayer.so into the correct folder go into a terminal and type "sudo nautilus" this will give you all the permission you need. to find the .mozilla folder in your home directory you will need to see hidden files. This can be done by pressing "control+H" whilst in the sudo version of nautilus or any other version of nautilus.

---

### Post by guitardennison on 2010-06-01
> **acrazyplayer said:**
> You want to go into synaptic and type in flash in the search bar then find any that you have installed and un-install them completely, Then to put the libflashplayer.so into the correct folder go into a terminal and type "sudo nautilus" this will give you all the permission you need. to find the .mozilla folder in your home directory you will need to see hidden files. This can be done by pressing "control+H" whilst in the sudo version of nautilus or any other version of nautilus.


Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

thats a no go

---

### Post by acrazyplayer on 2010-06-01
try "sudo -i"
then your password 
then "nautilus"

---

### Post by nhasian on 2010-06-01
okay type this in the terminal:

```
sudo apt-get purge flashplugin-nonfree flashplugin-installer
```

that should remove all the old flash from your computer.  then do this to setup the new one:

```
sudo cp /home/matt/Desktop/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
```

that ought to do it.  close firefox and reopen it.  then check ```
about:plugins
```

> **guitardennison said:**
> /home/matt/libflashplayer.so
/home/matt/Desktop/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/share/ubufox/plugins/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so

---

### Post by guitardennison on 2010-06-03
> **nhasian said:**
> okay type this in the terminal:

```
sudo apt-get purge flashplugin-nonfree flashplugin-installer
```that should remove all the old flash from your computer.  then do this to setup the new one:

```
sudo cp /home/matt/Desktop/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so
```that ought to do it.  close firefox and reopen it.  then check ```
about:plugins
```

Thanks,

No more flash problems at all!  I've got some other little problems but the biggest one is out of the way because of you.

I sent you a request boss.

---

