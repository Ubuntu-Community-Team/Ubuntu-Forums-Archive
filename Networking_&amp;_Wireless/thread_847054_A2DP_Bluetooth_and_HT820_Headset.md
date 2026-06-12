---
title: "A2DP Bluetooth and HT820 Headset"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by eeboy on 2008-07-02
I can't seem to get my HT820 headset to work in Ubuntu 8.04. I can see the device using Bluetooth Preferences under my Audio Services. I've successfully paired as well. Yet... no audio. 

Any suggestions?

---

### Post by michal.bedzin on 2008-07-11
If you have it in Ur Audio Services maybe U should try this command

gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "alsasink device=bluetooth"

U turn off this with this command

gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"

It'll move Ur sound from totem (or another applications which use GStreamer engine) to Ur HT820. This command gives very clearly sound. If somethink will be not good look at this page
[http://stateless.jogger.pl/2008/01/](http://stateless.jogger.pl/2008/01/)
It is polish page but I think that U'll understand :P or mail me (michal.bedzin@gmail.com) and I'll translate impartant parts... :D

Remember that U have to have actualy Bluez-Utils :P and good commands in ~/.asoundrc file. This file should look like this

pcm.bluetooth {

   type bluetooth

   device XX:XX:XX:XX:XX:XX

   profile "voice"

}

 where X's R Ur HT820 addres (if U don't know what is it check it with "hcitool scan" command when Ur headphones R in paired mode).

Have a nice sound.

---

### Post by MES5464 on 2008-08-06
I followed all of the instructions and the headset worked for about 3 songs. Then when Rhythmbox was shuffling to a new song it just went haywire and started jumping all over the place. It also beeped in between songs. Is there some other way?

---

### Post by yurukov on 2008-11-03
I have the same problem. I am using a Motorolla stick and there probably is a problem with the drivers. I will try it out on Intrepid and will get back to you.

---

### Post by yurukov on 2008-11-08
Nope, it didn't work. I think it's because of my drivers though.

---

### Post by michal.bedzin on 2009-02-21
I'm using ubuntu 8.04.2 and everything play well. Try this distro. Maybe it helps. About the 3 songs I don't know what's a problem. I don't use Rythmbox becouse of stoping his own engine. I don't know how to repair it. I use Xmms and everything is O.K.

Regards

michal.bedzin

---

### Post by proevofanatik on 2009-07-22
can someone please post a full step by step guide on how to get this headset working? i am using kubuntu jaunty.

thanks

---

