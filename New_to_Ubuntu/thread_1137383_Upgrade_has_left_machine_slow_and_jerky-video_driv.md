---
title: "Upgrade has left machine slow and jerky-video driver problem"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by pistos on 2009-04-25
I upgraded my computer from 8.10 to 9.04 over the Internet. It appeared to go OK. But, the graphics performance was slower than before. So, I looked through the Add/Remove and saw the ATI driver listed there, so I installed it, thinking that the slower performance I was seeing was related to not having the proper graphics driver installed. (I have a notebook with ATI Radeon 9700 mobility dedicated graphics, 128MB.)

Well, that was a huge mistake, because then my machine would not boot up properly at all. (Apparently the ATI driver no longer supports my graphics chip set.)

So, I dug through the forums here and uninstalled the ATI drivers by booting into safe mode and then executing the command to remove it.

Now my machine boots up, and appears to work fine for a few seconds (literally), and then gets jerky slow and the keyboard and trackpad become unresponsive. I can still move the cursor with the trackpad, but no button clicks work anymore, so no menu selection or anything. And, like I said the cursor movement with the trackpad is jerky slow. So, whatever drivers I have in there now are totally goofed up.

I am feeling really discouraged at this point. My machine was running great under 8.10. And now I am totally hosed and have no idea how to bring it back. I don't even know what question to ask at this point.

---

### Post by Seks on 2009-04-25
go into safe mode and run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

you should at least be able to run ubuntu in low graphics mode

---

### Post by Seks on 2009-04-25
[http://linuxd.wordpress.com/2009/02/11/ubuntu-810-support-dropped-for-ati-mobility-radeon-9700-rv300-chips/](http://linuxd.wordpress.com/2009/02/11/ubuntu-810-support-dropped-for-ati-mobility-radeon-9700-rv300-chips/)

---

### Post by pistos on 2009-04-25
> **Seks said:**
> go into safe mode and run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

you should at least be able to run ubuntu in low graphics mode

I did that and that is what has left me with a slow jerky machine that quickly degrades into a non-responsive keyboard and trackpad buttons.:(

How do I fix the mess I have now?

---

### Post by cariboo on 2009-04-25
Did you try System-->Administration-->Hardware Drivers to install the graphics drivers.

---

### Post by caravel on 2009-04-25
You need to purge fglrx and reinstall the open source Radeon driver.

I found this howto, if anyone knows of a better, more up to date one please link: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by pistos on 2009-04-25
I have already purged the fglrx driver from my system, but I executed the command again to make sure and it returned the message that it was not there to remove.

But, here is the very odd thing now. I plugged my USB mouse into the machine and started it up and the machine runs smooth as ever. But, if I start up without the USB mouse plugged in, then the machine does not do a clean boot up and gives the jerky thing and then dead buttons all around.

Does anyone have a clue as to what is causing this USB interaction problem?

---

### Post by pistos on 2009-04-25
I have the open source radeon driver installed and everything appears to be working, EXCEPT that it only works right if I have my USB mouse plugged in at boot up and keep it plugged in at all times.

If I boot up without the USB mouse plugged in the trackpad buttons and keyboard are both dead. And, the trackpad movement is very jerky.

Also, if I boot up with the USB mouse plugged in, I get a good boot up, but if I unplug the mouse after that, then the machine goes into the same strange mode, with the trackpad buttons and keyboard both dead and the movement becomes very jerky.

---

