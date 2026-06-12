---
title: "bluetooth obex [mac address] is not a valid location"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by systemintheglitch on 2007-12-14
I tried to hook up my thinkpad x60 tablet with both an iphone and a macbook and neither worked.. Instead i got that error both times with both devices.. What gives?
What the heck is an obex?

---

### Post by systemintheglitch on 2007-12-14
bump

---

### Post by u01p2109 on 2007-12-17
> **systemintheglitch said:**
> bump
bash: bump: command not found

---

### Post by vintermann on 2007-12-18
> **systemintheglitch said:**
> I tried to hook up my thinkpad x60 tablet with both an iphone and a macbook and neither worked.. Instead i got that error both times with both devices.. What gives?
What the heck is an obex?

I have a ThinkPad t60, and exactly the same problem. The machine isn't discoverable either, even though it says it is.

I'll look around and see what I can find.

UPDATE: sudo apt-get install gnome-vfs-obexftp. Strange, I am sure I have done it before from this machine. Perhaps the need for this package came at the latest dist-upgrade.

---

### Post by mizzikee on 2007-12-27
OMG YOU ROCK VINTERMANN!!!!! Fixed my issue!

---

### Post by robwales on 2008-01-06
Beautiful. This worked for me too with my Nokia mobile phone

---

### Post by MikeDixson on 2008-01-10
Thanks Vintermann, sorted me out too.

---

### Post by A + on 2008-01-11
"sudo apt-get install gnome-vfs-obexftp"

that did it for me too !

thanks

