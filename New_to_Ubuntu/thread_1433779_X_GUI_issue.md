---
title: "X GUI issue"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by saintj0n on 2010-03-19
How can I remove /tmp/X0-lock?  I need to fire up X but not reboot.

---

### Post by MechaMechanism on 2010-03-19
Try logging out of your Gnome session if you are logged in and if your already logged out and in a tty that is good.

```
sudo service gdm stop
``````
sudo service gdm start
```The above comands will restart X.  Of course if your using KDE then I think it might be kdm, but I'm not sure.

---

### Post by saintj0n on 2010-03-20
OK. I looked on terminal 7 and it has a gdm screen there after I type startx.  It is asking if I want to log in on 7 or 1.  It doesn't let me select either option on the dialog box, though.  It is broke.  I loaded off the live cd and rewrote the xorg.conf one line at a time. No joy so far.

Any ideas?

I could save time by loading my tested xorg.conf from usb, if I could get it to work. It is on Bus 001 Device 007: ID 0781:5151 under sda.  How can I mount it?

---

### Post by MechaMechanism on 2010-03-20
> **saintj0n said:**
> OK. I looked on terminal 7 and it has a gdm screen there after I type startx.  It is asking if I want to log in on 7 or 1.  It doesn't let me select either option on the dialog box, though.  It is broke.  I loaded off the live cd and rewrote the xorg.conf one line at a time. No joy so far.

Any ideas?

I could save time by loading my tested xorg.conf from usb, if I could get it to work. It is on Bus 001 Device 007: ID 0781:5151 under sda.  How can I mount it?You can try mounting the usb drive the following way.

```
sudo mkdir /mnt/usbdrive/
``````
sudo mount /dev/sda/ /mnt/usbdrive/
```What are you trying to do exactly?  Does your computer not work with Ubuntu?  Having video problems?

---

### Post by saintj0n on 2010-03-20
I have mepis but I want ubuntu.  My live cd won't start x because of some sort of video configuration problem.  I have the mepis xorg.conf that I know works but I can't get startx to work.  I am having a tough time with mounting the usb.  It says /flash is either busy o /dev/sda is already mounted.

---

### Post by saintj0n on 2010-03-20
I actually manually typed in the xorg.conf and got an x graphical screen.  However, there seems to be a problem with a hanging console screen.  I wonder if there is a  command line argument that could be entered when booting that would skip the gdm service.  Then I could just start it myself.

---

