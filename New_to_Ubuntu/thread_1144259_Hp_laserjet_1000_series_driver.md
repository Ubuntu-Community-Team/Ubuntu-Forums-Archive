---
title: "Hp laserjet 1000 series driver"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by heroidi on 2009-04-30
Hi!
Can someone tell me how can I install the drivers for this printer or is it any way like the wireless drivers with ndiswrapper because I have the windows drivers of the printer Ive installed all printing programs in synpatic manager and they found the driver but it does not print what could it be if this works I may be done with windows forever and never use it anymore witch will make me very happy.

Thanks in Atvantage...

P.S Im back on ubuntu after an other experience on windows with lots of BSOD's

---

### Post by Niniel on 2009-04-30
Before you went on your installation spree, did you try to just print?
Ubuntu is pretty good with printers out of the box.

---

### Post by stchman on 2009-04-30
> **heroidi said:**
> Hi!
Can someone tell me how can I install the drivers for this printer or is it any way like the wireless drivers with ndiswrapper because I have the windows drivers of the printer Ive installed all printing programs in synpatic manager and they found the driver but it does not print what could it be if this works I may be done with windows forever and never use it anymore witch will make me very happy.

Thanks in Atvantage...

P.S Im back on ubuntu after an other experience on windows with lots of BSOD's

The Laserjet 1000 printer uses the Zenographics engine.

Install the hplip package:

```
sudo apt-get install hplip
```

There is an option to download the proper firmware to the printer each time you power on the PC.

If you prefer the foo2zjs driver follow my tutorial.

[http://www.stchman.com/foo2zjs.html](http://www.stchman.com/foo2zjs.html)

Use the Gutsy script as Gutsy and later uses system-config-printer.

---

### Post by heroidi on 2009-04-30
yes i tried a lot of times

---

### Post by heroidi on 2009-04-30
any other solution found?

---

### Post by heroidi on 2009-05-01
plz help im driving mad :S

---

### Post by mgmiller on 2009-05-01
I just helped a friend with an HP 1018 with this exact problem.

Open a terminal  Applications > Accessories > Terminal

Enter the following command:
```
sudo /usr/share/hplip/plugin.py
```

 Answer 'd' and download firmware update,
 Answer 'y' to install updated firmware when prompted.

You can then install the printer driver that ubuntu finds without getting error messages.

You will have to reboot the computer with the _printer turned on_, you should see an amber light flash on the printer during boot, telling you the firmware is being loaded.

It should now print normally.

---

### Post by heroidi on 2009-06-08
not working still

---

### Post by alan tait on 2009-06-24
Same problem and this worked for me. Hats off to mgmiller!

---

### Post by mgmiller on 2009-06-24
> **alan tait said:**
> Same problem and this worked for me. Hats off to mgmiller!

Glad I could help.

I see you are still running Intrepid.  There was a fix for this problem released for Jaunty a few weeks after I posted the work around.  I believe that in Jaunty at least, the HP 1000 series printers are now "plug and play".  I'm not sure, but I think that the printer still must be turned on when you boot up, or it won't print.

Could you verify that?  If you boot up with the printer off and then turn it on, will it work?

---

### Post by gcontini on 2011-06-05
I'm using Natty and hp lj 1000w and the firmware installation worked for me too. Thanks mgmiller.

---

