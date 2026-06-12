---
title: "Connection problem"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by Steeltwist on 2007-12-13
I've just installed Ubuntu 7.10. Installation went great. Only problem is i cant connect to firefox. Well, cant connect to the internet all together. I dont know how to configure any of the settings as im new to this. Its on roaming or something. I have no idea what that is. Could someone possible tell me how to configure my network settings?

---

### Post by jagnikam on 2007-12-13
had u configured ur lan card ......? if No  
then first configure ***Lan Card ***
System---->adminiostration------->networkg------>Wired Connection----->properties----->static Ip address

After doing this do changes in ur firefox

Edit---->preference----->advanced------>Network---------->settings-------->select Direct connection

***_OR_***

if  u r using ***proxy server***........? then follow these steps 


go to 
Edit---->preference----->advanced------>Network---------->settings-------->Manual prexy setting
add IP & port no

---

### Post by Steeltwist on 2007-12-13
That didnt work :( Any other suggestions?

---

### Post by jarvoll on 2007-12-13
I (and apparently many others) had this problem, too.  While I don't think it'll enable Synaptic Package Manager to access the 'net, it should at least get Firefox into gear.

7.10 apparently uses a new IP called IPV6, whereas previous versions of Ubuntu (and most everything else including, importantly, most routers) uses IPV4.  My problem, and hopefully yours, was that my router couldn't deal with IPV6, so I had to disable it.  That's what I'll suggest you try.

1. Open Terminal (Applications > Accessories > Terminal)

2. Become root (type "sudo bash" without the quotes, then type your login/administrator password)

3. Type (again, without quotes) "gedit /etc/modprobe,d/aliases"

4. A text file will open to be edited.  Find in it the line: alias net-pf-10 ipv6

5. Edit this line to read: alias net-pf-10 off

6. Save the file, and reboot your computer.

7. Firefox should work!

Hope this helps :)

---

### Post by Steeltwist on 2007-12-14
Ok im gonna try this. I still dont know how im supposed to have my settings set up to connect to the internet though (like my ip and all that). No idea where to type those in. I'll try this and see how it works though.

---

### Post by Steeltwist on 2007-12-14
Nope didnt work. It wouldnt let me get passed typing my password in. Said registry not found or something.

---

### Post by xeth_delta on 2007-12-14
Let's fisrt see if your network is working.
In a terminal, what is the output of
```
ifconfig
```
and
```
ping www.bbc.co.uk
```
or ping to any other side for that matter. You can stop pinging with Ctrl-C

Xeth

---

### Post by Steeltwist on 2007-12-14
Would that do the same as doing host [www.google.com?](www.google.com?) If so, then it says connection timed out, no servers could be reached. So...evidently im not getting internet.

---

### Post by xeth_delta on 2007-12-14
> **Steeltwist said:**
> Would that do the same as doing host [www.google.com?](www.google.com?) If so, then it says connection timed out, no servers could be reached. So...evidently im not getting internet.

So it seems. try the following:
```
sudo /etc/init.d/networking restart
```

What was the output of ifconfig?

---

### Post by Steeltwist on 2007-12-14
Ping wouldnt connect to anything. I did the sudo /etc/init.d/networking restart but no idea what it did. It said ok. The ifconfig thing had alot of stuff come up but i had no idea what any of it was.

---

### Post by xeth_delta on 2007-12-14
> **Steeltwist said:**
> Ping wouldnt connect to anything. I did the sudo /etc/init.d/networking restart but no idea what it did. It said ok. The ifconfig thing had alot of stuff come up but i had no idea what any of it was.

Some of us know what the output is and might be able to help you. Please post the output of those commands, between code tags.

---

### Post by Steeltwist on 2007-12-14
All of that? How can i copy and paste it? Im on a totally different os..I pretty much know what the problem is its just everyone is ignoring what im saying. I dont know how/where to put my info in the network settings so it will connect. I dont know what to put and what to leave out.

