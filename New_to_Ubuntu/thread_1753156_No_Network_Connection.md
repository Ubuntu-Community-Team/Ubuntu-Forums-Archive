---
title: "No Network Connection"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by UncleAlan on 2011-05-08
When I boot up my 10.04 system it is saying the network is disconnected but it isnt.

On the grey bar at the top of the screen on the right hand side next to the speaker mute, I no longer have two arrows , instead I have several curved lines and a red bar. Putting the mouse pointer over it says "NO NETWORK CONNECTION" However if the wire from the hub is then plugged into another PC it works fine. When I plug the wire back into the non working pc the light on the socket comes on a steady green to my mind indicating there is network. I tried RE booting the PC by completely shutting down and leaving, I have also emptied the Cache. Even though the green light is on by the network socket am I to believe the pc is broken and now only fit as a hard drive? Or have I inadvertently switched something off vital to the internet?

Alan

---

### Post by r-senior on 2011-05-08
What do you get if you type 'ifconfig' as a command in the terminal?

---

### Post by UncleAlan on 2011-05-09
If I type ifconfig as a command in the terminal (Applications-Accessories-Terminal) I get the following:-



alan@alan-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:01:2e:0b:32:d4  
          inet6 addr: fe80::201:2eff:fe0b:32d4/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:7633 (7.6 KB)  TX bytes:6282 (6.2 KB) 
          Interrupt:17 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B) 

alan@alan-desktop:~$ 

I hope I have done this correctly, let me know,

Regards
Alan

---

### Post by jtarin on 2011-05-09
You are not connected. Your Ethernet card which is eth0 has no address. It shows no ppp or pppoe connection either. How do you normally connect? Cable,ADSL ?????

---

### Post by UncleAlan on 2011-05-09
I Connect via an ethernet cable from the internet hub. The cable plugs int the pc and a light on the socket glows green. It has worked until now. I have even plugged the same cable into another pc and it worked still but not in the pc at issue. Never had this before and I am right stumped. Any ideas?

---

### Post by grahammechanical on 2011-05-09
The curved lines with the red bar (actually an exclamation mark) is Network Manager's way of telling you that the PC does not have a connection to the router/modem/hub.

What do you see when you right and lift click the icon? Is there a tick mark against the line Enable Networking? Are the wired networks (ethernet ports) marked as disconnected? Is this a laptop? Is there a keyboard switch that you press to activate wireless? Do you have another operating system installed? Can wireless be switched off in that operating system? If it is switched off in the other operating system then, switch it back on. Try clicking Enable Networking to switch networking off and on.

If you hub is switched on and the cable is plugged in and not defective but you do not have a connection it might be because the wireless adapter in the machine (networking) is switched off. The questions I have given you might help you find the answer.

Regards.

---

### Post by jtarin on 2011-05-09
> **UncleAlan said:**
> I Connect via an ethernet cable from the internet hub. And the hub connects to......what provides your internet service????? Do you have to sign on with a name and password??

---

### Post by UncleAlan on 2011-05-10
Grahammechancal,

I do not have any wireless equipment. the PCs are desk top not lap tops. The problem PC does this:-
Left clicking on the said icon shows a dark grey box, the top line in  grey says wired network. the next line down says in an off white shade  disconnected, the line under this also in off white says Availalable,  below that in whit it says Auto eth0, below that in white it says VPN  Connections and a little arrow.

The problem 10.04 pc:
Right click shows :-
dark grey box, top line in white a tick Enable Networking, next line in  white a tick Enable Notifications, next line in off white Connection  Information, next line in white Edit Connections..., next line in white  About.

Comparig this to my working PC running 10.10

Left clicking on the said icon shows a dark grey box, the top line in  grey says wired network. the next line down says in WHITE  Auto eth0,  below that in white it says Disconnect,  below that in white VPN  Connections and a little arrow.
 
 Right click shows :-
 dark grey box, top line in white a tick Enable Networking, next line in  white a tick Enable Notifications, next line in white Connection  Information, next line in white Edit Connections..., next line in white  About.

note I am using the same hub for both PCs and have even tried swapping  the cables. On the Problem PC hovering the mouse over any grey or off  white (possiblly light grey) words doesnt do anything, ie over  "Available" no options show.I hope that is clear, 
Alan

