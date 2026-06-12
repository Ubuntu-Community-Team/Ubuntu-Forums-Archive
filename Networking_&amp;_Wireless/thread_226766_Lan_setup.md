---
title: "Lan setup"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by bailey_jatt on 2006-07-31
Hi everyone. complete linux newbie here .. 3rd day of linux and loving every moment.. 
i would appreciate if someone could help me out here...

i have two machines a i9100 laptop on which i installed simply mepis 6.0. everything went fine and i got internet running on it via wireless.
the second one is a tower on which i installed ubuntu 6.06. could you tell me how to set up both these computers on a wired Lan so that i can 
a) share files
b) eventually via internet sharing use the internet on the tower (via the laptop as the tower is too far from the wireless router to wire it up).

I read up a bit and it said i could connect using samba the two machines. but i cant find that on the ubuntu 6 on the tower. so is there any software/gui application that would allow me to connect to my laptop..
thanks in advance

---

### Post by Paerez on 2006-07-31
to share a file with samba on an ubuntu computer, right click the folder and select the sharing option, then pick SMB (short for samba).

It will not show up if you browse the network, though! If you computer is called "ubuntu" and the share is called "folder" you have to open nautilus and type:
smb:///ubuntu/folder/
to view the contents.

---

### Post by bailey_jatt on 2006-07-31
hi
when i right click on a forlder and click sharing it says you have to install either samba or nfs. the problem is i dont have direct internet access from the tower.. only on the laptop. Thats why i was wondering if there was a way to share files between the two machines

---

### Post by Paerez on 2006-07-31
So you have a LAN so that the two computers are connected, but only the laptop gets internet?

You could set up an ssh server on the laptop (or tower) and then mount the network drive via SSH. I know ssh comes with the installation, not sure about the ssh-server though.

---

### Post by bailey_jatt on 2006-07-31
yeah i have a LAN only between the laptop and the tower. the laptop gets internet.
ok you lost me there with the ssh server thing. pleas bear with me a bit more

so you mean i get a ssh server setup on the laptop. then share a drive via it, to which i can ssh from the tower?

---

### Post by Paerez on 2006-07-31
first, on one of the computers, run:
```
sudo apt-get install openssh-server
```
I would suggest from the laptop, since it has internet. Then go to the other computer, and say Places->"Connect to Server". Choose SSH as the server type, and type the laptop's IP in the server box. Then for username, put the username of a user on the LAPTOP. Then log in with that user's password.

Then you should be able to browse to that user's home.

---

### Post by bailey_jatt on 2006-07-31
sorry for being such a noob and i am feeling totally useless on this one.

i cant seem to find openssh-server. The synaptic manager says its installed. but i cant seem to locate the darn thing. i cant find it in KDE menu. i cant find it in my home folder. any idea how i could run the darn thing..
thanks a lot

---

### Post by Paerez on 2006-07-31
it should already be running. You can test it by typing:
```
ssh localhost
```
If it's not running, type:
```
sudo /etc/init.d/ssh start
```
then follow my other steps for the other computer.

---

### Post by bailey_jatt on 2006-07-31
hi Paerez
thanks for bearing with this noob one more thing and i will outta your hair :D 
i ran the ssh ..its up and running
now over to the tower... i followed ur instructions..ntn happened..
i opened up terminal and typed ping -c 5 192.168.2.6 (laptop's ip) says 100% packet loss
when i type its own ip ie ping -c 5 192.168.2.3 (tower ip) it goes with 100% success

so in essence i can ping the tower from the laptop and not vice versa..

---

### Post by Paerez on 2006-07-31
whoa that's weird. Are you sure you're not pinging the tower from the tower?

I don't know why you have an ip for both but they can't ping each other...

---

### Post by bailey_jatt on 2006-07-31
i am bit clueless here but this is what i did
gave an ip to the laptop - 192.168.2.6 and 
gave an ip to the tower - 192.168.2.3
can ping the tower from the laptop but cant do vice versa.. thats the bummer
figured thats why i cant ssh the laptop from the tower

---

### Post by Paerez on 2006-07-31
it's weird that it goes one-way. Is there any way you could install openssh-server on the tower?

---

### Post by bailey_jatt on 2006-07-31
will have to dig out my pen drive .. and try and install ssh on the tower. 
when i type ssh localhost on the tower it goes
connect to host localhost port 22: connection refused

maybe there is some kind of firewall blocking it  :confused:

---

### Post by HunterPro on 2006-07-31
whoah, Nelly. OpenSSH-server to share files? Because you cant connect to the internet? Yeah, it works, but SSHFS isnt really the most flexible tool in the shed.

The point is:

a) you want filesharing between the systems
b) you want the tower to be able to connect to the internet.

b is done via UTP cable to the laptop, which has a wireless connection to the wireless router.

You cant do A because you dont have internet (yet).

so, lets do B first! :)

