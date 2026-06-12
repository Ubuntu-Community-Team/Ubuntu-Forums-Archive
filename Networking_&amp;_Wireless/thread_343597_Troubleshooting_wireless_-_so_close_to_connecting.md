---
title: "Troubleshooting wireless - so close to connecting"
date: 2007-01-21
forum: Networking &amp; Wireless
---

### Post by Tdonohue on 2007-01-21
Can somebody please help finish setting up this wireless connection.  I have installed the ndiswrapper 1.8.  Installed the drivers.

$ ndiswrapper -l
Installed drivers:
net5211         driver installed, hardware present
 
$ sudo ndiswrapper -m
modprobe config already contains alias directive

But then I get this, I don't know what I'm doing wrong here:

$ dmesg|grep ndis
[17179739.816000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17179739.836000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179739.840000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180138.424000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180138.424000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17180138.424000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17180220.400000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17180220.400000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17180220.400000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17182047.368000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[17182047.368000] ndiswrapper (wrapper_init:129): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17182047.368000] ndiswrapper (wrapper_init:136): ndiswrapper: initialization failed
[17183020.216000] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)

I am stuck here and can't find the answer online as most HOW TO's and tutorials refer to wlan0 or wifi0, but my card shows  on ath0 (is this the problem).  When I did the scan on ath0 it came up with three connections, mine being one of them, but I couldn't connect.  Thats where all the HOW TO's and tutorials end, apparently with success. 

Any ideas?  Any help would be greatly appreciated!!!!!

---

### Post by Tdonohue on 2007-01-21
I don't know what I did, but now I get this:

$ sudo ndiswrapper -m
module configuration contains directive install pci:v0000168Cd00000013sv00000308sd00003405bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodule configuration contains directive install pci:v0000168Cd00000013sv*sd*bc*sc*i* /sbin/modprobe ndiswrapper
;you should delete thatmodprobe config already contains alias directive

?????

---

### Post by Tdonohue on 2007-01-27
Thank you everyone for ignoring all my threads.  I can't wait to get this piece of garbage off my laptop and get back to Windows as soon as possible where things always just work.

---

### Post by hggdh on 2007-01-27
I understand your frustration, but please complain with the vendor of your wireless device, and ask them to publish the device specs. Your problem is not Linux, but the fact that the manufacturer is not willing to allow Linux in (and provides a closed, binary only, driver -- for Windows!)

Anyway. 

First of all, you did not state your distribution (Dapper, Edgy, or whatever, and you did not state what is your kernel version. So, I will assUme you are running Edgy, at 2.6.17.

Secondly, it is important to realise that Linux 64-bit will require a 64-bit Windows driver (for ndiswrapper). So, if you are running Linux 64-bit, you need the correct 64-bit driver for your device.

Thirdly, ndiswrapper 1.8 is *very* old. You should not use it. go to [http://ndiswrapper.sf.net](http://ndiswrapper.sf.net) and grab the current STABLE release (1.34), and install it. You will have to build it from source. This is usually not a big issue, and the site has good instructions on it.

AssUming you have the necessary packages installed (build-essentials, kernel-headers, and friends), then you have to:

1. untar the ndiswrapper source
2. cd into the newly-created directory;
3. Run 'sudo make uninstall' as many times as necessary to remove any dangling piece of the old ndiswrapper;
4. sudo make install
5. sudo rmmod ndiswrapper (to unload the old driver)
6. sudo modprobe ndiswrapper (to load the new one)

Then see if your Windows-only driver was successfuly loaded by ndiswrapper, bu running 'ndiswrapper -l' -- this is a lower case L, not a vertical bar --, and 'dmesg | grep ndis'.

If in doubt, or not working, post the results here.

Please remember you are asking for help, and the people helping here are doing so because they want to help freely. We do not get paid to do that. Getting abusive will only result in  you being ignored.

---

### Post by hggdh on 2007-01-27
BTW -- looking more carefully at the dmesg output you provided... you are running ndiswrapper-utils 1.8, and ndiswrapper 1.22. Not that bad.

But... I would still like you to 'sudo rmmod ndiswrapper', then 'sudo modprobe ndiswrapper', and then post:

1. the bottom of the dmesg output (from the modprobe onwards)

2. manufacturer & model of your wireless device;

3. where you got the Windows driver from

4. the outout of 'uname -a'

---

### Post by Tdonohue on 2007-01-29
Thanks for your advice, and I apologize to anyone offended by my statement above.  Its just so frustrating when you're working with a dozen different directions to do one thing and none work.  

I gave it one last shot at a complete reinstall, tried a different card (belkin, even though it has the same Atheros chipset as the zyxel I was using), followed yet another HOW TO and managed to get it working complete with WPA2.  I will post the link to the Howto that worked for me when I find it.  

I think the problem was solved by changing all references to wifi0 or wlan0 to ath0.  I don't know why mine says ath0 (of the few posts that mention ath0, they all say it should work out of the box, i don't beleive thats true).

The only problem now is that I experience "hard freezes" where I have to pull the battery out of my laptop and restart.  I don't recall this happening before I had wireless working.  In the ndiswrapper list, it shows everyone using the driver that came on the disk (168c:0001a), so it doesn't appear I can try a different driver.  It freezes randomly, coming back from standby, clicking on a link, opening an app.  No pattern to it.  

any idea if its something on the wireless side I can change to fix it.

---

### Post by hggdh on 2007-01-29
Post-1.22 ndiswrapper has fixed some crashes. It might be a good idea to download the current stable (1.34) and go from there.

'wlan0' is not necessarily the name of the wireless interface; it is just a default. When your system comes up, it may decide on another name. For example, on mine it is 'eth1'.

So, yes, your problems were certainly compounded by you using the wrong name...

Also, on the hard freezes... if it was not happening before you had the wireless interface up, *and* the only change was bringing the wireless interface up, then it stands to reason it is related. This is why I am suggesting you to try 1.34, or even the development version.

---

### Post by dvdlvr on 2007-01-30
I had the same problem on one of my machines, while it worked with the same dongle on another.

The difference was the kernel version. I got it running this morning :D 

Both machines were single processor machines. One had SMP=yes set, the other had it set to "no". The latter one functioned right away.

So, I installed a different kernel on the other machine (SMP=no) and hey presto: It worked. I'm not sure about the preempt option. Both machines are set to preempt=yes but it may also work with preempt=no.

Try installing Ubuntu version linux-image-2.6.15-27-386 or recompile your current kernel with CONFIG_PREEMPT=y and CONFIG_SMP is not set.

---

