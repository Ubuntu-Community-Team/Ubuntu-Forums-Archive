---
title: "Strong network connection but cant always connect"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by randell6564 on 2006-07-24
Hello!

I use a Linksys wusb11 V.2.6 wireless adapter.  I always have a strong connection to my neighbors router, (network name, 'Linksys' no security key, I have permission by the way :) )

But I cant always access the net!  

I use to have my own connection, but we are moving so I had my service disconnected after my neighbor friend said that I could connect to his network until we find a place that we want to live.

I am connected now, but it doesnt always work.  Any ideas?

Where do I go to see available networks?

Thanks!

---

### Post by twotonz on 2006-07-24
Hi,
Hmmmmm, tricky subject wlan. To get a list of available networks, open a terminal and type....

iwlist [interface] scanning

Whereas, [interface] is the name of your wlan card - normally eth1, wlan0 or ra0.

Love & Peace (to all)
anthony

---

### Post by randell6564 on 2006-07-24
> **twotonz said:**
> Hi,
Hmmmmm, tricky subject wlan. To get a list of available networks, open a terminal and type....

iwlist [interface] scanning

Whereas, [interface] is the name of your wlan card - normally eth1, wlan0 or ra0.

Love & Peace (to all)
anthony

Thanks my friend.  I'll try that!

---

### Post by twotonz on 2006-07-25
my pleasure!
 One more thing that has occured to me, can you ping your friends router? Are you using static or dhcp.
 If you can ping his router, but cannot access the net, could mean that your friends router is "offline"

Love & Peace
anthony

---

### Post by randell6564 on 2006-07-25
> **twotonz said:**
> my pleasure!
 One more thing that has occured to me, can you ping your friends router? Are you using static or dhcp.
 If you can ping his router, but cannot access the net, could mean that your friends router is "offline"

Love & Peace
anthony

Hi!  He's not home right now and I dont know the addy to his router.  I'm sure that it's online cuz he uses wireless on his box and has no problem.

I'm having no problems right now, getting online.  It just does'nt work all the time.

Is'nt there a way to get his routers address? something that I can enter at the terminal to show it?

Thanks!

---

### Post by randell6564 on 2006-07-25
heres the results of the scanning for networks:

[B]bigboss@bigboss:~$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:14:BF:C3:FF:5D
                    ESSID:"linksys"
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Quality:0/0  Signal level:10/255  Noise level:0/0
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:E0:98:FB:10:0D
                    ESSID:"05B403727037"
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Quality:0/0  Signal level:3/255  Noise level:0/0
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s

[/B]

'Linksys' is the one that I'm using. The other one is too weak.  You notice, no encryption key.  so why I am having trouble is wierd!

---

### Post by twotonz on 2006-07-25
Hidihi,
Type in the console......
ifconfig

This should give you your current ip, the router address is proberly the same but with the last number-block being 1. For example, ifconfig shows that your ip is 192.168.2.56 , the router address will proberly (note-proberly) 192.168.2.1

The only other thing that I can add, is that wlan depends on many different factors. I have the same set-up as you here (online useing a kind neighbours ap). If other people are also useing wlan in your direct area, it can be that the signal is getting cancelled out, weather also plays a small factor. A good solution is to build your own attenna with a higher gain (many instructions on the net)

Love & Peace
anthony

---

### Post by randell6564 on 2006-07-25
> **twotonz said:**
> Hidihi,
Type in the console......
ifconfig

This should give you your current ip, the router address is proberly the same but with the last number-block being 1. For example, ifconfig shows that your ip is 192.168.2.56 , the router address will proberly (note-proberly) 192.168.2.1

The only other thing that I can add, is that wlan depends on many different factors. I have the same set-up as you here (online useing a kind neighbours ap). If other people are also useing wlan in your direct area, it can be that the signal is getting cancelled out, weather also plays a small factor. A good solution is to build your own attenna with a higher gain (many instructions on the net)

Love & Peace
anthony



"build" my own antenna huh?  Sounds interesting!  (I might never have to pay for internet service again! LOL!)

As far as IP, I know what mine is.  I was just thinking that when I lose internet, I could manually enter the IP of the router and then be able to access the net at will.

---

### Post by twotonz on 2006-07-26
Hallo again,
 If you use a static address, then you should first ask your neighbour. I have also used a static address, when I am having troubles, unfortuantly many people here use the same AP (I am lucky enough to have a big company next door, who offer a free ap to poor people like me), so useing a static ip is not good form, and can cause problems, so talk with your neighbour first.
 
 Concerning the Antenna, building your own is fun! You just would not believe what I have here. Basically it is a square copper plate, with 2 rings attached to each other, stuffed into a carboard box - total cost, around 7,00â‚¬ & works a treat (even better as the 50,-â‚¬ high-gain antenna that I brought about a year ago)  

Love & Peace
anthony

---

