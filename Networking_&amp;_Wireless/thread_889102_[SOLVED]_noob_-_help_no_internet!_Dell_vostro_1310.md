---
title: "[SOLVED] noob - help no internet! Dell vostro 1310"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by saffagirl on 2008-08-13
:confused:Ok, guys, I'm an absolute noob. I've done my 1st ubuntu install tonight (dual boot vista business) and like what I see but am absolutely frustrated. I have done lots of googling and have tried to setup my net connections but am getting nowhere fast, i really hope you can help me 

I  have the dell vostro 1310 , which looking at forums have a few problematic cards...
1. Wired network Realtek rt8111 /8168b
2. Wireless network Broadcom BCM4328 802.11a/b/g/n (aka dell wireless network 1505 pci express card)
Have also got nvidia 8400m card.....(along with mic and webcam, but i think that's another less nb matter right now)

Anyway, I've tried help in network settings. I keep on being asked for a wired network connection secure logon. I'm plugged into the ethernet and I'm not surfing... I've tried changing settings of a wired network which appears in network manager, dhcp back from enabling roaming mode 
Wireless: the wireless is detected in hardware, but I have no wifi light, no hint of a wireless connection.

Any help at all would be appreciated. I'm happy to do what needs to be done, but am a complete novice at Ubuntu so would like you guys to help me step by step. (any advice on knowing what I'm doing would be great.)

Baie Dankie :0)/ Cheers

---

### Post by saffagirl on 2008-08-14
Guys, I'm gonna bump this...sorry. 

Most suggestions I've read for wireless solution required wired networking and I can't get either. 

Thanks in advance.

---

### Post by starcannon on 2008-08-14
For your wireless, best I can offer is to follow this guide:
[http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/](http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/)

For your Nvidia 8400m gs(assuming you haven't tried other ways):

System->Administration->Hardware Drivers:

put a check mark in the field for the video card.

your wired network shoulda worked outta the box, not sure whats going on there.

Be patient with yourself, it takes time to learn anything new, once you get the hang of linux you'll be fine. You've got a dual boot situation, so no rush, take your time and enjoy the experience.

---

### Post by saffagirl on 2008-08-14
> **starcannon said:**
> For your wireless, best I can offer is to follow this guide:
[http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/](http://hasin.wordpress.com/2008/02/27/getting-dell-bcm4328-wifi-card-working-on-ubuntu-710/)

For your Nvidia 8400m gs(assuming you haven't tried other ways):

System->Administration->Hardware Drivers:

put a check mark in the field for the video card.

your wired network shoulda worked outta the box, not sure whats going on there.

Be patient with yourself, it takes time to learn anything new, once you get the hang of linux you'll be fine. You've got a dual boot situation, so no rush, take your time and enjoy the experience.


Starcannon, thanks for your help :)

I haven't got the laptop with me, but will try this suggestion for the wifi and graphics card l8r and post back what happens..I figure at least once I've got one net connection it'll make a big difference. One thing   need to add- it looks like the right version was v3 for my broadcom wireless, so can I assume that if I download the right driver on dell's website and then insert the right driver it'll do the same procedure running in ndiswrapper as per the blog you linked?

You're right, last night I was tearing my hair out and really glad I had dual boot, but I need to enjoy Ubuntu for what it is....it'll take time, but figured I'd been hearing so many good things for ages that I'd try it (plus I really am not that keen on vista...talk about an OS trying to tell you what to do).

PS
Re the wired connection: I've seen a lot posts which suggests a) it doesn't like dual boot b) there are issues in hardy with the driver...so I'm thinking this might have something to do with it?


PPS; in terms of versions - this is the windows sort of side to me; is it ok to do workarounds for a previous kernel of Ubuntu? I gather there are differences, but just want to get an idea.....

Thanks again, as your name suggests, you're a :KS

---

### Post by saffagirl on 2008-08-14
Ok, as we speak I'm not on the wireless.....

I've tried that suggestion,and I managed to get ndiswrapper to run in modprobe, however nothing sparked recognition when i told it to use the driver. I don't have any sign of wireless at all right now. 

Bear with me, this may sound a lame question, but how do i tell it where to find the file, cos i think this could've been the problem.

So anyway, now I've tried another suggestion here which I'm halfway through but have come to a sticking point.

[http://backports.ubuntuforums.com/showthread.php?t=779754](http://backports.ubuntuforums.com/showthread.php?t=779754)

I've downloaded fwcutter and installed it and have got the files that they recommended, which fwcutter has said will obviously need but how do i point to it...the appsta thing said it couldn't be found, but i'm guessing cos it's looking for a file that when downloaded had a different name but from same download link.

as for nvidia driver, I've had a look and it's ticked, but there's a red light next to it saying not in use (i'm guessing cos of proprietary drivers.

---

### Post by Ayuthia on 2008-08-14
> **saffagirl said:**
> 
1. Wired network Realtek rt8111 /8168b
Here is a link to the bug that is related to your card:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499)

It says to add pci=nomsi to your boot options.  To do this, you will need to edit your menu.lst file:
```
gksu gedit /boot/grub/menu.lst
```
You will need to scroll down until you see something like the following:
```

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=abcdefg-1234-54ab-79bc-efefef64646ff ro quiet splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

```

You will need to change the kernel line so that it will look like:
```

title           Ubuntu 8.04.1, kernel 2.6.24-19-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.24-19-generic root=UUID=7b0383bb-5672-40d1-8648-6bf55d774fee ro quiet **pci=nomsi** splash
initrd          /boot/initrd.img-2.6.24-19-generic
quiet

```
Save the file and then restart.  Hopefully your wired connection will then work.

---

### Post by saffagirl on 2008-08-14
Hi Ayuthia, 

thanks for getting back to me on this; I've added that piece of code into grub and I've had no joy...added to that I've just been told gstreamer isnt installed (I've had sounds b4 and I
can't seem to edit)...but anyway, we'll persevere ;)

