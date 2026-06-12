---
title: "Bluetooth A2DP (and more) not working"
date: 2014-02-10
forum: Networking &amp; Wireless
---

### Post by PureTryOut on 2014-02-10
On both my laptop and desktop, bluetooth seems to fail when it needs a constant connection (like with A2DP).
I want my phone to play all it's sound via my laptop speakers, so I can hear all notifications etc using my headset.
On both computers, this works fine on Windows 7. On Ubuntu (running 13.10, but also occurred on 13.04) it connects, but after that it's not usable.

When sending files from my pc to the phone I get an error message saying connection failed (i'm sorry but I can't show you the exact error at this moment).
If I click connect on my phone, it tries connecting for like a minute but then just stops.
Setting up A2DP using Blueman, it says "Stream setup failed".

After searching on Google **a lot** I found [this]("http://askubuntu.com/questions/287254/ubuntu-13-04-bluetooth-a2dp-does-not-work") thread, which describes my problem better.
The second answer in there worked for me, but I have to redo everything on every reboot which is a pain.

Is there a way to permanently fix this, or do I just have to deal with redoing everything every time I want to use A2DP or send files?

---

### Post by tgalati4 on 2014-02-10
So this is answer #2:

> 
I'm running ubuntu 13.04 and had a simlar issue after upgrading from 12.10, I've managed to temporarily get around it, but unfortunately this needs to be redone after each reboot. If anybody can automate this process please let me know how. Thanks.

First we need to kill pulseaudio, -- but pulseaudio always restarts, so we need to disable that - Into terminal; sudo gedit /etc/pulse/client.conf

change "autospawn = yes" to "autospawn = no", and set "daemon-binary" to "/bin/true". Make sure these lines are uncommented.

save, and close the file. Done, pulse audio will no longer restart after a crash or force close.

Next run, sudo gedit /etc/bluetooth/audio.conf

and under 'General' add Enable=Socket

close and save the file.

run in terminal; sudo service bluetooth restart

run in terminal; pulseaudio --kill

now connect to the bluetooth device (I've tested this using BLUEMAN)

run in terminal; pulseaudio

then in a different terminal window; sudo gedit /etc/bluetooth/audio.conf

remove "Socket", leaving "Enable="

save and close the file

run in terminal; sudo service bluetooth restart

connect to your bluetooth device again; - and it should (hopefully) work.

So this procedure describes a valid work-around, but it needs to be done after each boot.  So the next question is how to make this work-around stick?

1.) Leave autospawn set to *no*.  Then if you loose sound (which is rare), you will have to manually kill and restart pulseaudio.
2.) Put another script at the very end of your boot sequence that halts paulseaudio, resets the bluetooth stack (with the new, working settings), then restarts pulseaudio.
3.) Spends some time looking at the initial boot sequence and move the bluetooth daemon to start before pulseaudio daemon.
4.) Another procedure that I haven't thought of yet.

---

### Post by orble.h on 2014-04-09
I think I found the real reason at this problem. 
When desktop just started, run pacmd in terminal and "dump", compare to run pulseaudio manually and pacmd and "dump" !!!! 
What's different ? 
There are two special lines with running pulseaudio manually:
 [HTML]
load-module module-bluez5-discover
load-module module-bluez4-discover
[/HTML]
dam* it !  It doesn't load these modules when desktop just started. 

And .... I found "module-bluez5-discover" is  a bad thing, also cause "stream setup fail". 

Solved !!!  We just need to add a command below ,  at desktop session started:
[HTML]
sleep 30 && echo load-module module-bluez4-discover | pacmd
[/HTML]

---

