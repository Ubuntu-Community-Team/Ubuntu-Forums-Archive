---
title: "a SIMPLE wired home networking set up HOW TO"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by randlieb on 2008-05-13
I have 2 computers both running Hardy. I want to share files between the two. I already have a Linksys wired modem and router set up and an internet connection to both computers is live.

I want a simple (IN PLAIN ENGLISH) step by step HOW TO of setting up so the the two computers can 'talk' to each other.

Please do not tell me to set up/install so n' so WITHOUT EXPLAINING HOW TO DO IT...WHAT STEPS ARE INVOLVED.

If this needs to be put into the 'Absolute Beginner Talk' by the moderators, please feel free. 

I was under the impression that this (setting up a wired home network) was a simple straight forward process.

All thanks and humble gratitude in advance to anyone posting.:)

---

### Post by SpaceTeddy on 2008-05-14
lets see if i can speak plain english (haven't done it for a while) :)

so, i guess what you want is file sharing between two linux boxes - there is NO WINDOWS involved. I only state this because the solution that i am thinking of writing down here will NOT WORK to access windows machines.

I also do not know if there is a simpler way - this is the simplest way i know.

1.) install the openssh-server
to do that, type this command in both computers and let them run through. They may ask you to confirm the installation - say yes !

```
sudo apt-get install openssh-server
```

2.) find out the IP addresses of your computer
this is important to address the computers. use the following command to obtain your computers IP-Address
```
ifconfig
```

this should give you an output just like this one
> eth0      Link encap:Ethernet  Hardware Adresse 00:13:77:04:cd:26  
          UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Basisadresse:0x6000 Speicher:d2800000-d2820000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:992 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:30392 (29.6 KB)  TX bytes:30392 (29.6 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 00:13:02:0f:83:56  
          **inet Adresse:192.168.18.143**  Bcast:192.168.18.255 Maske:255.255.255.0
          inet6-Adresse: fe80::213:2ff:fe0f:8356/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:237037 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200628 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:208782489 (199.1 MB)  TX bytes:22525126 (21.4 MB)



your output can differ quite a bit, but the imporant information is just the bold bit. Thise four numbers are the address of the machine (do not use the 127.0.0.1 address - there must always be a second).
so, in my case the address would be 192.168.18.143.

3.) Access the other computer
Now, when you want to access a computer from the other, go to places -> connection to server. 
 - Choose SSH as the at the service type
 - the server is the IP of the other computer (the one you want to access)
 - the port can be left blank (this means it assumes port 22)
 - the folder you should put in is /home - but you can leave it blank
 - the username *must* be specified. This would be the user you use to log into the other computer.
 - also, enable the bookmark and choose a name for it. This means this connection will always reappear in your places menu and in the sidebar(left) in your filebrowser 

Most imporant - click ok :)
you will then be asked for the password of the user of the other machine. Put it in, and if you do not want to be bothered by this anymore - choose always remember.

Now a folder should open with the folder on the other machine. 

I hope that was simple enough - like i said, i haven't done simple for a long time :)

hope it helps.

---

### Post by randlieb on 2008-05-14
Everything you spell out looks good and logical to me given my (very) brief knowledge of Ubuntu and Linux. I've double checked everything (openssh server is installed on BOTH machines. got the ip address from the ifconfig readout from the machine I want to access). I just cannot get the password window to pop up after filling out the info you described and clicking on 'connect'. Instead I get the following...

[B]Can't display location "sftp://user@192.168.1.101/"

Timed out when logging in[/B]

My Wired Connection in Network Settings in both computers is set to DHCP.

Any ideas???

---

### Post by randlieb on 2008-05-14
Just thought of something. I have Firestarter enabled on both computers. Do I need to do anything to that to allow for local networking?

---

### Post by SpaceTeddy on 2008-05-14
yes, you need to allow ssh connections to the computers. ssh means you need to allow incoming connections on port 22 with protocoll tcp. 

I have never used firestarter (and most likely never will) - but i can tell you the raw iptables command to allow the connection. The problem is that they are not static and will be lost on every reboot...

---

### Post by randlieb on 2008-05-14
I disabled Firestarter in both computers and voila!, I have access. However I want to keep Firestarter enabled on both machines but can't access the 'Local network connected device' parameters under 'Network Settings' in the Firestarter preferences.

Please stay with me. I know I can get this going right.
Thanks for all so far.