---

### Post by xeth_delta on 2007-12-14
> **Steeltwist said:**
> All of that? How can i copy and paste it? Im on a totally different os..I pretty much know what the problem is its just everyone is ignoring what im saying. I dont know how/where to put my info in the network settings so it will connect. I dont know what to put and what to leave out.

Yes, you can copy and paste in the forum, in the same window you are posting from. Just use the code button above to introduce code tags.

About the exact problem you are having, I am sorry, but I don't understand what it is. Can you please explain again? Is it that you are looking for a gui to configure the settings of your connection? In that case Network manager ought to do it. Is your connection wireless or wired?

---

### Post by Teknyk on 2007-12-14
> **Steeltwist said:**
> I've just installed Ubuntu 7.10. Installation went great. Only problem is i cant connect to firefox. Well, cant connect to the internet all together. I dont know how to configure any of the settings as im new to this. Its on roaming or something. I have no idea what that is. **Could someone possible tell me how to configure my network settings?**

Can you tell us a little more about what kind of network you are connecting to or do you expect people to guess?

Are you on a static network or do you use DHCP
Do you use a router? if so is it wired or wireless?
Is this cable internet? DSL? Dial up?

When someone is trying to help you it is considered bad form to brush them off with "I know what the problem is" If you knew, you wouldn't have asked for help correct?

If you just want to know where to put your settings...
got to System > Administration > Network

---

### Post by Steeltwist on 2007-12-14
I dont see how i can copy it all then restart the comp and post it here in windows. Im sorry if im sounding like a prick but i thought i made it pretty clear what i was having problems with. Im not getting internet. Im not getting it because none of my info is where it should be. Like network connections on windows..it has the ip and all that already configured. On linux, there is nothing there.

What im saying is, the options to set up a connection, such as wired, modem etc, has no info in them. What im wanting to know, is how do i set it up? How do i put my ip and all that in so that it works? 

Your right, i know what the problem is. I just dont know how to fix it.

I use a router, its wired.
I have dsl.
I have no idea if i use static or DHCP. How do i check?

I know where to put it in..i just dont know how to set it up correctly. I apologize for my rudeness.

---

### Post by Teknyk on 2007-12-14
in windows do this.

open a command prompt (start > run > type cmd and hit enter)

type "ipconfig/release" and then "ipconfig/renew" (without quotes)

if it gives you an error about not being "in a state permissible" or something that will indicate you are using static


then in that window type ipconfig/all
paste that here.


no hard feelings and my apologies as well for being so abrupt with you.

---

### Post by Steeltwist on 2007-12-14
C:\Documents and Settings\Owner>ipconfig/release

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 0.0.0.0
        Subnet Mask . . . . . . . . . . . : 0.0.0.0
        Default Gateway . . . . . . . . . :

C:\Documents and Settings\Owner>ipconfig/renew

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1

C:\Documents and Settings\Owner>ipconfig/all

Windows IP Configuration

        Host Name . . . . . . . . . . . . : Bones
        Primary Dns Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Eth
ernet NIC
        Physical Address. . . . . . . . . : 00-11-09-14-A0-98
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 12.153.200.252
        Lease Obtained. . . . . . . . . . : Friday, December 14, 2007 12:49:44 P
M
        Lease Expires . . . . . . . . . . : Monday, December 17, 2007 12:49:44 P
M





I just copied it all cause i have no idea what im lookin at. Sorry if its hard to read.

---

### Post by Teknyk on 2007-12-14
ok that tells me you are using DHCP.

got to system > administration > network.
highlight the wired connection and click properties.

remove the check next to roaming and then from the pulldown select DHCP

save and try connecting again

---

### Post by xeth_delta on 2007-12-14
> **Steeltwist said:**
> I dont see how i can copy it all then restart the comp and post it here in windows. Im sorry if im sounding like a prick but i thought i made it pretty clear what i was having problems with. Im not getting internet. Im not getting it because none of my info is where it should be. Like network connections on windows..it has the ip and all that already configured. On linux, there is nothing there.