---

### Post by UncleAlan on 2011-05-10
jtarin,

a phone line provides my internet. I switch on the Hub, the lights come on, I switch on the pc and it always was ready to work, the same cable plugged into my other pc running 10.10  I'm typing this on does the same. My above reply to grahammechanical may give you some more clues, its a bit odd I must admit.

---

### Post by debd on 2011-05-10
> a phone line provides my internet.

it should be a ppp connection.
have you tried 
```
sudo pppoeconf
```

or may be its a problem with your computer's hardware?

> pc the light on the socket comes on a steady green

that gives me a feeling that your ethernet card is damaged. normally it should blink even when you ain't accessing internet.

a few days ago my ethernet card was damaged due to a lightning strike and the indicator would glow steady..with no connections.

---

### Post by UncleAlan on 2011-05-10
Debd,
 

 Tried: sudo pppoeconf
 

 Said it found an eth0 and I followed the instructions and got this:-
 

            Sorry, I scanned 1 interface, but the Access              
            Concentrator of your provider did not respond. Please     
            check your network and modem cables. Another reason       
            for the scan failure may also be another running pppoe    
            process which controls the modem.  
 

 

 Re the lights, The failed pc with the steady green Ethernet plug light briefly had a flashing orange light on booting up but nothing but the steady green after that. I then compared with the working PC which has both a steady green and a steady orange next to the ethernet plug and this works as expected.
 

 I note your comment on the &#8220;lightning strike&#8221; and I am quite familiar with this scenario at work. In the case of the failed pc we did have heavy rain on Sat night and although I dont recall any lightening but it could have struck many miles away. Our Telephone lines are all underground on this estate though and the hub is still working. The failed pc was plugged into the mains vai a surge / spike protection gang socket and was all switched off.
 

 The ethernet connection looks to be onboard, ie part of the motherboard.  
 

 I hope there are some helpful clues in the above
 Alan

---

### Post by jtarin on 2011-05-10
Try the command ```
route -n
``` and post results. Try the command ```
sudo pon dsl-provider
```and see if you connect.

---

### Post by debd on 2011-05-11
UncleAlan, your machine isn't being connected at all...ifconfig shows that.

Still am a bit suspicious about the ethernet adapter.
Could you check with a live CD or USB?
If its available, boot with that, configure network connection the way you are used to, and see if it connects.

---

### Post by UncleAlan on 2011-05-11
Hi jtarin,
here are the results for your last idea,

alan@alan-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
alan@alan-desktop:~$ 

then I ran the second sugestion. This produced a screen of "gibberish" and when it fineshed at the prompt it still had not connected.

Alan

---

### Post by UncleAlan on 2011-05-11
Hi debd,

I tried those things in your last reply and this was the result.


Booted from the live CD I used for installation and chose the try option. Still coming up with no connection.

I have also tried every combination of cable and port in the BT Hub. none work with the problem PC but all work with the PC I'm using for this message.

Still the pc isnt working but the bub obviously is. not looking good for the pc is it ?

Alan

---

### Post by jtarin on 2011-05-11
Open a browser and type this address in the url bar.
192.168.0.1
Does that access your router?

---

### Post by debd on 2011-05-12
> Booted from the live CD I used for installation and chose the try option. Still coming up with no connection.
pardon me if am being a bit silly, but did you configure the network connection before trying to connect (from the live CD)?

If that is 'yes', I think its a hardware failure...

---

### Post by UncleAlan on 2011-05-12
Open a browser and type this address in the url bar.
 192.168.0.1
 Does that access your router?

No ! it tells me it cant access it as I havnt got a network connection.

---

### Post by UncleAlan on 2011-05-12
debd,
Not silly at all. You know more than me.  I just switched it on!!! I dont think I have ever knowingly configured the connection, it just worked. I have not ever used the installation discs with the hub or its predecessor as they just worked. Tonight I did try the hub installation disc but it didnt work. The pc could see it and the set ups for internet things but it doesnt work. I looked at the menus from the connection drop down for left and right click and compared the results with the working 10.10 pc and they appear the same , so again point to a duff part of the main board in the dodgy 10.04.1 pc.