Sony Ericsson W810i / Canyon CN-BTU3 Class II ( &#8364;20 )

---

### Post by yingjai on 2008-01-16
Installing gnome-vfs-obexftp did nothing for me. Fortunately after a day or two, I found a solution that worked. I only followed part of the howto I was reading. This is exactly what I did to get my bluetooth mouse working with auto reconnecting (when turned off/on).

Press the connect button on device.

```
hcitool scan
sudo hidd --connect=YOUR_MAC_ADDRESS
```

Then I turned off my mouse, but you probably don't have to. It did prove that my laptop automatically recognized the mouse though.

```
sudo gedit /etc/bluetooth/hcid.conf
```

append to the end of the file:
```
device YOUR_MAC_ADDRESS {
name “Microsoft Mouse”;
}
```

save and restart bluetooth with:
```
sudo /etc/init.d/bluez-utils restart
```

or if you get a command not found error:
```
sudo /etc/init.d/bluetooth restart
```

Then I proceeded to turn on my mouse to do the pairing part of the howto, but my laptop already recognized it and asked if I wanted to authorize everytime it tries to connect. Check it and you're off.

The howto:
[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)

---

### Post by kenshinblade on 2008-01-17
brilliant Vintermann, it worked on my hp laptop too \\:D/

---

### Post by elbowgeek on 2008-01-22
Hi all.  I had the same message as the original poster.  I tried installing the obex-ftp thing which did change the message I was getting. I did as yinjai suggested, but to no avail.

The message I get now is: Couldn't display "obex://[00:17:00:57:01:0f]" 

If anyone has any insight that would be great.  I think I'm almost there *grin*.

Cheers

Oops, just wanted to clarify, I get the message when I click on the bluetooth icon in the bar at the top and click Browse Device, select the PEBL then press connect.  The phone buzzes briefly as it is definitely making some sort of connection, but thereafter it presents the message and that's it.

Cheers again

---

### Post by geoffatmk on 2008-01-26
Hi

I have the same issue as elbowgeek.  I am using a treo 650 on gutsy.  Can connect and browse my Nokia E61 but cannot make the connection stick with the Palm.

When I try to connect over my network setting to my PC from the treo (Preferences, network, my PC, connect) I get;

Error: Serial : timeout.  Could be bad cable or faulty modem (0x0305)

but my idle time out is set to 3 minutes so not sure what is happening.

Can anyone help?

---

### Post by richyrichuk on 2008-01-26
nice 1. worked for me to :D

---

### Post by wkimberly on 2008-01-26
> **elbowgeek said:**
> 
The message I get now is: Couldn't display "obex://[00:17:00:57:01:0f]" 


The command: [FONT="Courier New"] sudo apt-get install gnome-vfs-obexftp [/FONT]   worked like a charm.

 I got the message of **elbowgeek** when I took too much time to PAIR the devices. If I inserted the pass code quickly enough the timeout did not occurred. Do this steps quickly and you should not have the same issue:
- On Ubuntu (Gusty) choose to connect to the device you want.
- On the device enter the pass code.
- On Ubuntu click the bubble that appears near the bluetooth icon.
- Insert the same pass code and hit OK.

Hope this helps.

---

### Post by champs777 on 2008-01-29
Thank you Vintermann, That worked perfectly!

---

### Post by gajanan.khandake on 2008-02-04
Thanks Vintermann....
It ([COLOR="Indigo"]sudo atp-get install gnome-vfs-obexftp[/COLOR]) also worked in my case.
Weldone

---

### Post by pepe241185 on 2008-02-09
Thanks man ,,, this worked great on My Lenovo T60  !!

---

### Post by nicandris on 2008-02-10
Worked for me too (w880i)!!! sudo apt-get install gnome-vfs-obexftp

---

### Post by geoffatmk on 2008-02-11
Perhaps my problem is different to elbowgeek's.  I am paired and both devices see each other but my Treo 650 will not let my computer browse it.  Every time I try I get;

Couldn't display "obex://[00:07:e0:06:91:38]".
Check if the service is available.

I read that I need to add the Treo to my "Input Services" list in preferences but every time I try to do so the preference window closes (crashes?) and the Treo is not added.  I still cannot browse my Treo.

I am still looking for a soluiton.  Is this a Palm treo 650 issue rather than a bluetooth one?  I can connect and browse my Nokia E61.

Geoff

---

### Post by darxoul on 2008-02-17
> Couldn't display "obex://[00:07:e0:06:91:38]".
Check if the service is available.

I have the same issue with my Logitech HS03 V04 headset. I can see it in the list and when I try to connect it says: Check if the service is available...

---

### Post by teslarage on 2008-02-18
I am stuck.

Usually I can browse my SE w810i, but now all I get is:

Couldn't display "obex://[00:16:20:96:1c:6b]".
Check if the service is available.

I have installed gnome-vfs-obexftp, it was working fine... until now.

---

### Post by alexeix on 2008-02-22
I have this same error on 7.10 when trying to use my Plantronics M3000 bluetooth headset with Skype.

I've tried all of the relevant suggestions that I've found on the forum, but it's still not working and I'm losing patience.

I found a bug report which suggests there is a known issue, but I don't know when/if it will be fixed.

Can anyone recommend an inexpensive bluetooth headset which definitely works with Ubuntu 7.1 and Skype?

Preferably one which is available in the UK...

Cheers!

---

### Post by darxoul on 2008-02-22
I have also tried all the solutions I have found including changing the Bluetooth handler. Neither of them worked. I cannot say I am losing my patience, because I already lost it. I am using my headset which is only a few months old pretty much that I cannot switch to Ubuntu anymore. AS far as I have understood the bug is there even for 8.04?

---

### Post by Kivech on 2008-02-22
Well, looks like I have the same issue.

I can browse my phone for maybe 10 seconds, then suddenly everything becomes inaccessible and that's the end of it. Seems to me like it doesn't manage to maintain a connection with my Nokia for some reason.

I really would like a solution to this because now I cannot transfer my images from my phone to my PC.

Kivech

---

### Post by jroq on 2008-02-25
> **yingjai said:**
> Installing gnome-vfs-obexftp did nothing for me. Fortunately after a day or two, I found a solution that worked. I only followed part of the howto I was reading. This is exactly what I did to get my bluetooth mouse working with auto reconnecting (when turned off/on).

Press the connect button on device.

```
hcitool scan
sudo hidd --connect=YOUR_MAC_ADDRESS
```

Then I turned off my mouse, but you probably don't have to. It did prove that my laptop automatically recognized the mouse though.

```
sudo gedit /etc/bluetooth/hcid.conf
```

append to the end of the file:
```
device YOUR_MAC_ADDRESS {
name “Microsoft Mouse”;
}
```

save and restart bluetooth with:
```
sudo /etc/init.d/bluez-utils restart
```

or if you get a command not found error:
```
sudo /etc/init.d/bluetooth restart
```

Then I proceeded to turn on my mouse to do the pairing part of the howto, but my laptop already recognized it and asked if I wanted to authorize everytime it tries to connect. Check it and you're off.

The howto:
[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)

This all worked except for when it came to turning off and turning my mouse back on.

The command "sudo hidd --search" works as well for allowing me to use my mouse. The problem is that nothing seems to allow the mouse to be automatically detected when turned on without discovery mode being enabled on the mouse.

The mouse is a "Microsoft WIreless Laser Mouse 8000"

Thanks in advance for any tips!

-jroq

---

### Post by Kivech on 2008-02-25
Does anyone know how to get Bluetooth working properly under Ubuntu 7.10 (64 bits in my case)?

So far non of the suggestions made any difference for me. There must be a way to get it working properly.

---

### Post by sp200606 on 2008-02-27
U could try to delete the pairing directly on the phone, and then try to reconnect from the PC.

Worked for me, after all the above suggestions failed...

---

### Post by teslarage on 2008-02-28
well for me, i am using a w810i. the ONLY workaround that i found was to browse as fast as i can. if i were to stop for just a few moments, the connection will be 'destroyed'. if that happens, restarting my phone will allow me to get them connected again.

btw, try [blueman]("http://blueman.tuxfamily.org/"). I think it's a nice application to manage your bluetooth devices :)

---

### Post by EliBaskin on 2008-03-02
Worked on my Dell Inspiron 6400 as well. Thank you Winterman!

---

### Post by dee_kay on 2008-03-09
> **vintermann said:**
> I have a ThinkPad t60, and exactly the same problem. The machine isn't discoverable either, even though it says it is.

I'll look around and see what I can find.

UPDATE: sudo apt-get install gnome-vfs-obexftp. Strange, I am sure I have done it before from this machine. Perhaps the need for this package came at the latest dist-upgrade.


Cheers for this!  Spot on.  Connected to my Nokia now.

Rgds,
Dave

---

### Post by danevans29 on 2008-03-27
Amazing!  Works like a charm. Finally I can add piZero's New Gold theme...

Thanks a ton.

---

### Post by JaxDomino on 2008-04-04
What a life saver!  I thought I was going to have to fire up my damn Windows XP desktop at home, that I NEVER use!

---

### Post by babarhaq on 2008-04-05
> **Kivech said:**
> Well, looks like I have the same issue.

I can browse my phone for maybe 10 seconds, then suddenly everything becomes inaccessible and that's the end of it. Seems to me like it doesn't manage to maintain a connection with my Nokia for some reason.

I really would like a solution to this because now I cannot transfer my images from my phone to my PC.

Kivech

I have exactly the same problem with my e51.

---

### Post by zoopzoop on 2008-04-07
gnome-vfs-obexftp did it for me as well!

---

### Post by MES5464 on 2008-05-09
Ok. I am trying to connect my Lenovo X60 Tablet (Ubuntu 8.04) to a Motorola HT820 headset. I have them paired but when I try to connect I get:

--------
Couldn't display "obex://[00:07:A4:F2:2B:24]/".

Error: Host down
Please select another viewer and try again.
--------

I tried the following:
sudo apt-get install gnome-vfs-obexftp

with no success. Has anyone else made progress on this?

---

### Post by zehava on 2008-05-09
I wonder if you need to connect as an audio service.  Kinda like an input service.  

Check this out...  [http://ubuntuforums.org/showthread.php?p=4736516](http://ubuntuforums.org/showthread.php?p=4736516)

Hope it helps

Chuck

---

### Post by illbashu on 2008-05-12
> **MES5464 said:**
> Ok. I am trying to connect my Lenovo X60 Tablet (Ubuntu 8.04) to a Motorola HT820 headset. I have them paired but when I try to connect I get:

--------
Couldn't display "obex://[00:07:A4:F2:2B:24]/".

Error: Host down
Please select another viewer and try again.
--------

I tried the following:
sudo apt-get install gnome-vfs-obexftp

with no success. Has anyone else made progress on this?

i have the same prob, no one seems to have a fix. i made a thread and a bug report...

bug report
[https://bugs.launchpad.net/bugs/159887](https://bugs.launchpad.net/bugs/159887)

Thread
[http://ubuntuforums.org/showthread.php?t=791943](http://ubuntuforums.org/showthread.php?t=791943)

---

