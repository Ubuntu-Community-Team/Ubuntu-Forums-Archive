---
title: "o2 Mobile Broadband"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2009-09-24
can anyone help me to get the o2 mobile broadband working using the E1752 modem. ive tried nothing as i dont really know where to start. thanks in advanced-daniel

---

### Post by mikeyphi on 2009-09-25
> **betterthanjordan79 said:**
> can anyone help me to get the o2 mobile broadband working using the E1752 modem. ive tried nothing as i dont really know where to start. thanks in advanced-daniel

I've done a quick Internet search - it seems that the same question is being asked, nobody has got an answer for that modem.....however some of the other O2 modems seem OK.

I'd suggest checking the forums for a (different) suitable modem.

---

### Post by StuartN on 2009-12-01
> **betterthanjordan79 said:**
> can anyone help me to get the o2 mobile broadband working using the E1752 modem. ive tried nothing as i dont really know where to start. thanks in advanced-daniel

Have you tried configuring usb_modeswitch to allow Linux to see the modem, rather than the memory card within the USB stick? See [http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6](http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6) and post back if it works.

---

### Post by alexfish on 2009-12-01
> **betterthanjordan79 said:**
> can anyone help me to get the o2 mobile broadband working using the E1752 modem. ive tried nothing as i dont really know where to start. thanks in advanced-daniel

hi

can you keep the device plugged in and

from the menu / applications/ accessories ,select terminal

in the terminal type or copy this code into the terminal

lsusb

you may see in the output list of a modem and model

and post the results if possible



   thanks in advance 

  alexfish

---

### Post by ukripper on 2009-12-01
post output of these two commands, we go from there:
```
lsusb
```
and
```
lsmod
```

---

### Post by StuartN on 2009-12-02
I can confirm that the solution given in [http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6](http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6) works perfectly.

If you install usb_modeswitch, create the O2 connection in Network Manager, then edit /etc/usb_modeswitch.conf as described and run **sudo usb_modeswitch** in a terminal, then it will pick up the Huawei E1752 mobile broadband modem.

This procedure only needs to be performed once, thereafter the connection will be made automatically whenever the USB stick is inserted.

---

### Post by alexfish on 2009-12-05
> **StuartN said:**
> I can confirm that the solution given in [http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6](http://www.blogcatalog.com/blog/iwrite-2/dbbfb38ae5ef9ccef8540aad7f9edbd6) works perfectly.

If you install usb_modeswitch, create the O2 connection in Network Manager, then edit /etc/usb_modeswitch.conf as described and run **sudo usb_modeswitch** in a terminal, then it will pick up the Huawei E1752 mobile broadband modem.

This procedure only needs to be performed once, thereafter the connection will be made automatically whenever the USB stick is inserted.

just for info a update listing is available from this site

worth reading 

other devices are listed here as well


[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

you can use the copy and paste 

Load the latest [usb_modeswitch.conf]("http://www.draisberghof.de/usb_modeswitch/usb_modeswitch.conf"); the default place is "/etc". Last updated 2009-08-26

---

### Post by pythonsyntax on 2009-12-19
How do i do that?

---

### Post by StuartN on 2009-12-19
> **pythonsyntax said:**
> How do i do that?

If you have not already done so, then install usb-modeswitch using the Synaptic package manager, or whichever method you prefer. This will install a file /etc/usb_modesitch.conf belonging to root.

Go to the website [http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/) using your browser and save the latest version of usb_modesitch.conf (right-click and Save link as...). You need to replace the old /etc/usb_modeswitch.conf with this new version, so either:

```
*Open a terminal and go to the directory where you save the latest file, then*
sudo cp /etc/usb_modeswitch.conf /etc/usb_modeswitch.conf.old
sudo chown root:root usb_modesitch.conf
sudo mv usb_modeswitch.conf /etc
```
or:
```
*Open the new conf file in your browser or text editor, then open a terminal*
sudo cp /etc/usb_modeswitch.conf /etc/usb_modeswitch.conf.old
sudo gedit /etc/usb_modeswitch.conf
*and delete all contents from the old file and paste the new contents*
```

---

