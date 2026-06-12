---
title: "networking with ubuntu 8.04"
date: 2009-07-05
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-07-05
I've read there are some networking issues with hardy, but most of what I have read is simply over my head. I am trying to set up a wired network between my Ubuntu 8.04 box and an old Windows 98 box I want to snag some stuff from. I got it to work once and never again, and now I'm not even sure how I did that. I've tried rebooting Ubuntu but nothing seems to work. I think what I need is a kindergarten networking primer! Can someone walk me through it or point me to some simple instructions for the rank networking newb?

thanks
myst

---

### Post by LewRockwell on 2009-07-05
short answer with no costs: put the windows drive in your other machine as a slave and transfer data as desired

brief answer with some costs: pull the cover, plug this into the drive([http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062](http://www.newegg.com/Product/Product.aspx?Item=N82E16812104062)), and transfer data as desired

*****(10-10-09:Note that recent product reports seem to indicate that there is an electrical problem when using this device with SATA drives that may cause damage/destruction to your equipment...we are in the process of an analysis and investigation into this issue and so far we believe a design flaw does indeed exist)***(10-11-09:We have determined that a design defect DOES EXIST and an extender should be used between the power connector and the adapter so you can cut the red wire to stop the 5 volt connection that is damaging/destroying various components INCLUDING MOTHERBOARDS...An advisement has been sent to CoolMaxUSA but feel free to remind them!)*****

long answer: redacted for brevity, laziness, and a sincere desire for simplicity

.

---

### Post by LewRockwell on 2009-07-05
[http://en.kioskea.net/contents/configuration-reseau/creer-reseau-local.php3](http://en.kioskea.net/contents/configuration-reseau/creer-reseau-local.php3)

.

---

### Post by LewRockwell on 2009-07-05
[http://www.linuxplanet.com/linuxplanet/tutorials/6497/1/](http://www.linuxplanet.com/linuxplanet/tutorials/6497/1/)

.

---

### Post by mystmaiden on 2009-08-09
I'm still battling with samba and networking my computers together. I've gone through the tutorial you listed a couple of times, Lew  at [HTML] http://www.linuxplanet.com/linuxplanet/tutorials/6495/4/[/HTML][FONT=Verdana, Arial, Helvetica][SIZE=2][FONT=Verdana, Arial, Helvetica][SIZE=2]

In the tutorial I get to this point - 

[/SIZE][/FONT][/SIZE][/FONT]> [FONT=Verdana, Arial, Helvetica][SIZE=2][FONT=Verdana, Arial, Helvetica][SIZE=2]After browsing to and selecting a Workgroup from the network browser of your computer, you'll see icons for each computer on the network and in the Workgroup, that's properly configured for sharing.[/SIZE][/FONT][/SIZE][/FONT]

I'm not at all sure I'm looking in the right place because no where do I find  said workgroup and icons. I've assumed that means go to system/administration/network

I know there are issues with samba and 8.04 , but maybe I'm doing something to complicate things further.

myst
[FONT=Verdana, Arial, Helvetica][SIZE=2][FONT=Verdana, Arial, Helvetica][SIZE=2]
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by 3rdalbum on 2009-08-09
> **mystmaiden said:**
> 
I'm not at all sure I'm looking in the right place because no where do I find  said workgroup and icons. I've assumed that means go to system/administration/network

It means go to Places > Network and double-click on Windows Network. I think that's assuming that both computers are Ubuntu.

---

### Post by mystmaiden on 2009-08-09
thanks, found the workgroup icon, but it fails to open 'can't find share list'.

myst

---

### Post by cariboo on 2009-08-09
Have you sharing turned on, on your Win98 computer, and are they in the same workgroup?

It's been a long time since I had anything to do with Win98, but if I remember correctly Win98 uses WORKGROUP.

---

### Post by mystmaiden on 2009-08-12
> Have you sharing turned on, on your Win98 computer, and are they in the same workgroup?
Since I posted the beginning of this thread I went ahead and upgraded to 8.10 hoping that would solve some of the network issues. I think it further complicated the issue. But to answer your questions, Cariboo, I checked the windows 98 machine and its all set up correctly, and there is only one workgroup so I - think - its the right workgroup. However, I stumbled upon two things since the update. 

Now instead of a wired network, which is how things are set up, 8.10 is showing auto etho. In the drop down from the network icon in the top panel networking is showing as enabled. But under the systems/network configuration, there is an option to add or delete connections and a wired network tab at the top. I wonder if it could be as simple as just editing those.

In addition, I was looking for some information on my motherboard today and ran ```
mystmaiden@hal:~$ sudo lshw
```down toward the bottom of the output I found this section
```
*-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 4
             bus info: pci@0000:00:04.0
             logical name: eth0
             version: 90
             serial: 00:e0:06:09:07:85
             size: 100MB/s
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.15.100 latency=32 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ea:3a:ce:85:a0:1e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


I'm not sure if any of that actually sheds light on the difficulties I'm having or not, but it seemed relevant.  

As always, input is Most appreciated!
mystmaiden

---

### Post by powel212 on 2009-08-12
My tutorial on setting up file sharing on ubuntu.

[http://ubuntuforums.org/showthread.php?t=1233071](http://ubuntuforums.org/showthread.php?t=1233071)

I hope that helps

Powel

---

### Post by mystmaiden on 2009-08-12
Thanks, Powel. I followed your tutorial and have made some progress. The windows computer can see and get files from the Ubuntu computer now. But when go to the network on the  Ubuntu machine and click on the workgroup it returns 'Failed to retrieve share list from server'.

half way there !
mystmaiden

edited to add: I just checked the puppy linux that is also on the same network, though not in the workgroup, it can access the shares on Ubuntu now as well (using pnethood on the pup).

---

### Post by mystmaiden on 2009-08-12
well, I spoke too soon. I had to shut down awhile ago, and now the network isn't working again. Checking the settings in Powell's tutorial, I found that some of them had reverted back to what they were before I changed them. I went back through and set it up again according to the tut, but now, nothing is working. This is so frustrating, it is exactly what happened to me after the one and only time I got samba working in hardy. It worked once and never again.  I think the problem with accessing windows 98 from the Ubuntu box is that there is no user name for 98, but that doesn't explain why I can't access the Ubuntu box from Windows, which I could do earlier.

If anyone has any ideas at all, I'd love to hear them

mystmaiden

---

### Post by mystmaiden on 2009-08-14
I'm giving this a bit of a bump. I finally got puppy linux to see the Ubuntu box, but Ubuntu doesn't see anything on the network, in the work group or not. 

mystmaiden

---

