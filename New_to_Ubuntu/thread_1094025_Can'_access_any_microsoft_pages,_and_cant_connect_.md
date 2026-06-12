---
title: "Can' access any microsoft pages, and cant connect to xboxlive since yesterday"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Gojippo on 2009-03-12
Hi all, I'm quite new to all this stuff so I don't know if I'm posting in the right place.

Since yesterday, I cant' seem to access microsoft pages, particularli the main xbox site. I also can't connect on the xbox live. When I try the network test on my xbox, I get a message like I don't have enough MTU or whatever. I contacted the xbox support center, and my provider and both don't seem to know anything...

Thing is, everything was working fine until yesterday. Any idea, anyone ?
Does microsoft hate me cause I started to use Libuntu ? :)

---

### Post by Temposs on 2009-03-12
I can access [www.microsoft.com](www.microsoft.com) and [www.xbox.com](www.xbox.com) just fine as of now. Are you still having the issue? They could've just been having issues with their xbox servers.

---

### Post by Gojippo on 2009-03-12
Nope, I still can't :(
I really don't know why it's happening...

---

### Post by handydan918 on 2009-03-12
Paste this into your address bar, and let us know what happens...

```
65.55.42.140
```

---

### Post by Gojippo on 2009-03-12
The same thing than when I try to go on a microsoft page : it times out. :(

---

### Post by Miljet on 2009-03-12
Have you tried resetting your router? I had a similar problem last week, could access some sites, but not others. I unplugged the router for a couple of minutes, then plugged it back in, let it go through setup, and everything worked again.

---

### Post by Gojippo on 2009-03-12
By router, do you mean modem ? If yes, I tried some times to unplug it then to reconnect it, but with no success. I always reconnected it after a few seconds though, so I'll try to disconnect it for a longer time.
Thanks

---

### Post by Gojippo on 2009-03-12
I tried to unplug my modem, but still no success...
I don't use a router by the way, I connect my xbox directly to my modem.

---

### Post by DGortze380 on 2009-03-12
Are you running Ubuntu? On anything??

Sounds like you might have better luck in an XBox forum.

MTU - simply stated, the default size at which your network device fragments packets. XBox Live probably requires that you set you MTU below or above a certain threshold so they can maintain maximum throughput. 

This is simple to fix in most operating systems, or on most network devices. But we need some more information.

What systems do you have, what operating systems are they running?

You say you are directly connected to modem ... does this "modem" allow for multiple devices to be connected at the same time? (ie. your XBox and your PC)?

---

### Post by Gojippo on 2009-03-12
Hi,

I am running Ubuntu on my computer. I tried to change the MTU value with what microsoft recommends, but it does'nt help. Strange thing is that the error message I get says that I am connected with a route, and that I should try to connect directly with my modem, what am I doing...


> **DGortze380 said:**
> 
This is simple to fix in most operating systems, or on most network devices. But we need some more information.

What systems do you have, what operating systems are they running?

You say you are directly connected to modem ... does this "modem" allow for multiple devices to be connected at the same time? (ie. your XBox and your PC)?

I have a computer running ubuntu only, and my xbox running the classic OS it has. I am connected to an optic fiber internet connection in Japan, and the "modem" or device I have converts optic data in normal computer data (or so i read). I can only connect one device to it at the same time, so my xbox OR my computer.

The message error I get on my xbox says that I need at least 1374 MTU, with more than 1472 recommended.

Maybe it would be better to test why I can not connect to microsoft sites, like microsoft.com or xbox.com ?

---

### Post by DGortze380 on 2009-03-12
> **Gojippo said:**
> Hi,

I am running Ubuntu on my computer. I tried to change the MTU value with what microsoft recommends, but it does'nt help. Strange thing is that the error message I get says that I am connected with a route, and that I should try to connect directly with my modem, what am I doing...




I have a computer running ubuntu only, and my xbox running the classic OS it has. I am connected to an optic fiber internet connection in Japan, and the "modem" or device I have converts optic data in normal computer data (or so i read). I can only connect one device to it at the same time, so my xbox OR my computer.

The message error I get on my xbox says that I need at least 1374 MTU, with more than 1472 recommended.

Maybe it would be better to test why I can not connect to microsoft sites, like microsoft.com or xbox.com ?

On your ubuntu computer, try

```
 sudo ifconfig eth0 mtu 1500 
```

1500 is currently the typical mtu.

then try to connect to your sites.

---

### Post by Gojippo on 2009-03-13
Hi, tried it this morning but to no avail... I'll try my connection again tonight after work. If someone else has an idea, you're welcome to share it :)

---

### Post by Gojippo on 2009-03-13
Ok, I called microsoft, my provider and the company responsible for the line installation and nobody knows a freaking thing.
Everyone says everything is fine, but it is not.
Man, what should I do :confused:

---

### Post by Gojippo on 2009-03-13
Ok guys, good news : I managed to sign up on my xboxlive account. I changed some stuff to my DNS access. I cahnged it from Automatic to Manual, and changed the secondary DNS address by adding one to the last part of the IP address. And it worked. Now I can't access microsoft sites, no big deal anyway, but how do you change your DNS settings on ubuntu ? Thanks

---

### Post by Grizz Granlien on 2010-12-25
I know why you can't access they [www.xbox.com](www.xbox.com) site is because it needs silverlight 3 to view it Ubuntu can't view a lot of web pages because silverlight is for Windows and MAC OS that sucks just like you can't watch netflix with out silverlight as well.. Ubuntu needs to work on getting it,,,,

I think Microsoft should not have made silverlight ....


It should be law that all web pages made have to have a standard and if teh standard changes all changes eg. silverlight well then silverlight should be open source code and made available to all OS's like OS2/warp Linux all of them and free dos, DR DOS, RS dos.. A Dos , BEoS and every thing else before it is aloud to be used to make web pages...

---

