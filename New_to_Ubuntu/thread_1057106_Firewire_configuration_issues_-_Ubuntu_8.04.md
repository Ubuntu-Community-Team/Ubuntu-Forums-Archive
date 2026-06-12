---
title: "Firewire configuration issues - Ubuntu 8.04"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by gorbynet on 2009-02-01
Firstly, let me apologise if this post is in the wrong place. I've not posted before (although I've read a fair bit) and I'm a noob so it seems like a good place to start. Feel free to bump it if I've got it wrong! Secondly, it's quite a large post so I'll also apologise now for taking up your time; I figure it's best to try and describe the problem as fully as I can. I'd be grateful for any help as I've been banging my head against a brick wall with this for some time now, on and off, and I'm a bit stumped.

I'm trying to get a Firewire sound card operational on Ubuntu 8.04, running the 2.6.24 generic kernel. I'm using the onboard 1394 port on an eMachines M5124 laptop; I want to use an M-Audio Firewire Audiophile soundcard for recording and sequencing audio - I'm wondering if I can break my dependence on Windows XP. 

I am aware that there is limited support for the Firewire Audiophile via FFADO so I might have problems getting it to run. I've not got that far, though, since I'm having trouble getting /dev/raw1394 working. I get this output from lsmod after boot i.e. this is the current default state. I'm 99% certain that the 

mike@mike-laptop:~$ lsmod | grep "1394"
ohci1394               33584  0 
ieee1394               93752  2 sbp2,ohci1394

