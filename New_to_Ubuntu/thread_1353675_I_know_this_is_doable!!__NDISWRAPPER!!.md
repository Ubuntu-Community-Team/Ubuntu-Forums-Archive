---
title: "I know this is doable!!  NDISWRAPPER!!"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by emiliec15 on 2009-12-13
SORT OF SOLVED:  READ LAST POST
Please, don't yell at me!

I just installed ubuntu 9.04 (yes I know 9.10 is out but it was what I had)

I've had ndiswrapper working on this card before but now for the life of me I cannot seem to get it to work.  I know it can work under ndiswrapper for two reasons:
reason 1: it ran under 9.04 before
reason 2: it runs under my pclos (PCLinuxOS) installation.

Wireless card is a dwlg510 uses the mrv8k51 driver (I believe last time I ended up using the win2k version but whatever works is fine with me)

I've searched the forums, googled and somehow I cannot manage to get it to work this time!  Help!!

I promise to upgrade to 9.10 as soon as I get it working.

I have ndiswrapper installed from the cd and I have a copy of the drivers for the card.  In all technicalities this should be easy for me but I'm stuck!!

P.S.  I'll probably be a better forum member this time around, instead of being non-existent like last time.

---

### Post by frenchn00b on 2009-12-13
> **emiliec15 said:**
> Please, don't yell at me!

I just installed ubuntu 9.04 (yes I know 9.10 is out but it was what I had)

I've had ndiswrapper working on this card before but now for the life of me I cannot seem to get it to work.  I know it can work under ndiswrapper for two reasons:
reason 1: it ran under 9.04 before
reason 2: it runs under my pclos (PCLinuxOS) installation.

Wireless card is a dwlg510 uses the mrv8k51 driver (I believe last time I ended up using the win2k version but whatever works is fine with me)

I've searched the forums, googled and somehow I cannot manage to get it to work this time!  Help!!

I promise to upgrade to 9.10 as soon as I get it working.

I have ndiswrapper installed from the cd and I have a copy of the drivers for the card.  In all technicalities this should be easy for me but I'm stuck!!

P.S.  I'll probably be a better forum member this time around, instead of being non-existent like last time.
 
I know and had same feelings, it is difficult to install linux when we have new hardware. 

I had the same issue, will to get ndiswrapper for my non working wifi, but it is not on the installation cdrom.

