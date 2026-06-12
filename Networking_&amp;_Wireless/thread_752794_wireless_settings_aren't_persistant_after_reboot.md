---
title: "wireless settings aren't persistant after reboot"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by freebeer on 2008-04-12
Hi folks.

I'm using 8.04 beta and it would appear that it's natively supporting my D-link usb wireless "stick".  This is the first time I've dealt with wireless in Linux and I'm definitely ignorant of all the options/methods in dealing with wireless.

I can get it to connect, but I must do so manually.  (Via System -> administration -> Network) It seems to remember my essid but not the key/password.  By "seems" I mean that when I go into the above settings, I have to manually re-enter the password then all works until the next reboot.

I've checked /etc/network/interfaces and there's a (hex?) key in there but I can't tell if that's the correct hex-equivalent to my password.

Here's the output of iwconfig if it's of any value:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"FreeBeer"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:17:9A:9E:04:E6   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=93/100  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

``` 

If you need any other diagnostics, I'll be happy to provide them.  I could probably live with a manual restart all the time, but this machine is for my 74 year old father and I'd rather not burden him with having to manually restart every time.  It's an old clunker of a machine and it's slow enough as it is without burdening him even more. :lol:

Any insight would be appreciated.

---

### Post by bromptonaut on 2008-04-13
Hi there,

I am facing the same problem using Ubuntu 7.10 (64 bit)  with the slight difference that in my wireless configuration the password type is always reset from WPA2 to WPA (the password is still there).

There is a descriptions in the Ubuntu Wiki how to setup a WPA connection that is launched at system start: 
[https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29](https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29)

However, I have to admit that I did not yet manage to setup my wireless network that way.  Using the network manager seems much more convenient.  

So I would appreciate some help with this topic, too.

---

### Post by freebeer on 2008-04-13
Thanks for your post.  I'm still playing with different ideas.  I'll certainly post back if/when I make some progress.

---

### Post by NIT006.5 on 2008-04-13
I've got the same problem on Gutsy. Either the password seems to be "forgotten" or it changes automatically from WPA2 to WPA. However, I've also noticed that this doesn't seem to happen with all adapters, so assumed it was related to my wireless adapter.

---

### Post by bromptonaut on 2008-04-16
Hi,

I managed to find a work-around for my case.

I found out, that the configuration in 

/etc/network/interfaces

was still set correctly after reboot.  It was only that the network manager did not show the correct setting (WPA2 for my case) anymore.  That might have something to do with the fact that the settings for WPA and WPA2 seem to be the same anyway.

However, the network connection was not initiated at system start.

From the German Ubuntu forum I learned that you can ad the line 

/etc/init.d/networking restart

into /etc/rc.local to start the network connection when booting.

That worked for my system.

Cheers,
Bromptonaut

---

### Post by freebeer on 2008-04-16
Thanks!

I'll have a try at that and see how it goes.  [IMG]http://www.freebeer.is-a-geek.org/graphics/thumbsup.gif[/IMG]

---

### Post by Hachi-Roku on 2008-04-18
Hey... I get the same problem.

Theres a bug report on launchpad but it doesnt seem to be completely solved yet.

I tried that networking restart command for a different wireless problem and i found it didnt actually do anything. Some message like 'no devices found' came up.

let me know if you guys stumble upon a fix.... i'll do the same.

---

### Post by freebeer on 2008-04-18
I haven't tinkered with it this week.  I hope I'll get some time on the weekend.

---

