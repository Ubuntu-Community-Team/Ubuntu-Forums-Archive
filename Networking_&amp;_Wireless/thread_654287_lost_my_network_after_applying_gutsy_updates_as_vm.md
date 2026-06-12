---
title: "lost my network after applying gutsy updates as vmware guest"
date: 2007-12-30
forum: Networking &amp; Wireless
---

### Post by RobertGloverJr on 2007-12-30
I installed Gutsy on a Dell 1420n using the DELL Gutsy ISO and then installed a licensed copy of VMware Workstation 6.02.  Then I installed Gutsy as a guest using the official Gutsy install CD from Ubuntu (not the DELL Gutsy ISO).
   The Guest Gutsy worked fine and the networking was working. (I used the "NAT" vmware network config option).  I could use Firefix to surf the net okay.  
    Then I downloaded and installed all the Gutsy updates using the Update Manager. It said the updates were all applied perfectly.
It then said I should re-boot Gutsy.
     When Gutsy (the guest) came back up I had lost all networking. Runningg "ifconfig" shows only "lo"  (127.0.0.l) and nothing else.
    Before I lost my network by applying the Gutsy updates, running "ifconfig" showed (in addition to "lo":

> dgg2@rdgg2-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0C:29:89:34:22 
          inet addr:192.168.216.129  Bcast:192.168.216.255   Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe89:3422/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:859 errors:0 dropped:0 overruns:0 frame:0
          TX packets:549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1158480 (1.1 MB)  TX bytes:50663 (49.4 KB)
          Interrupt:16 Base address:0x2000


   I'm a newbie to Vmware and Ubuntu. 

    I defined a 2nd Guest machine and did the entire process a second time, and got the exact same results:  I lost my network as soon as I rebooted after applying the Gutsy updates.

    I would very much appreciate suggestion on what command to issue or what files to edit in order to get my network back.  I'm going to define a 3rd guest machine and install Gutsy a 3rd time, install the VMWare tools, and then use that as a reference to see if I can figure out what the difference is between that guest (where networking will fine) versus the other two guests where there is no networking.  I have not idea what to look for in comparing them, but I don't know what else to do.

---

### Post by IQworks on 2007-12-31
I have got the exact same thing. After updating from 7.04 to 7.10 i lost my network interface as well. My VMWARE is in bridged mode.
Probably some driver issue...

---

### Post by IQworks on 2007-12-31
It appears only DHCP and automatic adressing isn't working. I set my adress statically and everything is working fine. 
I presume a bug in the dhcp client.

---

### Post by RobertGloverJr on 2008-01-02
Can someone provide step by step instructions on how to get "eth0" back please.  I did not expect an update to Ubuntu Gutsy to make the network stop working.  I cannot get anymore Ubuntu Gutsy updates now because I don't have a network anymore.  
       I tried the advice of using a static IP address  but it does not work or else I don't know how to do it correctly.  I tried to do it in the "...manual configuration" option of the network application that has an icon on the top right in Gutsy.
      Please see my original post that started this thread and provide me step-by-step instructions on what to do.
      This is a really big disappointment because I have such great plans to use Gutsy in VMWare but I'm stopped dead in the water over this.  It doesn't seem fair that the Gutsy team would send an update that breaks Gutsy networking under Vmware.  Why did they do that?

---

### Post by Predator[23rd] on 2008-01-02
At the moment I am running Ubuntu 7.10 as virtual machine on my laptop.

Although I never had a real problem with internet connectivity (also using NAT for network connections) I noticed yesterday that my Ubuntu install had no eth0 entry in */etc/network/interfaces*. As with your install, **ifconfig** returned only lo for me too.

My suggestion will be to leave your VMWare settings alone (they usually work for almost every situation) and make sure your virtual network adapter starts "connected" ("Connect at power on" is not only checked but the adapter icon has no red cross on it when you boot the virtual machine). Then make sure you have the following two lines in the */etc/network/interfaces* file:
[I]
auto eth0
iface eth0 inet dhcp[/I]

Once done, type **sudo /etc/init.d/networking restart** and it (hopefully) will (should) work. :D

Remember: by adding and removing new virtual network adapters or copying/moving virtual machines device names might change...

---

### Post by RobertGloverJr on 2008-01-02
Thank you very much for your advice.  I will try it out as soon as I get home tonight.  By the way I discovered another forum earlier today that seems worthwhile (as this one is too) . It is for wmware workstation issues:  

[http://communities.vmware.com/community/vmtn/desktop/workstation?view=discussions#](http://communities.vmware.com/community/vmtn/desktop/workstation?view=discussions#)

---

### Post by RobertGloverJr on 2008-01-02
Your suggestion did not work.  
     As you suggested, I modified etc/network/interfaces.

Before:
>  auto lo
 iface lo inet loopback

after:
>  auto lo
 iface lo inet loopback
 auto etho
 iface etho inet dhcp
Then as you suggested I enterred "sudo /etc/init.d/networking restart" :
>  rdgg1@rdgg1-desktop:~$ sudo /etc/init.d/networking restart
  * Reconfiguring network interfaces...                                       

 etho: ERROR while getting  interface flags: No such device
 Internet Systems Consortium DHCP Client V3.0.5
 Copyright 2004-2006 Internet Systems Consortium.
 All rights reserved.
 For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
 
 SIOCSIFADDR: No such device
 etho: ERROR while getting interface flags: No such device
 etho: ERROR while getting interface flags: No such device
 Bind socket to interface: No such device
 Failed to bring up etho.

I then tried this command:  "iwconfig" :

> rdgg1@rdgg1-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I next tried "ifup"  :
> rdgg1@rdgg1-desktop:~$ sudo ifup eth0
[sudo] password for rdgg1:
Ignoring unknown interface eth0=eth0.

     I would appreciate additional suggestions.  I did not change any other VMWARE options. They are the same as in the guest that does not have the Gutsy updated applied.   I also checked and saw that the contents of  etc/network/interfaces. in the two guests are identical.  In other words, before I implemented your suggestion both guests had the following as the contents of  etc/network/interfaces. :
>  auto lo
 iface lo inet loopback

   And in the Gutsy without updates (the one that works) the results of issuing ifconfig are:
> rdgg3@rdgg3-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0C:29:C3:D3:41  
          inet addr:192.168.216.130  Bcast:192.168.216.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fec3:d341/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:249 errors:0 dropped:0 overruns:0 frame:0
          TX packets:191 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:288986 (282.2 KB)  TX bytes:21466 (20.9 KB)
          Interrupt:16 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)



---

### Post by szac on 2008-01-03
looks like you may have added o's instead of 0's in your /etc/network/interfaces file.  Also, this worked for me after I commented out the lines with lo in them. So my interfaces file ended up looking like:

```

#auto lo
#iface lo inet loopback
auto eth0
iface eth0 inet dhcp

```

I have no idea what commenting out those two lines is going to do.

---

### Post by Predator[23rd] on 2008-01-03
jupp. it has to be eth0 (eth-zero) not etho...

do not comment loopback out. some services and programs do need a loopback device in case they are unable to find a network device. in any case it does not do any harm :)

