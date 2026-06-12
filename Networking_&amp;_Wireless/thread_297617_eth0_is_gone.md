---
title: "eth0 is gone"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by cotn on 2006-11-11
Hi, 

I have posted this thread also here [http://www.ubuntuforums.org/showthread.php?t=296517](http://www.ubuntuforums.org/showthread.php?t=296517)

But I think it maybe fits better in here. And because I could't get any help I try it here.
It's very important to me do get the system running the way it was... Or better :)


A few day's ago I did an apt-get upgrade and somehow it went wrong by installing: pyhton-2.4.

The error message say's "The following packages have unmet dependecies: python2.4-examples, python2.4-gdm, python2.4-tk"
It depends python 2.4.1-2 and I have python 2.4.1-0 installed.

After that I did by accident a reboot and I shouldn't. My eth0 device is totally gone. I even cant find him in /dev. So ifup fails.

When I do lspci I can see my ethernetcard in the list but I can't alias him. (because eth0 is not in de /dev list.) 

Since I don't have a network connection, I can't get new sources to fix python or do anything.

What should I do ?
Any Idea to bring back my eth0 will do. 
From there I think I can figure out the rest.

---

### Post by spd106 on 2006-11-11
Do you know which driver the card uses? It should appear under **lsmod** if it is loaded. Perhaps post the output, and of **ifconfig** and **lspci** as well, so that we can see.

---

### Post by cotn on 2006-11-11
Okay, 

Because I have no network connection I cannot copy and paste the returned results so I have to type it over. Therefore I only write down some snippets. To type it all over is a hell of a job :D.

If you need more information, offcourse I will provide but I think these are the most important issues:

> lsmod |grep eth 
Doesn't give a satisfying result. Response is nothing.

> ifconfig and ifconfig -a
Responses only results for "lo" and "sit0 (only with ifconfig -a)". eth0 doesn't show up in the list.

> lspci
Shows my ethernetcard:
0000:03:10:0 Ethernet controller : Realtek Semiconductor Co., Ltd. RTL-8139/8139c/8139C+ (rev 10)

> ifup -a
Tells me: 

```

ifup : interface lo already configured
SCIOSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SCIOSIFNETMASK: No such device
SCIOSIFBRADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0

```

(yes typed it over)

---

### Post by cotn on 2006-11-11
When I do, 'less /proc/modules',  no ethernet device or something what refers to it is in here. Correct me if I'm wrong but it should be, right?

Also dmesg doesnt refer to ethernet devices, no errors no messages, nothing.

> modprobe eth0 
FATAL : Module eth0 not found

aaargh...

---

### Post by cotn on 2006-11-11
Ok. I have done some further research and I think the only option for me is to recompile the kernel with the eth0 module (somehow). Now I never have recompiled a kernel before and because I have no eth0 module, I'm afraid that I can't compile to the same kernel with the eth0 module. 

And the next question is; if it's possible, how will it affect my whole enviroment and settings?

Is the only solution then to reinstall a new fresh Ubuntu ? :S 

Please help me out here...

---

### Post by cotn on 2006-11-12
](*,) damn

---

### Post by bjd on 2006-11-12
Recompiling your kernel should not be neccesary. 
what happens if you do: *sudo modprobe 8139too*

---

### Post by cotn on 2006-11-12
Thanks four your repley.
Nothing happends, no error's no messages.

But after that I did ifdown -a, ifup -a and it looks like my eth0 was back.

**The folloing messegas are gone** :D
```

ifup : interface lo already configured
SCIOSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SCIOSIFNETMASK: No such device
SCIOSIFBRADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0

```

I thougt I das done this a trillion time the past few days but apperrently I must have something done wrong. 

Thanks eyh!

Eth0 shows up also in my ifconfig again but I can't ping other pc's in or outside my network. :(

---

### Post by bjd on 2006-11-12
ok, so it appears the device is not configured.
What is in /etc/network/interfaces ?
Also you could try to go to *System Settings->Network Settings->Network Settings->Network Connections* (*at least that's what it's called in Kubuntu 6.10)  and (re)configure eth0.

---

### Post by cotn on 2006-11-12
I only use the shell, because I have closed down the GUI a long time ago. I only use it as a web/file server instead of a desktop. 

```

> cat /etc/network/interfaces 

#The loopback network interface
auto lo
iface lo inet loopback

#This is a list of hotpluggable network interfaces
mapping hotplug
script grep #dunno what this is doing here. don't know what it does
map eth0

#The primary network interfaces
iface eth0 inet static #it's a server so I don't want DHCP
network 192.168.0.0
broadcast 192.168.1.255
dns-nameservers 192.168.1.1
adress 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```

---

### Post by bjd on 2006-11-12
That looks alright, other than that the auto eth0 is usually above the iface eth0 line, but i don't know if that's really required. You could try to move that auto eth0 line, but otherwise it looks as if it should work..

---

### Post by spd106 on 2006-11-12
It looks like the network line is wrong, change it to 192.168.1.0, or comment it out since it's not needed.

---

### Post by cotn on 2006-11-12
Hmm I did both things. but when I ping my router or [www.google.nl](www.google.nl) I receive the message: "Destination Host unreacheble"

Let's see what happends when I reboot my router

---

### Post by cotn on 2006-11-12
Okay.... Me and my stupid dumb *** plugged my cable in the wrong network card.. :-D 

But now it works !! I'm very thankfull for both of your help.
Oh and just one question: 
If I want my second ethernetcard to be eth1, I just do
modprobe "codeformyethernetcard" and eth1 is aliassed to my second networkcard ???

Again thanks !

---

### Post by cotn on 2006-11-12
hmm it's not allowed to say *** ?? :)

---

