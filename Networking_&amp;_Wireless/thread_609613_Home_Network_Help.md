---
title: "Home Network Help"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by sgtbob on 2007-11-11
I've googled, yahooed, Linuxed, Ubuntued, searched, etc., for a detailed step-by-step set of instructions on how to hard wire via a crossover cable, a Dell XPS 400 and a Dell 8250, each with NIC cards installed.  I have a number of books but most of them infer (1) Wireless (2) hubs and neither is what I need.

The responses I've read and/or received have never discussed a straightforward method to do this. I followed more blind alleys than Fred Allen (old timers will remember this radio show) and most of these devolve into techo-babble that I am unable to follow. One 'simple' site I was directed to had 64 pages of detailed instructions on the entire IP numbering system, but never got around to anything that could be used to actually set up the home network using a crossover cable. :(

Can anyone provide a  straighforward set of instructions?  Hopefully these would address in 'noob' terminology: (1) crossover cable is plugged into each of the NIC's;  (2) using 'terminal' type i[COLOR="Red"]fconfig[/COLOR]...... on XPS 400................... (3) well you get the picture that this 'noob' is trying to find detailed instructions without becoming an electronics engineer.

Any positive assistance would sure be appreciated.

Bob:confused:

---

### Post by Peter09 on 2007-11-11
not easy without the correct tools

---

