---
title: "Remote Control"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Zintha on 2010-05-10
> Running:
Desktop with Lucid/XP duel boot
Laptop with Lucid
Broadband (if applicable)


I have Ubuntu on my PC and my Laptop.

I will be going out with my laptop to a friends and I would love to be able to control my PC from there.

How do I do this? I honestly have no idea, a bunch of online how-tos didn't help/outdated or I run into issues.

Can someone point out a how-to that might be relevant or explain it to me?

---

### Post by bornagainlinux on 2010-05-10
Hi Zintha,

If you have any outside access to your computer over the internet, it is going to require you to setup your router to allow access. Basically you will need to know a few pieces of information about your setup.

1. IP address of your computer on your local network (there may be many ways to find this out. I use the NetworkManager applet on my panel and right-click on it to get "Connection Information")
2. Your IP address of your internet connection (you can find this out by going to a site like ipchicken.com or whatismyipaddress.com)
3. Port number that you use for the remote viewer application. For VNC connections the default port is 5900. For anything else (does anyone still use PCAnywhere?) you will have to find out.

After finding that little bit of information, then you need to setup your router to forward the Port number (ie 5900 for VNC) to the IP address of your computer from your local network.

Then to connect, you will use the IP address of your internet connection as the location to connect to and it should give you access. 

These are just general instructions. If you are totally lost at this point, I can help you out a step at a time.

Don

---

### Post by narendraD on 2010-05-10
> **Zintha said:**
> I have Ubuntu on my PC and my Laptop.

I will be going out with my laptop to a friends and I would love to be able to control my PC from there.

How do I do this? I honestly have no idea, a bunch of online how-tos didn't help/outdated or I run into issues.

Can someone point out a how-to that might be relevant or explain it to me?


Use Remote Desktop for this. Its already installed by default but needs to be activated. Its in System -->Preferences --> Remote Desktop.  You will need to know your IP and configutr the access parameters like password. Then its easy. Of course you need to be carefull whom you share your Remote desktop info with. There is no difference between someone sitting in front of your comp and someone sitting a 1000 miles away with remote desktop of your screen. You can basically do anything you want. So...

---

### Post by Zintha on 2010-05-11
> **bornagainlinux said:**
> Hi Zintha,

If you have any outside access to your computer over the internet, it is going to require you to setup your router to allow access. Basically you will need to know a few pieces of information about your setup.

1. IP address of your computer on your local network (there may be many ways to find this out. I use the NetworkManager applet on my panel and right-click on it to get "Connection Information")
2. Your IP address of your internet connection (you can find this out by going to a site like ipchicken.com or whatismyipaddress.com)
3. Port number that you use for the remote viewer application. For VNC connections the default port is 5900. For anything else (does anyone still use PCAnywhere?) you will have to find out.

After finding that little bit of information, then you need to setup your router to forward the Port number (ie 5900 for VNC) to the IP address of your computer from your local network.

Then to connect, you will use the IP address of your internet connection as the location to connect to and it should give you access. 

These are just general instructions. If you are totally lost at this point, I can help you out a step at a time.

Don
This helped perfectly!
Now its working, can remote control it. One problem though!

I get it connected, I see the screen, I can move the mouse... but then when I move a window or open anything or click on something.. it -works-... but I can't see it work from the laptop?

Like whatever it sees when its first connected is what its stuck on.

---

### Post by Zalbor on 2010-05-11
The default "Remote desktop" that comes with Ubuntu is thought by others to be very insecure, so maybe you should look into using something else (I don't have suggestions personally).

As for the "still image" problem, that happens if compiz (desktop effects) is enabled. It has to be disabled for remote desktop to work correctly.

---

### Post by Zintha on 2010-05-11
> **Zalbor said:**
> The default "Remote desktop" that comes with Ubuntu is thought by others to be very insecure, so maybe you should look into using something else (I don't have suggestions personally).

As for the "still image" problem, that happens if compiz (desktop effects) is enabled. It has to be disabled for remote desktop to work correctly.
Thank you for the recommendation.

This may seem rookie to ask but how do I disable compiz?

---

### Post by Zalbor on 2010-05-11
I don't remember fully well, but I think it was System>Preferences>Appearance>Desktop Effects>None.

A "quick" way, if you're ok with using commands, would be to press Alt+F2 to open the run dialog and use
```
metacity --replace
```
to disable the effects and
```
compiz --replace
```
to enable them.

---

### Post by Zintha on 2010-05-11
> **Zalbor said:**
> I don't remember fully well, but I think it was System>Preferences>Appearance>Desktop Effects>None.

A "quick" way, if you're ok with using commands, would be to press Alt+F2 to open the run dialog and use
```
metacity --replace
```to disable the effects and
```
compiz --replace
```to enable them.
Thank you!
Will be marking this topic as solved.

You guys rock.

---

