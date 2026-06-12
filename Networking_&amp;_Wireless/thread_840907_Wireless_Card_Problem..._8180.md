---
title: "Wireless Card Problem... 8180"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by outofexile on 2008-06-25
Hey guys, I'm fairly new to all this Linux stuff and well, i've having a bit of trouble.

I've did a lot of research into Ubuntu before deciding to install it on my old laptop; Windows was getting slow and it was time for a reformat, but I fancied something different.

So here I am, I've install Ubuntu (v6.10... it was the only version I could find with a fast enough download to make it worth-while (i'd  have installed XP again otherwise :P)). And i've come across a problem.

One of the first things I looked for, even before installing was - because of wireless card problems I had heard of before - wireless card drivers, and some to see if anyone had any problems with my wireless card's chipset. I came across a couple of things:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=(ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=(ndiswrapper")
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8180L")
[http://ubuntuforums.org/showthread.php?t=779574]("http://ubuntuforums.org/showthread.php?t=779574")

So I thought I would be ready to reformat the computer, do a fresh install of linux and get my wireless up and running in no time. So here I am now, at 02:35am and I still haven't got the wireless set up!

So back to what I've done... On the 'Realtek' website, it gives links to linux drivers, but they seemed dodgy to me due the the title having 'fedora' in them, and well I didn't fancy having a go at compiling them like my friend told me I would have to do. So i've got the Ndiswrapper route; I've downloaded the package, along with the gtk for it and installed the drivers... guess what? It didn't work.

I then decided it would be best to go back to one of those threads and consult the 'terminal' method to see if that would work any better... I bet you can guess what I'm going to say next. It didn't work.

What I find weird is, when installing via the GTK, I the driver will install and I can get it to connect to the network (or so I am led to believe), but not the internet like I would expect.

But yeah, some other information that you might find helpful, is the fact it gives me this message when installing (using 'ndiswrapper -i ~/Desktop/NET8180.INF':

```
Installing net8180

couldn't copy /root/Desktop/NET8180.INF at /usr/sbin/ndiswrapper line 135.
```

This message when checking if the driver has been installed (using 'ndiswrapper -l')

```
Installed ndis drivers:
net8180 invalid driver!
```

I would guess by know that you realise that my card's chipset is 'RTL8180'... so yeah, does anyone think they could help me out?

---

### Post by outofexile on 2008-06-25
I am going to kick myself so hard now. All I had to do was click the tick box next the wireless card in the networking options and it works >.<

Thanks for looking either way (if you did!)

---