If you have a Read / write cdrom to burn, that you can erase and rewrite, you could give a try this:
[http://cdimage.debian.org/cdimage/daily-builds/daily/20091206-5/i386/iso-cd/debian-testing-i386-netinst.iso](http://cdimage.debian.org/cdimage/daily-builds/daily/20091206-5/i386/iso-cd/debian-testing-i386-netinst.iso)
it works with my wifi (but you install debian stable, instead of debian unstable/sid  (ubuntu))
 
otherwise, there is nice a nice site for non working hardware:
[http://kmuto.jp/debian/d-i/](http://kmuto.jp/debian/d-i/)
but you install debian stable, instead of debian unstable/sid (ubuntu))
 
I like the stability in my case of a distro, that's important for my point of vue.

you need minimun kernel >=2.6.30
> uname -a

---

### Post by emiliec15 on 2009-12-13
Just so you know ndiswrapper is on the cd, it is not installed by default but you can use synaptic to install it from the cd after you get ubuntu up and running.  It doesn't take long and for most cards installing the drivers via ndiswrapper isn't problematic.  Except for a few of them, at least that give a full-blown fury.

Oh and both of the links you gave me aren't working completely one takes me here 
[http://kmuto.jp/debian/d-i/](http://kmuto.jp/debian/d-i/)
and the other gives a 404 error.

 I just need someone to let me know how to do this I can drop packages onto my ubuntu desktop from pclos (using root priveleges) therefore I REALLY shouldn't HAVE to burn anything to disc, I should be able to get this up and running somehow.  I did it last time but how did I?

---

### Post by emiliec15 on 2009-12-13
I just installed ndisgtk and when I open that application (yeah I know its a front end gui) it gives a message stating that it is unable to locate my hardware.  Anyone know of anyway to fix this?

---

### Post by staffann on 2009-12-13
I've got my Belkin USB wifi stick working even though ndisgtk said "Unable to see if hardware is present" (it still does when everything is up and running).

I just ignored that, pressed the "Install new driver" button and installed the drivers. If I remember correctly the drivers should be put somewhere on the harddrive first (I downloaded the WinXP drivers onto a USB memory stick on a windoze machine and transfed them to my home directory). Once done ndisgtk say netmw245 drivers are installed (and although I get the annoying popup when I start the app it says "netnw245 hardware present:yes".

After that the next thing is to configure the wifi networking. The "configure network" button in ndisgtk didn't work on my Ubuntu 9.10 so I went to System.->Preferences->Network Connections to do that. If that doesn't work as it should, ask me again - I finally chose to manually set up the wifi in the interfaces file.

---

### Post by lkraemer on 2009-12-13
First of all, you need to know if you have 32 bit or 64 Bit Ubuntu 9.04
installed.  Then you also need the same Windows Drivers (32 Bit or 64 Bit)
for installing via ndiswrapper.  Mixing and matching isn't allowed.
If you have that information handy it shouldn't take long.

Do one thing at a time, and don't try three other guides at the same
time so we know what your doing......and so there is no confusion.

If you are going to try and use your Windows Drivers you will need the
INF and SYS files. For example, bcmwl5.inf * bcmwl5.sys are the ones
I have previously used. Yours will be different according to your
Wifi card manufacturer. If you have XP available you can go to Control
Panel, and locate what the driver is named, then search for it.
Make sure you have the proper 32 bit or 64 bit drivers from the
proper Windows version that matches which Ubuntu (32 or 64 Bit) is
installed.  Google search on the Internet for Drivers also.....

You will also likely have to blacklist some other already installed
drivers that were included with Ubuntu.

In 8.04 the blacklist file is located at /etc/modprobe.d/blacklist,
but as of 9.04 and later, the files is /etc/modprobe.d/blacklist.conf

Install your Wifi Card, Power Up, then:
Post the output of the following Terminal commands:  (cut & paste to prevent errors)
```

lspci
lsusb
lshw -C network
lsmod
cat /etc/modprobe.d/blacklist.conf
iwconfig
sudo ndiswrapper -l
dmesg | tail

```
Post the outputs of the above.

If..... ndiswrapper -l   returns anything, then do:

sudo ndiswrapper -e xxxxxxxx <press enter> where xxxxxxxx is the driver returned in the ndiswrapper -l previously. Do this until nothing is returned from the ndiswrapper -l.

If lsmod shows module b43, bcm43xx, and others installed you will
need to blacklist them, since you are going to be using ndiswrapper.
You may have to remove the following depending on what lsmod
shows:
```

modprobe -r b44
modprobe -r b43
modprobe -r b43legacy
modprobe -r ssb

```
You can use sudo gedit /etc/modprobe.d/blacklist.conf
and add the necessary modules to blacklist.conf

change directory to where the driver files are located:
cd xxxxxxxx <press enter> where xxxxxxxx is the path to the folder containing the driver files.

To load the Windows Driver use these commands:
```

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
cd /etc
sudo gedit modules

```
( and add a new line to the end of the file. Type the following:
ndiswrapper <press enter>)

Now save the file and exit the editor.

Once this is all straightened up..........
I'd reboot or try:
```

sudo /etc/init.d/networking restart

```
If you know the routers essid and the correct <interface>,
shown by using iwconfig ie wlan0, ath0, etc.... replace that
as the <interface> below:
```

ifconfig
iwconfig
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo iwconfig <interface> essid "youressidofrouter"
sudo iwconfig <interface> mode Managed
sudo ifconfig <interface> up
sudo dhclient <interface>
iwconfig

```

lk

---

### Post by emiliec15 on 2009-12-13
Yeah!!

It worked!! At least after I burnt the disc to install 9.10 it did. 
Couldn't get it to work with 9.04 so I gave up and upgraded manually to xubuntu 9.10.

I'm online!  

One small issue though....I get a stronger signal within PCLOS.  Is there anyway to fix this or is it just reporting the strength differently?

---

### Post by lkraemer on 2009-12-13
Well, that is another way of fixing the problem...........But,
the other readers of this forum will once again be left wondering
exactly what you did or did not try, because at least one of them
will be in the same boat down the road, and will be looking for
exactly the same help.

If you're happy, that suits me!

lk

---

### Post by emiliec15 on 2009-12-13
I know its not the best way and that it may not help anyone else but at least they will know that the card does work under xubuntu and perhaps they will be trying to get it to work under xubuntu 9.10 and in that case this thread may prove helpful.  

Besides, that is why I said it was sort of solved or circumvented and not trully solved.  I wouldn't want to say that it wasn't possible but at least it works for me.

---

### Post by firsttimeubunter on 2009-12-27
folks...I have the UBUNTU jockey distro.... I pretty much ran in to all of the above issues.... as I was following the Ubuntu ndiswrapper how to. I have a Dell Wireless car bcmwl5 is the WinXP driver for it. I think mine is the broadcom 4318 chipset....
one thing I always saw in Ubuntu and OpenSuse 11.2 is whenever I do ndiswrapper -l (thats l for list not one) I see bcmwl5 installed alternate driver present ssb.

when I have the ndisgtk GUI installed it kept saying something like cannot find hardware.I tried to install the b43 firmware by broadcom but that won't install too.

so I thought if UBUNTU is providing an alternate driver, why not try it... so I did this

sudo modprobe -r b43 b44 ssb ndiswrapper
got a bunch of messages saying the blacklist file has to have a .conf extension if not it will be ignored.... realized this was my doing so did

sudo rm -r /etc/modprobe.d/blacklist 

NOTE:this is a file created by my doing... not the blacklist.conf itself, so the blacklist file is deleted after this step (though it might have not been necessary to begin with).

then did 
sudo modprobe ssb

lo and behold the wireless card picked up all available wireless connections.... I connected to mine and now I am beginning to "bunter".

I think it is all these freaking drivers conflicting and UBUNTU doesn't know which one is better....hope this helps you'll

Cheers
R

---