I found the following page:
[http://tldp.org/HOWTO/libdc1394-HOWTO/install.html](http://tldp.org/HOWTO/libdc1394-HOWTO/install.html)

I've not recompiled the kernel - as a noob, it's beyond what I feel comfortable doing, and the instructions are for 2.6.10, so I've skipped that step. I'm also not bothered about video support - I don't have any applicable devices so that's not important.

So, I've checked with Synaptic Package Manager and I have various 1394-related packages installed:
libavc1394-0
libdc1394-13
libraw1394-8
libraw1394-dev
libraw1394-doc
so I've skipped the next steps about installing libraw and libdc.

We then get to the modprobe commands - I've just done the following, since ohci1394 and ieee1394 are already listed:
mike@mike-laptop:~$ sudo modprobe raw1394
[sudo] password for mike: 
mike@mike-laptop:~$ lsmod | grep "1394"
raw1394                29144  0 
ohci1394               33584  0 
ieee1394               93752  3 raw1394,sbp2,ohci1394

so I now seem to have the raw1394 module installed. I've discovered that permissions are important for access to the firewire port, so I've done the following:

mike@mike-laptop:~$ cd /dev
mike@mike-laptop:/dev$ ls -l raw1394
crw-rw---- 1 root disk 171, 0 2009-02-01 17:52 raw1394
mike@mike-laptop:/dev$ sudo chmod 666 raw1394
mike@mike-laptop:/dev$ ls -l raw1394
crw-rw-rw- 1 root disk 171, 0 2009-02-01 17:52 raw1394

so, I reckon I should now have read-write access to the firewire port. I've tried testing it like this:
mike@mike-laptop:/dev$ testlibraw
successfully got handle
current generation number: 1
1 card(s) found
  nodes on bus:  1, card name: ohci1394
using first card found: 1 nodes on bus, local ID is 0, IRM is 0

doing transactions with custom tag handler
trying to send read request to node 0... completed with value 0xf668362c

using standard tag handler and synchronous calls
trying to read from node 0... completed with value 0x3384362c

testing FCP monitoring on local node
got fcp command from node 0 of 8 bytes: 01 23 45 67 89 ab cd ef
got fcp response from node 0 of 8 bytes: 01 23 45 67 89 ab cd ef
testing config rom stuff
get_config_rom returned 0, romsize 64, rom_version 3
here are the first 10 quadlets:
0. quadlet: 0xa0540404
1. quadlet: 0x34393331
2. quadlet: 0x32a264e0
3. quadlet: 0x21250300
4. quadlet: 0xdd550030
5. quadlet: 0x04420300
6. quadlet: 0x25030003
7. quadlet: 0x02000081
8. quadlet: 0xc083000c
9. quadlet: 0x2a2c0600
update_config_rom returned 0

polling for leftover messages

I don't know how to interpret this output. Any ideas what this means? I've also tried running testlibraw after switching on the firewire sound card, I get the following output:

mike@mike-laptop:/dev$ testlibraw
successfully got handle
current generation number: 1
1 card(s) found
  nodes on bus:  2, card name: ohci1394
using first card found: 2 nodes on bus, local ID is 1, IRM is 1

doing transactions with custom tag handler
trying to send read request to node 0... failed with error: Resource temporarily unavailable
trying to send read request to node 1... completed with value 0x0f746761

using standard tag handler and synchronous calls
trying to read from node 0... failed with error: Resource temporarily unavailable
trying to read from node 1... completed with value 0x7c80af61

testing FCP monitoring on local node
got fcp command from node 1 of 8 bytes: 01 23 45 67 89 ab cd ef
got fcp response from node 1 of 8 bytes: 01 23 45 67 89 ab cd ef
testing config rom stuff
get_config_rom returned 0, romsize 64, rom_version 4
here are the first 10 quadlets:
0. quadlet: 0xa0540404
1. quadlet: 0x34393331
2. quadlet: 0x32a264e0
3. quadlet: 0x21250300
4. quadlet: 0xdd550030
5. quadlet: 0x04420300
6. quadlet: 0x25030003
7. quadlet: 0x02000081
8. quadlet: 0xc083000c
9. quadlet: 0x2a2c0600
update_config_rom returned 0

polling for leftover messages

I notice that there is an extra node (that fails) - is this the sound card?

The next step on the page above is mknod - do I need to do this command? The mknod man pages are best described as cryptic so I've no idea what this actually does; from what I've seen the node is (probably) operational.

And then we get to the next problem. As noted in the howto, all this configuration work disappears when I reboot. :(

So, I guess the questions I need to ask are:
Are these the right steps to take to get the firewire port working?
How do I get the changes to 'stick' so I don't need to do this every time I boot?
And then the $60,000 question - how do I get the sound card to work (although that's probably a whole new post topic - I've not even started getting to grips with Jack, ALSA, Freebob and/or FFADO)?

Thanks in advance for your help, it's much appreciated.

---

### Post by gorbynet on 2009-02-01
I've done a bit more digging and found this page:

[http://www.bxlug.be/en/articles/220](http://www.bxlug.be/en/articles/220)

Progress!

I've added raw1394 to /etc/modules and made the /etc/init.d/firewire script as advised, then did the link command. I rebooted and /dev/raw1394 is present:

mike@mike-laptop:~$ ls -l /dev/raw1394
crw-rw---- 1 root disk 171, 0 2009-02-01 20:52 /dev/raw1394
mike@mike-laptop:~$ testlibraw
couldn't get handle: Permission denied
This probably means that you don't have raw1394 support in the kernel or that
you haven't loaded the raw1394 module.
mike@mike-laptop:~$ sudo !!
sudo testlibraw
[sudo] password for mike: 
successfully got handle
current generation number: 1
1 card(s) found
... etc.

so permissions for it are wrong. I tried adding 
test -e /dev/raw1394 && chmod 777 /dev/raw1394
to the /etc/init.d/firewire script 
before and after the '|| mknod -m 666...' line, but no joy on reboot. Permissions are still set wrong. I'm hoping that this page might help, I'll update when I've checked it out.
[http://www.linuxquestions.org/questions/linux-general-1/raw1394-permissions-522866/](http://www.linuxquestions.org/questions/linux-general-1/raw1394-permissions-522866/)

---

### Post by gorbynet on 2009-02-01
**sudo adduser mike disk** sorted out the permissions problem. Getting there.

---

### Post by GMachine_24 on 2009-02-01
Hey... this will probably be of no help... but a couple years ago I struggled to get an external hard drive to be recognized by Ubuntu .... here is a link to the thread that I started ....it was all very confusing for me ... and, as I said, I don't know if any of this will help you, but I thought, just in case....

[http://ubuntuforums.org/showthread.php?t=147565&highlight=gmachine_24+firewire](http://ubuntuforums.org/showthread.php?t=147565&highlight=gmachine_24+firewire)

---

### Post by gorbynet on 2009-02-02
GMachine_24,

Thanks for the post; I do appreciate your time and effort in replying. I've had a scan through your thread and (to a noob like me) it doesn't look connected to the issues I've been having. I've made a bit more progress since my last post. The adduser instruction seems to have sorted out the permissions problem so testlibraw succeeds without using sudo. 

I've installed all the freebob and jack packages through synaptic. If I boot the machine in Windows and start the device, then reboot into Ubuntu (a process that's down to the device manufacturer, not Ubuntu), I can see the expected number of audio inputs and outputs in jack. Getting sound out of it is a different matter, though...

It looks like the firewire configuration issues are sorted out now, so I'll close the thread. I'll have a bit more of a bash at getting the sound to work tonight - I think I'll probably end up posting another thread about that!

Cheers.

---

