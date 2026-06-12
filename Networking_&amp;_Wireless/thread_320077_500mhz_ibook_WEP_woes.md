---
title: "500mhz ibook WEP woes"
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by djlyx on 2006-12-16
Greetings everyone,

I am new to ubuntu and networking.  I am trying to get my airport (not extreme) working on my home network.  After many hours or searching, and trouble shooting through trial and error I am still unable to connect to the internet. ](*,) 

I noticed most of the messages/posts in this forum refer to the airport extreme card. and the few that refer to the original airport are beyond my comprehension.

I am running edgy eft on an apple 500mhz g3 ibook ppc.

My network is 128-WEP encrypted.

Can anyone help me configure the airport or point me to the right direction.

Thanks a mill

---

### Post by x64Jimbo on 2006-12-16
Is anything working yet? You have to give us a starting place. Is the interface recognized? If not, what have you tried? If so, can you connect to open APs? What network management tools have you tried? All this info is essential to helping you. Otherwise we're just spinning our wheels.

---

### Post by djlyx on 2006-12-16
I am using an app called "Wifi Radar" and it appears to be detecting my network.

---

### Post by x64Jimbo on 2006-12-16
ok so that means that your interface is detected and that it is working
Now you need to get connected. First, before you use tools to get connected, have you tried configuring the interface through the console? The tools are just fancy front ends for basic shell commands that you should know how to use. 
Read the man files on the following commands:
ifconfig
iwconfig
dhclient

If this works, then try getting the interface configured in your interface manager applet (in your system tray)

---

### Post by djlyx on 2006-12-16
Thank you for the reply.

I'm confused, what do I do with the information I get from 

ifconfig

and
 
iwconfig ?

what is the purpose of those three commands? 
ifconfig
iwconfig
dhclient

I dont see any applet for interface manager in my system tray.

---

### Post by Old Pink on 2006-12-16
[http://ubuntuforums.org/showthread.php?t=299462](http://ubuntuforums.org/showthread.php?t=299462)

^^ Ultimate connection utility. Wouldn't be surprised if that fixed it.

---

### Post by djlyx on 2006-12-16
I installed the program and it detects my network, however i'm still not able to join. :-(

---

### Post by djlyx on 2006-12-16
Am I supposed to make any modifications to these fields?

Please view the attached images.

---

### Post by djlyx on 2006-12-16
Well, for now I've gotta install xubuntu on this ibook, its so slow with regular ubuntu.

I'll let you know what's next

---

### Post by djlyx on 2006-12-17
still have the same problem with xubuntu :-(

---

### Post by djlyx on 2006-12-17
I've decided to switch back to OS X, i gotta have my wireless.

---

### Post by maxamillion on 2006-12-17
I actually find it surprising that you had issues with AirPort, the support for that is built in and should work "out of the box" I run Xubuntu on my iBookG4 w/ AirPortExtreme and as of early dapper testing releases I have had success with it.

---

### Post by x64Jimbo on 2006-12-17
Why so fast? We're still trying to help you. 
Yes, those fields that you filled out in the pictures you posted are the correct place to input your network key. You are putting in the hexadecimal value, correct (not your passphrase, but its hex translation)?
Don't give up yet; have patience. Just because it takes a while to reply doesn't mean that we don't want to help. Just means we're normal people like you and have things to do during the day. :)

---

### Post by djlyx on 2006-12-18
I still have xubuntu however, I am dual booting with OS X.  I haven't given up :-)

Like my signature says, I always got ubuntu on my mind. 

In any case. I did put the hex translation (long alpha numeric password) however I didn&#8217;t display it on the screen shot for obvious reasons.  I'm just wondering if I need to set it as static IP or DHCP?  I don't really know what to do.  
I know I can connect to my neighbor&#8217;s wireless internet, they don't have encryption hehe.  But that&#8217;s wrong and I'd rather use my own signal, after all, I'm paying for it.
If it all helps, I have a linksys router.

Thanks for your replies btw.  Keep'em coming!

---

### Post by x64Jimbo on 2006-12-18
OK so your card obviously works. time to set it up with encryption. Definitely put it in DHCP mode, since that will be the best way to ensure that you connect properly to the AP. 
Those commands I gave you are network management commands. they will help you set up the interface. 
sudo ifconfig <interface> down (brings down the interface so we can tweak it)
sudo iwconfig <interface> essid <ssid> key <key in hex> (sets the SSID and encryption key)
sudo ifconfig <interface> up (brings it back up so we can use it)
sudo dhclient <interface> (tells it to get an IP from your DHCP server/router)

Try those commands in that order and see if it helps.

---

