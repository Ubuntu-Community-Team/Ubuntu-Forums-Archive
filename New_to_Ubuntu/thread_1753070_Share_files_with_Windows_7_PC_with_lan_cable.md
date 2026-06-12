---
title: "Share files with Windows 7 PC with lan cable"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by N_L on 2011-05-08
(11.04 version)
2 different ones actually.
First I did it with laptop, I downloaded samba and got it to work easily, could see each other and all but the speed I was getting was terrible, around 300-350 kbps! I messed with samba config file, raised tpc thing etc but I could only get few dozen KB more so I gave up since it would take a lot of hours to move these 20 gb.

Then I got home and tried it with my PC, I messed samba up and spent few hours now fixing it and I'm back at start. My Windows doesn't see ubuntu(laptop) yet I see windows on ubuntu. I tried copying file from PC and it went ~700kbs, and to there ~1-1.2mbs which is still very slow.


Anyone got any thoughts how to do this as painlessly as possible so I don't spend hour(s) first trying to figure out why they can't see eachother and why is the speed so slow? It's not the cable, I've used same cable on same pc and laptop(although older ubuntu version) and speed was fine, gonna try with windows laptop and PC just to make sure, and then again windows laptop and ubuntu laptop to check again to be sure that everything's fine hardware wise.

---

### Post by speedrcj on 2011-05-08
The post is a bit confusing, but have you tried pinging everything to make sure you have connectivity?

in command line type "ping <ip>" and see if you get a response.  

To find your IP in Ubuntu open the terminal and type "ifconfig" and look for a field titled "inet addr".

In Windows, Start>Run type "cmd" then in the command line type "ipconfig "

as far as speed goes,  if you've got a lot of traffic on your switch and it's only 10/100 it could potentially slow down quite a bit.  Are you doing this on a LAN? or over the interwebs?

---

### Post by RedRat on 2011-05-08
Win7 only recognizes NTFS partitions. You need a special little program to run on your Windows machine so that you can read the various Ubuntu partitions. Can't remember the program right now, perhaps someone can help here. Make sure that your Windows permissions are all OK so that others can see it. MS changed the network security in Win7, not the same as Vista and XP.

---

### Post by N_L on 2011-05-08
I'll try ip stuff soon, having more trouble now getting 2 windows 7 to share files between eachother..

But as for seeing ubuntu stuff, I already did this morning with friend's laptop who I tried transfering folders from. He could see me and open my shared files and I could access his whole computer and now at home my Win7 doesn't see ubuntu and I can access some files on it through ubuntu.

Yeah I guess this is bit confusing hm

---

### Post by speedrcj on 2011-05-08
> **RedRat said:**
> Win7 only recognizes NTFS partitions. You need a special little program to run on your Windows machine so that you can read the various Ubuntu partitions. Can't remember the program right now, perhaps someone can help here. Make sure that your Windows permissions are all OK so that others can see it. MS changed the network security in Win7, not the same as Vista and XP.


This is only an issue if he's physically taking the drive out of his linux machine and putting it into Windows.  Over Samba share, it doesn't matter what the file system is.

---

### Post by RedRat on 2011-05-08
> **speedrcj said:**
> This is only an issue if he's physically taking the drive out of his linux machine and putting it into Windows.  Over Samba share, it doesn't matter what the file system is.
Oops, I think I misunderstood. I thought that his Win7 machine was not recognizing the Ubuntu machines. I know I had to install this little program (forgot its name) on my XP machine to read the Ubuntu files on my Ubuntu machine running 8.04. Ubuntu has no problems reading and writing to NTFS partitions.

---

### Post by N_L on 2011-05-08
> **speedrcj said:**
> The post is a bit confusing, but have you tried pinging everything to make sure you have connectivity?

in command line type "ping <ip>" and see if you get a response.  

To find your IP in Ubuntu open the terminal and type "ifconfig" and look for a field titled "inet addr".

In Windows, Start>Run type "cmd" then in the command line type "ipconfig "

as far as speed goes,  if you've got a lot of traffic on your switch and it's only 10/100 it could potentially slow down quite a bit.  Are you doing this on a LAN? or over the interwebs?
I'll recap what I'm trying to do.
I have crossover ethernet cable, I need to transfer ~20gb and I figured it would go faster this way then via USB flash drive. So I connected my laptop, which has ubuntu on it and friend's laptop which has win7 on it.
I downloaded samba and some stuff, enabled file disovery on win and it all went file, except the speed was ~350kbs so it was very slow. Only thing I was doing and as I changed settings it would raise a bit so I'm sure it's some settings problem. So  this is my first problem.