install the packages ipmasq and ipmasqadm on the laptop. ipmasq is a package that completely sets up your system to share an internet connection. More info [here](http://lyre.mit.edu/~powell/debian-howto/ipmasq.html) and on Google. 

After getting your tower online, you can simply install samba etc and do that stuff at your own pace.

Good luck!

---

### Post by Paerez on 2006-07-31
that sounds like a better plan. I didn't know how to do that, so hopefully that'll get you going faster.

---

### Post by bailey_jatt on 2006-07-31
thanks a lot anyways paerez.. atleast i got to know a thing or two bout ssh :D
hunter your turn to bear with me now..:P ..i did download and install those two packages that you mentioned. the guide you linked to is kind of greek with me understanding bits and pieces..so could you help me on ahead a bit.. so with the ip mas thing set up on the laptop how do i get the tower up on the internet or is their a gui for this app from where i can set the rules


-- gui :D  -- i am so full of windows that i guess it will take me a while to change

---

### Post by HunterPro on 2006-08-01
> **bailey_jatt said:**
> thanks a lot anyways paerez.. atleast i got to know a thing or two bout ssh :D
hunter your turn to bear with me now..:P ..i did download and install those two packages that you mentioned. the guide you linked to is kind of greek with me understanding bits and pieces..so could you help me on ahead a bit.. so with the ip mas thing set up on the laptop how do i get the tower up on the internet or is their a gui for this app from where i can set the rules


-- gui :D  -- i am so full of windows that i guess it will take me a while to change

on the tower, make sure you have your IP settings set to 'dhcp'. 

To check this, go to your network settings ('Networking' in the Administration submenu). Select your network interface ('Ethernet' connection) and choose Properties. Make sure the connection is enabled, and that configuration has 'DHCP' selected. 
The rest of the boxes should be empty. 

Make sure your network cables are connected and all the link-lights are on (so you know the physical connection works) and press OK. In the Network settings window, press OK again to close it. 

Right now, you should get an IP address from the laptop.

Open the Network Tools from the Administration menu, and select the Ethernet interface. In the table there should be an IP behind IPv4. What is that IP adress now? :) If its in the 192.168.x.y range, you should be able to access the internet now. :)

just see how far you'll get and yell if it doesnt work!

---

### Post by bailey_jatt on 2006-08-01
hi hunter.. 
followed all steps..xcept in the last one instead of an IP behind IPv4 it says IPv6 with its wierd ip address.
if the tower ethernt ip is set on DHCP what should i set the ip for the laptop ethernet which connects with the tower?

---

### Post by dmizer on 2006-08-01
they should both be dhcp.  if you are connected directly to your laptop via lan cable (ie no router present), the lan cable has to be crossover cable.  are you using crossover cable?

also, if both clients you need to share files between are linux boxes, there's no reason to go through the pain of a samba file sharing system.  use nfs instead.  it's faster and will create less extra traffic on your network.

---

### Post by bailey_jatt on 2006-08-01
dmizer the laptop is on a wireless conn to the internet.
i want to get the tower on the internet too(it is too far frm the router). so there is a cable connecting the laptop n tower.. hunter was running me thru ip masquerade to get internet on the tower.....am kinda stuck in that

---

### Post by HunterPro on 2006-08-01
> **bailey_jatt said:**
> dmizer the laptop is on a wireless conn to the internet.
i want to get the tower on the internet too(it is too far frm the router). so there is a cable connecting the laptop n tower.. hunter was running me thru ip masquerade to get internet on the tower.....am kinda stuck in that

bailey, does the laptop also run linux? if yes, which one? :) (good morning ;))

---

### Post by dmizer on 2006-08-02
> **bailey_jatt said:**
> dmizer the laptop is on a wireless conn to the internet.
i want to get the tower on the internet too(it is too far frm the router). so there is a cable connecting the laptop n tower.. hunter was running me thru ip masquerade to get internet on the tower.....am kinda stuck in that

yes i understand. you have the following configuration:
modem-->wireless router - - -> laptop-->desktop.

so ... to connect your desktop to your laptop as in the above configuration,  you must have a crossover type cable between the laptop and desktop. if you do not, no ammount of changes to the laptop or desktop will make a bit of difference.

---

### Post by bailey_jatt on 2006-08-03
hi dmizer
you are right about the cable. But my laptop has an auto sensing port. So it doesnt matter which cable i put into it. i tried my cable both ways and the laptop always pings the tower when i give them both static IP's. so i think the cable is ok.
ps- the laptop runs simply mepis 6.0 and the tower ubuntu 6 lts

---

### Post by mips on 2006-08-03
For BOTH machines:

1. Please post output of **ifconfig eth**
3. Please post output of **route -n**
4. Please post output of **cat /etc/resolv.conf**
5. Please post output of **cat /etc/network/interfaces**
6. Please post output of **cat /etc/dhcp3/dhclient.conf**

Why would you want to run samba between two linux PC's ?

---