### Post by bigken on 2006-07-26
give this a try [http://www.ubuntuforums.org/showthread.php?t=222047](http://www.ubuntuforums.org/showthread.php?t=222047)

---

### Post by randell6564 on 2006-07-26
> **twotonz said:**
> Hallo again,
 If you use a static address, then you should first ask your neighbour. I have also used a static address, when I am having troubles, unfortuantly many people here use the same AP (I am lucky enough to have a big company next door, who offer a free ap to poor people like me), so useing a static ip is not good form, and can cause problems, so talk with your neighbour first.
 
 Concerning the Antenna, building your own is fun! You just would not believe what I have here. Basically it is a square copper plate, with 2 rings attached to each other, stuffed into a carboard box - total cost, around 7,00â‚¬ & works a treat (even better as the 50,-â‚¬ high-gain antenna that I brought about a year ago)  

Love & Peace
anthony

Not really sure why there would be a problem useing a static address, or even how to set one. I know that by manually setting one, there are other numbers that I would be required to enter like subnet mask and gateway. I dont know what to enter for these.

Would subnet mask be the same as it is when set up for dhcp?  And how about gateway?

Thanks!   (Gotta look into the antenna thing for sure!)

---

### Post by twotonz on 2006-07-27
Hallo again,
 Sorry about the delay, i've just been given "half-life" to play around with for a few days :) 
 Setting a static (or manuall) address could cause problems if someone else is using the same ip on a lease (unlikly, but could happen). As for the other settings, it is not too dificult (when you know how of course). Three settings are important....
Your ip address (we use for this example 192.168.2.46)
192.168.2.46
The Network mask (all computers on the network must have the same mask, for home networks it is always......)
255.255.255.0
Lastly. comes the Gateway (the address of the router)
192.168.2.1

I am not really very good at explaining things, but I am tring to keep it simple. 
As you can see from the above, the Gateway (also known as-router) must have the same 3 digit blocks as your  own ip (192.168.2). Whe using dhcp, the wlan card looks for all available networks, chooses the best one, asks the router for an ip, if the router agrees, then it will give you the Gateway address automatically. (GATEWAY=ROUTER address) This also applies to any further computers connected to the network. 
The mask 255.255.255.0 has been reserved especially for home-networks, and is in 99% also so. The subnet mask remains the same for dhcp or static

Of course your neighbour can also at any time change these settings, but the above example will apply in most cases though (it seems that many people leave everything with the default settings)

I tried to upload a foto of the anttena, so that you could have a laugh, didn't work though. If I remember, I will put on my web-site, and give you the link, could take a couple of days though.

Love & Peace (to all)
anthony

---

### Post by randell6564 on 2006-07-27
Thanks for the help!  Look forward to seeing the antenna!

---

### Post by twotonz on 2006-07-27
Hi,
here it is......

Have fun :D 

anthony

---

### Post by randell6564 on 2006-07-27
> **twotonz said:**
> Hi,
here it is......

Have fun :D 

anthony

HA! Amazing!  And it works Huh?  How do you plug it in to your box?

Are those just two metal rings sodered to the copper plate?  Mind if I attempt to copy it?

Pretty cool, My Friend!

---

### Post by twotonz on 2006-07-28
Hidihi,
It is hard to believe I know, but like I said, works a treat. The pc that this thing is connected to, is stuck in the far corner of my room, with a b-card inside (asus a7n8x-e delux), so all a bit old. Before this I had a g-card with an acx111 chip & high gain anntenna (brought over the net) - I was getting nothing, then I found the add-on card for the MoBo at a car-boot sale for an amazing 4,- euro.
 Of course I do not mind if you have ago yourself - I do not own the copyright :o  I built this antenna, quite a while ago, so I shall have to try and find the spec's, otherwise I shall just measure out everything. It was quite simple, and took less than an hour. 
 Basically you have a plug on one end, that screws onto the wlan (connectors available at conrads/radio shack). You then need cable, I have about 2 mtrs, the shorter the better, because you lose gain through the cable, also the cable must have the right impedence (or resistence, I forget which, best bet ask at the same place where you get the connectors). The cable is then soldered to a small copper pin about 4cm that pokes through the cardboard box. (I used this cardboard box because I didn't really think it would work, so it was just an experiment) The pin is shielded and also goes through the copper plate.............

 I am just reading through this again, Oh dear, I am not very good at giving instructions - I shall make a load of photo's, measure everything out, & work on better instructions (perhaps I find the original plan) - if you send me your email address, then I can put it all in a zip archive and send it to you. (DO NOT put your email address here - unless you want a load of spam, send me a pm). I shall also have to take everything here apart, take the photo's, and then put everything back together again, so please give me a few days. (By the way, the rings are soldered to the cable, they do not touch the copper plate at all, and are well shielded with rubber. I think the thoery is, that the signal (wave) is reflected from the plate onto the rings, which are exactly a 1/4 (or an 1/8) of the wave lenth)

 I would like to finish off a few other threads that I am involved in first, then I shall go off line and start (sunday I think), so please have a bit of patience.

Love & Peace (to all)
anthony

email with the fotos should be with you by now.......have fun

---