---

### Post by SpaceTeddy on 2008-05-14
ok, so i installed firestarter and had a look at it...
i am by far sure what you need to do - but i guess i understand how this thing goes.

under policies (third tab), choose "allowed service" and do a rightclick on it. that will bring up a little windows to allow a service to connect to your computer.

from the dropdown list, choose ssh and let everyone connect to it. It doesn't matter of if it is not restricted to your LAN, since nobody from the outside can acces it anyway. Furthermore, even if they can, ssh is one of the most secure services. So unless you have really weak password, this is not a problem.

if you are not comfortable with that, choose not everybody but network source instead and put in 192.168.1.0/24 - meaning only someone from your internal lan can connect, or put in the ip of the other computer to restrict it even further... 

since i cannot afford to load firestarter on my comp i cannot test the rules - sorry :)

hope it helps

---

### Post by spai on 2008-05-14
> **randlieb said:**
> I disabled Firestarter in both computers and voila!, I have access. However I want to keep Firestarter enabled on both machines but can't access the 'Local network connected device' parameters under 'Network Settings' in the Firestarter preferences.

Please stay with me. I know I can get this going right.
Thanks for all so far.

This is seriously a great co-incidence. I too am trying to connect two home computers for sharing files. However one of them is Ubuntu and the other is on Arch.
In Ubuntu I can even ping myself!:confused:

If I try to ssh on to my own machine, it says port 22 connection refused...
So how do I make my ssh work successfully, open port 22 ?


P.S:randlieb, sorry for intruding in your thread. My problem is exactly like yours. So i did not create another thread... So do you have any ideas? And what is this firestarter?

---

### Post by avtolle on 2008-05-14
Firestarter is a GUI to allow you to control iptables, the "built-in" firewall in Ubuntu.

---

### Post by randlieb on 2008-05-14
> **SpaceTeddy said:**
> ok, so i installed firestarter and had a look at it...
i am by far sure what you need to do - but i guess i understand how this thing goes.

under policies (third tab), choose "allowed service" and do a rightclick on it. that will bring up a little windows to allow a service to connect to your computer.

from the dropdown list, choose ssh and let everyone connect to it. It doesn't matter of if it is not restricted to your LAN, since nobody from the outside can acces it anyway. Furthermore, even if they can, ssh is one of the most secure services. So unless you have really weak password, this is not a problem.

if you are not comfortable with that, choose not everybody but network source instead and put in 192.168.1.0/24 - meaning only someone from your internal lan can connect, or put in the ip of the other computer to restrict it even further... 

since i cannot afford to load firestarter on my comp i cannot test the rules - sorry :)

hope it helps

YES! I have Firestarter enabled and set the rule to allow only the other computer access to each other. Tested by copying some files to each. Everything looks good.

THANK YOU...THANK YOU...THANK YOU....!!!!!! I am going to put together the whole how to and keep it in a file on my computer. WELL DONE!

Ever since I switched to Ubuntu in Aug 2005 as my ONLY OS, I have never failed to get an answer to any and all my problems, questions, concerns via this Forum.

---

### Post by SpaceTeddy on 2008-05-14
glad i could help... 

