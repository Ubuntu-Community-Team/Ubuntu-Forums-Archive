---
title: "Gateway Built in wireless FN"
date: 2007-09-03
forum: Networking &amp; Wireless
---

### Post by gfk10 on 2007-09-03
Hey guys I'm hoping you can help me out.  I've searched around but to no avail really.  I have a gateway laptop with a built in wireless card that can be activated by pressing the FN(function) key 
[IMG]http://www-307.ibm.com/pc/support/site.wss/x40fnkey.gif[/IMG]

and F2.  Well the Fn key isn't working on ubuntu,so i'm not sure how to activate my wireless?  If anybody could help me I would appreciate it. Thanks

---

### Post by noob12 on 2007-09-04
What model of Gateway do you have?   and can you post the output of these commands
```

lspci -nn

sudo lshw -C network

```

---

### Post by gfk10 on 2007-09-12
my model is 7324gz



here are the results:

gfk@gfk:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
01:04.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023]
01:05.0 CardBus bridge [0607]: Texas Instruments PCI1510 PC card Cardbus Controller [104c:ac56]
01:06.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
01:09.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
gfk@gfk:~$ sudo lshw -C network
gfk@gfk:~$ 

All help appreciated, thanks

---

### Post by noob12 on 2007-09-12
Check your BIOS settings to see if there is a control for enabling the wireless initially.  According to the support matrix here: [http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix) all of the Gateway models have pure hardware support for the rf switch.

This command
```

gfk@gfk:~$ sudo lshw -C network

```
should have printed something.    I wanted to see if you had installed the driver for your card and which one.

My guess is that you don't have the driver set up.  The bcm43xx driver in Ubuntu doesn't have firmware that works with most cards.

Try following the sticky HOWTO here: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) . It should make sure you have the driver setup right.

Note that even with a working driver in Ubuntu, if you have an indicator LED, it may not actually turn on.

---

### Post by gfk10 on 2007-09-12
alright... how would i check my bios settings? thanks

---

### Post by noob12 on 2007-09-13
If you haven't installed drivers already, you can do that first.  Follow the HOWTO thread.   You may not need to do anything in the BIOS.  If after you install the drivers the iwconfig command shows the radio is disabled, you will need to check the BIOS settings.

Manipulating BIOS settings is very specific to your computer.  When you first power up, you'll probably see a message flash on the screen about hitting DEL or F1 or some key to enter SETUP or BIOS Setup.  You want to do that and you'll get to a set of menus which you need to navigate to find settings for the wireless device.  Your user manual might provide more instructions.

---

### Post by gfk10 on 2007-09-13
okay... i'm trying to install that but it gives me this error when I enter my password

Failed to run ./bcm43xx.sh as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program.  Contact the system administrator.  



I don't really understand, I entered the password that i use for my user account that I use to login.  I know my root password also.. but i don't know what to do?  thanks for all your help

---

### Post by noob12 on 2007-09-13
Hmm. 

This might have to do with how you extracted the contents of the tar file.  Can you check to see that the file has the execute bit set for everyone (**ls -l ./bcm43xx.sh** while in that directory)?

Also make sure you are in the **admin** group.  The commands **groups** or **id** will list the groups you are running with.

The other possibility is that you or somebody else modified the default **/etc/sudoers** file. The default one gives you rights to run all programs as long as you are in the **admin** group.

---

### Post by gfk10 on 2007-09-13
> **noob12 said:**
> Hmm. 

This might have to do with how you extracted the contents of the tar file.  Can you check to see that the file has the execute bit set for everyone (**ls -l ./bcm43xx.sh** while in that directory)?

Also make sure you are in the **admin** group.  The commands **groups** or **id** will list the groups you are running with.

The other possibility is that you or somebody else modified the default **/etc/sudoers** file. The default one gives you rights to run all programs as long as you are in the **admin** group.

i'm pretty sure it's  not with how i extracted it because i can't do manual configuration of my wireless networks either.. it asks for my password and when i enter root password it says wrong password and when i enter my user password it gives that same error the bcm43xx program did.  how would i know if i'm in the admin group?  the results of those commands were

gfk@gfk:~$ groups
gfk adm dialout cdrom floppy audio dip video plugdev scanner netdev lpadmin powerdev
gfk@gfk:~$ id
uid=1000(gfk) gid=1000(gfk) groups=4(adm), 20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),1000(gfk)

---

### Post by noob12 on 2007-09-13
You are not in the **admin** group.  It would be listed as the word **admin** in the output of **groups**

If you know the root password you should start a root shell first by typing
```

su -

```
entering the root password at the prompt.

At that point, I would **cat /etc/sudoers** to see what it looks like.  The default one  will have a line like this
```

%admin ALL=(ALL) ALL

```
which says that everyone in the admin group can do anything using sudo.

Also see if your own username (gfk?) is mentioned at all in any of the lines.
If it is specifically listed, then make sure the rest of the line says **ALL=(ALL) ALL**.
If it is not specifically listed, then do nothing.

If you found the entry for the **admin** group in **/etc/sudoers** but no entry for yourself specifically, then you should add yourself to the **admin** group using the following command.
```

usermod -a -G admin *yourusername*

```
or substitute your actual username for **yourusername** in the above.

Once you have done that you will need to logout and log back in to use **sudo** properly.

Using the root shell you can also run the scripts that you would have run using **sudo**.

(Either way you can then continue with the driver installation).

---

### Post by gfk10 on 2007-09-13
THANK YOU! I got it up and running :) thanks so much

---

### Post by gfk10 on 2007-09-13
one more thing though... would you happen to know how to get volume working :(

---

### Post by noob12 on 2007-09-13
Not off hand.  But I've heard these guys are pretty friendly:  [http://ubuntuforums.org/forumdisplay.php?f=138](http://ubuntuforums.org/forumdisplay.php?f=138)
:)

---

