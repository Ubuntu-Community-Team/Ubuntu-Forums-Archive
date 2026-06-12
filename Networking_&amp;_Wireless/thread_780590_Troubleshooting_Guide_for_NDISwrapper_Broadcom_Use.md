---
title: "Troubleshooting Guide for NDISwrapper Broadcom Users"
date: 2008-05-03
forum: Networking &amp; Wireless
---

### Post by Ayuthia on 2008-05-03
This is not a comprehensive troubleshooting guide, but hopefully a helpful guide to help you understand how to fix your NDISwrapper install.  This will be updated periodically to add any other information that may be helpful.

If you are looking for a way to get your Broadcom wireless driver to work on Hardy, please see [http://ubuntuforums.org/showthread.php?t=779754](http://ubuntuforums.org/showthread.php?t=779754)

If you are looking for the b43/b43legacy troubleshooter, please see [http://ubuntuforums.org/showthread.php?t=780692](http://ubuntuforums.org/showthread.php?t=780692)

**NDISwrapper Troubleshooting Tips**
TSN 1.0:
NDISwrapper does not start up on boot:
Sometimes to get NDISwrapper to start on boot, you need to add ndiswrapper to /etc/modules.  There are some modules that the kernel does not start at boot.  /etc/modules is the file that will load the modules for you.  So check and see if ndiswrapper is in the file:
```
cat /etc/modules|grep ndiswrapper
```
It should return the word ndiswrapper.  If it does not, add the following at the terminal:
```
echo ndiswrapper|sudo tee -a /etc/modules
```

TSN 2.0:
NDISwrapper is not starting up:
Verify that NDISwrapper is installed.
```
ndiswrapper -v
```
Something like the following should appear:
```
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-generic SMP mod_unload
```
Then everything is fine.  Hardy needs to have an NDISwrapper version of 1.50 or greater.

If you see something like:
```
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
modinfo: could not open ndiswrapper: Invalid argument

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net
```
Then you might try another version of NDISwrapper.  If you used the NDISwrapper from the Ubuntu repository and you are up to date on updates, try compiling NDISwrapper from source.  [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) has instructions on how to do this.  If you already compiled from source, try another version.

TSN 2.1:
Verify which driver is being used by NDISwrapper:
```
ndiswrapper -l
```
You should see something like:
```
bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: ssb)
```
You want to be able to see that bcmwl5 is there and it says driver installed.  Sometimes the alternate driver shows up, but it is ok.  If you don't see bcmwl5, then the correct driver is not installed.  Check [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) or [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net) for suggested drivers.

TSN 2.1.1:
I have an invalid driver that I want to remove:
```
sudo ndiswrapper -e <driver>
```
If anything shows up as an error, most likely you have the wrong driver.

TSN 2.2.2:
Check for conflicting modules:
NDISwrapper cannot have b43, b43legacy, or bcm43xx drivers running at the same time.  Not only that, it has to be loaded before ssb(not a Hardy bug, but kernel design).  ssb is a new module that was introduced with the new b43/b44 modules.  The b43 and b44 modules need it to run.  Check and see if any of the modules are running
```
lsmod|grep -i -e b43 -e b44 -e bcm43xx -e ssb
```
Keep track of the list of modules that show up.  We will need to make sure that they do not get loaded in the future.  If any of the bcm43xx, b43, b43legacy, b44, or ssb show up, they will need to be removed before trying to load NDISwrapper.  Do the following to remove the module:
```
sudo modprobe -r <module>
```
You can do multiple modules at the same time (i.e. sudo modprobe -r bcm43xx b43 b44 ssb).  You only have to remove the modules that show up from the lsmod command.  Make sure that ssb is the last module to be removed.  Since other modules depend on it, it will not allow you to remove it until the others have been removed.

We now need to make sure that NDISwrapper is not loaded:
```
sudo modprobe -r ndiswrapper
```

Now we can try loading NDISwrapper again:
```
sudo modprobe ndiswrapper
```

Now check and see if your wireless is working.  If it does and you had b44 show up in your lsmod query, you will need to load this module back:```
sudo modprobe b44
```
This is your wired module.  Without it, your wired connection will not work.

If you don't have b44 in your lsmod list:
If all is working, you will need to blacklist bcm43xx, b43, b43legacy, and possibly ssb.  To blacklist them, do the following:
```
echo blacklist <module>|sudo tee -a /etc/modprobe.d/blacklist
```
Replace <modulle> with either bcm43xx, b43, b43legacy, or ssb.  Do it for each module.  This will add the modules to the end of the blacklist file.

If you do have b44 in your lsmod list:
If you have bcm43xx in your lsmod list, blacklist it:
```
echo <module>|sudo tee -a /etc/modprobe.d/blacklist
```
For the rest, refer to [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-a9c75e76532933266fabeef1b1aa742f3df4444c) and choose one of the versions.

Make sure that b43/b43legacy/bcm43xx are not in /etc/modules:
```
cat /etc/modules
```
If you see any of them without a # in front of it, you will need to edit the file and place a # in front of it:
```
gksu <gedit/kate>
```
Choose either kate(Kubuntu) or gedit(Other Ubuntu version) or you can use your favorite editor.  Just make sure that you update the file with sudo/root privilege or else it will not save (/etc is a protected directory).

---

### Post by vociferous666 on 2008-05-27
thanks mate!!!

ive been wondering about the various commands used for troubleshooting modules and especially my wireless.  i got halfway through your guide and my wireless was up and running.  took less than 5 minutes!

dreadfully awesome guide.   many thanks.

---