What im saying is, the options to set up a connection, such as wired, modem etc, has no info in them. What im wanting to know, is how do i set it up? How do i put my ip and all that in so that it works? 

Your right, i know what the problem is. I just dont know how to fix it.

I use a router, its wired.
I have dsl.
I have no idea if i use static or DHCP. How do i check?

I know where to put it in..i just dont know how to set it up correctly. I apologize for my rudeness.

And a way we would have been able to see whether your connection is up and if you were only missing an assigned IP, would have been with the output I suggested. But if you cannot post that information... it's another issue. 

You could have as well placed that information in a text file on a windows partition you could write to. Then just open it in Windows.

Anyway, you must understand that we are here to help you on a voluntary basis, if we ask more information is because we need more in order to help you. Rudeness will only manage to drive away those trying to give you advice. Please try to avoid it.

Good luck, I hope you manage to solve your problem

Xeth

---

### Post by Steeltwist on 2007-12-14
> **Teknyk said:**
> ok that tells me you are using DHCP.

got to system > administration > network.
highlight the wired connection and click properties.

remove the check next to roaming and then from the pulldown select DHCP

save and try connecting again

Ok i did that. Still no internet :confused: Is there anything else i should type in or somethin? I know on windows i had to type in my DNS thing at once point to get the internet to work. Not sure how linux is.

Btw im sorry for being rude.

---

### Post by Teknyk on 2007-12-14
Then we are really going to need to find out what ifconfig shows you as xeth_delta mentioned earlier.

you should see something like the following

```

eth0    Link encap:Ethernet  HWaddr 00:14:A5:96:EB:06  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe96:eb06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83588 errors:0 dropped:4432 overruns:0 frame:0
          TX packets:95436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54836209 (52.2 MB)  TX bytes:12550102 (11.9 MB)
          Interrupt:10 Base address:0x4000 

```

you may see more than one eth listed...
look for the one that shows HWaddr 00:11:09:14:A0:98

It should have a line directly below it that looks something like...
inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0

*edit*
write down what those lines show you if need be so you can post them here please.

---

### Post by Teknyk on 2007-12-14
Another thought,
There isn't a listing for your NIC under System > Administration > Restricted Drivers Manager by any chance is there?

I don't use Realtek so I am not sure. Anyone else know?

---

### Post by Steeltwist on 2007-12-14
> **Teknyk said:**
> Then we are really going to need to find out what ifconfig shows you as xeth_delta mentioned earlier.

you should see something like the following

```

eth0    Link encap:Ethernet  HWaddr 00:14:A5:96:EB:06  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:a5ff:fe96:eb06/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83588 errors:0 dropped:4432 overruns:0 frame:0
          TX packets:95436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54836209 (52.2 MB)  TX bytes:12550102 (11.9 MB)
          Interrupt:10 Base address:0x4000 

```


Ok this is confusing. I'll use yours as an example. The second line( inet addr) isnt even there on mine. Your third line reads inet6 addr: fe80::211:9ff:fe14:ae98/64 Scope:Link on mine. Your 4th line is like mine. Your 5th and 6 line is nothing but 0s on mine. Your 6th line is like mine. Uh i didnt even look at the 7th line. Interrupt is 19 and base is 0x0000 i believe.

Its showing i have 2 ethernet things and something else. As for your other post, i dunno let me check.

Edit: It says my hardware doesnt need a restricted driver or somethin.

---

### Post by grizzed on 2007-12-14
I suspect I'm having the same problem.  
I've got the command on my home machine ... but I ran the command to check the dhcp request and saw that my gutsy install wasn't getting the request.

Thanks to those helping out - I'll be following the thread closely.

I'm going to start over with 7.04 to ensure some network changes I had to make aren't part of my problem.  This machine worked with win2K and fawn .. and only saw problems with 7.10, but with my changes I need to start over to make sure it's not something I did.

