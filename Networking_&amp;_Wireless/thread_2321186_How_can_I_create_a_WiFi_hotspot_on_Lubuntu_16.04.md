---
title: "How can I create a WiFi hotspot on Lubuntu 16.04?"
date: 2016-04-21
forum: Networking &amp; Wireless
---

### Post by vasa1 on 2016-04-21
EDIT: I got my router going. But I'll leave this here just in case!

My system is Lubuntu 16.04 upgraded, not a clean install, from 14.04 and fully updated.

I'm not familiar at all with networking, its components, or the terminology.

I ran the script recommended in the sticky post and that information is attached.

I can access the internet by plugging a cable into my laptop. I also have a functional WiFi router; to use that I need to unplug the cable from the laptop and connect it to the router. Unfortunately, my ISP requires that I use either one. I'm not allowed to switch between the modes without their intervention.

Now, that I've got 16.04 going, I can move to the WiFi router. Then I can use my smartphone as well (Android Lollipop) over WiFi whenever I want.

But my question is whether it's possible to make my laptop into an access point (?) or hotspot so that my smartphone can use that WiFi. The GUI for doing so is shown in  [https://help.ubuntu.com/16.04/ubuntu-help/net-wireless-adhoc.html](https://help.ubuntu.com/16.04/ubuntu-help/net-wireless-adhoc.html) but that is for Ubuntu. A similar GUI is not present in Lubuntu.

I also don't know if the wireless component of my laptop can be used the way I want.

---

### Post by Lloydb39 on 2016-04-21
I'm not an expert so you might want to wait for an answer from one. But I think you have the whole concept wrong. Your phone can be a hotspot for your laptop, but there is no point doing it the other way around. If you are near wi-fi, both the laptop and phone can connect. The phone has a data connect over 4G. You can buy a thumb drive device for your laptop to give you such a connection but you will have to pay your phone carrier to use it.

---

### Post by sammiev on 2016-04-21
Hi,

Hotspot stopped working in 16.04 a few weeks back.

There is a [work around]("https://prahladyeri.wordpress.com/2013/05/26/how-to-turn-your-linux-machine-into-a-wifi-access-point/") posted by one of the members with a little effort.

---

### Post by vasa1 on 2016-04-21
> **sammiev said:**
> Hi,

Hotspot stopped working in 16.04 a few weeks back.

There is a [work around]("https://prahladyeri.wordpress.com/2013/05/26/how-to-turn-your-linux-machine-into-a-wifi-access-point/") posted by one of the members with a little effort.
Ah!

Yes, I remember runrickus [posting that]("http://ubuntuforums.org/showthread.php?t=2297174&p=13467565#post13467565"). I took a long look at it. But it seems really, really technical (a polite way of saying it's beyond my skills).

I have several other links on the topic. A relatively recent one is this: [http://www.linuxveda.com/2015/08/23/how-to-create-an-ap-in-ubuntu-15-04-to-connect-to-androidiphone/](http://www.linuxveda.com/2015/08/23/how-to-create-an-ap-in-ubuntu-15-04-to-connect-to-androidiphone/) but if Hotspot is broken in 16.04 then ... :(

---

### Post by QLee on 2016-04-21
> **vasa1 said:**
> 
I can access the internet by plugging a cable into my laptop. I also have a functional WiFi router; to use that I need to unplug the cable from the laptop and connect it to the router. Unfortunately, my ISP requires that I use either one. I'm not allowed to switch between the modes without their intervention.

That can mean that they authenticate your connection by the MAC address of the connected device however there are other possibilities. If that is the case then, many routers allow the cloning of the MAC address of the interface connected to them (for example your computer plugged into a real port on the router), if you do that then the router would present to the ISP a MAC that it recognised and allow connection. How to do this will be in the documentation for the router if it is possible. That might allow you to use it without having to call the ISP for switching.

Vasa1, I know you are able to use a search engine for any terms you don't understand, you answer a lot of questions here. 

My guess is that you would be happier running both your devices through your router. Then the computer would not have to be on for the phone to have WiFi. 

I don't know about hotspot on 16.04 But I have used it quite a bit on 14.04. The most important thing is to have a wireless interface that is capable of being in AP mode. (capable of acting as an Access Point). But then you would have to leave your computer plugged into the router (or the broadband line.) and on for the phone or any friends that you want to have access to WiFi.

---

### Post by vasa1 on 2016-04-21
> **QLee said:**
> That can mean that they authenticate your connection by the MAC address of the connected device however there are other possibilities. If that is the case then, many routers allow the cloning of the MAC address of the interface connected to them (for example your computer plugged into a real port on the router), if you do that then the router would present to the ISP a MAC that it recognised and allow connection. How to do this will be in the documentation for the router if it is possible. That might allow you to use it without having to call the ISP for switching.

Vasa1, I know you are able to use a search engine for any terms you don't understand, you answer a lot of questions here. 

@QLee, thanks for responding. If you notice, none of my answers relate to networking or even to hardware :) 

And the router's documentation is minimal. It's a local brand. I guess if I had a Netgear router, things would be better documented. But *The Man* pushed the local brand saying that if it broke I could return it to him whereas if the Netgear one broke, the process would be more complicated. 

> **QLee said:**
> My guess is that you would be happier running both your devices through your router. Then the computer would not have to be on for the phone to have WiFi. 

I don't know about hotspot on 16.04 But I have used it quite a bit on 14.04. The most important thing is to have a wireless interface that is capable of being in AP mode. (capable of acting as an Access Point). But then you would have to leave your computer plugged into the router (or the broadband line.) and on for the phone or any friends that you want to have access to WiFi.

You make a valid point but I keep the laptop connected all the time I'm awake but I use the WiFi on my phone in a very limited way mostly to backup to my Google account. I'm not very social and so I'm at peace with the cell's WiFi off.

Re. *The most important thing is to have a wireless interface that is capable of being in AP mode. (capable of acting as an Access Point).* I could almost be certain that the **iw list** command's output indicated that my built-in device *was* capable in 14.04 but when I just run it in 16.04 all I see is
```
	Supported interface modes:
		 * IBSS
		 * managed

```So I'll visit my ISP today and get this over! Thanks for the prompting :)

---

