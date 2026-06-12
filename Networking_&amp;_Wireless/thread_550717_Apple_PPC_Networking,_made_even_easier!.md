---
title: "Apple PPC Networking, made even easier!"
date: 2007-09-14
forum: Networking &amp; Wireless
---

### Post by Kopachris on 2007-09-14
[COLOR=Blue][SIZE=4][B]This guide is for people with an Apple PowerPC computer with Airport Extreme on Ubuntu 6.10 (Edgy).  
[SIZE=3][COLOR=Black]Intro:
[/COLOR][/SIZE][/B][SIZE=3][COLOR=Black][SIZE=2]I have a PowerBook G4.  Naturally, it has an Airport Extreme card.  Ubuntu 6.10 has a lack of support for the BCM43xx cards.  I have searched high and low for answers.  When I finally diagnosed the problem, I thought the solution would be easy.  It could have been, if I knew what I was doing.  Well, here's so you'll know what you're doing.  This guide is a compilation of stuff from all over (but mostly this wiki: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)) in (what I hope is) an easy to digest format.

[/SIZE][/COLOR][/SIZE][/SIZE][/COLOR]
**1. **This is all meant to be done just about first thing after you install Ubuntu.  First, you need to check your Internet connection.  Make sure your wireless card is enabled and all your settings are filled in.  Are you getting Internet through another computer?  Does it work?  If it works satisfactorily, you can stop here.  Others, go on.
**2.** Next you're going to download the new driver.  The only place I found told you to use terminal to download the new driver, but I don't have internet and neither do you.  Go onto another computer with a flash drive or something and go to "**[http://ubuntu.cafuego.net/pool/edgy-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb](http://ubuntu.cafuego.net/pool/edgy-cafuego/bcm43xx/bcm43xx-firmware_1.3-1ubuntu2_all.deb)**".  Save it on the flash drive and copy it to your home directory on your Ubuntu machine.
**3. **Now to install it:
```
sudo dpkg -i bcm43xx-firmware_1.3-1ubuntu2_all.deb
```After that you need to load the module:
```
sudo modprobe bcm43xx
```Check which eth prt it is with iwconfig.
**4. **Now check your internet again.  Try going into Network Manager (System>Administration>Network Manager, under GNOME) and pinging a network computer.  If there's 100% packet loss, but It still finds the computer, your firewall is in the way.
**5. **Use this to let your network computers through the firewall:
```
sudo iptables -t nat -A POSTROUTING -s *ip.address* -o *ethX* -j MASQUERADE
```where *ip.address* is the IP address you want to let through, and *ethX* is the eth card that you use (you used iwconfig, remember?).  There you go!  Your internet should work perfectly now.  Now you can run software updates and  check your email and stuff.

---