Sorry I appear a dunce, I can follow step by step instructions with a very large spoon but my knowledge is lacking.

Alan

---

### Post by jtarin on 2011-05-12
> **UncleAlan said:**
> Debd,
 

 Tried: sudo pppoeconf
 

 Said it found an eth0 and I followed the instructions and got this:-
 

            Sorry, I scanned 1 interface, but the Access              
            Concentrator of your provider did not respond. Please     
            check your network and modem cables. Another reason       
            for the scan failure may also be another running pppoe    
            process which controls the modem.  
 

 Try this again with the other PC disconnected from the hub.

---

### Post by debd on 2011-05-13
> I dont think I have ever knowingly configured the connection, it just worked.
so you have a connection with [DHCP]("http://goo.gl/pwtg")

Uh..I never used dhcp.. 
the Internet service provider generally provides with a leaflet/book with some of their network device addresses(like DNS addresses, subnet musk and some others) for manual configuration, if needed. 
Do you have something like that?
If you do, you may give it a last try :)

right click on the network-manager-applet , click on 'edit connections'
In the "wired" tab, click 'add'
Go to the "IPvSettings" tab -> From the "method" drop menu choose "manual" and click "add' beside the "addresses" table. put in the three addresses as in the supplied leaflet ; add the DNS servers(separated with commas if more than one. Leave search domains blanc. Give the connection a name.

Now disconnect if any previous network connection was trying to connect, and select the newly configured connection from the nm-applet..and see if any thing happens.


Still nothing?...grab a PCI ethernet adapter :p

> You know more than me.

little do I know... but that makes me feel glad :D

---

### Post by jtarin on 2011-05-13
In your picture,,,change method to automatic.

---

### Post by dineshs on 2011-05-13
I dont know if [this]("http://ubuntuforums.org/showthread.php?t=1753698&page=2") is related.The post says an automated hub update may have caused the problem and the remedy is
[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9)

---

### Post by UncleAlan on 2011-05-13
jtarin,

Unplugged everything else and tried again and got the same result

I found 1 ethernet device:                                
            eth0                                                     
                                                                    
           Are all your ethernet interfaces listed above?           
           (If No, modconf will be started so you can load the      
           card drivers manually).                                  
                                                                    
           Or press ESC to abort here.                              
                                                                     
                                                                    
                         <Yes>      

          
       Sorry, I scanned 1 interface, but the Access             
           Concentrator of your provider did not respond. Please     
           check your network and modem cables. Another reason       
           for the scan failure may also be another running pppoe    
           process which controls the modem.                  


Worth a try though.

---

### Post by UncleAlan on 2011-05-13
debd, jtarin,

had a good look in the booklet with the hub, cant see anything useful in there.Had a brain wave and went through the network connection screens for left and right click and compared the duff pc with the good one and they were the same (of course). Looked in the case and found no room for another card!!!!! Then 2nd brain wave ...if I take one out I dont use , a pci ethernet card looks like it will fit as there is a long orange mount on the board there doing nothing. Looks like I can get one for £10 or less.

---

### Post by UncleAlan on 2011-05-13
dineshs,

IT WORKED !!!!!!!!!!!!!!

Just returned from dancing round the garden and cursing BT !!!

I just did the first fix with the scripts, frightened myself going into strange screens and praying. Then switched it off and hid, counted to 25 to make sure and switched it on and everything worked. I shut it down and came back to it and it started up and still worked.


TOO ALL WHO HAVE ASSISTED ME THIS WEEK I THANK YOU ALL VERY MUCH. I can follw simple instructions but have not a great understanding of PCs, people like me rely on those who know more being kind and understanding to help us.

Have a good wk end all. Regards Alan.

---

### Post by jtarin on 2011-05-13
Way to go.....a very one-off solution to a one-off problem. Kudos to dineshs for locating the fix.

---

### Post by debd on 2011-05-14
great call dinesh!
I'm going to bookmark this thread.

Wish a good week-end to you too Alan.

---

### Post by dineshs on 2011-05-16
The credit goes to Irony for posting [this]("http://ubuntuforums.org/showthread.php?t=1753698&page=2") :)

---

