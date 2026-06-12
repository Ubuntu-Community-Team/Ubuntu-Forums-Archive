---
title: "gtkwhiteboard fails to connect to wiimote"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by Statik on 2010-01-27
Hi all,

Just saw the Johnny Lee's video and thought I'd look into linux versions of his software. Low and behold an ubuntu version! So, I sudo apt-get install gtkwhiteboard

This gives me a runnable application. I click on connect and follow the instructions but nothing connects.

So, I run it in terminal. Here is the output:
```
statik@statik-laptop:~$ gtkwhiteboard
running new thread self.w.connect
inquiry complete
Unhandled exception in thread started by 
Traceback (most recent call last):
  File "/usr/share/gtkwhiteboard/whiteboard.py", line 258, in Connect
    self.wiimote.Connect()
  File "/usr/share/gtkwhiteboard/linuxWiimoteLib.py", line 213, in Connect
    self.isocket.connect((self.bd_addr,19))
  File "<string>", line 5, in connect
bluetooth.btcommon.BluetoothError: (22, 'Invalid argument')

```

I have connected and tested the wiimote with wmgui and everything works.

Any ideas?

Thanks,
Statik

---

### Post by J V on 2010-01-27
looks like sloppy programming to me... someone used "<var>" rather than $var, idk how to fix it exactly, but if you take a 10 minute python course you should be able to tinker it yourself ;)

---

### Post by Statik on 2010-01-27
From what I can see, its an issue with the Python-Bluez module. There is a patch, which I don't know how to use, and the patch is encorporated into version 0.18 of python-bluez. However, the repositories only have 0.16

Can't seem to fix this.

The patch is at [http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg660555.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg660555.html)

Statik

---

### Post by Statik on 2010-01-28
Well, since I couldn't get the gtk whiteboard to work, I went looking for other solutions. I have 2 working ones now.

[http://www.uweschmidt.org/wiimote-whiteboard](http://www.uweschmidt.org/wiimote-whiteboard)

The instructions here: [http://wiki.uweschmidt.org/WiimoteWhiteboard/Troubleshooting](http://wiki.uweschmidt.org/WiimoteWhiteboard/Troubleshooting) which point to a forum post as well, worked great.

This one seems a little slower, which is expected since it runs in Java but the calibration is quick, the UI is nice and it just works.

[http://code.google.com/p/linux-whiteboard/](http://code.google.com/p/linux-whiteboard/)

Had trouble getting this one working originally. The build instructions just don't work. However, found the easy way to install it.

To use it, use the svn checkout here: [http://code.google.com/p/linux-whiteboard/source/checkout](http://code.google.com/p/linux-whiteboard/source/checkout)

then go into the build directory and run the make-deb.sh script. This builds a deb in its root directory which you can then install.
I found the calibration harder in this because it requires you to hold the pen still for 10 seconds or so, for each corner. Takes longer and can be frustrating to calibrate.

Minorly faster than the Java app above. Gui is much more basic.

I have not tried the python-whiteboard referenced on the site.

Statik

---

### Post by bh56 on 2010-07-30
Morning
I've followed the instructions to install Wiimote Whiteboard on Linux (ie bluecove.jar) but when the application is started i get:
31/07/2010 10:43:09 AM com.sun.corba.se.impl.ior.IORImpl getProfile
WARNING: "IOP00511201: (INV_OBJREF) IOR must have at least one IIOP profile"
org.omg.CORBA.INV_OBJREF:   vmcid: SUN  minor code: 1201  completed: No
	at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:473)
	at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:495)
	at com.sun.corba.se.impl.ior.IORImpl.getProfile(IORImpl.java:334)
	at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:787)
	at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:761)
	at com.sun.corba.se.impl.encoding.CDRInputStream.read_Object(CDRInputStream.java:231)
	at com.sun.corba.se.impl.resolver.INSURLOperationImpl.getIORFromString(INSURLOperationImpl.java:120)
	at com.sun.corba.se.impl.resolver.INSURLOperationImpl.operate(INSURLOperationImpl.java:130)
	at com.sun.corba.se.impl.orb.ORBImpl.string_to_object(ORBImpl.java:836)
	at org.GNOME.Accessibility.AccessUtil.getRegistryObject(AccessUtil.java:143)
	at org.GNOME.Accessibility.JavaBridge.registerApplication(JavaBridge.java:1147)
	at org.GNOME.Accessibility.JavaBridge.<init>(JavaBridge.java:398)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:372)
	at java.lang.Class.newInstance(Class.java:325)
	at java.awt.Toolkit.loadAssistiveTechnologies(Toolkit.java:786)
	at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:875)
	at java.awt.Toolkit.getEventQueue(Toolkit.java:1698)
	at java.awt.EventQueue.invokeLater(EventQueue.java:957)
	at javax.swing.SwingUtilities.invokeLater(SwingUtilities.java:1292)
	at org.jdesktop.application.Application.launch(Application.java:181)
	at org.uweschmidt.wiimote.whiteboard.WiimoteWhiteboard.main(WiimoteWhiteboard.java:79)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.simontuffs.onejar.Boot.run(Boot.java:306)
	at com.simontuffs.onejar.Boot.main(Boot.java:159)
