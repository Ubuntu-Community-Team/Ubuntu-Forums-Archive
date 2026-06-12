---
title: "USB Modem installer"
date: 2017-12-17
forum: Networking &amp; Wireless
---

### Post by Hari5g900 on 2017-12-17
Recently bought a USB Modem (3G) for my laptop as I found myself traveling a lot to places with no WI-fi or 4G. I don't like setting up hot-spots from my phone as it runs it's battery dry in about 1 hour. I dual boot my laptop with Windows 10 and Ubuntu 16.04. While the thing works like a charm on Windows, I can't receive SMS's on Ubuntu (I use the mobile broadband option in network manager). The modem comes with a linux installer, but It doesn't want to work. It's a tar.gz package, so I extracted it to my desktop. Ran 'install.sh' but I required root permissions, so I did this:

```
 
sudo '/home/liney/Desktop/pcl_india_channel/install.sh' 
[sudo] password for liney: 
..................start install.................
*** Check for root...ok...
/PCCFG/Description.xml,/tmp/two_phase_temp/Description.xml
Device is open : (0x19d2, 0x1594)
stage 1
stage 2
Stage 3
cp: cannot stat 'ZTE.tar.gz': No such file or directory
tar (child): ZTE.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
chmod: cannot access '/opt/ZTE/usr/share/applications/ZTE.desktop': No such file or directory
cp: cannot stat '/opt/ZTE/usr/share/applications/ZTE.desktop': No such file or directory
chmod: cannot access '/opt/ZTE/usr/share/pixmaps/ZTE.png': No such file or directory
cp: cannot stat '/opt/ZTE/usr/share/pixmaps/ZTE.png': No such file or directory
ls: cannot access '/usr/share/applications/desktop.*.cache': No such file or directory
/home/liney/Desktop/pcl_india_channel/install.sh: line 382: cd: /opt/ZTE/usr/lib: No such file or directory
cp: cannot stat 'UniCodec.so': No such file or directory
cp: cannot stat 'UniDevManager.so': No such file or directory
cp: cannot stat 'UniSdk.so': No such file or directory
cp: cannot stat 'UniVousb.so': No such file or directory
cp: cannot stat 'CoreSDK.so': No such file or directory
cp: cannot stat '/opt/ZTE/bin/ZTE.conf': No such file or directory
chmod: cannot access '/opt/ZTE/pppd/ip-up.local': No such file or directory
cp: cannot stat '/opt/ZTE/pppd/ip-up.local': No such file or directory
chmod: cannot access '/opt/ZTE/pppd/ip-down.local': No such file or directory
cp: cannot stat '/opt/ZTE/pppd/ip-down.local': No such file or directory
chmod: cannot access '/opt/ZTE/pppd/get_route_info': No such file or directory
cp: cannot stat '/opt/ZTE/pppd/get_route_info': No such file or directory
/home/liney/Desktop/pcl_india_channel/install.sh: line 557: /opt/ZTE/bin/SysPATH: No such file or directory
/home/liney/Desktop/pcl_india_channel/install.sh: line 558: cd: /opt/ZTE/bin: No such file or directory
sed: can't read SameNameSh: No such file or directory
chmod: cannot access '/opt/ZTE/bin/ZTE': No such file or directory
cp: cannot stat '/opt/ZTE/bin/ZTE': No such file or directory
chmod: cannot access '/opt/ZTE/Data/aplay.sh': No such file or directory
chmod: cannot access '/opt/ZTE/Data/launchFirefox.sh': No such file or directory
chmod: cannot access '/opt/ZTE': No such file or directory
chown: cannot access '/opt/ZTE/ZTE': No such file or directory
chmod: cannot access '/opt/ZTE/ZTE': No such file or directory
chmod: cannot access '/opt/ZTE/ZTE': No such file or directory
chmod: cannot access '/opt/ZTE/uninstall.sh': No such file or directory
chmod: cannot access '/opt/ZTE/wirelessconfig': No such file or directory
chmod: cannot access '/opt/ZTE/wirelessconfig/*': No such file or directory
chmod: cannot access '/opt/ZTE/scripts/*': No such file or directory
******Begin to /opt/ZTE/driver
/home/liney/Desktop/pcl_india_channel/install.sh: line 625: cd: /opt/ZTE/driver: No such file or directory
chmod: cannot access 'driver_install.run': No such file or directory
/home/liney/Desktop/pcl_india_channel/install.sh: line 627: ./driver_install.run: No such file or directory
libphonon.so libphonon.so.4 libphonon.so.4.4 libQtCore.so libQtCore.so.4 libQtCore.so.4.7 libQtDBus.so libQtDBus.so.4 libQtDBus.so.4.7 libQtGui.so libQtGui.so.4 libQtGui.so.4.7 libQtNetwork.so libQtNetwork.so.4 libQtNetwork.so.4.7 libQtSql.so libQtSql.so.4 libQtSql.so.4.7 libQtWebKit.so libQtWebKit.so.4 libQtWebKit.so.4.7 libQtXml.so libQtXml.so.4 libQtXml.so.4.7 wine-devel ZTE End to /opt/ZTE/driver
/home/liney/Desktop/pcl_india_channel/install.sh: line 633: cd: /opt/ZTE/driver: No such file or directory
chmod: cannot access 'se': No such file or directory
cp: cannot stat '/opt/ZTE/bin/9-cdrom.rules': No such file or directory
cp: cannot stat '/opt/ZTE/bin/7-zte-mutil_port_device.rules': No such file or directory
udevadm is exist!
install completed!!!
....After setup, you will find the ZTE in "Applications->Internet->ZTE". Click the ZTE and the application will run
press any key to continue.... 
/home/liney/Desktop/pcl_india_channel/install.sh: line 701: ZTE: command not found

```

Way too many "no such file or directory"... Maybe I need to install something to read those files?

---

### Post by sisco311 on 2017-12-17
It looks like the script tries to copy the files from the current working directory. I'd try:```
cd ~/Desktop/pcl_india_channel
sudo ./install.sh
```

---

### Post by Hari5g900 on 2017-12-17
Welp! That worked! That was such a stupid mistake on my part. I've had this problem before and I solved it, somehow I forgot it this time.

---