Then I came home and connected ubuntu laptop with my main PC which also has Windows7 on it, did all the same things but this time I couldn't see ubuntu in network while on PC, but ubuntu could see PC's folders, and this is my 2nd problem. Which is fine I guess since I can work around it but again speed was slow. Only 1mbit when copying to or ~7kbs when copying from, again only  trying to do this so no load on network at all.

Then I tried 2nd laptop with windows 7 and my pc and couldn't get these two to work either... And now finally trying my ubuntu laptop with another windows7 laptop and I can't get it to work either. I can ping it and it works both ways but they don't see eachother in network :S 
Could also ping ubuntu and main pc and it worked :/ tried fixed IP and automatic but nothing worked.

Meh, why can't this be simple... I just want to plug damn cable and transfer files over fast and that's it -.-

---

### Post by speedrcj on 2011-05-08
hmmmm... try opening the folder browser in windows and navigate to \\<ip of samba share>/<name of share>/ and see if it finds it that way.  It might just be stupid Windows workgroup thing that I don't understand.  Good luck!

---

### Post by N_L on 2011-05-08
> **speedrcj said:**
> hmmmm... try opening the folder browser in windows and navigate to \\<ip of samba share>/<name of share>/ and see if it finds it that way.  It might just be stupid Windows workgroup thing that I don't understand.  Good luck!
I did try but got some bs errors, I've stopped trying now after 5+ hours, I need a break from this. Why can't it be simple, why...

I've googled and googled but to no end, if anyone can give me a good guide that will work for 11.04 <=> win7 to try I'd be greatful, don't know what else to do.
Any other way to share large files fast?

---

### Post by N_L on 2011-05-10
Any ideas, took me a long time to transfer them with usb sticks, would rather fix this and do it proper :/

---

### Post by New00Folder on 2011-06-05
I've also searched for a solution to this problem many times... and I've been frustrated always. I'd appreciate if someone would tell me how to transfer files to/from an Ubuntu machine with samba from/to other Ubuntu/Windows machines using only a LAN cable.

Just plugging in the wires doesn't work. The only thing in Network places are my own shares. On the other hand when the machines are connected to a public network like my college's wi-fi network I can access the shares on any machine without a problem except that the transfer speed is less than 1MB/s.

---

### Post by RedRat on 2011-06-05
> **New00Folder said:**
> I've also searched for a solution to this problem many times... and I've been frustrated always. I'd appreciate if someone would tell me how to transfer files to/from an Ubuntu machine with samba from/to other Ubuntu/Windows machines using only a LAN cable.

Just plugging in the wires doesn't work. The only thing in Network places are my own shares. On the other hand when the machines are connected to a public network like my college's wi-fi network I can access the shares on any machine without a problem except that the transfer speed is less than 1MB/s.i
I may be thinking of something else here,but don't you need a "crossover" connector when connecting two computers that way? I may be confused, but I suspect maybe that is part of the problem.

---

### Post by speedrcj on 2011-06-05
> **RedRat said:**
> i
I may be thinking of something else here,but don't you need a "crossover" connector when connecting two computers that way? I may be confused, but I suspect maybe that is part of the problem.


You definitely need a crossover cable when connecting two computers without a switch between them.  The OP says he was using a crossover cable already, but anyone else reading this you definitely need one in that case.

---

### Post by alphacrucis2 on 2011-06-05
> **speedrcj said:**
> You definitely need a crossover cable when connecting two computers without a switch between them.  The OP says he was using a crossover cable already, but anyone else reading this you definitely need one in that case.

They also need to make sure that the two machines have ip addresses in the same subnet otherwise it won't work. I think if no DHCP server is available, Windows makes up an address in 169.x.x.x. Check on Windows via the Windows command prompt:

```
ipconfig
```

In Ubuntu to see the address being used at the Ubuntu end:

```
ifconfig
```

Make sure the addresses assigned to the ethernet connection at each end are in the same subnet. If not then change the Ubuntu end to set an address in whatever subnet Windows is using (or visa versa)

---

### Post by New00Folder on 2011-06-06
Hi Alphacrucis2!

You are right about different subnets. Windows had ip address like 192.xxx while ubuntu's ip was 169.xxx

To set ip address manually using network manager I need to give values for default gateway, subnet mask and DNS server as well. I guess subnet mask would be 255.255.255.0. But what should I put for other addresses?

---

### Post by alphacrucis2 on 2011-06-06
> **New00Folder said:**
> Hi Alphacrucis2!

You are right about different subnets. Windows had ip address like 192.xxx while ubuntu's ip was 169.xxx

To set ip address manually using network manager I need to give values for default gateway, subnet mask and DNS server as well. I guess subnet mask would be 255.255.255.0. But what should I put for other addresses?

