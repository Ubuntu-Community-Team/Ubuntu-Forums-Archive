---
title: "VPN client Release 4.8.00.0490 installation on Ubuntu"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by mitchelljj on 2008-02-27
Hi,

I need to know if I can install VPN client Release 4.8.00.0490 on Ubuntu, and if so how do I install it.  The installation file is called vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz, and I have attached the readme file.

Thanks,

John

---

### Post by undadecor on 2008-02-27
Try checking this out:  [4.8.00.0490 on Feisty Fawn]("http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/")

---

### Post by mitchelljj on 2008-03-02
I installed VPN client Release 4.8.00.0490 installation on Ubuntu and it said that it successfully installed and also it successfully connected.  Doing installation it said that it would automatically execute the VPN client during restart, but how do I know that the it was successfully connected?
I tried to manually reconnect via "sudo vpnclient connect InSequence" and it gave an error which I have attached.

Thanks,

John

---

### Post by fromans on 2008-04-11
It does not automatically load the module on startup. The installation claims to have that option but from my experience it is lying. You will just have to start the service when you want to use the vpn client. You will only have to do this once, until you reboot. 

```
sudo /etc/init.d/vpnclient_init start
```

Bearing any typos on my part (this is from memory), that should do the trick and you can then start your session.

```
vpnclient connect <profile>
```

---

### Post by mawalters1 on 2008-07-14
Since this is an old thread the issue is no longer valid, however for others. 

Once the module is compiled for your kernel, using driver_build.sh, then you can do the install.  I had to modify the source interceptor.c file due to a binary operator exception, ask for details if same issue.

During the execution of vpn_install, it will as if you want start the service automatically,  specfically it asks,  "Automatically start the VPN service at boot time"  If you answer yes, it will hook into your runlevel, theoretically, I chose to start manually.

My issue start after I execute /etc/init.d/vpnclient_init start
then execute:   (the default install area)
/opt/cisco-vpnclient/bin/./vpnclient 
My system locks up, no mouse no keyboards, have to hard reset system.

Currently I am looking for some user documentation.

---

