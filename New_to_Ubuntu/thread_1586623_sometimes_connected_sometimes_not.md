---
title: "sometimes connected sometimes not"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by gotchanisa on 2010-10-02
Hi there,

Though I have registered on these forums a long time ago, I'm really a newbee. I've just installed 10.04 on a dell 610 laptop and was having connection issues. But I was able to get some help and was able to get back online. Now for some reason, I'm facing a similar issue. This time, I'm not even able to ping. It just comes back saying cannot find ubuntu.com. Sometimes the network connections says disconnected. Right now it is connected. I was able to connect and download all the updates available.

I don't know if trying to troubleshoot wireless issues was causing this issue. But I've not really got anywhere here also. I haven't even able to enable the wireless connection. It is grayed out. I'm not sure if it has got to do with drivers.

Now I know one of you is going to ask me to paste the output of lspci. I'm posting this on a windows machine and wondering if there is a faster way than typing it all!

HELP!!

---

### Post by gotchanisa on 2010-10-02
I'd appreciate it very much if anyone could help. Just point me to a thread that could help. I've searched for over an hour and haven't found a similar situation.

---

### Post by mörgæs on 2010-10-02
Does it work with 9.10 or 10.10?

---

### Post by gotchanisa on 2010-10-02
I haven't tried. I just installed 10.04 and it was working for a while... I don't have 9.10... You recommend downloading 10.10? Isn't it in Beta?

---

### Post by JBAlaska on 2010-10-02
10.04 will work fine with your laptop. To get your wireless working correctly:
Put the Ubuntu LiveCD in your drive and go to: **System, Administration, Software sources** and check the box below "Installable from CDROM". Then open a terminal and do:
```
sudo apt-get update
```

Then:
```
sudo apt-get install bcmwl-kernel-source
```

Now reboot and select the **BroadcomSTA** driver in **System, Administration, Hardware Drivers** Reboot again and your wireless should work.

---