but i cannot say the same about my question... they usually disapper unanswered... :(

---

### Post by mapes12 on 2008-05-15
I followed this thread and in particular the idiots guide posted above by SpaceTeddy (Thank you!) and can now connect my 2 boxes over my LAN. I think this thread should be posted as a OpenSSH HOW TO Sticky. Excellent advice  \\:D/.

My next task is to see if I can use SSH to transfer files over the interent between my home machines and my son at college. Any suggestions on how to do this please??

---

### Post by SpaceTeddy on 2008-05-15
mhm - yes. But that takes a little more research on your part, as it involves either your son or you to configure your router to do port forwarding. 

In general, your computer is all setup for anyone to transfer files to you or to get files from you. The only thing that is in the way is your little router box inbetween you and the internet. 
You will need to figure out how to do a port forwarding (sorry, i cannot be more specific here, as there are a million different devices, and all them use a different name for it) for tcp port 22 to the ip of the computer that you want your son to connect to.

then reconfigure your firestarter to allow ssh connection from anywhere and no only from one specific IP. But be ware that this will enable anybody to in the internet to attempt a login on your machine via ssh. 
In general, i would not worry about that, since ssh is (mostly) a very secure and good server. So as long as you have proper passwords set, there should not be any reason to worry about it.

Once the port forwarding is set, and your firestarter is reconfigured, you will need to visit a sire like [http://whatismyip.com/]("http://whatismyip.com/") to figure out your internet ip (this does NOT correspond to the IP's you have set on your computer) and tell that to your son. He can then connect to your computer the same way you used to connect your computer (if he has ubuntu) or use winscp (just an example) to connect to your computer if he uses windows. 

hope it helps :)

---

### Post by mapes12 on 2008-05-15
Yep, [http://whatismyip.com/](http://whatismyip.com/) gives an an IP address of 86.147.xxx.xxx (last 2 octets x out for security on forum) which obviously is not the private address on this LAN where DHCP allocates addresses on the class C range of 192.168.xx.xx

How do I configure SSH to not only reach the ISP assigned IP address but then the Private address within the LAN I'm trying to connect to?

---

### Post by SpaceTeddy on 2008-05-16
see my earlier post. That is about as specific as i can explain it... anything more specific requires intense knowledge of your setup and used hardware...

sorry :(

---

### Post by mapes12 on 2008-05-16
Not a problem and many, many thanks for your help in getting me this far  :lolflag:

---

### Post by carloslosgrande on 2008-05-27
[FONT="Comic Sans MS"]Hey SpaceTeddy, I've been looking around and reading thru posts til my head swam and still couldn't make heads nor tails - until now. [COLOR="DarkOrchid"]*simple, worked a treat. Mucho gracias.*[/COLOR]
To anyone else reading this it takes a restart and several attempts for tho process to actually work, but right now I have 2 machines reading each others files.:guitar:[/FONT]

---

### Post by insyte2 on 2008-06-15
This thread was really useful to me. First time for me to use ssh. Connected a desktop and a laptop with Hardy on both. Thanks :)

---

### Post by randlieb on 2008-06-15
This may sound like a REALLY DUMB question but here goes! I started this thread wanting to hook up my own 2 computers and now I have someone who wants me to hook up 3 computers. It looks like this should work for an unlimited number of computers but what do I know?! Tell me if I am wrong (or right). Thanks!!!

---

### Post by Dale Sexton on 2008-06-19
> **randlieb said:**
> hook up 3 computers

I'll be doing the same as soon as I can get the two to work. One computer can get into the other, but not vice-versa. The other is still getting "Cant display location: No route to host". My firestarter is set up right. Any other ideas? 

Dale

---

### Post by Dale Sexton on 2008-06-19
Hmmm.... seems I need to get a stronger prescription on my glasses. That 0 looks like an 8.

Nevermind...   ;)

Dale

---

### Post by greyghost60 on 2008-06-21
Thanks a reaaly good simple how to that works. One small addition is that you need SSH on both machines.

---

### Post by sydbat on 2008-06-21
Absolute and sheer genius! Thank you so much.

---

### Post by tikbjamin on 2008-06-22
Thanks so much.  My first time using SSH. 

I do not wish to have a permanent nor even long term connection.  How do I close the connection?

---

### Post by unutbu on 2008-06-22
To close the connection, simply type

```
exit
```
in the terminal where you had before typed 
```
ssh user@host
```

If you made an ssh connection using Places>Connect to Server, then go to Places>Network. This will open a nautilus window. Right-Click on the name of the connection you wish to close. Select "Unmount volume".

You can right-click + "Unmount volume" in a variety of places, actually. You can also do that in any nautilus window that has the name of your connection. For example, in the left side panel. Also, an icon representing your remote connection's filesystem may appear on your desktop. You can right-click+"Unmount volume" that too.

---

### Post by tikbjamin on 2008-06-22
Thanks all.

tikbjamin

---

### Post by Dale Sexton on 2008-06-22
> **tikbjamin said:**
> I do not wish to have a permanent nor even long term connection.  How do I close the connection?

It's like I told the cat that followed me home.

Shoo kitty!

---

### Post by mamboze on 2008-12-13
> I hope that was simple enough - like i said, i haven't done simple for a long time :)

hope it helps.


Thanks, it worked and it was simple enough. Another satisfied customer :)

---

### Post by macjorgen on 2009-09-15
thanks guys. utterly awesome:) ssh rocks!

cheers
macj

---

### Post by tahitiwibble on 2009-09-20
Thanks a million Space Teddy, it works beautifully! You're a champ!

---

