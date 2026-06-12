---
title: "Networking between Linux and Windows"
date: 2005-12-02
forum: Networking &amp; Wireless
---

### Post by cparsons on 2005-12-02
I have a windows XP desktop, a hub etc... but how do i network my linux laptop to the windows desktop?

I need to be able to use the internet connection on the desktop as well as the printer attached to it.

---

### Post by MetalMusicAddict on 2005-12-02
[THIS]("http://ubuntuguide.org/") guide is for 5.04 but still works. Its a great guide for starters and answers your question. You have a router right?

---

### Post by cparsons on 2005-12-02
a router being? The IT people @ work said that i would only need a hub, which i have bought...

---

### Post by MetalMusicAddict on 2005-12-02
What brand/model is the "Hub". I think we're talkin' about the same thing. :)

---

### Post by cparsons on 2005-12-02
a DAYNAstar, 10 speed, 8 port...

---

### Post by cparsons on 2005-12-02
thinking that this is the same thing (hub / router)

i tried to connect following the instructions in the guide you posted, but nothing happened. 

i remember reading somewhere about "samba" (?) and using it through writing in instructions into a terminal.

would that work? how do you do it?
:???:

---

### Post by MetalMusicAddict on 2005-12-02
Got a couple of questions.

How do you get your internet connection? ie: Dial-up, DSL or Cable-modem?

I cant find info on your "hub" and I am a little confused on how they work. Hopefully someone will help with that.

Is there any config app for the hub?

---

### Post by cparsons on 2005-12-03
1, internet connection = dial up
2, hub - i.e cat five cable M-M connects from comp to hub. another cat 5 cable connects from hub to laptop. then that leaves another 6 ports to connect to other items.

---

### Post by MetalMusicAddict on 2005-12-03
Ok. So you XP machine connects through your dial-up modem and is then shared via a network (same pc) and hub. Right? So you want to share the desktops internet connection? I havnt done that in windows in years. But here goes.

I think it would involve going to "Network Connections" in windows. Then right-clicking the modem connection. Properties, then "Advanced" tab. There should be a box that says " Allow other network users to connect..." Click the box.

Post after you see that.  Do you have a IM app? Im on AOLIM. coryisatm

---

### Post by chilebeans on 2005-12-06
cparsons

My problem relates to yours but today both my pc's are connected. Check out the last page in my conversation thread, but better yet, read the whole thing and I think you will figure it out.I will explain the scenario of what happened below. 

XP could connect while Ubuntu did not. 

Was informed to configure router with DHCP server and Client under PPPoE.

PPPoE configurations never connected so I could not assign IP   in PPPoE to set a network with connection through the DHCP.

Learned XP and Ubuntu needs to be automatically connected than. Went to router and configured it with WAN. Under Quick Configuration I typed in Username & Password while using the setting for automatic connection ( PPPoA in my case). Your ISP can provide you the router settings.

So now I had a automatic connection with the DHCP server and DHCP client. Now the whole purpose for the automatic connection was so I was one step closer ( not having to look for the un & pwd) to connecting.

Next I went to Root terminal and typed in the following commands(next post so I can copy and paste it)

---

### Post by chilebeans on 2005-12-06
ifconfig

ifconfig eth0 down

nano /etc/network/interfaces

#auto eth0
#iface eth0 inet dhcp

#auto eth0
#iface eth0 inet static
# address 192.168.1.1
# netmask 255.255.0
# network 192.168.1.0
# broadcast 192.168.1.255
# gateway # 192.168.1.2

/etc/init.d/networking restart

ifconfig

pppoeconf

/etc/resolv.conf

/sbin/ifconfig ppp0

ping ftp.cl.debian.org

ifconfig ppp0

/etc/resolv.conf



you will notice a ping command I did which will not apply to you.So of course you have to use your own ping. You should look under google with a title like I used to find the commands I needed. So type:

"Configuration with PPPoE en Ubuntu and Debian"

The above title got me the right commands. I think you will be able to get your XP and Ubuntu running. This is all I can tell you really because this is what I did. I am a newbie so this is the extent of what I should say...I did...it worked....

---

### Post by chilebeans on 2005-12-06
oh yeah, in the commands type everything you see. So even the: #  number sign you see in the command list

---

### Post by cparsons on 2005-12-09
sorry i have taken so long to get back to you - called away on short notice (grumble)

- chilebeans - sorry, but i don't quite understand this - i am very new at using ubuntu and i have never networked before. sorry!


- MetalMusicAddict - [I]Ok. So you XP machine connects through your dial-up modem and is _then shared via a network (same pc) and hub_. Right? So you want to share the desktops internet connection? I havnt done that in windows in years. But here goes.

I think it would involve going to "Network Connections" in windows. Then right-clicking the modem connection. Properties, then "Advanced" tab. There should be a box that says " Allow other network users to connect..." Click the box.
[/I]

This is the problem, i want to share the printer, internet connection and files BUT i don't have a network yet. it is plugged in to the hub. thats all. i tried networking through the wizard in windows, but it didn't do anything, and i don't know what to do in ubuntu :mad: 

where do i go from here? (lost)

---

### Post by cparsons on 2005-12-09
Actually, seeing as i am lacking any ability to network these together, are there any programmes which will do it for me?

---

### Post by cparsons on 2005-12-13
I have worked out the IP address, gateway and subnet mask numbers for my desktop and have input them into ubuntu. where do i go from here?

---

