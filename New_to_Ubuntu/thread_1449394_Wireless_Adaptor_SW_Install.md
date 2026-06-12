---
title: "Wireless Adaptor SW Install"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by randl on 2010-04-07
I am as Linux green as green is.  I did a clean install of Ubuntu (latest) in an old desktop that was previously running XP with an Airlink Wireless Adaptor  (AWLL3025).  The Ubuntu load was flawless (very Impressive) and as a stand alone machine it works great.  I could not figure out how to make the wireless connection to my router.  I found out I needed to download code =-> compile it -> and install the module in the Airlink Dongle.  Easy right?

I went through 20 websites (on a neighboring machine) trying to find out how to do this and couldn't.  I got this far:

Found the code in:  [http://home.arcor.de/ironpanther/usbstick/zd1211-4715.tar.gz](http://home.arcor.de/ironpanther/usbstick/zd1211-4715.tar.gz)
Loaded the zip to a flash drive and loaded it to the Ubuntu machine.
Went to Applications -> Accessories -> Terminal to try to compile the code but no matter what I did I could not.

HELP! somebody?
Thanks

---

### Post by spcwingo on 2010-04-07
You might want to have a look here:

[http://ubuntuforums.org/showthread.php?t=35896]("http://ubuntuforums.org/showthread.php?t=35896")

---

### Post by randl on 2010-04-07
That is where I was but I need more help as I specified in my original message:
Need help:
1. How to compile
2. how to "install" the compile module in the Airlink flash drive.

Thanks for the try.

---

### Post by spcwingo on 2010-04-08
I have no idea how to compile a module (I've never had to do it before).  If I had a guess it'd probably be just like compiling any other software...like this.

```
cd /path/to/source/code/
```

followed by:

```
./configure
```

then:

```
make
```

finally:

```
sudo make install
```

Some software doesn't require all the steps above just the last part (sudo make install).

If for some reason you can't get it going, you can always try ndiswrapper...it'll let you use some windows drivers for wireless cards.  Let me know if you can't get it going by compiling the module and I'll try to give you a hand with setting up your card that route (ndiswrapper).

---

### Post by lkraemer on 2010-04-08
Dup!

---

### Post by lkraemer on 2010-04-08
randl,
You have the file named zd1211-4715.tar.gz downloaded to probably the
Downloads or Desktop.

COPY & PASTE the COMMANDS!

With the USB Device UNPLUGGED, Open a Terminal window and type:
```

lsusb
lsmod

```
lsmod will display all the modules that are loaded.
Now, plug in the USB Device, wait 30 Seconds and type
```

lsusb

```
again.  You should see the device.  Now you need to compare that USB:id
to the list at:
[https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211](https://help.ubuntu.com/community/WifiDocs/Driver/zydas_zd1211)

If it all checks out that the device is supported you just need to extract the folder with the source code.  I'd just double left
click on the File and it should ask you where you want to extract
to.

Let's assume Desktop.  The source file has the actual source code
a few folders down inside the compressed file.  You should see
/./zd1211-4715/zdsta/ to get to the source folder and the makefile.
I'd suggest just extracting the zd1211-4715 folder to your Desktop.
So, on your Desktop you should see a folder named: zd1211-4715

Now in the Terminal Window type:
```

pwd
ls -alt
cd Desktop
pwd
ls -alt
cd zd1211-4715
pwd
ls -alt

```

Open a Second Terminal Window:
```

sudo -s

```
enter your password.  NOTICE the Last CHAR has changed to a # meaning
ROOT ACCESS.  exit can be typed to exit ROOT ACCESS.

You need an Ethernet Connection to get the following downloads:
Next there are some packages that need to be installed so the driver
can be built:
```

aptitude install linux-headers-$(uname -r) build-essential

```
This should download the correct headers and build-essential,
which is required for the compile.

Switch to the First Terminal Window:
```

make clean
make
sudo make install

```
This should comple with the second command, and install with the last
command.  If you have errors stop and post the results.  The first command cleans up before the compile if it is the second or third attempt.

Now we need the compiled module loaded, and set up for reboots.
```

modprobe zd1211
echo zd1211 >> /etc/modules
ifconfig wlan0 up
lsmod

```
The last command should show the module you compiled as being loaded.

Exit the Terminal Windows.

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

### Post by anewguy on 2010-04-08
For normal Ubuntu, the build-essential package is on the LiveCD in /pool/main/b, but I haven't ever found the headers out there so you'd still need to download them.

Dave ;)

---

### Post by randl on 2010-04-08
K, Thanks a bunch for the detailed message.  I printed it and followed it carefully but got stuck were noted in red below.
----------------------------------------------------0000-------------------------------------------

[QUOTE=lkraemer;9091865]randl,
You have the file named zd1211-4715.tar.gz downloaded to probably the
Downloads or Desktop.

**COPY & PASTE the COMMANDS!  **[COLOR=Blue]can not do this since the machine is stand alone (no net connection)[/COLOR]

Now in the Terminal Window type:
[code]
pwd
ls -alt
**cd Desktop**  [COLOR=Red]This command failed, the message said: "no such file or directory"[/COLOR]
pwd
ls -alt
cd zd1211-4715
pwd
ls -alt

---------------------------------------------------0000-------------------------------------------
Any suggestions?
Again Thanks,
R.

---

### Post by randl on 2010-04-08
[QUOTE=randl;9093461]K, Thanks a bunch for the detailed message.  I printed it and followed it carefully but got stuck were noted in red below.
----------------------------------------------------0000-------------------------------------------

[QUOTE=lkraemer;9091865]randl,
You have the file named zd1211-4715.tar.gz downloaded to probably the
Downloads or Desktop.

**COPY & PASTE the COMMANDS!  **[COLOR=Blue]can not do this since the machine is stand alone (no net connection)[/COLOR]

Now in the Terminal Window type:
[code]
pwd
ls -alt
**cd Desktop**  _*[COLOR=Red]This command failed, the message said: "no such file or directory"[/COLOR]*_
pwd
ls -alt
cd zd1211-4715
pwd
ls -alt

---------------------------------------------------0000-------------------------------------------
I was wrong, the instruction was flawless, my typing sucks!  I did the whole thing again and typed desktop correctly as "Desktop" and it worked.

Now the question I have is: how can I download the modules you are talking about  to a flash drive in a windows machine so I can load them to the Ubuntu machine?  Or, is this even possible?

Thanks for the diligent help,
Randl

---

### Post by randl on 2010-04-08
SOLVED - for now.  how could this be?  I restarted the machine after some issues. on restart, it asked me to sign in to my netwoek through the Airlink dongle I was trying to load with Linux code.  I signed in and it worked!  I am typing this from the machine I was trying to connect to the network with the Airlink dongle.

In my mind though, I loaded nothing new to the firmware, but it works!
I am not going to argue.  I am just going to use it.

Thank you K. for the great help.  I know it took a lot of time and care to put your message together and I appreciate the effort.  This is a sign of the type f folks that live in this universe.

Thanks,
Randl

---

