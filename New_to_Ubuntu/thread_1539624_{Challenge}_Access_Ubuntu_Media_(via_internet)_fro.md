---
title: "{Challenge} Access Ubuntu Media (via internet) from Win7 Laptop"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by tk112190 on 2010-07-26
Hey everybody,

First off let me explain my situation. I have a desktop media server (Ubuntu) and it's streaming movies and music to my ps3 through the network (Using program called PS3 Media server).

Now I have enabled access from my Ubuntu-box to let the Music/Video folder to be shared. (via right-clicking and hitting "Sharing Options", it even lets me add to it from my Win7 laptop!! ). 

So as you can see, I have my entire network, for the most part, streamlined. But one thing is lacking... and I was wondering if anyone who is familiar with any of this software (Windows Media Player particularly) or anything on the Linux computer, that will enable me to access media, while roaming the city with my win7 laptop (internet connected)?

If my desktop was Win7 too, this wouldn't be a problem. As Windows Media Player has an option to do that [(via Linked Online ID).]("http://windows.microsoft.com/en-US/windows7/Stream-your-media-over-the-Internet-using-Windows-Media-Player")

I would like to be able to stream music from ubuntu on my laptop while at work or on the go. This would be amazing!

Judging by how Linux > Windows... yet 2 Windows computers can do this, I'm sure the power of Linux can overcome any compatibility issues of the two different operating systems. Please use your expertise and let me know if there is anything I can do to assist you guys.

Thank you very much, and I look forward to hearing from you. 

Computers
1. Ubuntu Media Server [desktop], [COLOR="red"]holding all the files (music/videos)[/COLOR]
2. Win7 [laptop], [COLOR="Red"]wants to access desktop media via internet[/COLOR], [COLOR="Blue"]*preferably from Windows Media Player IF POSSIBLE.*[/COLOR]

**_*all methods for execution and solving this challenge are welcomed very much._**

---

### Post by friv_livs on 2010-07-26
Would a samba share set up between the two, then tell your windows media player to look at the ubu server directory work?

I know no details of how to do this, but someone else should.

---

### Post by Linux&amp;Gsus on 2010-07-27
Well, SAMBA, yes, but when you are on the go the laptop wont find he computer at home by its name or IP address.
So, IMHO you'll need a VPN first and then SAMBA could work with that. I don't know what that Windows Online ID thing is, but I assume it basically is similar to a VPN and is most likely using a MS Server for authentication and linking things together.

Setting up a VPN yourself might be a bit more work then the Microsoft way of pushing some buttons (and probably registering with them somewhere online). But once it's setup it can do more then just accessing music through MS Media Player. Like accessing any kind of file you made accessible via SAMBA, FTP, what ever you do...

Don't know if that is the best way to do it but it's what comes to my mind as first option.

To get started have a look here:
[http://openvpn.net]("http://openvpn.net")
[Install Instructions]("http://openvpn.net/index.php/open-source/documentation/howto.html")

In this howto you'll probably come across something like this or similar:
[http://www.dyndns.com]("http://www.dyndns.com") 
That is make your home network reachable from outside, even though the IP address of your modem is changing.


Hope that helps.
L&G

---

### Post by tk112190 on 2010-07-27
> **Linux&Gsus said:**
> Well, SAMBA, yes, but when you are on the go the laptop wont find he computer at home by its name or IP address.
So, IMHO you'll need a VPN first and then SAMBA could work with that. I don't know what that Windows Online ID thing is, but I assume it basically is similar to a VPN and is most likely using a MS Server for authentication and linking things together.

Setting up a VPN yourself might be a bit more work then the Microsoft way of pushing some buttons (and probably registering with them somewhere online). But once it's setup it can do more then just accessing music through MS Media Player. Like accessing any kind of file you made accessible via SAMBA, FTP, what ever you do...

Don't know if that is the best way to do it but it's what comes to my mind as first option.

To get started have a look here:
[http://openvpn.net]("http://openvpn.net")
[Install Instructions]("http://openvpn.net/index.php/open-source/documentation/howto.html")

In this howto you'll probably come across something like this or similar:
[http://www.dyndns.com]("http://www.dyndns.com") 
That is make your home network reachable from outside, even though the IP address of your modem is changing.


Hope that helps.
L&G


Wonderful! Thank you very much for your help.. I'll look into this. I wish there were an easier way, but things always get complicated when you use both Windows+Linux. 

Next time I'll take the full dive into the world of Ubuntu...

Anyway, do I install the VPN on the Linux media server, or the on-the-go laptop? Not too familiar with VPN.

Thanks again

---

### Post by Linux&amp;Gsus on 2010-07-27
Well, first off all, this has nothing to do with a mixed OS environment. I'm all Linux (except the Windows that I use to check if my websites work with Windows) and I at least I haven't found an easier way to connect to my home server from outside.
So, even if you are all Linux this might still be the thing you have to do. However, as I said, this is only the way that I know off. There might be other option for just accessing/streaming music. But since I don't do that I am not familiar with any possibilities.


So, the VPN Server needs to be installed on your Linux Media Box. Then you use a VPN Client software on your to-go-laptop. Windows might have something built in by default, I don't know, or you need to install something small to make that happen. The OpenVPN site should tell you everything you need to know about it.

I would suggest that you read through the install instructions first and try to understand what is happening / what you need to do. Yes, you will need to get your hands dirty on the command line, but it's really no big deal, nothing too complicated. Even I managed to do that. That kinda means something... :D

While you read through you also should come across all the needed software to make the connection, e.b. what you need on the Windows side of things.
You can look into all those things and then you can do it.


If you have questions please feel free to ask. I'll try to help as much as I can.



Cheers,
L&G

PS: Yes, it seems to be more complicated to setup the the Windows things. But as I said earlier, this set up is far more flexible.

---

