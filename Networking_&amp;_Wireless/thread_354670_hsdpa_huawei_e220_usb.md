---
title: "hsdpa huawei e220 usb"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by jmvidalvia on 2007-02-06
I read many posts regarding howto install hsdpa huawei e220 usb, but could't solve it running Ununtu (Xubuntu/Edgy).
Ordinary Howto's seem to work with other Linux distributions, except for Ubuntu.
¿did anyone get the solution?
Many thanks, 

jm

---

### Post by jmvidalvia on 2007-02-07
I could solve it!
I downloaded huaweiAktBbo-i386.out from [http://www.kanoistika.sk/bobovsky/archiv/umts/](http://www.kanoistika.sk/bobovsky/archiv/umts/)
Made:
sudo chmod a+x huaweiAktBbo-i386.out
And created this script:

#/bin/sh
sleep 5
sudo rmmod usb-storage
sleep 5
sudo modprobe usbserial vendor=0x12d1 product=0x1003
sleep 15
sudo /your/route/huaweiAktBbo-i386.out
sleep 10
sudo wvdial huawei

It seems stupid, but the key was the sleep order. It allows the device to get use to the system! :-)
Remember to custom made:
1- "sudo /your/route/huaweiAktBbo-i386.out" acording to your route
2- "sudo wvdial huawei" according to your wvdial.conf

Best luck!

---

### Post by svenkatesan on 2007-03-05
Hi Jim
Can you pl tell me bit elaborate.
I type this script in an editor...
what should I do? save in a place? with what ext.?
Anywhere will do?
How am I activate this script?Thro console?
Pl give a direction to follow.
Is any way to stop the connection?
Thanks in advance.

---

### Post by jmvidalvia on 2007-03-05
Well, I am not an expert, but...
1- Use your prefered editor to create the script. A script is just a text file able to be ejecuted by the system. In my case I use "vim", so:
1-In console type:
vim myscrypt.sh
2- It opens the editor in the console. Type "i" letter to activate insert mode. Copy the text for the script from this forum and paste it into the screen of the console. Press escape ant type ":wq", to save and quit.
3- The script has been created, but it has no execution permission, so in console type:
chmod 777 myscript.sh
Now everybody can execute the program.
If you execute it from the directory where the file is, y must do, form console:
./myscript.sh
That's all.
From a diferent place:
/complete/route/myscript.sh

It is very important, as I said, that modify my sample script according to your directories, in:
1- "sudo /your/route/huaweiAktBbo-i386.out" acording to your route
2- "sudo wvdial huawei" according to your wvdial.conf.

You would need to learn a little bit about wvdial. You can use this page:
[http://www.mybroadband.co.za/vb/showthread.php?t=21726](http://www.mybroadband.co.za/vb/showthread.php?t=21726)

Good luck,

---

### Post by svenkatesan on 2007-03-05
Thanks a lot Jim.
This is the thing I want.This will help lot of new commers.
Anyway,u didn't answer one last ?
How to Kill/stop the modem?

---

### Post by jmvidalvia on 2007-03-05
Very easy!
From console, 

sudo killall wvdial

You can also make a small script (you already know how to!) with this order.
Regards,

---

### Post by svenkatesan on 2007-03-05
Hi Jim
Connecting the modem works great.
Kill- script!!
I can do  it,when I go back home.
"Can" was brought by you.
Thanks on behalf of "New Bees".

---

### Post by jmvidalvia on 2007-03-06
Glad to hear I've been helpfull for anybody, after so much time learning from forums..
That's the magic of linux...
Enjoy it!

---

### Post by skywatcher on 2007-03-09
Hi Jmvidalvia

I have just come across your advice that seems to work for the E220 USB modem. I'll certainly try it, because I've been struggling for about two weeks now to get it to work. Just a question or two: at what stage do I plug in the modem, and do I have to unplug/plug it again at any stage?

Thanks

---

### Post by jmvidalvia on 2007-03-09
Hi skywatcher, 

Start the computer, plug the usb modem, whait a little bit thil the usb-device is mounted (if you have auto-mount), and start the script.
It is important you switch off the pin verification of your huawei card, to avoid problems.
Just put the small card in any cellular phone and set it not to ask the pin code every thime.
Best luck!

---

### Post by skywatcher on 2007-03-09
Hi jmvidalvia

Thanks for your advice. Everything works until I get this response:

'--> Using interface ppp0'

Then it gets stuck, and the system re-initializes the modem repeatedly, but it never gets to the last four lines:

--> local  IP address 10.62.100.132
--> remote IP address 10.64.64.64
--> primary   DNS address 196.207.40.165
--> secondary DNS address 196.43.46.190

This has been my problem for two weeks now!

Do you have an idea of what could be wrong here?

Cheers

---

### Post by jmvidalvia on 2007-03-09
I am afraid i can not help you.
I am not skilled enough...
Best luck!

---

### Post by krisravn on 2007-03-17
I had the same problem,
The problem was caused by an incorrect configured atn address.

You will find that in the /etc/wvdial.conf

```
[Dialer internet]
Init5 = AT+CGDCONT=1,"IP","internet"
```

Replace "internet" with the atn you have been supplied by your 3g provider

---

### Post by rage_ext on 2007-07-06
Just wondering weather or not you are using this following driver and software for Huawei E220?

[https://forge.vodafonebetavine.net/projects/vodafonemobilec/](https://forge.vodafonebetavine.net/projects/vodafonemobilec/)

It works on my computer without problems. Just remember to call your phone company to ask the settings... ;)

---

