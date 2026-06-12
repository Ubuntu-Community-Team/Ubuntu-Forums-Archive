---
title: "Thomson tg585 drops connection and ask again for authentification every few seconds"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by buntavid on 2010-05-04
I am absolutely new to Linux ... just know it exists ... installed Ubuntu10.4 LTS on my Windows XP Pro with dual-boot.
 
My Thomson TG585 won't connect to any machine (whatever the Operating System running it) unless I install the CD that came with the router (or is it modem ?!). Its working fine in Widows environment. The CD says it spports only Windows or Mac Operating Systems, so I couldn't run it on Ubuntu. I couldn't even see setup.exe in the file manager. Ubuntu sees all available networks, connects to the one I'm using to surf the Internet, but drops and asks me for the password again even tough I'm certain it's correct. What does this CD do anyway ?
 
Thank You for the quick reply.

p.s: I can't access that 192.225.. that connects you to the router using the default user me and password ... i think the guy at the Intenet Service Provider put his own passwords ... why would he do that ?

---

### Post by madjr on 2010-05-04
found this maybe it could help

[http://signsofsuccess.co.nz/wordpress/?p=68](http://signsofsuccess.co.nz/wordpress/?p=68)


[http://community.plus.net/forum/index.php/topic,76267.msg611889.html#msg611889](http://community.plus.net/forum/index.php/topic,76267.msg611889.html#msg611889)

---

### Post by buntavid on 2010-05-04
thanx ... but I've done my homework and read both sites before posting my problem here. Neither gives steps and a lot of knowledge is implied.
 
thanx anyway
 
keep the suggestions coming please

---

### Post by madjr on 2010-05-04
> **buntavid said:**
> thanx ... but I've done my homework and read both sites before posting my problem here. Neither gives steps and a lot of knowledge is implied.
 
thanx anyway
 
keep the suggestions coming please

ok cool

well we want to make sure is not ubuntu 10.04, so do have any other version you can try? either older or different (like kubuntu) or another linux distro: opensuse or pclinuxOS

no need to install, should work from the live-cd/dvd

then if the problem is with 10.04 we can open a bug report.

this is probably the easiest way without having to hack into the system.

i always keep older versions lying around just in case :)

---

### Post by buntavid on 2010-05-04
I'm certain the problem isn't from ubuntu ... here's why:
My father and I each own a laptop computer ... although his runs exclusively on Windows Vista: it also wouldn't stay connected to the router for long before requiring authentification again, until the CD was installed and then it worked like a charm. Same thing with my own computer.
 
Anyway, the installation wizard would ask us to enter stuff like "SERIAL NUMBER", "SSID", "WEP (hex)", and "WPA PSK" (I don't know the mening of any of this jargon by the way). The same thing happened with a new Windows XP netbook (no optical drive) we bought. I am sure if I find a way to copy the CD image to a USB key I would be able to install it on the new netbook.
However, as I said in the first post, the CD doesn't run in Ubuntu. Is there a way I could enter these values manually?

---

### Post by lisati on 2010-05-04
> **buntavid said:**
> I'm certain the problem isn't from ubuntu ... here's why:
My father and I each own a laptop computer ... although his runs exclusively on Windows Vista: it also wouldn't stay connected to the router for long before requiring authentification again, until the CD was installed and then it worked like a charm. Same thing with my own computer.
 
Anyway, the installation wizard would ask us to enter stuff like "SERIAL NUMBER", "SSID", "WEP (hex)", and "WPA PSK" (I don't know the mening of any of this jargon by the way). The same thing happened with a new Windows XP netbook (no optical drive) we bought. I am sure if I find a way to copy the CD image to a USB key I would be able to install it on the new netbook.
However, as I said in the first post, the CD doesn't run in Ubuntu. Is there a way I could enter these values manually?

I have a TG585v7 provided by my ISP which came with a customised installation CD. 

I'd recommend setting yours up with a wired connection.

I'm not sure what the serial number you are being asked for refers to, unless it's referring to the serial number printed on the bottom.

The "SSID" is the name you want for your home WiFi network.
"WEP" and "WPA PSK" refer to different kinds of security on your WiFi network.

You might need to tell your modem/router to scan for wireless devices while you are trying to connect via wireless, so your computers can be "registered" on it. One way is by pressing the button on the front of the device.

---

### Post by buntavid on 2010-05-04
You're absolutely right about the serial number, it's on the bottom ... and now that you mention it, I think that whole thing is a customized package too (I wasn't able to get into the router through the default "Administrator" and blank password thing with the 192.1.255 stuff all these forums are talking about)
 
Also, I haven't used the cable for so long, the copper-made pins have rusted ... :lol: ... plus it defeats the purpose of paying the premium price of a wireless modem right ?!
 
And apparently, according to other posts I have read, the button on the front will only work in v7 (or is it v8 ? I can't remember). And suppose it does work, won't it also register my neighbours computers ?
 
Can you give me specific steps please, like
1 sign into ubuntu
2 open this and that
 
Thank you for indulging me

p.s: I found it ... the password I was entering at the authentification window was actually the one for accessing the router with the administrator thing ... anyway, all is fine now ... as a matter of fact i'm writing this from the ubuntu OS ... i'm loving it .... count me as a convert
thank you all for your (wasted) time ... :P

---

### Post by madjr on 2010-05-04
> **buntavid said:**
> You're absolutely right about the serial number, it's on the bottom ... and now that you mention it, I think that whole thing is a customized package too (I wasn't able to get into the router through the default "Administrator" and blank password thing with the 192.1.255 stuff all these forums are talking about)
 
Also, I haven't used the cable for so long, the copper-made pins have rusted ... :lol: ... plus it defeats the purpose of paying the premium price of a wireless modem right ?!
 
And apparently, according to other posts I have read, the button on the front will only work in v7 (or is it v8 ? I can't remember). And suppose it does work, won't it also register my neighbours computers ?
 
Can you give me specific steps please, like
1 sign into ubuntu
2 open this and that
 
Thank you for indulging me

p.s: I found it ... the password I was entering at the authentification window was actually the one for accessing the router with the administrator thing ... anyway, all is fine now ... as a matter of fact i'm writing this from the ubuntu OS ... i'm loving it .... count me as a convert
thank you all for your (wasted) time ... :P

glad to help

our time wasn't wasted at all, this is our mission to help people.

the linux community is known for this :)

now that you were able to solve the issue, i think this next guide will help you in your new journey :o

[http://www.omgubuntu.co.uk/2010/05/danny-piccirillos-rockin-post-install.html](http://www.omgubuntu.co.uk/2010/05/danny-piccirillos-rockin-post-install.html)

---

