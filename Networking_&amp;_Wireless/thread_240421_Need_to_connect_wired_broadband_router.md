---
title: "Need to connect wired broadband router"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by singersdd on 2006-08-20
I just installed Ubuntu on our other computer.  We have cable internet and a wired broadband router to connect the two computers to the cable modem.

What do I tell Ubuntu to look for to find the router?

Thanks!

Susan

---

### Post by chinaski on 2006-08-20
which router it is?

usually you open firefox and type something like:

192.168.1.1 or 192.168.0.1 in the url address

the exact address should be in the rotuer manual

---

### Post by singersdd on 2006-08-20
Okay, thanks...

now to figure out where hubby hid the manual...

---

### Post by singersdd on 2006-08-20
Okay, that didn't work.  I have the IP address, but I didn't see a place to type it in the Firefox browser.  I only get an info page on Ubuntu when I open Firefox.  Do I need to change a setting in system tools or connect to network or server or something?
thanks!

---

### Post by Fass on 2006-08-20
You should type it in the normal address bar. Where the "www.address.com" goes. If you don't see it... hmm... go into "View -> Toolbars -> Navigation toolbar" in the Firefox window.

Could you do me a favour? Could you open a terminal (it's under "Accessories" in the applications menu) and write ```
ifconfig
``` in it, press enter and then just paste the output it gave you here. I just want to see if your computer is getting an IP address from your router.

---

### Post by singersdd on 2006-08-21
I typed that in and I got nothing.  It just has a command line (I think that's what it's called) that says susan@ubuntususan:~$

I probably did something wrong when I installed it, knowing my luck...

---

### Post by singersdd on 2006-08-21
I typed that in and I got nothing.  It just has a command line (I think that's what it's called) that says susan@ubuntususan:~$

I probably did something wrong when I installed it, knowing my luck...

I tried typing the ip address into the address box on firefox and got nothing there, either.  the router can see my computer, but Ubuntu can't see the router.

---

### Post by Fass on 2006-08-21
> **singersdd said:**
> I typed that in and I got nothing.  It just has a command line (I think that's what it's called) that says susan@ubuntususan:~$

Something is very wrong if when you enter "ifconfig" at the command line and press enter it gives you nothing in return... it really says nothing about "lo" or "eth0" or something like that?

---

### Post by singersdd on 2006-08-21
Nope. Nothing.

---

### Post by Fass on 2006-08-21
> **singersdd said:**
> Nope. Nothing.

What does ```
cat /etc/network/interfaces
``` say?

---

### Post by singersdd on 2006-08-21
bash:cat/etc/network/interfaces: no such file or directory

I have a feeling I did something wrong when I installed it... should it have been installed as a network station, possibly?

---

### Post by Fass on 2006-08-21
Please, re-enter the command, making sure there is a space between cat and /etc/network/interfaces. You seem to have omitted it.

```
cat /etc/network/interfaces
```

---

### Post by singersdd on 2006-08-21
Oops.  It came back with # Used by ifup(8 ) and ifdown(8 ).  See interfaces(5) manpage or # /usc/share/doc/ifupdown/examples for more information

(I added spaces after the 8s so I wouldn't get smilies...)

---

### Post by Fass on 2006-08-21
Well, it seems like when you installed Ubuntu the network was not set up at all. We have two options here. You and I can spend some time trying to set up the network, or you can reinstall Ubuntu. The latter is the easiest and the quickest, I must admit, for us both. :\

---

### Post by singersdd on 2006-08-21
*sigh*

That's what I figured.  

So I need to install it as a station on a network, right?
And use the simple, easy installation and not try to be an expert this time, right?

---

### Post by Fass on 2006-08-21
I would recommend that you use the easy method, yes, as that one will be more forgiving and automatise more things for you, and that if you get the choice to choose that it be a station on a network. 

By the way, did you install with the graphical method or the text-based method? The former is the one that has "pretty" windows and the latter has "ugly" blue "fake" windows and a bunch of text. If you did the text-based installation, I would recommend the graphical one (it's the "Desktop CD" in the downloads) as it is much simpler and easier to get right.

---

### Post by singersdd on 2006-08-21
I might have done text-based the first time, but I'll make sure to install it easy, as a network station, graphics this time.

I'm sure this will be worth it when I get it up and running.

---