With a point to point connection that doesn't go anywhere except the two PC's on either end of the cable, there is really no default gateway, so you don't need, or want one in this case. If it forces you to enter something, which it should not, just enter the address of the other PC as the dgway. There are no DNS servers in this scenario either unless you are running a DNS server on one of the two PC's. If you want to use names then you can add entries into /etc/hosts file on ubuntu. There is an equivalent file in windows under c:\windows\system32\drivers\etc\hosts - Note that the exact folder might be different in different versions of windows but it should not be too difficult to figure it out.

---

### Post by New00Folder on 2011-06-06
Thanks a lot alphacrucis2. It worked as you said.
I'm getting 11-12 MB/s transfer speed which is good enough.

---

### Post by crispy_420 on 2011-06-07
So no longer interested in a proper samba share? Or you only looking to move the files?

Do you have a router at home?

---

### Post by alphacrucis2 on 2011-06-07
> **crispy_420 said:**
> So no longer interested in a proper samba share? Or you only looking to move the files?

Do you have a router at home?


I believe he did use Samba. The issue was getting the underlying tcp/ip connectivity working

---

### Post by speedrcj on 2011-06-07
> **New00Folder said:**
> Hi Alphacrucis2!

You are right about different subnets. Windows had ip address like 192.xxx while ubuntu's ip was 169.xxx

To set ip address manually using network manager I need to give values for default gateway, subnet mask and DNS server as well. I guess subnet mask would be 255.255.255.0. But what should I put for other addresses?

Doh!  It's always the easy stuff.  Glad someone had the sense to ask the simple questions first =)

---

### Post by miscellanyous on 2012-01-06
> **alphacrucis2 said:**
> They also need to make sure that the two machines have ip addresses in the same subnet otherwise it won't work. I think if no DHCP server is available, Windows makes up an address in 169.x.x.x. Check on Windows via the Windows command prompt:

```
ipconfig
```

In Ubuntu to see the address being used at the Ubuntu end:

```
ifconfig
```

Make sure the addresses assigned to the ethernet connection at each end are in the same subnet. If not then change the Ubuntu end to set an address in whatever subnet Windows is using (or visa versa)

Thanks that's very helpful. 

I have a strange problem though. My ubunutu shared folder works and I can read/write to it from the windows box. But The ubuntu box doesn't see the windows shared folders.

More strange, I can ping from the windows box to the ubuntu box just fine. But I cannot ping from the ubuntu box to the windows box.

Here's the **ifconfig** status on ubuntu box:
inet addr: 192.168.100.1 Bcast: 192.168.100.255 Mask: 255.255.255.0

And here's the **ipconfig** from the windows box:
IP Address: 192.168.100.200
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.100.1

What can I try to mount the windows shares on the ubuntu box?

---

### Post by speedrcj on 2012-01-07
> **miscellanyous said:**
> Thanks that's very helpful. 

I have a strange problem though. My ubunutu shared folder works and I can read/write to it from the windows box. But The ubuntu box doesn't see the windows shared folders.

More strange, I can ping from the windows box to the ubuntu box just fine. But I cannot ping from the ubuntu box to the windows box.

Here's the **ifconfig** status on ubuntu box:
inet addr: 192.168.100.1 Bcast: 192.168.100.255 Mask: 255.255.255.0

And here's the **ipconfig** from the windows box:
IP Address: 192.168.100.200
Subnet Mask: 255.255.255.0
Default Gateway: 192.168.100.1

What can I try to mount the windows shares on the ubuntu box?

This is probably due to the enhanced win7 security.  I think it's kinda stupid to turn off the ability to ping by default but... whatever.  

1.) Open up the network and sharing center
2.) On the left hand side go to "Advanced Sharing Settings"
3.) The 2nd option down is "Turn On File And Printing Sharing".  This has to be enabled to get a ping, and I think also it will also block connections to the shares that aren't in the same "Workgroup".  I never completely figured out Windows sharing settings =)

---

### Post by miscellanyous on 2012-01-08
> **speedrcj said:**
> This is probably due to the enhanced win7 security.  I think it's kinda stupid to turn off the ability to ping by default but... whatever.  

1.) Open up the network and sharing center
2.) On the left hand side go to "Advanced Sharing Settings"
3.) The 2nd option down is "Turn On File And Printing Sharing".  This has to be enabled to get a ping, and I think also it will also block connections to the shares that aren't in the same "Workgroup".  I never completely figured out Windows sharing settings =)

Excellent - thanks! It turned out this was not exactly it. Rather, some security antivirus software that was running an **extra** firewall. After I disabled the firewall everything's copacetic.

---