---

### Post by grizzed on 2007-12-14
> **Steeltwist said:**
> Your third line reads inet6 addr: fe80::211:9ff:fe14:ae98/64 Scope:Link on mine. 
Its showing i have 2 ethernet things and something else.

Take your guidance from Tek, but I think the inet6 think means you still have Internet Protocol 6 enabled, which you should probably disable for this troubleshooting.

You said you had two ethernet thins ... one probably says eth0 - what is the other one labeled?

---

### Post by Teknyk on 2007-12-14
then you are probably going to need to do as jarvoll suggested but I found a typo in his instructions.

1. sudo gedit /etc/modprobe.d/aliases
2. type in the password you use to log into ubuntu
3. Find the line: alias net-pf-10 ipv6
4. Edit this to: alias net-pf-10 off
5. Save the file and reboot

---

### Post by Steeltwist on 2007-12-14
It says command not found. Are you spacing anything? I cant tell.

---

### Post by Teknyk on 2007-12-14
Yes.

sudo<space>gedit<space>/etc/modprobe.d/aliases

(that is a period next to the "d" above not a comma)

---

### Post by Steeltwist on 2007-12-14
Ok done. Rebooted and still no internet.  :(

---

### Post by Teknyk on 2007-12-14
Dang,
One last thing that I can think of trying and then I will have to defer to someone else with more Ubuntu experience than myself.

go back to System > Administration > Network and set you wired lan for roaming again.

shut off your pc and then unplug your router for about 30 seconds.
Power the router back up and after about a minute power your pc back up.

If this doesn't work my friend then this will need someone with more knowledge using Ubuntu than I have, sorry.

*edit*
I am subscribing to this thread also so I can follow what happens to finally solve this issue.

---

### Post by Steeltwist on 2007-12-14
Sigh. That didnt work either. I've followed what you've been telling me to do and i've done a few things on the site such as the pppoeconf things but nothing seems to work. I dunno what else to do :(

---

### Post by Teknyk on 2007-12-14
another ubuntu users advised me to ask you what the output of 
sudo dhclient eth0

You should see something like below

```
Listening on LPF/eth1/00:14:a5:96:eb:06
Sending on   LPF/eth1/00:14:a5:96:eb:06
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.100 -- renewal in 33171 seconds.
```

*note*
Mine is eth1 not eth0 because I am using wireless not the wired LAN.

---

### Post by Steeltwist on 2007-12-14
```
Listening on LPF/eth0/00:11:09:14:a0:98
Sending on   LPF/eth0/00:11:09:14:a0:98
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS recieved.
No working lease in persistent database - sleeping
```

Thats what mine looks like.

---

### Post by Teknyk on 2007-12-16
Sorry it took me so long to respond but I been sick.
It looks like you are not getting any DHCP offer from your router for some reason.
Your PC sends the discover but no offer ever comes back from the router.

If you haven't solved this already lets try setting it static if you are up for it.

go to system > administration > network.
highlight the wired connection and click properties.

remove the check from Roaming and set the pulldown to Static.

use the following:

IP Address: 192.168.1.102
Subnet mask: 255.255.255.0
Gateway: 192.168.1.1

click OK

then click the DNS tab and click add
where it says type address type 4.2.2.1 and then hit enter.

click close and try your connection again.

---

### Post by Steeltwist on 2007-12-16
That didnt work either :(  I think what im going to do is call a technician out here and see if they can do something with it. That is, if you have nothing else to offer. You've been a great help so far. I'd like to get this solved without having someone come out, but it seems i've tried everything :mad:

---

### Post by tospig on 2007-12-16
can I jump in here and ask a question...

have you run the command
sudo ethtool eth0

and on the last line where it says "Link detected" do you have yes or no?


if it's no then I think I'm having the same problem, and will also follow this thread :)

---

