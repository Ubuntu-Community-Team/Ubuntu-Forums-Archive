---
title: "Default gateway problem with wireless router"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by jpjohnj on 2011-08-02
hi....

i made my lab setup as like bellow

internet--wireless ADSL router--Unmanagable switch-
            (192.168.2.1,DHCP    (16 port switch)
              enabled)                ||
                                      ||
                      --------------- ||  ---------
                        ||                      ||
                  wireless router1        wireless 
                  (10.10.1.254)          router2
                    DHCP enabled         
                      |
                      |
            -----------------------
              |    |    |    |
             Pc1  Pc2  pc3  pc4


i can able to connect with internet with PC1 and PC2.but i cannot able to connect with internet to PC3 and Pc4..



Settings with pc1 and pc2
Default gateway- 10.10.1.254
dhcp server - 10.10.1.254
dns  server- 192.168.2.1

setting with pc3 and pc4

Default gateway- 192.168.2.1 and 10.10.1.254
dhcp server - 10.10.1.254
dns  server- 192.168.2.1 and 8.8.8.8

here i connected 4 pc's with same access point....

did i made any wrong set up.....

or

help me to connect my 4 pc ,like above setup.

please explain the concept of wireless router function and the port avaliable with that router.

---

### Post by jtarin on 2011-08-02
What happens when you try to access the internet with PC 3/4? Can you ping the router you are trying to connect to?

I don't know about others but your description is a little confusing for me as to exactly what you want to achieve....with what hardware. Maybe if you could draw an illustration in Gimp and post.

---

### Post by EkuquoL on 2011-08-02
Are you using serial switch or are you trying to connect computers over the net ?

---

### Post by jpjohnj on 2011-08-02
hi..

i draw the labsetup here..... you can access with bellow link

**[http://i51.tinypic.com/20zcxgw.png](http://i51.tinypic.com/20zcxgw.png)**
[IMG]http://i51.tinypic.com/20zcxgw.png[/IMG]

i need an explanation of the entire lab ....

now i am confusing with default gateway.  


from my understanding internet connected to the wireless router will share the internet connection to all the other device.

i create a connection with ethernet cable from the port one of wireless adsl router 1 to the 1st port that unmanagable switch. 

(so function of wireless ASDL router is to share the internet connection to other device with lan port that has and through wireless.....)

(i want to know the function of unmanagable switch and what is the uses of those port )

and use 9th port of that switch to connect the wan port of wireless router 2

(i need to know the difference between wireless router and APs.)

when i am connected my four pc's to the same wireless router 2...

with pc1 and pc2 i can connect with internet...but with pc2 and pc3 cant.....

(how to group the wireless network )

please help me to understand the concept of device working here.....

---

### Post by overdrank on 2011-08-02
Threads merged :)

---

### Post by spook1980 on 2011-08-02
1st off on any network there should be only 1 dhcp server thats prob your main problem

and if these computers are all on the same network then they should only be 1 default gateway, i had to learn this the hard way as when i switched from dsl to cable i could no longer use the qwest dsl routers i ended up converting the dsl router i had into a switch and turning and old POS computer into a router (i couldn't aford to shell out $50 for a new router) networking can be a pain in the *** 

my network(ip addresses changed for privicy reasons)

gateway= the device in witch all trafic must pass to access the outside world,
for example i have my router set to an ip address of 192.168.1.1
dhcp enabled on router
(the cable modem is bridged to my home made router so its ip address is not important in this)
my switch (old adsl router) is set to 192.168.1.2 with dhcp disabled, and wireless access point turned on

computer 1 is set to 192.168.1.3
computer 2 is set to 192.168.1.4
xbox set to 192.168.1.5

all have the same netmask 255.255.255.0
all have the same network 192.168.1.0
and all have the same broadcast 192.168.1.255

now resently i picked up another switch  set the ip to conected to the 1st switch 192.168.1.100, and i can connect devices up to it no problem,

hope i was of sum help

---

### Post by AgentZ86 on 2011-08-02
Hi,

Your wireless router should external connection should access the wired router connection to the internet via the same address as the router itself.

If you access your wired router which is connected to the internet via IP address. Meaning when you log in to that router what is the IP address.

So the external portion of your wired router should be the same as that IP address.

Then your netmask gateway for the wireless router must be outside the range of the router that accesses the internet 

So if the wired router has this netmask 255.255.255.0

Then you should have something like 255.255.255.256 or something.

Additionally, you should setup DNZ zone in your wired router connected to the internet, so that your wireless router will manage the connection and all traffic of the ip range or your wireless router's local connections so yes you can setup dhcp for the wireless router and those ip addresses cannot overlap the ip range of the wired router.

Then you can setup the small IP range of your wireless router to include maybe only 2 or 3 IP's or however many you would like this would secure the wireless router and yes the DNZ on your wireless router would be turned off and all the connections that make it to the wireless would be managed via your wireless router for security.

Then your wireless router will act as a gateway and dish out internal IP's to your wired network and the wireless router itself will manage the IP range of that particular internal network.

So essentially you have to setup your wired router which is connected to the internet to allow the other router to connect and thus you setup DNZ for that router's IP and netmask.

I hope this helps it's a little confusing but I have a SME gateway server behind an unmanged switch and that is behind the Verizon wireless/wired router - to the internet.

And all this works in same way. 

I'm sure there is other ways to do it and to manage the connection also, but this is how I'm familiar with.

Hope this helps

---