Thanks for your help, you guys know stacks about networking!

---

### Post by Ayuthia on 2008-08-14
> **saffagirl said:**
> Hi Ayuthia, 

thanks for getting back to me on this; I've added that piece of code into grub and I've had no joy...added to that I've just been told gstreamer isnt installed (I've had sounds b4 and I
can't seem to edit)...but anyway, we'll persevere ;)

Thanks for your help, you guys know stacks about networking!

I just looked at the bottom of the bug report that a solution is to rebuild the old driver for it (r8168.ko).  This will require you to download the source and install build-essential.  Unfortunately, this will require you to download the following packages:
```
build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl linux-libc-dev patch
```along with getting the source code for compiling.  It might be easier to get the wireless up first and then try to get this installed next.

---

### Post by muhdazmil on 2008-08-17
i had a problem too but after i follow the step in here -> [http://www.jamesonwilliams.com/hardy-r8168.html]("http://www.jamesonwilliams.com/hardy-r8168.html"),the problem solve

---

### Post by dodle on 2008-08-17
You can try this:  [http://ubuntuforums.org/showthread.php?t=880218&highlight=broadcom]("http://ubuntuforums.org/showthread.php?t=880218&highlight=broadcom").  I'm about to.  I'll let you know if it works for me.  I'm using an older card though.

---

### Post by saffagirl on 2008-08-18
Wow, this looks great. I haven't had a chance to look at this, but will let you know the outcome as soon as i do.

---

### Post by Ayuthia on 2008-08-18
You might want to check this out for your wired card.  This might fix your problem:
[http://ubuntuforums.org/showthread.php?p=2901884](http://ubuntuforums.org/showthread.php?p=2901884)

---

### Post by saffagirl on 2008-09-01
Hi Ayuthia and Dodle, 

sorry for the delay in getting back to you. I've been away! Anyway, thanks both for suggestions.
Dodle, that idea looks super- i'm hoping it'll work, but sadly  still have no working net connection to use the activate the update it looks like by far the easiest route.
Is there anyway to save onto a memory stick and update from there?
Ayuthia, I'll reply to you in the other post as it's easier to keep track of....thank you for your help guys!

Wifi working with wl , although still drops occasionally. Wired ethernet now working :)

---

### Post by bainorama on 2008-10-31
If anyone else has followed all the given instructions and still having no joy, check the MTU for the interface. Somehow mine got set to 64 bytes, which prevented DHCP from working (too me a while to register why it was complaining that the packets were too big). Worked fine once I increased it.

---

### Post by barbex on 2008-11-20
> **bainorama said:**
> check the MTU for the interface. Somehow mine got set to 64 bytes, which prevented DHCP from working (too me a while to register why it was complaining that the packets were too big). Worked fine once I increased it.

Oh, this looks like my problem! (I have a Vostro A860)
I get "send_packet: Message too long" on dhclient. Is that the complaint you were referring to? 
So would you please be so kind and point me towards the MTU setting? Cause I'm about to go craaaaazy here!

---

### Post by Ayuthia on 2008-11-20
> **barbex said:**
> Oh, this looks like my problem! (I have a Vostro A860)
I get "send_packet: Message too long" on dhclient. Is that the complaint you were referring to? 
So would you please be so kind and point me towards the MTU setting? Cause I'm about to go craaaaazy here!

This comes from the [bug report]("https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/274069"):
> 

The message in "dhcp error" makes me think about a broken/misconfigured router.
Furthermore there is this line in dmesg.log:

[ 82.885456] sky2 eth0: Link is up at 10 Mbps, half duplex, flow control rx

Can you attach the output of "ifconfig eth0" and the file /etc/dhcp3/dhclient.conf

Can you try the following things and tell if it helps:
- set the router to full duplex
- lower the mtu "sudo ifconfig eth0 mtu 1436" or something lower
- remove the option interface-mtu in /etc/dhcp3/dhclient.conf

Thanks.


---

### Post by barbex on 2008-11-20
Strangely enough this [http://ubuntuforums.org/showpost.php?p=6075456&postcount=24](http://ubuntuforums.org/showpost.php?p=6075456&postcount=24) solved my problem:

> **JFo NZ said:**
> This is how I've fixed the problem.

Edit /etc/network/interfaces

Add 2 new lines:

auto eth0
iface eth0 inet dhcp

Then restart machine. Fixed.

[I]Command to edit file:
sudo gedit /etc/network/interfaces[/I]

Why that solved it? Beats me.

Thanks everybody!

---

