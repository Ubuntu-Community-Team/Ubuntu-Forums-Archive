---
title: "Slow internet speeds"
date: 2010-08-09
forum: New to Ubuntu
---

### Post by hellolife on 2010-08-09
I'm sorry if this is a tired thread-- I've had Ubuntu for a while but don't use the computer much so I haven't really learned what I need to know.

I have absolutely horrible internet speeds and even worse download speed.
[IMG]http://i755.photobucket.com/albums/xx194/samhoperain/Screenshot.png[/IMG]

I am on an Asus EEE PC 1005HA. I'm currently running Lucid Lynx and its version of netbook remix (Utility, I believe).

I tried installing Namebench but I'm not savvy enough to install it, apparently. Is there any other approach to boost my speeds? 

Thanks!

---

### Post by Elmer Fudd on 2010-08-09
> **hellolife said:**
> I'm sorry if this is a tired thread-- I've had Ubuntu for a while but don't use the computer much so I haven't really learned what I need to know.

I have absolutely horrible internet speeds and even worse download speed.
[IMG]http://i755.photobucket.com/albums/xx194/samhoperain/Screenshot.png[/IMG]

I am on an Asus EEE PC 1005HA. I'm currently running Lucid Lynx and its version of netbook remix (Utility, I believe).

I tried installing Namebench but I'm not savvy enough to install it, apparently. Is there any other approach to boost my speeds? 

Thanks!

Your upload and latency cirtainly seem deficient.

I guess that since you are posting this here that you believe the problem is Ubuntu/linux related.

Do you get higher speed running Windows.

What speeds are you paying for/ expecting from your service

DSL or CABLE?

Wired or wireless connection to your router.

Make and model number of router

---

### Post by jtarin on 2010-08-09
Is this a dual boot with Windows? What is your normal speed? How long has this behavior exhibited itself?
Post results from the command ```
ifconfig -a
```

---

### Post by TriBlox6432 on 2010-08-09
If you can, go to speedtest.net and post the output here.  I just wanna see what speeds you're dealing with.  :p

---

### Post by jtarin on 2010-08-09
> **TriBlox6432 said:**
> If you can, go to speedtest.net and post the output here.  I just wanna see what speeds you're dealing with.  :p
Did you miss the illustration in his first post????;)

---