---

### Post by RobertGloverJr on 2008-01-03
>> looks like you may have added o's instead of 0's 

       Your advice is awesome, classic, textbook.  Thank you so much.  I learned a very valuable lesson.  I resolve to be more careful in the future checking "o" versus "0" and "1" versus "l".  I will try it out tonight.   Thanks again.

---

### Post by RobertGloverJr on 2008-01-04
My network in the Gutsy guest  is working now.  In addition to changing "etho" to "eth0" in /etc/network/interfaces  I also (at the suggestion of a "Liz" at: [http://communities.vmware.com/thread/119452](http://communities.vmware.com/thread/119452) ) uninstalled VMware Tools and then re-installed Vmware tools.

    The network then worked  again  after I re-booted

     I did not change anything else or do anything except those the two items listed above.

     I have another Gutsy guest that is not working in the exact same way.  As an experiment I will try uninstalling the VMware tools and reinstalling them, without adding "eth0" to  /etc/network/interfaces.  Will post the results of that later.

     Thank you to everyone for the help.:)

---

### Post by Predator[23rd] on 2008-01-04
Hi mate!

A word to Liz's advice:

The suggested vmware-tools reinstall has nothing to do with your network problem itself.

As you know there are two possible ways to install vmware-tools: using the rpm package (which never worked for me with ubuntu) or compiling everything on your own with the tar.gz archive and vmware-tools-installer.pl script (I love that method :))

I guess you also installed it with the perl script. Now, vmware-tools are a set of kernel modules which are compiled for your kernel at install time. Every ubuntu update which updates the kernel has a chance to brake something in vmware-tools. If such a thing occurs you will see the usual warning in the vmware-window (down, left): "vmware tools not installed". At that point you need to recompile (reinstall) vmware-tools to have automatic guest resizing, shared folders and automatic mouse switching (auto alt-ctrl). I never noticed a real advantage having the network kernel-mod loaded or not ...

Bottom line: vmware-tools will not fix a configuration problem. it makes just interactiong between host and guest OSs easier.

---

### Post by movrshakr on 2008-01-28
I just have to post to help clear my VERY unhappy feelings right now.  I haven't read all of the details here (will do so), but I must vent--or explode.

I installed recommended updates (tonight, 1-28-08) and lost network..  This seemed the closest thread, although I do not have vmware involved--pure Gutsy not even a dual boot.  My machine was running so sweet, basically being used as a file server with a samba shared directory the other Windows machines used as a file storage.

dl the updates.  No machines can contact the "server."  Reboot it. No machines can contact the "server."  Go back to it.  Can't even ping the router to which it is connected.

I am so unhappy.  I am so mad.  I will never install another update if they can't make them any better than this.  That's assuming I don't reinstall XP on that machine, which seems the most straightforward solution.  I really don't need this in my life right now.  So much is going on.  I need this machine.  It has critical stuff on it. (Yes I have backups from 3 days ago--but they are not online for use.  Now this--surely hours and hours of research ahead to try to find the fix.  I wanna say bad words.

What file did they change that killed my machine?

Will make another thread on this since this one is about vmware.

---

