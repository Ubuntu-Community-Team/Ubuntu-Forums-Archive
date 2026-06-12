---
title: "KVpnc crash"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by gchiacch on 2010-11-11
Hello to everybody!
I'm having problem with the starting of kvpnc, I am trying this application since few days and until yesterday the application started giving problems during connect, I found an interesting thread at ([http://linuxfreedom-technoshaun.blogspot.com/2008/11/how-to-configure-ubuntu-pptp-vpn-client.html](http://linuxfreedom-technoshaun.blogspot.com/2008/11/how-to-configure-ubuntu-pptp-vpn-client.html)  )  that I would like to apply and see it helps but unlikely since yesterday the kvpnc application refuse to start anymore that is it crash on every attempt to start even after system reboot. 
I reported this problem through the Reporting Assistant which lead to the creation a bug report in the KDE bug reporting system  (256613) and I got the following answer :  "_Please report this bug to your distribution and ask them to either update KDE or KVpnc_"  I downloaded Ubuntu 10.04 from Ubuntu home page some weeks ago and then upgraded to 10.10
From here on I do not know how to proceed further. KVpnc was installed by Synaptic Package Manager and I also uninstalled/installed it again but it did not help. Would someone be so kind to help me to find out what I should exactly do for applying the underlined above suggestion?   Thank you in advance.

---

### Post by gchiacch on 2010-11-12
problem solved by uninstall/reload sources/install.   In previous attempt I was just uninstall/install the KVpnc.

---

### Post by mxconsult on 2010-11-17
Can you please clarify how did you reload the sources?

---

### Post by gaxi on 2010-11-22
I did it that way:

dpkg --remove kvpnc
dpkg --remove kvpnc-data
dpkg --purge kvpnc
dpkg --purge kvpnc-data
 apt-get update
apt-get install kvpnc

There ARE more efficient ways to to this, anyway this is how I actually did it.

I have to start kvpnc by sudo kvpnc, with the shortcut via Applications/Internet it does not start on my computer.

GaXi

---