### Post by linux18 on 2010-08-09
[[IMG]http://www.speedtest.net/result/909126639.png[/IMG]](http://www.speedtest.net)

I'm not much better, but I have 3 servers so I don't complain

---

### Post by hellolife on 2010-08-09
> **Elmer Fudd said:**
> Your upload and latency cirtainly seem deficient.

I guess that since you are posting this here that you believe the problem is Ubuntu/linux related.

Do you get higher speed running Windows.

What speeds are you paying for/ expecting from your service

DSL or CABLE?

Wired or wireless connection to your router.

Make and model number of router

I guess I should've been a bit more clear about a few things (sorry :???:)
I don't run windows. I've been using  Mac/Ubuntu for a while now. This is not a dual boot or partition- just Ubuntu.
I have the "essential" package with Cox/Comcast (cable), which states that I should receive up to 3 mbps (so I have next to the slowest package), but I had this same package living somewhere else and using Karmic and the internet speeds seemed to be better and the downloading was definitely better.

It's a wireless router and modem in one, called the Motorola SURFboard.

I'm not sure if it's Lucid Lynx or the area. 

I'm hoping it's not Lucid as I like it much more than Karmic.

---

### Post by hellolife on 2010-08-09
> **jtarin said:**
> Is this a dual boot with Windows? What is your normal speed? How long has this behavior exhibited itself?
Post results from the command ```
ifconfig -a
```

Nope, not a dual boot. Just Ubuntu. I'm not sure what my normal speed is, I just know it was definitely faster than this. It's been doing this I'd say for a couple of weeks at least. 

Results:

eth0      Link encap:Ethernet  HWaddr e0:cb:4e:1b:9b:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5396 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:429621 (429.6 KB)  TX bytes:429621 (429.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:e5:19:7c  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fee5:197c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1478984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1154825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1506375647 (1.5 GB)  TX bytes:395930112 (395.9 MB)

---

### Post by Elmer Fudd on 2010-08-09
> **hellolife said:**
> I guess I should've been a bit more clear about a few things (sorry :???:)
I don't run windows. I've been using  Mac/Ubuntu for a while now. This is not a dual boot or partition- just Ubuntu.
I have the "essential" package with Cox/Comcast (cable), which states that I should receive up to 3 mbps (so I have next to the slowest package), but I had this same package living somewhere else and using Karmic and the internet speeds seemed to be better and the downloading was definitely better.

It's a wireless router and modem in one, called the Motorola SURFboard.

I'm not sure if it's Lucid Lynx or the area. 

I'm hoping it's not Lucid as I like it much more than Karmic.

With what you say/show here, I would be much more suspicious of the quality of your service than Lucid. 

Can you connect with a ethernet cable to the Surfboard to eliminate any wireless issues or have a friend try a wintel laptop to see any differences?

Looks like your download speeds are what you are paying for.

---

### Post by 29732 on 2010-08-09
mine isn't quite the best either:
[IMG]http://www.speedtest.net/result/909160889.png[/IMG]
but im happy with it, gets what i need to do fairly quick

---

### Post by hellolife on 2010-08-09
> **Elmer Fudd said:**
> With what you say/show here, I would be much more suspicious of the quality of your service than Lucid. 

Can you connect with a ethernet cable to the Surfboard to eliminate any wireless issues or have a friend try a wintel laptop to see any differences?

Looks like your download speeds are what you are paying for.

I've already tried connecting with an ethernet and it seems to be pretty much the same.
I realise that's what my service provider is saying that's the max I'll get, I've just gotten better than this with the same package/rate.

I thought there might be some possible tweak or slight fix to give it a boost?

---

### Post by Elmer Fudd on 2010-08-10
> **hellolife said:**
> I've already tried connecting with an ethernet and it seems to be pretty much the same.
I realise that's what my service provider is saying that's the max I'll get, I've just gotten better than this with the same package/rate.

I thought there might be some possible tweak or slight fix to give it a boost?

Just want to make sure that I understand:
You are paying for (the classic marketing amount of) "up to 3.0" and you are getting 2.64 MB/s. So the download speed is as expected.

The latency and upload are ugly.

Since it is a Cable pipe the time of day (kids getting home in the neighborhood) can affect available bandwidth.  

Anyway to answer your question, there are ways to tune your TCP/IP communication with the internet, but I suspect the benefits will not be substantial.

check out:
[http://fasterdata.es.net/TCP-tuning/linux.html](http://fasterdata.es.net/TCP-tuning/linux.html)

and don't forget to post your results.

---

### Post by jtarin on 2010-08-10
You get what you pay for...they give you the minimum...and that's all they will guarantee. Anything above that is hype.

---

### Post by hellolife on 2010-08-10
> **Elmer Fudd said:**
> Just want to make sure that I understand:
You are paying for (the classic marketing amount of) "up to 3.0" and you are getting 2.64 MB/s. So the download speed is as expected.

The latency and upload are ugly.

Since it is a Cable pipe the time of day (kids getting home in the neighborhood) can affect available bandwidth.  

Anyway to answer your question, there are ways to tune your TCP/IP communication with the internet, but I suspect the benefits will not be substantial.

check out:
[http://fasterdata.es.net/TCP-tuning/linux.html](http://fasterdata.es.net/TCP-tuning/linux.html)

and don't forget to post your results.

Yes, I know the download speed is expected. If I had the money I would pay for the upgrade, but I don't. So this is what I'm stuck with.

I appreciate everyone's suggestions. I will try these out to the best of my ability (or have someone help me) and respond with my results as soon as I can (it may take me a little while).

Thank you!

---

### Post by hellolife on 2010-08-12
Okay, so I took a different route than explained to me here.

I decided to try a system restore to Lucid Lynx (not Unity or Karmic's netbook remix) and it seems to have improved things slightly.

[IMG]http://i755.photobucket.com/albums/xx194/samhoperain/speedtest.png[/IMG]

Also, upon doing some research, I started using Deluge and it seems to work much better than Transmission (download speeds have been around 200-300 kb/s which is much better than the 20 kb/s I was getting). 
I'm going to have someone help me with the other suggestions as I said I'm still not too savvy with this. I'll post as soon as we figure it out.

Thank you.

---

