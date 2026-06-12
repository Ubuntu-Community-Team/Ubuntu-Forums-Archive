---
title: "rt73 problems (Connects just swell, but can't use the connection)"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by BrianEwing on 2008-06-12
OK, so I installed the 8.04 Desktop release, and it installed fine, no problems there, but when I proceeded to connect to my wireless network (1MVP), it connected - Though at first it asked me to input the WPA2 passphrase twice. Again, it connected, but wouldn't allow me to use it (I tried pinging, tracerouting, and using firefox to connect to here). It still wouldn't work.

I then opened up the 'Network Settings' dialog, and manually set the parameters. It didn't work again. I downloaded the package "[rt73-common_1.0.3.6-cvs20071123-dfsg1-3_all.deb](http://debian.ihug.co.nz/debian/pool/contrib/r/rt73/rt73-common_1.0.3.6-cvs20071123-dfsg1-3_all.deb)" which installed alright, and tried to connect again. It didn't ask me for the passphrase twice this time, but connected as usual. (Here's a surprise :P) - It didn't work. I'm hijacking the ethernet from the server which I shouldn't really be doing. Does anyone know what I can do to fix it? Anyone had the problem before?
I'll provide any extra information you may need

Thanks for your time,
Brian.

---

### Post by linkunderscore on 2008-06-13
I have this exact problem. 

It connects fine, great signal strength..just can't use it. I actually had a little glimmer of hope when it let me connect once, just ONCE, with my router (192.168.1.1) and ONCE with google.com. Then from then on it hasn't been working.

It worked perfectly with 7.10... 

I have NO idea how to resolve this, so I am relegated to my XP partition until I can figure out a way to access the net on ubuntu.

---

### Post by issih on 2008-06-13
I had much the same problems, The different things I tried were:

1) Compile the serialmonkey drivers - these worked but don't integrate with ubuntu very nicely:

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)

2) Compile the ralink drivers - can't remember if I got these working, I had some problem with them, I forget what.

[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

3) Use Ndiswrapper.

In the end I opted for Ndiswrapper, which is a shame, but I couldn't get the others to play nicely. It probably will depend on your exact hardware as to how succesful you are though.

Do note that if you do try to replace the drivers, you are going to need to blacklist rt723usb and probably rt2500usb in order to stop them loading ahead of your newly compiled modules.

Hope that helps

---

### Post by linkunderscore on 2008-06-13
This fixed mine perfectly:

> **james_vanb said:**
> I have Belkin F5D7050 installed on an old Dell Latitiude CP M233St with xubuntu hardy herron and a Desktop running ubuntu hardy herron. Responding on Desktop using Belkin F5D7050, v. 3000 with rt73 driver. Install has been the same using ndiswrapper and the install cd as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```


I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist rt2500usb" and "blacklist rt73usb" (Without the quotes) to end of list, save and close.

***_[COLOR="Red"]REBOOT[/COLOR]_***

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin". Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following (If the .inf file you copied is not the rt73, replace as appropriate below) :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows (If you are using Xubuntu, replace gedit with mousepad):

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

**note the red underline bold thing I highlighted...this is very important. You need to reboot after that or it won't work**

When u finish the modprobe ndiswrapper command give it about 2 minutes to get the dns stuff up and running. :guitar:

---

### Post by jtbalt on 2008-07-20
link,

I've followed your directions and all seems to go well, until the end.  I'm using Hardy 8.04 and use an ethernet to download all updates prior to trying the install for the f5d7050 v3000.  

When I run the command to make the alias

sudo ndiswrapper -m

I get a reply saying the command is deprecated.  When I reboot my network manager shows that I'm connected to my wireless network and yet the browser won't connect, nor can I download updates.  If it does connect to the internet, it only seems to stay connected for a brief time before it won't allow any further downloads or browsing, although network manager still shows a good connection to my wireless network.

Any ideas?  Anyone?

Thanks in advance,

---

### Post by battledean on 2008-08-29
I had this exact problem with the kernel version of the rt73 drivers for my edimax usb wireless.  I followed the instructions [here]("http://ubuntuforums.org/showthread.php?t=400236") and they worked exactly as given with no problems at all.  Now my wireless is flawless.

---

