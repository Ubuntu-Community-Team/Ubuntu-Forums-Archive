---
title: "Problem Creating a ADSL Connection - A complete newbie to linux an ubuntu"
date: 2007-02-01
forum: Networking &amp; Wireless
---

### Post by joel85 on 2007-02-01
hi there,
I am a complete newbie to this linux and the best of linux (ubuntu) I really like this OS so i wish to stay with it rather than uninstalling from my system.... since I am a newbie i encounted one major problem. I have a conextant ADSL USB modem. Its recognized in the ubuntu device manager but I'm unable to create and use a working internet connection. Please help me with this issue... thank you.

---

### Post by anubhavrocks on 2007-02-01
try running

sudo pppoeconf

---

### Post by joel85 on 2007-02-01
hi thanks for the speedy reply
tried running sudo pppoeconf but it says modconf not installed... pls help, i'm in a desperate situation
my modem is a conextant accessrunner modem connected to PC via USB cable
thanks in advance

---

### Post by anubhavrocks on 2007-02-01
sudo apt-get install modconf

---

### Post by anubhavrocks on 2007-02-01
This should help
[https://help.ubuntu.com/community/UsbAdslModem/AccessRunner](https://help.ubuntu.com/community/UsbAdslModem/AccessRunner)

---

### Post by joel85 on 2007-02-01
hi thank you very much for your time in giving me a reply... although i'm an advanced user in windows i'm null in linux... pls help me furthur... well I tried all the above links and methods but none of them work...

so is there are any alternate methods?
thanks again

---

### Post by anubhavrocks on 2007-02-02
can you just retrace  the steps you have followed and put the resulting outputs,if you need help you should be providing atleast some info.

---

### Post by joel85 on 2007-02-06
yes definitely Anubhavrocks... thanks for the interest shown... i jus finished downloading the ubuntu 6.10 DVD... ill install and follow the same steps again....

---

### Post by joel85 on 2007-02-06
Hi, Anubhavrocks or any other experienced user please tell me how to set up an ADSL connection... My USB Conextant accessrunner ADSL modem is detected and the network light is on... but cant connect to the net as I'm unable to set up my connction parameters (VCI, VPI, Handshake protocol, encapsulation...,etc) please help me to set it up...

many thanks

---

### Post by anubhavrocks on 2007-02-08
This link might help you
[http://accessrunner.sourceforge.net/connection.shtml](http://accessrunner.sourceforge.net/connection.shtml)

---

