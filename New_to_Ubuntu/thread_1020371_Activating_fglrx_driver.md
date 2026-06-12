---
title: "Activating fglrx driver"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by reydempto on 2008-12-24
Hi,

Every time i try to "Activate" the ATI driver in System>Administration>Hardware Drivers, I get a pop up window saying: 

"You are not authorized to perform this action."

how can i give myself the authority to perform such actions??

---

### Post by reydempto on 2008-12-24
-BUMP-

Anyone have any suggestions?

---

### Post by reydempto on 2008-12-25
-Christmas Bump-

---

### Post by taurus on 2008-12-25
Are you the original user that you created during the installation?  What's the output of this command from a terminal?

```
id
```

---

### Post by reydempto on 2008-12-25
> **taurus said:**
> Are you the original user that you created during the installation?  What's the output of this command from a terminal?

```
id
```


uid=1000(reydempto) gid=1000(reydempto) groups=4(adm),20(dialout),21(fax),
24(cdrom),26(tape),29(audio),30(dip),44(video),46(plugdev),104(scanner),106(fuse),
108(lpadmin),114(netdev),123(admin),124(sambashare),1000(reydempto)

---

### Post by daveball on 2009-01-24
I have the exact same problem with Ubuntu 8.10 and get the same error message.

I upgraded my very, very old AGP graphics card to an HD4350 (my motherboard is one with AGP and PCIe slots).

I then tried to enable the proprietary ATI drivers in System->Administration->Hardware Drivers and hit this problem.

In the end I downloaded the driver direct from ATIs website [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html]("http://ati.amd.com/support/drivers/linux64/linux64-radeon.html").  Its a straightforward self-extracting installer thingy. At the command-line in the folder you downloaded the driver too, just run:

[FONT="Courier New"]sudo ati-driver-installer-8-12-x86.x86_64.run
[/FONT]
Then you'll need to reboot. ATI say if X fails to start up then you should enter this command at the terminal session (I didn't have to do this):

[FONT="Courier New"]aticonfig --intial -f
[/FONT]

Its all running fine now, except that if I set System->Preferences->Appearance->Visual Effects to "Extra" some screensavers (the OpenGL ones I think) and other applications flicker very badly. Keep Visual Effects at "Normal" or "None" and all is fine though.

If it doesn't work and you need to uninstall the ATI driver it's just:

[FONT="Courier New"]cd /usr/share/ati/
sudo sh ./fglrx-uninstall.sh
[/FONT]

I also found out the hard way - if for any reason you mess up your X settings and run the usual life-save command "dpkg-reconfigure xserver-xorg" this will disable the fglrx driver. I probably should have used the aticonfig command above instead.

---