### Post by SpiritIsReality on 2007-11-11
howdy
You could try A No-Network Network here, and then see the At Home. The headings are on the left hand side of the page, in red. At Home is just under half way down. The No-Network is a little further down. any help?
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm) and the contents page [http://aboutdebian.com/contents.htm](http://aboutdebian.com/contents.htm)
links
[http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
trails
At the top of your screen, click System > Help and Support > Advanced Topics > 
Installing Server Applications > Ubuntu Server Guide Ch.4 might help

---

### Post by sgtbob on 2007-11-13
Thanks guys but I had read lots of the data suggested and still am having trouble understanding the technical stuff.  Its all right to know about IP address technical data, but what I want is a clue on how to assign for example an address for PC1 and another for PC2 and have them talk to one another so I can see what PC2 has on it from PC1.  Is that even possible?  I already have both PC's with internet access through a router to the cable modem and that I understand.  But how do you assign IP data? What are teh entries I need to make in the terminal to change which specific file?

In using Ubuntu 7.10 I am able to access the Windows XP on each of the boxes from Ubuntu, i.e., open a windows .doc file into Ubuntu, work on the file  with as .odt and then save it back to the Windows box.  I would like to have the ame ability when on PCI Ubuntu, to access PC2 Windows data. Is that even possible?

Here  if my ifconfig on PC1:

[B]bob@XPS400:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:72:11:7E:CA  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe11:7eca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:9989034 (9.5 MB)  TX bytes:513726 (501.6 KB)
          Base address:0xcce0 Memory:fe3e0000-fe400000 

eth1      Link encap:Ethernet  HWaddr 00:04:5A:58:69:E2  
          inet6 addr: fe80::204:5aff:fe58:69e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:468 (468.0 b)
          Interrupt:20 Base address:0xbc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:47 errors:0 dropped:0 overruns:0 frame:0
          TX packets:47 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27197 (26.5 KB)  TX bytes:27197 (26.5[/B] KB)


So what does the above tell me? and how do I use it? 

Please be specific, I do appreciate the reply, but I'm a 'non-geek' and although can speak a couple of language, techno-speak is apparently beyond my ability. :-)

Bob

---

### Post by SpiritIsReality on 2007-11-13
howdy
At the top of the screen, click System > Administration > Network . Hopefully you will see two wired connections. Click on the top one, and click Properties. Read what it says at the top of the window. eth0 or eth1. If you want to keep the eth0 as 192.168.1.100 static, click the expansion arrow at Configuration, select Static IP address,  and then fill out the boxes so that they read, from
eth0 Link encap:Ethernet HWaddr 00:13:72:11:7E:CA
inet addr:192.168.0.100 Bcast:192.168.0.255 Mask:255.255.255.0

Configuration Static IP address
IP address 192.168.0.100
Subnet Mask 255.255.255.0
If you have not changed your router's address, it will most likely be 
192.168.0.1 if a d-link
192.168.1.1 if a linksys, and I think netgear too. If you have the manual, it will be in there.
Type the address of your router (that leads to the internet) in the gateway box.

Is eth1 connected to anything? It will be the network card (nic) closest to the floor in the tower.

Windows xp nic card configuration can be found here
xp configure nic [http://www.google.ca/search?hl=en&q=...G=Search&meta=](http://www.google.ca/search?hl=en&q=...G=Search&meta=)
[http://www.microsoft.com/windows/pro...a/default.mspx](http://www.microsoft.com/windows/pro...a/default.mspx)
[http://windowshelp.microsoft.com/Win...windowsxp.mspx](http://windowshelp.microsoft.com/Win...windowsxp.mspx)
[http://www.microsoft.com/windows/pro...p/default.mspx](http://www.microsoft.com/windows/pro...p/default.mspx)

Please post back and let us know how you make out.
trails

---

### Post by tommynz1975 on 2007-11-13
sgtbob...  I fully understand why you started this thread.. is all good to learn the full nuts and bolts, but one just needs to be spoon feed in creating a basic network..  then be able to have an explanation of what each step did/does.. I have a dram of creating my own server and network.. so I can log onto my account from any computer.. then publish a no-nonsense book on how I did it... then explain at the end of the book what every step ment.. I wish you well best of luck.....

---

### Post by SpiritIsReality on 2007-11-13
3or4links
Unified documentation site - I need your input [http://ubuntuforums.org/showthread.php?t=579726](http://ubuntuforums.org/showthread.php?t=579726)
Documentation of Ubuntu [http://ubuntuforums.org/showthread.php?t=602668](http://ubuntuforums.org/showthread.php?t=602668)
Networking And Wireless Documentation Links [http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608751&highlight=documentation)
LTSP Documentation Links [http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=documentation)

---

### Post by SpiritIsReality on 2007-11-14
in the attachments at the bottom of the post, 
the first shows a crossover cable hooked to the nic cards of two comps. A crossover cable can do that, a straight cat 5 ehternet cable can not.(that's why they call it a crossover cable)
the second and third show comps networked together with straight cat5 cable.
[http://en.wikipedia.org/wiki/Crossover_cable](http://en.wikipedia.org/wiki/Crossover_cable)
cat5 cable [http://en.wikipedia.org/wiki/Category_5_cable](http://en.wikipedia.org/wiki/Category_5_cable)

[http://www.google.ca/search?hl=en&q=linux+networking+beginner&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=linux+networking+beginner&btnG=Search&meta=)
[http://www.google.ca/search?as_q=linux+networking+beginner&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.ca/search?as_q=linux+networking+beginner&hl=en&num=10&btnG=Google+Search&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by sgtbob on 2007-11-14
Spirit - Ok I understand the basic setup shown in the first scene at the bottom of your last post - that showing a crossover cable hooked to the nic cards of two computers. (BTW - how did you get those neat thumbnails to show at the bottom of your text?) This is the system I propose until I learn more about the options. Regarding the otherr two options you show, I am on cable  - no DSL or dial up and I want to leave those until later to try. Setting up each PC's codings at the moment is the bottleneck I am facing.

Now,  In going to 'System --> Administration --> Network' and then selecting the first option (which says it is eth1) and clicking on 'properties' I find another box pops up entitled 'eth1 properties' and a selection of 'enable roaming mode'.  If I exit at this time nothing appear to me to have changed.  

If I 'unclick' this 'enable roaming mode', it appears that data is to be entered for the 'Connections Settings'.  There are now four boxes -  'Configuration', 'IP Address', 'Subnet Mask', and 'Gateway Address'.  Clicking on the down arrow for 'Configuration' brings up three selections 'static IP Address', 'Automatic configuration (DHCP)',  and Local Zeroconf Network (IPv4 LL)' - none of which I have a clue!

To further complicate me, clicking on 'help' brings up a set of instructions that do not coincide with the screen details I see.  Most confusing!

---

### Post by sgtbob on 2007-11-14
Tommyz1975 - I haven't the faintest clue as to what you are trying to do to help me understand this problem, but I appreciate your response.:confused:

---

### Post by SpiritIsReality on 2007-11-14
howdy
Post Reply > Post Reply Page > scroll down the page and see a button marked Manage Attachments, click on Manage Attachments > click a Browse Button > navigate to an image or file, > Open > Upload. and "bob's your uncle" ! (an english expression, I don't really know what it means other than it means success. I like 'you're in the saddle" meaning something the same as 'back in the saddle again" meaning something along the lines of success, as opposed to being bucked off = not in the saddle.) I'm sorry I'm not able to come up with the "right stuff" to get us "on the road" (on the road again..just can't wait to get on the road again...I saw willie in kamloops just this past summer) OK, if you could please send me a picture, ...yes you do..have to draw me a picture.... we can get this
show on the road. 
click Applications > Graphics > Gimp 
You should see a few windows open up. In the bottom of the screen, you will see three gimp heads. click on Gimp. In the Gimp window, click File > New > and click OK in the window that opens.> the window that opens will be a plain white box, titled Untitled.
Now, in the window called Gimp click on the pencil, then click on the Brush: dot, and choose the size of lead (haha!) the caliber you would like to draw (shoot) with. In the Untitled window, please draw me a picture of what it is you're lookin to do, or take a picture of your setup at home with a camera (digital) and post them as attachments and we'll see what we can do, one step at a time, step by step . .. ... ...
..._ got it?
or what would you like to try to solve this . This is your thread, you're the boss, I'm just waiting to hear orders.
[http://en.wikipedia.org/wiki/Buffalo_soldier](http://en.wikipedia.org/wiki/Buffalo_soldier)

---

### Post by sgtbob on 2007-11-14
I'll give this a try and get back to you.

BTW - Since I see the Buffalo Soldier emblem on your site, are you near FT. Leavenworth, KS and have you visited the Buffalo Soldier monument?  Very impressive setting. We see it quite fequently when we visit the post.

Bob

---

### Post by SpiritIsReality on 2007-11-14
No I haven"t been to the monument. I've been as close as Arizona, and Florida., but if you send me your address on a non refundable round trip bus ticket I'll come down there and help you get your network up and runnin and then maybe we could go see it together.
I want more than lunch to get your network up and runnin' partner.I just read that last sentence and it didn't come out right. What I mean is that if I could make a deal with Spirit that if I skipped lunch, you could get your network set up, it'd be no skin off my a##! I'd do it in a heart beat. The reason I kind of like that crest and name, is it reminds me of well, you. And I'm a buffalo rancher, so you can see how it appeals to me?
If there was only one word that I was allowed to say, before the curtain falls, it's be 


NUTS!!!

---

### Post by SpiritIsReality on 2007-11-14
Where did you buy your rigs?
If I was the guy that you bought them from I'd be more than willing to help you get them networked.
Could you check around? Computer store that has the same Spirit as you.
trails, pard
If you could ask at a computer store that does network custom work , or maybe check at the highschool or the university and ask if one of them would show you?
If you can get them to help you with the hardware, then post back here, WE"LL TALK. I mean that once your hardware is strung together, then this forum has got to be the best place to be. It's the best place to be regardless, but you just happened to get the wrong guy answering your post as far as being able to guide a soldier by clicking on a typewriter. I have trained some guys that were in the British Army how to pack horses. After they finished that they were posted to Ireland.Captain Parker was a hell of a guy.
One of the guys said there was an officer inspecting the troops, who were all lined up, for inspection, and the officer made the mistake of askin' one of the guys what he was lookin' forward to doin' after his time in the service. The guy said, takin' a sh## without a shovel, Sir!
Computer tech school in the phone book or ?
Computer store that holds night classes?
[http://www.google.ca/search?hl=en&q=texas+computer+networking+nightschool&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=texas+computer+networking+nightschool&btnG=Search&meta=)
What do you think
[http://www.google.ca/search?hl=en&q=texas+computer+retailers&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=texas+computer+retailers&btnG=Google+Search&meta=)
Here's where I'm at [http://maps.google.ca/maps?oe=UTF-8&hl=en&tab=wl&q=](http://maps.google.ca/maps?oe=UTF-8&hl=en&tab=wl&q=) type in the box, kamloops bc canada. > click maps> once it's finished loading, you can zoom out by clicking the minus sign. You ever tried google earth. man that's great stuff.You don;t have to click that link. At [http://www.google.com](http://www.google.com) click maps.
PALS

---

### Post by SpiritIsReality on 2007-11-14
[http://ubuntuforums.org/showthread.php?t=608738#post3744324](http://ubuntuforums.org/showthread.php?t=608738#post3744324)
[http://ubuntuforums.org/showthread.php?t=484846&page=5#post3454166](http://ubuntuforums.org/showthread.php?t=484846&page=5#post3454166)

---

### Post by SpiritIsReality on 2007-11-14
some guide I am, I just realized you're not from texas. and i'm too lazy to do the searches for  night school and colleges again, so click on the links and change texas to kansas. Sorry about that. Holler if you find anything. Holler if you don't find anything.
You want to know what I learned about packin horses? They're heavy. haha!
[http://www.google.ca/search?hl=en&q=joe+back+%22horses+hitches+and+rocky+trails%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=joe+back+%22horses+hitches+and+rocky+trails%22&btnG=Google+Search&meta=)
that's what.

---

### Post by sgtbob on 2007-12-01
Status at present:
(1) I gave up on the crossover cable - couldn't make it work;
(2) I set up my Broadband Router with PC1 and PC 2 hooked to the Router and then a cable from the Router WAN outlet to my Cable Modem;
(3) I then set up the 'Network' (I think)  for PC1 with IP address as 192.168.0.1 and on PC2 with IP address as 192.168.0.2;
(4) I  made a 'share' folder in each PC and set permissions as 777 on each share folder in each PC;
(5) when I 'ping' from either PC, I see that data is transmitted and received so I presume they 'see' each other;

Observations:
(1) when I attempt smb://192.168.0.2 from PC1 or smb://192.168.0.1 from PC2, it tells me there is no such file;
(2) In addition, with the PC's set up thusly, access to the internet is lost.

Conclusion:
(1) Networking is an illusion; and/or
(2) I'm too dense to comprehend how to set up and use;

Can someone tell me where I am going wrong in non-geek terms, I do not know what SSH is, so that is no help.

Please advise

Bob :confused::confused::confused::confused:

---

### Post by koenn on 2007-12-01
I'm quite terrible at "non-geek" explanations, but I'll have a go anyway. 

First Thing I don't understand why  you're so hooked on having a crossover between the 2 pc's, requiring a 2nd NIC,  while you could just - as you have now - plug everything into a  router with multiple LAN ports an be done with it. 

Given that you can ping between the 2 PC's, both are networked together. Therefore 
a/ networking is not an illusion
b/ the reason you can not transfer data is probably due to your samba configuration (~'how you set up file sharing') or a permission issue (the user on PC1 has no permission to read files on PC2

Could you explain what you're trying to do, a bit of your reasoning on how you want(ed) to do it, and possibly a drawnng of what is where and how they're connected  / how you want them to be connected  + basic configuration so far (like the ifconfig output you posted, but for both PC's - and what's the router's address ?)

---

### Post by jonandrews on 2007-12-01
If , as the previous post suggests, you do have a functioning network connection, you might like to read my step-by step networking guide for Ubuntu / XP machines....

[http://www.europe.eclipse.co.uk/Ubuntu/](http://www.europe.eclipse.co.uk/Ubuntu/)

which tells you what should happen at each stage of the process, along with screenshots.

---

### Post by sgtbob on 2007-12-01
I have made an attachment explaining what I hope will give sufficient information to see what I am trying to do. The sketch is my feeble attempt to show the setup.

 Bob

---

### Post by koenn on 2007-12-02
OK, that helps.

Here's a couple of commands you have to run to verify that your network is functional. Networkin works in layers : you need to have network connectivity before you can share files over the network, so we check the network first.

On both pc1 and pc2 , while running linux :
check local network
```

route -n
ping  -c4  [ipaddress of other PC]

```

check internet access (you may have to 'sudo apt-get install traceroute' first)
```

ping -c4 www.google.com
traceroute www.google.com

```

route will show the router/gateway address the pc's are using. The rest is just basic connectivity testing.

You may want to do the same while running windows, 
click start -> run,  type cmd.exe, hit enter. you get a command prompt. run these commands :

```

ipconfig /all
ping (ipadress of other pc)
ping (ipaddress of default gateway shown in ipconfig output)
ping www.google.com
tracert www.google.com

```

copy&paste the output in a text file so you can review them afterwards, or post them here.

since you're dual-booting, it's woth checking that the ip address of the pc's is identical under Windows and Linux. 

Also  note that your PC1 ip address seems to be changing (and we can thus assume that this may also be the case for pc2)

ifconfig in post #4 says :    inet addr:192.168.0.100 
ifconfig in setup.odt says :  inet addr:192.168.0.101


if you're getting a different address every time you boot, and you're trying to access shares via an ip address, you're not going to get anything if the  target pc has gotten a different ip address in the mean time.


once you have these networking issues sorted, jonandrews' explanation on how to share files looks very useful.

---

### Post by sgtbob on 2007-12-02
Thanks for all the advice.  I think I will have to have someone set up my Windows network  and then I will tackle the UIbuntu side of the boxes - I do not seem to be able to do so.  Everytime I think I have it, another issue crops up and I do not have the experience to solve the new issue.

Anyway, I really do appreciate all the suggestions - most of them worked  - up to the point I had a problem and then I didn't know how to fix it.  I'll see if I can take the PC's to a 'fix it' shop and see what they can do.

Will be monitoring this forum.

Bob :(

---

