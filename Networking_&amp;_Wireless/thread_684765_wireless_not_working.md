---
title: "wireless not working"
date: 2008-02-01
forum: Networking &amp; Wireless
---

### Post by airplanesrule on 2008-02-01
I have a belkin F5D9050 and I can't figure out how to configure it to work with ubuntu, it works fine with windows, but wont do anything with ubuntu

any suggestions??

thanks in advance

---

### Post by trehoffman on 2008-02-01
airplanesrule,

I just installed this model last night so I should be able to help you configure it.

A couple of questions:

[INDENT]1) Do you have the appropriate driver for Windows that came with the wireless usb adapter?[/INDENT]
[INDENT]2) Do you have ndiswrapper installed (i'm assuming you don't)?[/INDENT]

---

### Post by Hightide on 2008-02-01
> **airplanesrule said:**
> I have a belkin F5D9050 and I can't figure out how to configure it to work with ubuntu, it works fine with windows, but wont do anything with ubuntu

any suggestions??

thanks in advance

Hi Airplanesrule

when you check with trehoffman, have a look at this similar thread

[http://ubuntuforums.org/showthread.php?t=441049](http://ubuntuforums.org/showthread.php?t=441049)

regards

:lolflag:

---

### Post by airplanesrule on 2008-02-01
I have already seen that thread, but I still couldn't get it to work. and I do have the windows drivers and I also do have ndiswrapper, I just can't seem to configure it correctly so I can get internet

---

### Post by trehoffman on 2008-02-05
Here's what I did to get mine working:

1) install ndiswrapper (you said you've done this already)

2) open a terminal and "cd" to the location where you have your driver and type "sudo ndiswrapper -i rt72.inf" into the command line(i think that was the name of the driver that came with the adapter on a CD...if not it is similar)

3) to check and make sure everything went as planned type "sudo ndiswrapper -l" into the command line and you should see something like "rt72 driver present, hardware present" (make sure the Belkin adapter is plugged in in order to see the "hardware present" part)

4) type "sudo ndiswrapper -m" into the command line

5) now type "sudo gedit /etc/network/interfaces" into the command line (or use whatever text editor you want)  you are going to insert the following text somewhere in the "/etc/network/interfaces" file:
[INDENT]iface wlan0 inet dhcp
auto wlan0[/INDENT]
save the file and go back to the terminal.

6) type "sudo ifup wlan0" into the command line and everything should start working (check and see if the green light starts blinking).  if the internet is still not connecting yet, unplug the adapter and then plug it back in (it seems like i have to do this sometimes when i restart the computer too but not all of the time).

7) I stole most of these instructions from [http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux]("http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux") so check there first if you have any trouble.

Let me know how it goes!

---

### Post by airplanesrule on 2008-02-05
thanks, ill give it a try

---

### Post by airplanesrule on 2008-02-06
it all worked until the ifup wlan0 part, then it says

 "There is already a pid file /var/run/dhclient.wlan0.pid with pid 13539"

???

---

### Post by trehoffman on 2008-02-08
I'm not sure, but I would try using wlan1 in place of wlan0 and see what happens.

---

### Post by airplanesrule on 2008-02-08
ill try it

---

### Post by airplanesrule on 2008-02-08
nope, im gonna reinstall ubuntu

---

### Post by trehoffman on 2008-02-11
Before you do that I would open that file and see if you can edit it appropriately?

---

### Post by Mr.Johnny on 2008-02-11
I didn't read the whole thread, but gtkwifi has helped me in some cases (i.e., my wireless would only work in 7.04 with it).

[http://gtkwifi.sourceforge.net/](http://gtkwifi.sourceforge.net/)

after installing, open a terminal and type: gtkwifi "run-in-window"

---

### Post by khmer04sti on 2008-03-07
> **trehoffman said:**
> Here's what I did to get mine working:

1) install ndiswrapper (you said you've done this already)

2) open a terminal and "cd" to the location where you have your driver and type "sudo ndiswrapper -i rt72.inf" into the command line(i think that was the name of the driver that came with the adapter on a CD...if not it is similar)

3) to check and make sure everything went as planned type "sudo ndiswrapper -l" into the command line and you should see something like "rt72 driver present, hardware present" (make sure the Belkin adapter is plugged in in order to see the "hardware present" part)

4) type "sudo ndiswrapper -m" into the command line

5) now type "sudo gedit /etc/network/interfaces" into the command line (or use whatever text editor you want)  you are going to insert the following text somewhere in the "/etc/network/interfaces" file:
[INDENT]iface wlan0 inet dhcp
auto wlan0[/INDENT]
save the file and go back to the terminal.

6) type "sudo ifup wlan0" into the command line and everything should start working (check and see if the green light starts blinking).  if the internet is still not connecting yet, unplug the adapter and then plug it back in (it seems like i have to do this sometimes when i restart the computer too but not all of the time).

7) I stole most of these instructions from [http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux]("http://czarism.com/easy-peasy-wireless-w-ubuntu-debian-linux") so check there first if you have any trouble.

Let me know how it goes!

This worked perfectly, thanks! My only problem was that the USB would "disappear" upon restart but it still shows up whenever I type:

[INDENT]ndiswrapper -l[/INDENT]

What I ended up having do to was manually configure the USB card using instructions from [here]("http://ubuntuforums.org/showthread.php?t=684495").

---

### Post by airplanesrule on 2008-03-29
finally got it working, thanks a lot :)

---

