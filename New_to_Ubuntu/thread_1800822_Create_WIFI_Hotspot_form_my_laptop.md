---
title: "Create WIFI Hotspot form my laptop"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by sptutusukanta on 2011-07-09
I want to create a WIFI Hotspot on my computer.
I am using Ultimate Desktop (a ubuntu distro). Please Help!

---

### Post by hakermania on 2011-07-09
Hello sptutusukanta, here in ubuntu forums we are not willing to help people who want to do illegal things (who talks!!!)...
Anyway, can you please your final purpose of doing this (which I assume it's not hijacking data right?) ;)

---

### Post by mrhhug on 2011-07-09
a wifi hotspot is a great idea, except that im not sure your laptop will contain a wifi chip capable of doing this. you would definitively need to connect the laptop to the internet through another source like another wifi chip or ethernet. lets start with telling us the type of wifi chip you have. ```
sudo lshw
``` and then look for network

---

### Post by sptutusukanta on 2011-07-09
I have WIFI in my laptop and have done creating WIFI Hotspot using an application - Connectify and a command "netsh" for Windows. But I dont Know how to do this in Ubuntu.

Actually I want to tether the net on my laptop using WIFI. So that, I can connect my android phone to the Intrenet.

Thank You!

---

### Post by waynefoutz on 2011-07-09
> **sptutusukanta said:**
> I have WIFI in my laptop and have done creating WIFI Hotspot using an application - Connectify and a command "netsh" for Windows. But I dont Know how to do this in Ubuntu.

Actually I want to tether the net on my laptop using WIFI. So that, I can connect my android phone to the Intrenet.

Thank You!

Not sure which Android phone you are using, but Easytether works great for me. This uses the usb cable, not wifi. 

[http://www.mobile-stream.com/easytether/android.html]("http://www.mobile-stream.com/easytether/android.html")

Go there and download the .deb file for Ubuntu. You can get EasyTether or EasyTether Lite .apk files for your phone there as well, or they will be in the Android Market, providing your carrier hasn't blocked it. The Lite version is free, but you can't access htpps sites with it. The full version is ten dollars. 

Once you get it installed on your phone, and the .deb on Ubuntu, open up a terminal and type 

```
easytether connect
```

And you are connected.

---

### Post by sptutusukanta on 2011-07-10
> **waynefoutz said:**
> Not sure which Android phone you are using, but Easytether works great for me. This uses the usb cable, not wifi. 

[http://www.mobile-stream.com/easytether/android.html]("http://www.mobile-stream.com/easytether/android.html")

Go there and download the .deb file for Ubuntu. You can get EasyTether or EasyTether Lite .apk files for your phone there as well, or they will be in the Android Market, providing your carrier hasn't blocked it. The Lite version is free, but you can't access htpps sites with it. The full version is ten dollars. 

Once you get it installed on your phone, and the .deb on Ubuntu, open up a terminal and type 

```
easytether connect
```

And you are connected.
Don't get confused what I've said is that I want to **tether the net on my laptop to the phone**. I **don't want to tether my phone's net**.
You just say some command or any application to host network through WIFI on my laptop not on phone.

---

### Post by spiky001 on 2011-07-10
How dose the laptop connect to internet is it by wireless or do you have a 2nd connection eg wired. if so just set the wireless connection to shared.

---

### Post by sptutusukanta on 2011-07-10
> **spiky001 said:**
> How dose the laptop connect to internet is it by wireless or do you have a 2nd connection eg wired. if so just set the wireless connection to shared.
The laptop gets Internet Connection from Wired source.

---

### Post by spiky001 on 2011-07-10
So you want to share the wireless. If you open network manager and share the wireless the phone should be able to connect

---

### Post by mrhhug on 2011-07-10
> **sptutusukanta said:**
> Don't get confused what I've said is that I want to **tether the net on my laptop to the phone**. I **don't want to tether my phone's net**.
You just say some command or any application to host network through WIFI on my laptop not on phone.

I know what your saying. Let me repeat to be clear. you want to use your laptop as a router. There are definite reasons to use a full fledged linux as a hotspot. first off, your server would most likey be the AP instead of some extra device that Cisco made and they put on tools they think you might need. in your situation you have complete and utter control (why i fell in love with linux in the first place) yes dd-wrt routers are for the enthusiast. but adding a router just adds another ip, another fail point, another cat5, another thing for someone to spill coffee onto, and it can stay more secure for your unique situation by total firewall customization; say one day in the future your hardware firewall is identified to have a massive security breach exploitable by every 13 year old; you have 25 of these firewalls. You previously would have been placing a huge newegg overnight order VS sudo aptitude upgrade.

I and found this. [http://ubuntuforums.org/showthread.php?t=376283](http://ubuntuforums.org/showthread.php?t=376283) looks good haven't tried it but like i suspected previously you have to switch the wifi chip into master mode, and that will mean you have to connect the laptop to internet using something else (ethernet most likey)

now that you brought this up, i am considering switching my OLD OLD OLD N gateway into ethernet passthrough mode and buying a decent N card to increase range here at home - my old gateway didn't support NTOP either and that made monitoring traffic so painful..

---

### Post by tumutanzi on 2011-07-30
This post shows how to set up it step by step with pictures: [**How to Make an Ubuntu Laptop as a WIFI Hotspot**]("http://tumutanzi.com/archives/3293")

---

