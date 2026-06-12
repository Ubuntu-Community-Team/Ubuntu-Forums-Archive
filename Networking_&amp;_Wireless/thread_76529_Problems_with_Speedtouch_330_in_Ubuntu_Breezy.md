---
title: "Problems with Speedtouch 330 in Ubuntu Breezy"
date: 2005-10-15
forum: Networking &amp; Wireless
---

### Post by pezz1986 on 2005-10-15
Hi people, I can't install my usb modem Speedtouch 330, in the version 5.04 this manual [http://www.linux-usb.org/SpeedTouch/ubuntu/]("http://www.linux-usb.org/SpeedTouch/ubuntu/") work fine but in 5.10 not work. ¿Anybody can tell me how can I install it?

---

### Post by RU63 on 2005-10-15
I was about to install breezy for a friend and realized they are using a speedtouch modem, in UK.  I don't use speedtouch myself so . . .
Is there a problem with speedtouch not getting picked up on install?

---

### Post by hsf on 2005-10-16
[QUOTE=pezz1986]Hi people, I can't install my usb modem Speedtouch 330, in the version 5.04 this manual [http://www.linux-usb.org/SpeedTouch/ubuntu/]("http://www.linux-usb.org/SpeedTouch/ubuntu/") work fine but in 5.10 not work. ¿Anybody can tell me how can I install it?[/QUOTE]

Hi!

I had hoary working fine with it then i've upgraded to breezy and it is working fine too :D .

But, in another computer, i've set a new fresh breezy and then I realized that those steps don't work on it :???:

Maybe it's something simple...
Can someone help?

---

### Post by frank_b on 2005-10-16
In my case, I had my internet connection working fine in Hoary and when I upgraded to Breezy it stopped working.

I then tried to reinstall the connection and followed again the instructions in [http://www.linux-usb.org/SpeedTouch/ubuntu/](http://www.linux-usb.org/SpeedTouch/ubuntu/) that worked for Hoary but don't seem to work now in Breezy... :(

---

### Post by pezz1986 on 2005-10-18
I have found something but it's in French [http://wiki.ubuntu-fr.org/materiel/modem_adsl_speedtouch_330]("http://wiki.ubuntu-fr.org/materiel/modem_adsl_speedtouch_330")
I have tried to do it but I do not understand much.

---

### Post by bruce89 on 2005-10-18
It works absolutely fine for me, as I followed the instructions yesterday.

---

### Post by frank_b on 2005-10-19
Nice pezz1986! :)

I'll be busy in the next day or two, but I know a bit of french and I think I can translate it. I'll post a translation here as soon as I can.

Meanwhile, I'll also send an e-mail to the person who wrote the [http://www.linux-usb.org/SpeedTouch/ubuntu/](http://www.linux-usb.org/SpeedTouch/ubuntu/) tutorial to see what he has to say.

All this when I have the time to do it.

Until then.

---