### Post by gotchanisa on 2010-10-03
Thanks for the reply. I did exactly as described above but no drivers:( . When i open hardware drivers from system administration, It just says No proprietary drivers are in use on this system. 

Was the CD supposed to be in the system while restarting or do I remove it, restart it and then place it in? It was trying to install ubuntu again after the restart, so I removed it, restarted, placed it inside and followed the steps.

Now my wired connection is detected. But I'm unable to ping. It says the address .... cannot be found.

Now what do I do?

---

### Post by JBAlaska on 2010-10-03
Can you paste the text following this command:
```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by gotchanisa on 2010-10-03
ifconfig eth1 gives me

eth1 Link encap:Ethernet HWaddr 00:13:ce:d7:99:a6
Broadcast muclticast MTU:1500 Metric:1
RX packets:0 dropped:0 overruns:0 frame:0
TX pakets:0 dropped:0 overruns:0 frame:0
collisions:0 txquelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:17 Base address:0x4000 Memory:dfcff000-dfcfffff

---

### Post by gotchanisa on 2010-10-03
Oops... posted at the same time
Anyway, the reply it gives is 
E: Couldn't find package bcwl-kernel-source

---

### Post by JBAlaska on 2010-10-03
Did you Put the Ubuntu LiveCD in your CD drive and go to: **System, Administration, Software sources** and **check the box below "Installable from CDROM"**?

Then close that window, update your scorces list with the:
```
sudo apt-get update
```

Then try:
```
sudo apt-get install bcmwl-kernel-source
```

It should install bcmwl-kernel-source and after you reboot (With the CD [COLOR="Red"]out[/COLOR] of the drive), you should see the Broadcom STA driver in **System, Administration, Hardware Drivers** Enable it and reboot again and your wireless should work fine.

---

### Post by gotchanisa on 2010-10-03
I've done it again just like you described above. After the reboot, I continue to get No proprietary drivers are in use on this system. And the box is empty.

I also tried pinging the router with 192.168.1.1 and it was able to get through with 100% success.
The last time I could ping but I couldn't browse. Now I can't do both. Can someone check if my DNS settings are correct?

---

### Post by JBAlaska on 2010-10-03
I hate to keep harping on this, but if you want your native wireless card to work you are going to **HAVE** to install **bcmwl-kernel-source**

Again what text do you get when you enter:
```
sudo apt-get install bcmwl-kernel-source
```

If it still says "E: Couldn't find package bcwl-kernel-source" **you must not have your sources configured correctly or your Ubuntu LiveCD is not being read properly.**

As far as DNS servers for your wired connection, use 8.8.8.8[COLOR="Red"],[/COLOR]8.8.4.4

If you get your wired connection working with the above DNS, you can forget the LiveCD and enable the **restricted (multiverse)** repository, under **System, Administration, Software sources**, then install bcmwl-kernel-source and note the text, if it installs you can reboot and enable the driver, if it does not install, you are missing a step.

---

### Post by gotchanisa on 2010-10-03
Sorry if I'm not doing something correctly. Please bear with me. 
This is what I get when I run the sudo apt-get install bcwl-kernel-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package bcwl-kernel-source


All this I did when the cd was inside the system. It is the same CD that I used to install UBUNTU. I have restarted the system and when I go to hardware drivers, it searches for a while can comes back with the same message - No proprietary drivers are in use on this device.

Can you tell me how to manually enter/change the DNS information?

---

### Post by JBAlaska on 2010-10-03
> **gotchanisa said:**
> Sorry if I'm not doing something correctly. Please bear with me. 
This is what I get when I run the sudo apt-get install bcwl-kernel-source
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: **Couldn't find package [COLOR="Red"]bcwl[/COLOR]-kernel-source**


All this I did when the cd was inside the system. It is the same CD that I used to install UBUNTU. I have restarted the system and when I go to hardware drivers, it searches for a while can comes back with the same message - No proprietary drivers are in use on this device.

Can you tell me how to manually enter/change the DNS information?

No problem, we'll get it, looking at the above error I think the command was misspelled (In red), It has to be exactly:
```
sudo apt-get install bcmwl-kernel-source
```

To set your dns, right click on the network-manager applet (next to the clock) and choose edit connections, then hilight the connection you want to modify and click edit. uncheck automatic and enter your ip,dns,gateway etc.

Hope this helps, Late here, I'll check this post in the morning. Good Luck

---

### Post by gotchanisa on 2010-10-03
Terribly sorry about the typo. This time, it didn't give me the same error. It went ahead and installed something. However, I still don't see anything when I go to hardware drivers.
This is what I get when I use this ```
sudo apt-get install bcmwl-kernel-source
```

Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot patch
Suggested packages:
diffutils-doc
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot patch
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get1,205kB of archives
After this operation 3,764KB of additional disk space will be used.
Do you want to condinue Y
WARNING: The following packages cannot be authenticated!
  dkms bcmwl-kernel-source fakeroot
Install these packages without verification y
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main dkms 2.1.1.2-2fakesync1
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid restricted  bcmwl-kernel-source 5.60.48.36+bdcom 0ubuntu3
  Something wicked happened in resolving 
'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main fakeroot 1.14.4-lubuntul1
Something wicked happened in resolving 
'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main patch 2.6-2ubuntu1
Something wicked happened in resolving 
'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.1.1.2-2fakesync1_all.deb)
Something wicked happened in resolving 
'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot_1.14.4-1ubuntu1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot_1.14.4-1ubuntu1_i386.deb)
Something wicked happened in resolving 
'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i286.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/p/patch/patch_2.6-2ubuntu1_i286.deb)

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


 Whew.... that was a marathon typing session.
Lots of wicked things happening on my system. Help!!

---

### Post by Irony on 2010-10-03
I assume that JBAlaska means for you to install the bcmwl kernel source from the cd, i.e. boot up as normal into ubuntu, now stick the live cd disk in and then go to synaptic and tick the cdrom in repositories and install the the package.

Do not boot from the cd.

However if you have an internet connection via wire then install the package from the web as normal and don't bother with the cd.

However, I have no idea what one actually does with the bcmwl kernel source package once it is installed.

---

### Post by Irony on 2010-10-03
> **gotchanisa said:**
> Whew.... that was a marathon typing session.
Lots of wicked things happening on my system. Help!!
I hope you are joking as you should just paste the output in, and also put code tags around it like this;

```
I hope you are joking as you should just paste the output in, and also put code tags around it like this;
```

---

### Post by gotchanisa on 2010-10-03
No I'm not joking.
Since I don't have connectivity on the Ubuntu, I have to type out exactly what I see on the windows pc. Is there a faster way?

---

### Post by mörgæs on 2010-10-04
If you have a USB stick you could paste the screen output to a file, save it on the USB stick and move it to the windoze machine.

---

### Post by gotchanisa on 2010-10-04
Thanks for the idea. Now can someone help me with my connectivity issue please?

Perhaps I should install 8.04 and try?

---

### Post by gotchanisa on 2010-10-06
Here is my daily quota of 1 bump. Can some help me get connected please:confused:

---

### Post by gotchanisa on 2010-10-07
Went back to 8.04 and both wired and wireless connections are working. I'm currently installing the updates ... and enjoying the connectivity :)

I will try to upgrade when 10.10 goes GM.

---