JarClassLoader: Warning: Unable to load native library: java.lang.NullPointerException
Native Library bluecove not available
java.lang.IllegalStateException: Bluetooth failed to initialize. There is probably a problem with your local Bluetooth stack or API.
	at wiiremotej.WiiRemoteJ.<clinit>(WiiRemoteJ.java:74)
	at org.uweschmidt.wiimote.whiteboard.WiimoteConnector.connect(WiimoteConnector.java:48)
	at org.uweschmidt.wiimote.whiteboard.WiimoteDataHandler.<init>(WiimoteDataHandler.java:84)
	at org.uweschmidt.wiimote.whiteboard.WiimoteWhiteboard.startup(WiimoteWhiteboard.java:99)
	at org.jdesktop.application.Application$1.run(Application.java:171)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)
Caused by: javax.bluetooth.BluetoothStateException: BlueCove library bluecove not available
	at com.intel.bluetooth.BlueCoveImpl.loadNativeLibraries(BlueCoveImpl.java:381)
	at com.intel.bluetooth.BlueCoveImpl.detectStack(BlueCoveImpl.java:429)
	at com.intel.bluetooth.BlueCoveImpl.access$500(BlueCoveImpl.java:65)
	at com.intel.bluetooth.BlueCoveImpl$1.run(BlueCoveImpl.java:1020)
	at java.security.AccessController.doPrivileged(Native Method)
	at com.intel.bluetooth.BlueCoveImpl.detectStackPrivileged(BlueCoveImpl.java:1018)
	at com.intel.bluetooth.BlueCoveImpl.getBluetoothStack(BlueCoveImpl.java:1011)
	at javax.bluetooth.LocalDevice.getLocalDeviceInstance(LocalDevice.java:75)
	at javax.bluetooth.LocalDevice.getLocalDevice(LocalDevice.java:95)
	at wiiremotej.WiiRemoteJ.<clinit>(WiiRemoteJ.java:67)
	... 12 more
31/07/2010 10:43:15 AM org.uweschmidt.wiimote.whiteboard.WiimoteWhiteboard startup
SEVERE: Error on startup
java.lang.IllegalStateException: Bluetooth failed to initialize. There is probably a problem with your local Bluetooth stack or API.
	at wiiremotej.WiiRemoteJ.<clinit>(WiiRemoteJ.java:74)
	at org.uweschmidt.wiimote.whiteboard.WiimoteConnector.connect(WiimoteConnector.java:48)
	at org.uweschmidt.wiimote.whiteboard.WiimoteDataHandler.<init>(WiimoteDataHandler.java:84)
	at org.uweschmidt.wiimote.whiteboard.WiimoteWhiteboard.startup(WiimoteWhiteboard.java:99)
	at org.jdesktop.application.Application$1.run(Application.java:171)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:602)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)
Caused by: javax.bluetooth.BluetoothStateException: BlueCove library bluecove not available
	at com.intel.bluetooth.BlueCoveImpl.loadNativeLibraries(BlueCoveImpl.java:381)
	at com.intel.bluetooth.BlueCoveImpl.detectStack(BlueCoveImpl.java:429)
	at com.intel.bluetooth.BlueCoveImpl.access$500(BlueCoveImpl.java:65)
	at com.intel.bluetooth.BlueCoveImpl$1.run(BlueCoveImpl.java:1020)
	at java.security.AccessController.doPrivileged(Native Method)
	at com.intel.bluetooth.BlueCoveImpl.detectStackPrivileged(BlueCoveImpl.java:1018)
	at com.intel.bluetooth.BlueCoveImpl.getBluetoothStack(BlueCoveImpl.java:1011)
	at javax.bluetooth.LocalDevice.getLocalDeviceInstance(LocalDevice.java:75)
	at javax.bluetooth.LocalDevice.getLocalDevice(LocalDevice.java:95)
	at wiiremotej.WiiRemoteJ.<clinit>(WiiRemoteJ.java:67)
	... 12 more
I've used both Linux Mint and Puppy Linux and get the same bluetooth error. I assume the bluetooth stack is working on both distributions as I can connect to my phone using bluetooth.
On Linux Mint I disabled the bluetooth manager in case it was interfering with the application but I still get the same error.
Can any one help? Thanks
Brendan

---