### Post by pezz1986 on 2005-10-19
I solved the problem follow the first guide. I downloaded libatms for breezy [http://packages.ubuntu.com/breezy/libs/libatm1]("http://packages.ubuntu.com/breezy/libs/libatm1") 
and br2684ctl for ppoe [http://packages.ubuntu.com/breezy/net/br2684ctl]("http://packages.ubuntu.com/breezy/net/br2684ctl")
but br2684ctl I did not install doing dpkg -i. instead of that I did it of this form sudo sudo install -m 755 br2684ctl_20040226-1_i386.deb /usr/sbin
thank you very much guys :eek:  you are the max

---

### Post by frank_b on 2005-10-19
I got some time today and was about to start translating the french tutorial, but if you say it works that way I guess it's not needed anymore.

Beeing new to linux it seems a strange procedure.

I remember I didn't exacly follow the procedure for Hoary and got the debian or ubuntu packages instead also.

The libatm1 package, it's supposed to be already in Breezy, from what I read (Can't check now... have to reinstall it again), but isn't a ".deb" package only possible to "install" using the "dpkg -i" command?

Whatever. When I get some more time, I'll calmly compare the two tutorials.

I'll e-mail the first tutorial guy anyway.

Thanks for the tip.

---

### Post by frank_b on 2005-10-21
Strange thing...

The "libatm1" package that comes with Breezy must have a bug or something like that.

I managed to get it working with the [http://www.linux-usb.org/SpeedTouch/ubuntu/](http://www.linux-usb.org/SpeedTouch/ubuntu/) tutorial.

But what I did was to install the "br2684ctl" package from [http://packages.ubuntu.com/breezy/net/br2684ctl](http://packages.ubuntu.com/breezy/net/br2684ctl) with the "dpkg -i" command and not the "libatm1" package at first.

I rebooted the computer and didn't work.

I had checked in Synaptic for the "libatm1" package and there it was, the same version that you can download from [http://packages.ubuntu.com/breezy/libs/libatm1](http://packages.ubuntu.com/breezy/libs/libatm1).

I then tried to install the "libatm1" file I downloaded from packages.ubuntu.com, the "dpkg" command didn't complain that it already had that version installed and the package was installed.

I rebooted my computer and had my connection working. :)

---

### Post by frank_b on 2005-10-21
It's not a problem with the "libatm1" package. That doesn't make any sense.

Sorry for the newbies like me that might be confused with that statement.


I've been experimenting and the thing is that the connection is just not always successful.

I couldn't "see" what was happening at first because I was used to check the "Ctrl-Alt-F1" window to check the connection trials, but then I discovered that the same windows is now in "Ctrl-Alt-F8".


I checked this window and saw that, no matter if I "disable[d] compression" or not - actually I'm more successful when I don't - the connection was sometimes successful, sometimes not.

I think the "problem" might be with the boot script... since that, with this one I can only see it trying to connect once and I'm successfull only around half the times... and for Hoary I could see it trying to connect 4 or 3 times and was successful in almost all of them.


I'm just about to send that e-mail...

---

### Post by frank_b on 2005-10-27
I think I got it.

Indeed, in my case, the problem is with how the boot script is written.
I don't know how the ADSL lines work in other countries, but in my case, with a revision 4 modem, it takes a while before I can successfully attempt to connect to my ISP, after booting my computer either in Linux or Windows.
The line seems to take a while "getting ready" or something, even after the "ADSL" green light stops blinking and I always have to wait for some time before which it's no use trying to connect to my ISP.
And this seems to be why, with the boot script that is given, it doesn't always connect.

The version for Hoary, I just checked, had a "sleep 20" command before the "pppd call speedtch" one that tries to make the connection. While the more recent version for Breezy tells the computer to "sleep" for only 10 seconds.
In my case, this seems to be more than half the times not enough. And when I increase the value to bigger "sleep" times I can then always get a connection.
Therefore, I think that the solution for anyone who has problems getting a connection is just a question of finding out how much time is enough for you to wait before trying to connect to your ISP.
At least that's how it works for me.

In case anyone has doubts about what I'm talking about, this is the line in question (in **bold**) in the boot script:

[I]
#!/bin/bash
modprobe ppp_generic
modprobe pppoatm
modprobe br2684
count=0
while [[ $count -lt 40 ]]
do
  sync=$(dmesg | grep 'ADSL line is up')
  if [ ! -z "$sync" ]
  then
    br2684ctl -b -c 0 -a VP.VC
    sleep 3
    ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up
    **sleep 10 <- THIS ONE (TRY INCREASING THE VALUE IN THIS LINE TO MORE SECONDS)**
    pppd call speedtch
    exit 0
  fi
  sleep 1
  let "count += 1"
done
echo "The Speedtouch firmware didn't load"[/I]


Also, you can always just try to connect again after the computer boots with the "sudo pppd call speedtch" command in a terminal...

---

### Post by jeffreyvergara.NET on 2005-10-27
anyone having a problem auto connecting after disconnected? I experienced this last night, I was surfing then the led starts on blinking, I waited it to get steady but I didnt get any connection back. I don't have this problem (I think) in hoary and breezy preview... this is really weird

---

### Post by frank_b on 2005-10-28
(To complete my previous post: I don't know how ADSL lines work in other countries but I am obviously assuming that they work the same way...)

Just to tell you that I've tried and it works also if you copy the "dial" file to, for example, your home folder and execute it there with the command "sudo sh dial" a while after the computer boots.

---

### Post by Hugo Bio on 2005-11-03
Sorry guys, but it's not working for me... The script error is senseless, as i make my own script... I'm getting an error message in the second step (using br2684ctl to make the bridge)... It simply does not create the nas0 interface! and without it, i can't manage to use pppoe... in Ubuntu 5.04, i managed to use it as follow:

First> Upload firmware to modem;
Second> Use br2684ctl to create nas0 interface (it's like using Usb instead of eth0);
Third> Using pppoe to connect to my ISP (it requires autentication).

My problem is, as soon as I type br2684ctl -b -c 0 -a 0.35 it displays an error message: unable to create nas0 interface (or something like that).

besides, i'm encoutering another problem... i can't install rp-pppoe!

Ugh! Can someone help me please?

---

### Post by Hugo Bio on 2005-11-05
Anyone? Please?
is there another way to create one interface such as nas0, eth0, ppp0 anything? So i can use it with rp-pppoe? or even with pppoeconfig?

---

### Post by bissej on 2005-12-03
hello. i am a new user and i'm having some trouble. everything was working fine with 5.04. i upgraded to breezy the other day, and now i'm having trouble connecting to the internet. i have an ethernet connection, and now it is very unstable. it will work for a few minutes but then regularly goes down, and i can usually reconnect but it often takes awhile. any ideas? i want to try to change the sleep time in the boot script like recommended, but i couldn't find this particular script. where is it located?
thanks.


[QUOTE=frank_b]I think I got it.

Indeed, in my case, the problem is with how the boot script is written.
I don't know how the ADSL lines work in other countries, but in my case, with a revision 4 modem, it takes a while before I can successfully attempt to connect to my ISP, after booting my computer either in Linux or Windows.
The line seems to take a while "getting ready" or something, even after the "ADSL" green light stops blinking and I always have to wait for some time before which it's no use trying to connect to my ISP.
And this seems to be why, with the boot script that is given, it doesn't always connect.

The version for Hoary, I just checked, had a "sleep 20" command before the "pppd call speedtch" one that tries to make the connection. While the more recent version for Breezy tells the computer to "sleep" for only 10 seconds.
In my case, this seems to be more than half the times not enough. And when I increase the value to bigger "sleep" times I can then always get a connection.
Therefore, I think that the solution for anyone who has problems getting a connection is just a question of finding out how much time is enough for you to wait before trying to connect to your ISP.
At least that's how it works for me.

In case anyone has doubts about what I'm talking about, this is the line in question (in **bold**) in the boot script:

[I]
#!/bin/bash
modprobe ppp_generic
modprobe pppoatm
modprobe br2684
count=0
while [[ $count -lt 40 ]]
do
  sync=$(dmesg | grep 'ADSL line is up')
  if [ ! -z "$sync" ]
  then
    br2684ctl -b -c 0 -a VP.VC
    sleep 3
    ifconfig nas0 192.168.0.1 netmask 255.255.255.0 up
    **sleep 10 <- THIS ONE (TRY INCREASING THE VALUE IN THIS LINE TO MORE SECONDS)**
    pppd call speedtch
    exit 0
  fi
  sleep 1
  let "count += 1"
done
echo "The Speedtouch firmware didn't load"[/I]


Also, you can always just try to connect again after the computer boots with the "sudo pppd call speedtch" command in a terminal...[/QUOTE]

---

### Post by rufian1 on 2005-12-10
I am using the version 4 gray speedtouch 330 modem with PPP Over ATM . I configured succesfully on 5.04 Hoary using the method described in [http://ubuntuforums.org/showthread.php?t=44763&page=1&pp=10]("http://ubuntuforums.org/showthread.php?t=44763&page=1&pp=10") but upon upgrading to breezy 5.10 this method no longer worked. Modem syncs as shown by *tail -f /var/log/messages* but firefox won't navigate. I get a "www.whatever.com could not be found. Please check the name and try again" msg.

Same results with the method posted on [http://www.linux-usb.org/SpeedTouch/ubuntu/]("http://www.linux-usb.org/SpeedTouch/ubuntu/").

I am a totally green newbee. Help is highly appreciated. Thanks

---

### Post by adrian34 on 2005-12-11
Hi, I'm trying to install Ubuntu 5.10 on my desktop computer.
It is a clone and it has an integrated network card and a USB SpeedTouch 330.
With my ISP I need to use the speedtouch.
At the beginning the net card is detected (apparently) OK.
But after that, the installation try to DHCP and obviously nothing happens and the system hangs.
I'm not skilled enough on linux and as I can't get the system working, I can't follow the posted directions I saw on speedtouch.
Can anybody help me?:confused: 
(I`m a spanish speaker, sorry for my English)
Thanks in advance
Adrian

---

### Post by Gallows on 2006-03-19
Adrian

You really need to have a look at [this]("http://ubuntuforums.org/showthread.php?t=44763&page=1&pp=10") It's the speedtouch USB howto on the Ubuntu forums.  It has really helped me but it's just a shame that the Speedtouch modem is such a pain to get working.

---

