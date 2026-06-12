---
title: "remote desktop login with kubuntu"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by myname on 2007-02-01
Hello, 

I am trying to set up my work machine with remote desktop.  I am running Kubuntu Edgy, and trying to follow the information here:

[http://ubuntuguide.org/wiki/Ubuntu:Edgy#Remote_Desktop_Sharing.2FDuplication_via_VNC](http://ubuntuguide.org/wiki/Ubuntu:Edgy#Remote_Desktop_Sharing.2FDuplication_via_VNC)

I can't find the section they list.  However, under Internet, I found the krfb app, and ran that, set it up with uninvited connections.  When I try to connect to it from a Mac OSX box using Chicken of the VNC, my krfb session crashes.  Anyone else experience the kfrb server crashing?  Do I need to install another VNC server on kubuntu?

any help is always appreciated.

--Kevin

---

### Post by squirrel_f13 on 2007-02-09
I have a MBP and the popular program "Chicken of the VNC" was terribly slow when connecting to my Ubuntu machine under OS X. If you're looking for easy performance gains download the Java client for tightVNC and use it under OS X. It allows you to disable a couple things (mouse side pointer - brutal under Chicken) that makes it WAY faster. VNC is useable now.

You do need a bash script to launch the java viewer on OS X easily (otherwise you have to do it manually via terminal).

Although Chicken is supposed to be great (and it may be) I've had nothing but problems with it.

```
#!/bin/bash
cd /Users/PATH/tightvnc/classes
java VncViewer HOST "HOST-IP" PORT 5900
```

---

### Post by chuck2 on 2007-08-02
I have the same problem when using realvnc in windows.

Is there any fixes for this yet?

---

