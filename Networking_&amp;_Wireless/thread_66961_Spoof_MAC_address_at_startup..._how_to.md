---
title: "Spoof MAC address at startup... how to?"
date: 2005-09-18
forum: Networking &amp; Wireless
---

### Post by mulletman13 on 2005-09-18
Hey all,

I read a decent article that went through the steps, but it was specifically for redhat, and Ubuntu doesnt have a /etc/sysxxx folder, which doesnt contain the ifcfg-eth0 file/folder. 

Is there any way I can run a script that will spoof the MAC addy during startup before it searches and acquires an IP?  

SOrry I'm a noob to linux and have no idea what to do right now.  The reason I'm trying to spoof via ifconfig is to get around a MAC filter (school only allows one MAC addy per user)

I'd like to see if this could be automated because I hate changing everything, disabling and re-enabling the adapter.

Thanks in advance,

Ken

---

### Post by heimo on 2005-09-18
[QUOTE=mulletman13](school only allows one MAC addy per user)[/QUOTE]

And do I understand correctly that you want to add multiple computers with same MAC address? That's... not a very good idea. It'll mess up networking on these computers and not too hard to notice. Don't do it. Your school has some reason not to allow more computers and most probably reason is resources.

If you want network connection for multilple computers, maybe you could share the network connection through one machine (if that's allowed) - this way only one computer is facing outside world and you don't need questionable hacks.

Please make yourself a favour and consult your schools it guys beforehand. Sometimes answer is no - and you should accept it. I really, really feel sympathy for everyone working for school it deparment.

EDIT: That being said: You can find answer to "how to change mac address" on these forums. Correct file to change is /etc/network/interfaces Please consider what I said and don't do anything foolish. If you don't know what you're doing, you should not.

---

### Post by mulletman13 on 2005-09-19
Hey there,

Thanks a lot for telling me where the resource is... and here is my explanation of what I'm doing.

I'm not using all of these computers at the same time to go online -- that would result in two different IP's with the same MAC address -- not a real smart idea.  I'm using the same exact connection that I use with my iMac that I am with the Thinkpad (the same cord that is), so in essence I'm only using one computer, and not using anymore resources than allowed.

The main resason they do this is (like some ISPs) to limit the bandwidth.  

I've been doing this with a Windows laptop and Mac desktop all of last year (when I'm not using one I use the other), and it has worked perfectly, and I don't see a problem with it.

As for feeling bad for our IT guys -- they aren't all that capable of doing too much.... for example they believed my PowerBook last year had a virus- and proceeded to use Virex scanner 23 times before deducing that they were wrong, although never admitting to it.

All they do is run Spybot, Ad Aware, Norton... and if all those fails they format.

Hell, the school doesnt even officially support linux, so I mean I'm already doing something they don't 'allow'.  But that's just how it is here (UWMilwaukee), it may be different at other schools. 

Sorry if you see something wrong with what I'm doing, but thanks a lot for your information.

---

### Post by heimo on 2005-09-19
Hi! Great to hear that my first impression was wrong and you seem to know what you're doing. :) If I recall correctly, man interfaces will give you all advice you need, it was something quite simple - adding hwaddress [mac-address-here] line or similar. And no, I don't think it's wrong - what difference would it make to just physically change network adapter? :)

Sorry if my answer was too much nursing - but you do understand, I believe - as you know, not all of us know what we're doing (and some of them work for it departments) and some caution is needed when giving advice that might cause trouble.

---

### Post by mulletman13 on 2005-09-19
Hrmm... I've searched the forum, and all I've seen were the traditional ways of changing the mac...

```
ifconfig eth0 down
ifconfig eth0 hw ether (can't use x's to be mistaken for smileys)
ifconfig eth0 up
``` 

... however there are no places on where to set this in the /etc/network/interfaces file...  this is what mine looks like 

```
mapping hotplug
script grep
map eth0

#The primary network interface
auto eth0
iface eth0 inet dhcp
``` 

Now I added a "hdaddr=(can't use x's to be mistaken for smileys)" (or whatever it is) to the end of the file -- and upon restarting that did absolutely nothing.

A simple fix could be to write a script that simply runs

```
ifconfig eth0 down
ifconfig eth0 hw ether (can't use x's to be mistaken for smileys)
ifconfig eth0 up
``` 

However, I would have no idea how to go upon doing this, nor where to put it in the filetree.

As for googling I've found mixed results, but nothing on how to do this :(

Thanks in advance

---

### Post by heimo on 2005-09-19
[QUOTE=mulletman13]
```
mapping hotplug
script grep
map eth0

#The primary network interface
auto eth0
iface eth0 inet dhcp
``` 

Now I added a "hdaddr=(can't use x's to be mistaken for smileys)" (or whatever it is) to the end of the file -- and upon restarting that did absolutely nothing.
[/QUOTE]
Syntax is like this:
hwaddress ether 01:02:03:04:05:06

---

### Post by TimDuncan on 2008-07-05
Unfortunately I've tried this also and it just plain won't work in hardy heron with my interface wlan0.
The only way i can change my mac address is 
ifconfig wlan0 down
ifconfig wlan0 hw ether 00:00:00:00:00
ifconfig wlan0 up

Which changes it, however, once changed my network manager won't recognise my wifi card and i cannot connect to ANY network, even my unfiltered home network.....

---

