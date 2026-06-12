---
title: "Remote Desktop Cant connect"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by alek66 on 2009-12-02
I have a 9.10, recently installed, I activated Remote Desktop [like this]("http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html") (like I always did)

I want to connect to it, and on the target ubuntu it shows that someone is trying to conect, and on my laptop it shows that it is connecting to the ubuntu. after a time it times out, and I cant connect to it.

Any idea what logs should I see?

---

### Post by yeats on 2009-12-02
Sounds like a firewall issue on one of the computers... can you verify that?

---

### Post by alek66 on 2009-12-02
Target system is a fresh ubuntu 9,10... I dont know if that comes with a firewall installed as default, but I´ll check.
The "client" is a mac os x, and i can verify that it has no fwall.

router´s firewall should be checked as well?

On 8.04 it used to worked great!

---

### Post by k()()zmi4 on 2009-12-02
> **alek66 said:**
> Target system is a fresh ubuntu 9,10... I dont know if that comes with a firewall installed as default, but I´ll check.
The "client" is a mac os x, and i can verify that it has no fwall.

router´s firewall should be checked as well?

On 8.04 it used to worked great!

Oh, I'm having trouble accessing my ubuntu karmic box from my macbook(10.6.2) too. 
The only way I could connect is by enabling password authentication in remote desktop settings on my ubuntu machine.

But... I got a frozen picture on my mac which wouldn't change, though I checked everything worked fine (I mean remote control) on ubuntu - mouse, apps opening, etc.

Router's (asus wl-500gp) firewall enabled/disabled.

Guess might try some 3rd party apps...

---

### Post by BearWayne on 2010-01-05
I have the same issue as k()()zmi4, except that I'm using ubuntu 9.04.  I've tried using both Chicken of the VNC and JollysFastVnc clients on the Mac.  Same result for both.

I am able to connect to the ubuntu box, I see the screen on the ubuntu box, I do a few mouse clicks and the commands are carried out on the ubuntu box, but the screen on the Mac never updates to show the changes that have occurred on the ubuntu desktop.  I have turned the Mac firewall off and that made no difference.

---

### Post by BearWayne on 2010-01-06
So apparently this is a known issue....  found a workaround in another thread:

[http://ubuntuforums.org/showpost.php?p=7214210&postcount=5]("http://ubuntuforums.org/showpost.php?p=7214210&postcount=5")

Turning off visual effects as described in that post worked for me.

---

### Post by k()()zmi4 on 2010-01-17
> **BearWayne said:**
> I have the same issue as k()()zmi4, except that I'm using ubuntu 9.04.  I've tried using both Chicken of the VNC and JollysFastVnc clients on the Mac.  Same result for both.
Actually, JollyFastVNC worked (and still does its job) fine for me straight outta the box

---

