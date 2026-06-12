---
title: "Palm Centro as USB modem?"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by dagar on 2008-06-24
Has anyone had any luck with using a Palm Centro (or any other Palm smartphone) as a USB modem?  I am not having much luck with this at all.
Thanks
Derek

---

### Post by sunbird on 2008-07-18
bump.

i'm thinking about getting a centro and would like to use internet sharing while i'm traveling, either via usb or (ideally) bluetooth.

anyone had any luck?

---

### Post by hbj on 2008-07-20
I have used the [USB Modem]("http://software.palm.com/us/html/display_palm_product.jsp?id=prod5691584") software without any problems on Hardy and Gutsy, 32-bit and 64-bit, with my Treo 700p.  Worked great!  Just moved to a Centro and I don't expect any problems.

---

### Post by hbj on 2008-07-31
I'm typing this now connected via the USB Model software mentioned above.  Running Hardy, 64-bit, using my Palm Centro.  Works great, no problems at all.

Heath

---

### Post by dagar on 2008-07-31
Is that software just on the phone or also on the PC?  If it is just on the phone, how do you set it up on the PC?

---

### Post by Deach on 2008-08-06
I'd be curious to know this too.....Any help on getting it going out there?

---

### Post by underdog512 on 2008-10-09
I am curious about this as well

---

### Post by nuclearfungus on 2008-12-01
I am using USBmodem on verizon wireless with no problems at all the software only goes on the phone not the pc as well.

The first step (and simplest way I found to connect) is to copy the connection script from the USB Modem archive to your /etc/ppp/peers/ directory. I used this command (assuming you’ve unzipped the archive to your Desktop):

type
    sudo cp ~/Desktop/drivers/linux/ppp-script-evdo-template /etc/ppp/peers/ppp-script-treo

 and hit enter

At this point you’ll want to reach over to your Treo / Centro enter usb modem and click “Enable Modem Mode”. 

Now that the phone is set to “Modem Mode” run the following command on the Linux machine:
(first ensure you are in the home directory by typing "cd .." and hitting enter a few times)

then type:

    sudo pppd /dev/ttyACM0 call ppp-script-treo

hit enter 

then if using firefox go to file menu and ensure work offline is not checked

---

### Post by jaynewstrom on 2008-12-12
Is it possible to use this without the PAM plan?
I am guessing that you will need the PAM plan to use this.
If so does anyone know of anything that will allow you to do something like this without the PAM plan?

Thanks,
Jay

---

### Post by hbj on 2009-05-06
I don't know what the PAM plan is, but you will need to have a data plan on your phone to do this.  I am running 9.04, AMD64 and everything still works.  To make starting the connection easier, I made a little script that I put in /usr/local/sbin/treo-modem

```
#!/bin/bash
sudo pppd /dev/ttyACM0 call ppp-script-treo

```

since otherwise I'd never remember the command.  Then to connect, just hit the Enable button on your phone, wait a second or two, and run treo-modem.

The ppp-script-treo script needs a bit of configuring, but there are instructions included with the USB Modem software that are pretty easy to follow.

---

### Post by RBPhoto on 2009-06-15
> **hbj said:**
> I have used the [USB Modem]("http://software.palm.com/us/html/display_palm_product.jsp?id=prod5691584") software without any problems on Hardy and Gutsy, 32-bit and 64-bit, with my Treo 700p.  Worked great!  Just moved to a Centro and I don't expect any problems.

I am using a centro now, was using a 700p. I used to tether with the 700p (MAC), but with a smidge of initial setup complexity- meaning, I could not find the right data on HOW very easily. Once I got it set up, it wasn't that hard to use.

I currently am trying the same things with the Centro. I am having the same troubles finding the "how". I have tried my USB Modem program. I am trying verizon's support, but they suck on this. They just won't help. I have had SOME success getting things "close", meaning, I can see that the phone is bluetoothed and trying to connect, but it always fails.

Can anyone help me find a way to walk through this and get some results? I want to use this for work (via USB OR bluetooth), and just feel I need the right settings in the network and other dialog boxes...

Much thanks for any expert on this field that can help me get this to work...

---

### Post by unix1adm on 2009-06-18
How do you sync your phone with Ubuntu? I have a 700W and will be migrating to another win CE device or a black berry storm, samsung sage or samsung omni pro 2. 

I wan tot use it as a modem and sync it to my laptop.

---

### Post by brimorse on 2009-07-13
I have a Palm Centro- be sure you use the usb: setting to get it to sync.

I was able to do this, but when I bring up JPilot I can't see any of the info that was sync'd.  Went through the package manager to make sure I had all JPilot packages installed, and they were.

What am I missing?

---

### Post by oscarguzmanr on 2010-01-16
Hi you guys!

I just installed the software you mencioned, and works out of the box on Ubuntu 9.10 Karmic Koala:

1.- Installed the software from palm site .PRC file  (on your Palm Centro)

2.- Run the software "usb modem" on your palm and plug into usb.

3.- To create the connection on ubuntu using the Network Manager, right click, edit connections and under BAM tab, follow the "add" wizard, at the end the new connection appeared on left click on Network Manager.

(I call Network Manager, the little icon near the clock on my desktop, the one that shows the wifi or ethernet icon when connected)

Hope this works for you, and my comment is useful.

Thanks for the link to get "usb modem for palm"
[http://software.palm.com/us/html/display_palm_product.jsp?id=prod5691584](http://software.palm.com/us/html/display_palm_product.jsp?id=prod5691584)

P.S. I would post this comment using GPRS connection, but my data plan is for Kb used

---

### Post by pdc on 2010-01-16
well done; good work

---

