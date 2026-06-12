---
title: "Alternative to Network Manager for Wireless?"
date: 2007-05-09
forum: Networking &amp; Wireless
---

### Post by Josh1 on 2007-05-09
Network Manager worked fine for wireless (picked up my wireless router, logged into it) until I changed my password. Now it won't let me configure it at all.

Is there a good alternative to network manager or is there a way to change the password of the wireless (I had it set to automatic with the default keychain).

---

### Post by dannyboy79 on 2007-05-09
> **Josh1 said:**
> Network Manager worked fine for wireless (picked up my wireless router, logged into it) until I changed my password. Now it won't let me configure it at all.

Is there a good alternative to network manager or is there a way to change the password of the wireless (I had it set to automatic with the default keychain).


not sure if I understand. network-manager has nothing to do with configuring your wireless router. also, the password used to change settings in network-manager within ubuntu is the same password as you use for sudo commands. if you can't perform a simple sudo command like this which will temporarily change you to the root user then somehow you have forgotten or changed your password to something else accidentally.

sudo -i
(enter your password)

to change your users password (which is the same thing that makes sudo work) this is what you can do:

Turn your computer on.
5. Press ESC at the grub prompt.
6. Press e for edit.
7. Highlight the line that begins kernel ........., press e
8. Go to the very end of the line, add rw init=/bin/bash
9. press enter, then press b to boot your system.
10. Your system will boot up to a passwordless root shell.
CAUTION: This is a FULL ROOT SHELL! You can damage your system if not careful!
11. Type in passwd <username>. Set your password.
12. Type in reboot.

A totallly different situation is if you can no longer log into your wireless router because it won't accept your password, this can be caused by 2 different things.

1. The password it is asking for is the password for the keyring (it's like a password for all of the passwords associated with it) usually the keyring password is the same as your desktop login password (and if so there should be an option for it not to be requested), but it can be different. It does not have anything directly to do with your wireless account password so that would mean that your sudo password isn't working and follow the instructions above.

OR

2. IF you changed your router's password but can't get into it even without using the default keychain then you'll need to perform a factory reset on the wireless router. normally there is a little button on the bottom or back of it, just press and hold that for over 10 secs. sometimes you even need to unplug it, press in the reset button and hold it pressed in, then plug it in and still hold in the reset button for 20 seconds to get it to reset. 

then there is a certain way you need to plug everytyhing in again. this is how my netgear router works,

turn off everything, computer, modem, router and unplug both power wires from the router and modem and the ethernet cord from the router to the modem also.

after you have reset your wireless router, and everything is unplugged (ethernet and power), first plug in the power for the modem and wait at least a minute until all the lights are on (obviously not the activity or transfer light), then plug in the ethernet cable from the modem to the router (NO power on the router yet!), after you plug in the ethernet cord from the modem to the router, then plug in the power to the router. now wait a couple secs. now finally plug in the ethernet plug from the router to the computer (computer is still OFF don't forget) now that modem is on, connected to router, router is on and connected to the computer, now turn on the computer. It's impossible to configure your router for the first time using wireless so that's why we hooked the computer to the router with ethernet. when your computer boots up, open any browser, most routers are either 192.168.0.1 or 192.168.1.1 and the default username and password are always listed on the manufacturers website, it'lll be either **admin** and **password** or **admin** and **1234**. 

Ok now that you're logged into your router, you can set it up again and whne you change the password this time, make sure you carefully enter it and write it down.

Let us know which one is your situation and then if the above steps helped you fix it. Good luck

---

### Post by Josh1 on 2007-05-09
Sorry, I didn't explain myself enough.

What I meant is that when I was on my server (wired) I changed the Wireless password for the router. I then went back to my laptop, and turned it on. I found that I could not connect to the wireless network because the password was changed for the wireless.

So on my laptop in NetworkManager, I am looking for a way to change the password I had put in earlier or an alternative I could use.

Cheers and sorry for the confusion.

---

### Post by dannyboy79 on 2007-05-09
> **Josh1 said:**
> Sorry, I didn't explain myself enough.

What I meant is that when I was on my server (wired) I changed the Wireless password for the router. I then went back to my laptop, and turned it on. I found that I could not connect to the wireless network because the password was changed for the wireless.

So on my laptop in NetworkManager, I am looking for a way to change the password I had put in earlier or an alternative I could use.

Cheers and sorry for the confusion.


what authenitification are you using for your wireless? WPA or WEP or what?

---

### Post by cwmaxson on 2007-05-09
I use WICD because network manager gave me too much guff:
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by Josh1 on 2007-05-09
> **dannyboy79 said:**
> what authenitification are you using for your wireless? WPA or WEP or what?

WPA-PSK

---

### Post by dannyboy79 on 2007-05-09
you can simply edit your interfaces file located within /etc/network/ 

here is a good guide for that. [http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+wireless](http://ubuntuforums.org/showthread.php?t=202834&highlight=wpa+wireless)

OR

if you want a gui than follow the above suggestion to use a different wireless management program.

---

### Post by chocolatedude91 on 2007-05-09
Is there a good guide for WEP?  Thanks.

---

