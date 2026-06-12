---
title: "Network help please...kinda urgent."
date: 2008-02-12
forum: Networking &amp; Wireless
---

### Post by rockinlinux on 2008-02-12
Ok here is my problem. I was installing hardy alpha 4 and now both ubuntu (gusty) and windows says my ethernet card is no longer in my notebook...so i guess its broke. I do wokr on the internet so i went and found the only wifi router i could find, well i could not find a router so i get a access point. I have a new ISP, they give out only static IP addresses.

The ISP gave me:

IP-91.xxx.xxx.xx
subnet- 255.255.255.192
gateway- 91.192.157.65
DNS- 193.111.156.4
DNS 2- 91.192.159.1

I went into the access point and made the ip address, subnet and gateway the same as the isp gave me. I enabled DHCP and put the same gateway (91.192.157.65) set the ip start and end points and put the first DNS the ISP gave me as the DNS for the DHCP.

Then i went to windows and ubuntu and added the DNS's...still no internet. I can ping the router but not the gateway or DNS servers....


I dont really know much about networking so anyhelp would be great.

thanks in advance.

:)

---

### Post by PmDematagoda on 2008-02-12
Moved to the Networking and Wireless section.

---

### Post by rockinlinux on 2008-02-12
where it will not get any replys...

---

### Post by PmDematagoda on 2008-02-12
This thread concerns networking support, therefore this will receive the best help in the appropriate section.

---

### Post by mrsteveman1 on 2008-02-12
I can help, just let me look over what you said for a bit and figure out what to do.

---

### Post by mrsteveman1 on 2008-02-12
When you said you can ping the router do you mean over wifi?

post the results of the following commands: 

```

sudo lspci

sudo ifconfig -a

sudo cat /etc/resolv.conf

sudo route
```

Also elaborate on how you have this access point wired, is there a switch involved? Is the access point plugged directly into a cable modem or DSL device? Are you only using the wireless network because wired eth isn't working at the moment?

---

### Post by rockinlinux on 2008-02-12
yes i mean i can ping the IP i gave the router (91.192.xxx.xx) the same ip my ISP gave me. I cant run the command, im at a internet cafe trying to figure out what to do...

I am reading a lot about this and i think that i need to make the gateway in the DHCP part of the configuration the same as the router ip address.

thanks :)

---

### Post by rockinlinux on 2008-02-12
my internet connection is strange. I just have a cat 5 cable running intop my flat...no modem no nothing. My isp gave me a static ip, it worked when i used it hard wired...and yes im only useing wireless because my card is broke.

---

### Post by rockinlinux on 2008-02-12
and to be honest i have only tried to get this working with linux for 10 minutes...i just fond windows eaier because the "user manual" that came witht the AP...its says almost nothing.

also i find it strange that in the AP settings there is DNS field except for the DHCP settings.

---

### Post by mrsteveman1 on 2008-02-12
So you normally use a wired router, right?  Is the AP directly connected to the cable coming into your place?

---

### Post by rockinlinux on 2008-02-13
yes, the AP is directly connected to the cat5 coming into my place. normally i just plug that cable into my computer.

thanks :)

---

### Post by mrsteveman1 on 2008-02-13
In that case, the AP is just a bridge, all the IP settings should be on your computer.

Have you configured the computer itself for your IP settings? I would avoid DHCP for the moment just to remove it from the equation.

---

### Post by rockinlinux on 2008-02-14
ok well everything I did was right. It turnd out after talking to countless tech support guys and 3 days they had the wrong mac address so i was not able to connect to the gateway/dns servers. what idiots...i even told them to look at that a few times!

thanks for the help guys!

---

### Post by rockinlinux on 2008-02-14
one thing though, im still not using the wireless ap...i am using my other pcmcia ethernet card i have,,,how do i make this ap a bridge? there are a few settings, i dont remember off the top of my head but the setting are like:

AP
peer to peer bridge
some other bridge 
a few other types.

when i have more time i will look and get back to you.

---

