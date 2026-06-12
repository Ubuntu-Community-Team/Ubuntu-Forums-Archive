---
title: "Able to send files via bluetooth but not receive..using Hardy"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by scottptn on 2008-07-18
Hello,

Im using Ubuntu 8.04 (Hardy Heron) and the Gnome desktop environment . Im able to send files from the PC to my Nokia 6600 but not the other way round .In Preferences->General, I have "Receive files from remote devices" selected. I have also paired up my phone to the PC, and set the connection as authorized, still when i try to send a file from my mobile phone to the pc, i get a message "Unable to connect"

Please help
Thanks

---

### Post by scottptn on 2008-07-19
OK..i got it fixed :) . There is a bug in bluez-utils package that comes with Hardy , so sending files from phone to PC does not work out of the box, and downgrading the bluez-utils package to the Gutsy version is required.
While googling i came across : [http://technology-included.blogspot.com/2008/07/using-bluetooth-on-hardy-ubuntu-804.html](http://technology-included.blogspot.com/2008/07/using-bluetooth-on-hardy-ubuntu-804.html) , and following the instructions there resolved the problem :)

---

### Post by scotcella on 2008-07-19
Thank you so much!!!

I had the same problems as you and I had been trying for over a month trying to get my bluetooth working!! The site you found worked for me.

I was aware that the ulitiz package was faulty but downgrading wasn't working out for some reason. 

YAY! That site was a little clearer than what I have been trying to understand :)

Happy as larry now! Thanks Thanks Thanks Thanks!!!

---

### Post by quirks on 2008-07-27
Thanks a lot! I don't know how much more time I would have wasted, if I hadn't found your post.

I hope they fix this soon. I hate having a dozen utilities on my machine where each of them only works for a specific purpose.

---

### Post by waster on 2008-09-06
alternatively, upgrading:

libbluetooth2
bluez-utils
obex-data-server

to intrepid versions (you also need the lsb-base package from intrepid).
remove gnome-bluetooth

reboot if it doesn't work, and try killing and invoking bluetooth-applet from the command line.

i cannot believe this bug wasn't fixed in hardy.

---

### Post by prabath_fun on 2008-09-07
Hi,
  I got reverse Problem. That is, I could not able to transfer the file from my PC to Bluetooth device (Sony Ericssion W810I). 
Please help me.
With Thanks,
PrAbAtH

---

### Post by prabath_fun on 2008-09-09
Please help me.....

---

### Post by prabath_fun on 2008-09-19
Still waiting for someones help.............

---

### Post by prabath_fun on 2008-12-16
Hi,
   Any body got succeeded? Now, I am using Ubuntu 8.10. here also same problem.

Update me please..........

---

### Post by sunvald on 2009-01-27
I have the same problem. Can send from SE 810I to PC but not reverse. I use Ubuntu 8.1. Would like a solution.

---

### Post by frekja on 2009-02-17
> **waster said:**
> alternatively, upgrading:

libbluetooth2
bluez-utils
obex-data-server

to intrepid versions (you also need the lsb-base package from intrepid).
remove gnome-bluetooth

reboot if it doesn't work, and try killing and invoking bluetooth-applet from the command line.

i cannot believe this bug wasn't fixed in hardy.

I'm running intrepid and have the problem described above (can send from computer to phone, but not the reverse), which makes me think that intrepid hasn't fixed this problem.

---

### Post by prabath_fun on 2009-10-22
Hi,
   I can able to send the files in both way. Just I install-ed Ubuntu 9.04. No problem with this...

Prabath

---

