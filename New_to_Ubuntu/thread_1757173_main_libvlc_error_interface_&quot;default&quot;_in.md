---
title: "main libvlc error: interface &quot;default&quot; initialization failed"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by apurvtwr on 2011-05-13
Hi,
I am not sure if this is the right forum to ask this question, if so please redirect me to the correct forum.

Everything was fine until VLC player on my Ubuntu 10.10 suddenly decides to quit working.
If started from terminal, I get the following log:
[COLOR=Red]VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x81ac63c] main interface error: no suitable interface module
[0x8101914] main libvlc error: interface "default" initialization failed[/COLOR]

Any ideas?
Thanks

---

### Post by varunendra on 2011-05-13
Try uninstalling then reinstalling vlc:
```
sudo apt-get purge vlc
```

then, two precautionary steps (not always necessary)
```
sudo apt-get clean
sudo apt-get autoremove
```
The first command will empty your apt-cache (packages downloaded with apt). So back up your /var/cache/apt/archives directory if you want to keep those packages.
The second command will remove all those packages that are no longer required.

then, reinstall vlc:
```
sudo apt-get install vlc
```

---

### Post by apurvtwr on 2011-05-14
Thanks Varun!
But vlc still doesn't work :confused: .
Actually, now that I notice, anything working on qt4 doesn't work. 
I recently got a new data card which ships with a Linux installer. I guess it's GUI uses qt4. vlc (and every other application on qt4) works perfectly when I uninstall this application.
I would however prefer having a workaround rather than having it uninstalled permanently.

Thanks.

---

### Post by varunendra on 2011-05-14
Post back the output of:
```
ldconfig -p | grep -i libqt
```
Run this command while that data card application is installed.

---

### Post by apurvtwr on 2011-05-14
Here is the output:
```

    libQt3Support.so.4 (libc6) => /usr/lib/libQt3Support.so.4
    libQtXmlPatterns.so.4 (libc6) => /usr/lib/libQtXmlPatterns.so.4
    [COLOR=Red]libQtXml.so.4 (libc6) => /opt/3GModem/3rd_setup/3rd/libQtXml.so.4[/COLOR]
    libQtXml.so.4 (libc6) => /usr/lib/libQtXml.so.4
    libQtWebKit.so.4 (libc6) => /usr/lib/libQtWebKit.so.4
    libQtSvg.so.4 (libc6) => /usr/lib/libQtSvg.so.4
   [COLOR=Red] libQtSql.so.4 (libc6) => /opt/3GModem/3rd_setup/3rd/libQtSql.so.4[/COLOR]
    libQtSql.so.4 (libc6) => /usr/lib/libQtSql.so.4
    libQtScript.so.4 (libc6) => /usr/lib/libQtScript.so.4
    libQtOpenGL.so.4 (libc6) => /usr/lib/libQtOpenGL.so.4
    libQtNetwork.so.4 (libc6) => /usr/lib/libQtNetwork.so.4
   [COLOR=Red] libQtGui.so.4 (libc6) => /opt/3GModem/3rd_setup/3rd/libQtGui.so.4[/COLOR]
    libQtGui.so.4 (libc6) => /usr/lib/libQtGui.so.4
    libQtDesignerComponents.so.4 (libc6) => /usr/lib/libQtDesignerComponents.so.4
    libQtDesigner.so.4 (libc6) => /usr/lib/libQtDesigner.so.4
   [COLOR=Red] libQtDBus.so.4 (libc6) => /opt/3GModem/3rd_setup/3rd/libQtDBus.so.4[/COLOR]
    libQtDBus.so.4 (libc6) => /usr/lib/libQtDBus.so.4
   [COLOR=Red] libQtCore.so.4 (libc6) => /opt/3GModem/3rd_setup/3rd/libQtCore.so.4[/COLOR]
    libQtCore.so.4 (libc6) => /usr/lib/libQtCore.so.4
    libQtCLucene.so.4 (libc6) => /usr/lib/libQtCLucene.so.4
```
The ones I marked red are dependencies from the new installation.
Thanks again.

---

