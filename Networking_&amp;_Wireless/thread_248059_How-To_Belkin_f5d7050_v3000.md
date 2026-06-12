---
title: "How-To Belkin f5d7050 v3000"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by waldschm on 2006-08-31
First off, just want to say that if you're looking for a good wireless card for Linux, do not buy this one, do a search in these forums or on google for a card/USB adapter with good compatibility. Secondly, this is how I got the Belkin f5d7050 v3000 to work, if your model number is f5d7050, that does not mean this will work. Belkin was naughty and made versions 1000,2000,3000,and 4000. They have different chipsets but the same model # of f5d7050. So my method is not relevant to versions 1000, 2000, or 4000.. check on the box for the version! OK that being said here's what I did starting with a clean install of Dapper Drake 6.06:

1. Install network-manager-gnome, ndiswrapper-utils and ndisgtk(probably not necessary) from repository using Synaptic or sudo apt-get. I had to use packages.ubuntu.com since the computer had no wired connection

2. Once ndiswrapper-utils is installed, plug in Belkin USB, and pop in the CD that came with it.

3. Navigate to the WinXP drivers on the CD and copy the rt73.inf and rt73.sys files to your desktop

4. in the terminal (Applications -> Accessories -> Terminal)
```
cd Desktop
sudo ndiswrapper -i rt73.inf
ndiswrapper -l
```

5. Reboot your computer (modprobe with ndiswrapper doesn't work for some reason so yes just reboot)

6. After reboot, click on Network Manager icon and click on your network if you have no encryption or WEP. If you have WPA, click on "Connect to Other Wireless Network..." Enter the password for your connection if necessary.

7. Try out the wireless for a few reboots, what happened is mine worked fine on the first reboot, but from then on would only work if I unplugged the Belkin USB and plugged it back in. Then it would drop connectivity after 5 minutes and refuse to reconnect. Obviously not good

8. To fix this I found that I had to follow this bizarre procedure. Write a shell script to continuously ping your router as follows using gedit or editor of choice

```
gedit ~/ping.sh
```

then enter the following and save the file:

```
#!/bin/bash
X=0

while [ $X -le 20 ]
do
    ping 192.168.1.1
done
```
(modify 192.168.1.1 to the ip address of your router, Linksys routers are usually at 192.168.1.1, my Motorola was at 192.168.10.1, but check to be sure)

9. Now that you have this script saved we have to make it run on startup so enter these commands to do so:

```
chmod 755 ~/ping.sh
sudo cp ~/ping.sh /etc/init.d/ping.sh
sudo update-rc.d ping.sh defaults

```



OK, this did it for me, I still have to do one little thing to get it to work: each time on reboot it tries to connect automatically and fails, I unplug and replug the USB try to connect again, and I have a working connection that will last without disconnecting. This was a real pain and this is sort of a sloppy fix, so if anyone can find any solution that works better for the v3000 let me know. I think the problem is the device goes into power-saving mode and disables but I couldn't figure out how to configure it to avoid this. I also tried the rt73 Windows drivers from the ralink website and those installed but failed to work at all. I haven't tried the Linux rt73 drivers on the page or compiling a newer version of ndiswrapper from source, but if that works better for anyone go ahead and post that solution.

Note: my computer does not completely shutdown now because of my script, does anyone know if I have to modify my run levels from the defaults of update-rc.d so that it shuts down properly?

---

### Post by alecjw on 2006-09-01
The IP address of a Belkin router is 192.168.**2**.1

---

### Post by Arevos on 2006-09-01
I use an open wireless network and a Belkin F5D7050 USB wireless stick to connect to it. I run Dapper and had none of your problems (perhaps they are due to WPA usage?).

However, I did discover that the Belkin drivers lock up the system if a lot of data flows through the wireless USB stick. If you use the Belkin F5D7050 and your computer is freezing inexplicably, then the culprit is most likely the F5D7050.

---

### Post by waldschm on 2006-09-01
You have the f5d7050, but do you have the v3000? If it's supported by default in dapper it's probably the v2000 or v1000 since I believe these use the rt2500usb drivers which are much more supported. The v3000 according to what I've seen scouring the forums has a prism chipset and prism usb drivers for linux are supposedly much more experimental. I tried the v3000 on two separate computers both with fresh installs of Dapper, maybe I did something wrong but I'm pretty sure they are not supported out of the box.

---

### Post by ruraltodd on 2006-10-10
followed your steps after following several other threads advice steps and your was the only one that got me anywhere - got right through to ndiswrapper -l which gave rt73 driver and hardware detected - my connection was showing on the attached wireless tools but as shown i cannot connect but get connected failed after numerous boots - i will watch for a reply here if you can help or email me [email]toddrenouf@dodo.com.au[/email] - any help would be appreciated - ruraltodd

---

### Post by alecjw on 2006-10-15
I think there are actual Linux drivers for this card, you don't need ndiswrapper:
[http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)

---

### Post by ironopolis on 2006-11-03
Hi,

I am new to Ubuntu, could you tell me what to do with the driver once I have it.

Thank you for your help

ironpolis

---

### Post by FrodoB on 2006-11-13
See this thread for detailed instructions. The rt73 devices work well with Linux.

[http://www.ubuntuforums.org/showthread.php?t=296281](http://www.ubuntuforums.org/showthread.php?t=296281)

---

### Post by barksten on 2006-11-19
Thank you very much!!!
I agree that it's not a nice solution but atleast it works on 6.10 without ndiswrapper!
I just edited /etc/network/interfaces as suggested in /usr/doc/wpasupplicant/modes.readme..

Hopefully someone (or even I?) will find another solution but until then I will have the pingscript running. I just hope my router doesn't ban me for flooding ;)

oops.. didn't notice the link to the other post. I will check it out right away!

---

### Post by barksten on 2006-11-19
*deleted*

---

