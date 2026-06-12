---
title: "My Dad Is Fed Up With Ubuntu (BT Home) Please Help!"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by demonboy on 2011-02-28
When I was last home I installed 10.10 on my father's netbook as Windows 7 didn't run well on it. I sold him the ethos of Ubuntu and left him happy.

Since then he has switched service providerrfrom Orange to BTHome and can no longer get a satisfactory wifi connection. Unfortunately I am not there and cannot sit down with the computer and he is not well and not able to spend the hours and hours he has already spent on it to get it working. He is extremely frustrated but I'm hoping someone can help us. Here is what he has sent me. 

> 
[FONT=Times New Roman][SIZE=3]Last  week I switched on and it logged straight in - no  problem. [/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Today I  started off at around 10: 30 am and switched on and Ubuntu could "see"  the following:[/SIZE][/FONT]

 [FONT=Times New Roman][SIZE=3]BT Home  Hub (mine)[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]BTFon (the  hotspots throughout the UK)[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]BT  Openzone (Usually in towns & cities)[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Talk  Talk[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Sky  12740[/SIZE][/FONT]

 [FONT=Times New Roman][SIZE=3]Some of  these were encrypted (or WEP key only). It did not log on so I clicked on Home  Hub. No go -so I clicked on BTFon still -no go. So then I deleted all   reference to wireless (System-Preferences-delete all wireless). Clicked on  "Re-start "[/SIZE][/FONT].[FONT=Times New Roman][SIZE=3] Came back  up but did not log into any specific wireless. 

Closed down completely &  re-started. Still did not log in. So I plugged in the Ethernet cable to go  online. I then went into the BT website and logged in. There is a function  called BT Desk Top Help which allows you to download software to assist in  login. Firstly I clicked on the wizard. Got this message" We have detected that  you are using an operating system not currently supported by BT Desktop. Systems  supported are: Windows XP ,SP 1 or above, Windows Vista & Windows 7".  [/SIZE][/FONT]

 [FONT=Times New Roman][SIZE=3]I then  went to Applications/Accessories/Terminal and did the usual sudo apt-get updates  and installed everything. After that [/SIZE][/FONT][FONT=Times New Roman][SIZE=3]I went onto  the Ubuntu Update Manager Feeds & downloaded all the new bits. I also went  to the Drivers downloads but there was nothing new. I returned to the BT  site and clicked on download the software and got the _same  message_ as when I tried uploading the original CD. It's also what I got when  I copied the CD onto a memory stick and tried to upload it.  A new window  automatically opened and this is what it said:[/SIZE][/FONT]

 [I][FONT=Times New Roman][SIZE=3]"Archive  Manager.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]An error  occurred while loading the archive.[/SIZE][/FONT][/I]  [I]
[FONT=Times New Roman][SIZE=3]Command  Line Output[/SIZE][/FONT][/I]  [I]
[FONT=Times New Roman][SIZE=3]Archive :/tmp/BTBBDesktopHelp Install  exe[/SIZE][/FONT][/I]  [I]
[FONT=Times New Roman][SIZE=3][/tmp/BTBBDesktopHelpInstall.exe] End- of - central-  directory[/SIZE][/FONT][/I]    [FONT=Times New Roman][SIZE=3]*signature  not found. Either this file is not a zip file, or it constitutes one disk of a  multi-part archive. In the latter case the central directory and zip file  comment will be found on the last disk(s) of this archive/ zipinfo:cannot find  zip file directory in one of /tmp/BTBBDesktopHelpInstall.exe or  /tmp/BTBBDesktophelpInstall.exe.zip, and cannot find  /tmp/BTBBDesktopHelpInstall.exe  ZIP/period "    *Just to confirm _there is no  second_ disk.[/SIZE][/FONT]

 [FONT=Times New Roman][SIZE=3]At 13:30  hrs I logged in again (that was the 4th time ) and it locked onto the BT  Openzone (71% strength). I input my pass word and got on the internet. I left it  switched on and logged in. 

At 16:30 hrs I checked and it was still on the  internet.  I logged out and then logged back in again. Ubuntu logged  straight back into BTOpenzone at 78% signal. [I]

It's obvious it looks for the  strongest signal to start with.BUT..........[/I] guess what,  Firefox  could not establish a connection (surprise) .[/SIZE][/FONT]

 [FONT=Times New Roman][SIZE=3]PART  TWO 
IN the morning as there is a lot more to type (error messages and more  log-in/log-out)s until I gave up at 1905 hrs! In between all this I tried to  re-set the wireless connections (advanced as well but did not understand all  the  silly abbreviations). I know they mean something but there is no help  facility on some of the functions. [/SIZE][/FONT]
 


---

### Post by Grenage on 2011-02-28
Some people have only ever used Windows, and in a world where most user software is advertised and provided for Windows, it's often easiest for people to install and use it.

Regarding the wireless, I've noticed a few problems with 'some' network gateways, most of which were cured by changing the Wifi channel; it might be worth giving that a try.

---

### Post by aeiah on 2011-02-28
if the wireless connection worked fine with orange and the modem/router orange provided and not with BT and the modem/router BT provided, it kind of makes sense that it isn't ubuntu that's at fault.

but to be sure, you should find out what wireless card he has (sudo lshw -html will spit out all system information in html - probably useful to keep somewhere for future reference)

also find out what sort of uptime his broadband connection is getting, and any logs that the router is spitting out.

for the record, all the below ones are of his router:
BT Home Hub (mine)
BTFon (the hotspots throughout the UK)
BT Openzone (Usually in towns & cities)

BT securely shares your connection (with the names BTFon and openzone) by default with other BT customers

---

### Post by cchhrriiss121212 on 2011-02-28
Maybe he is just not using the right key? I have a home hub, you will find the key on a sticker on the base. Ask him to double check it.

---

### Post by Bölvaður on 2011-02-28
> **cchhrriiss121212 said:**
> Maybe he is just not using the right key? I have a home hub, you will find the key on a sticker on the base. Ask him to double check it.
This is what I am thinking.
Make sure he is using the right key to get into it. Make sure it is the right bit length of WEP or WPA. If it worked before it should work now. I would rule out simple error like this before changing the channel of the wifi router.

It might also be worth getting someone else with another laptop to connect to the wifi and see if it works. But be warned that wifis are weird, my friend was unable to log into her wifi on xp but when I used live cd with ubuntu then the same computer was able to connect without any problem at all.

---

### Post by nickdc on 2011-02-28
I've been experiencing similar problems to your dad. I posted about a week ago but got no replies :(. Around the same time though, there were other postings relating to wireless problems, suggesting there may be an issue with 10.10 for some people. See this thread in parrticular 			 			[WiFi issue in Ubuntu 10.10]("http://ubuntuforums.org/showthread.php?t=1596043") 			where you may find some ideas. My problem certainly started after an update about two weeks ago. My wireless signal is strong, I'm using no encryption, yet ubuntu keeps dropping the connection, or showing it as very weak signal at same time as my smartphone is showing it strong. Even more weirdly, when I visited my son last week, I was able to connect and stay connected to his wireless without any problems. I'm way out of my depth in terms of how it all works technically, but I strongly suspect there's an issue relating to the interaction between the latest version of ubuntu and some wireless chips. Best of luck - it's bad enough doing your own troubleshooting, but far worse doing it at a proxy for someone else!

---

### Post by Mark Phelps on 2011-02-28
On a side-note ... the desktop help file your dad tried to install is most probably an MS Windows self-extracting archive -- which won't install or work in Ubuntu.  This is not unusual as most ISP support types are familiar ONLY with MS Windows.

---

### Post by demonboy on 2011-03-01
Thanks for the messages so far. I am still waiting to hear back from him regarding the terminal print-out aeiah requested. I will post this up when he gets back to me later today. In the meantime I received part 2 from him this morning.

> 

As I said Firefox came up with the following message: (this is a regular feature-I have seen this message MANY times before even when I have a strong signal up to 98%). 

Firefox can't establish a connection to the server at [www.btopenzone.com:8443](www.btopenzone.com:8443) (this could also be Google or something else) I did look at the Firewall settings but did not understand them.

So I switched off and re-booted. It logged me into BTFon (briefly). It fell out again and came up with the same message as above.

So I clicked "disconnect" BTOpenzone. Tried clicking on the Home Hub symbol. Connection established with 65% strength. Clicked on Google-went straight in at 1635hrs.

I logged out at 1640 hrs . At 1715 hrs I logged in again, it went straight into BTOpenzone with 78% signal strength. Clicked on Firefox, it spent ages thinking about it then fell over and, you guessed it, I got the same message as above. So I clicked on disconnect to BTOpenzone and then clicked on Connect to the Home Hub as it did not connect automatically. It kept asking for authentication WPA key, when I clicked "connect" tab nothing happened. I then clicked Cancel, disconnect. After a short time the wireless icon started flashing on its own and a message came up "Configuring Wireless Network Connection" [Auto BTFon]. It then disconnected and came up with the message "No Wireless Connection" . I shut down.

at 1855hrs I switched on and got the message "Unable to Connect". I tried to log in to BT Home Hub-but gave up and logged out at 1900hrs after clicking on System-Preferences-and deleted all wireless connections. I shut down at 1900hrs. I then re-booted and logged in. No wireless signal came up so I chose Home Hub but it would not log in so I gave up at 1903hrs and shut down at 1905 hrs.

Now for technical stuff:

Default settings:            -  Broadband user name (PPP) [email]bthomehub@broadband.com[/email]

Broadband password:     none required

Encapsulation:                 PPPoA or PPP over ATM

Multiplexing:                    VC based or VC Mux

VPI/VCI:                        0/38

Wireless Key:                   WPA PSK WEP

Wireless interface:              wi-fi 802.11.b, g or n

Authentication:                 WPA-PSK or WPA2-PSK (also known as WPOA personal)

Encryption type:                 AES or TKIP 

IP address:                        86.134.72.57

Setup:                               Infrastructure (not Ad Hoc) 

The last item is mine as I discovered it when reading the help files. Why I kept re-booting was because when I changed anything (like removing all the wireless setups) I assumed that was the best procedure. I noticed all the wirless settings were back again once Ubuntu could "see" the differing hotspots. I often leave the computer in "standby or Hibernate" state, but Ubuntu does not like this at all as it seems to remember if I have clicked "disconnect" and  when I turn back on it does not permit me to re-connect, which is why I have been forced to shut down each time.



---

### Post by migs73 on 2011-03-01
> **Mark Phelps said:**
>  This is not unusual as most ISP support types are familiar ONLY with MS Windows.


Yet most of their routers run on Linux. The double standards are aggravating.

---

### Post by cchhrriiss121212 on 2011-03-01
The problem is that he is connecting to a Openzone and BTfon, when he should be using the HomeHub connection. Tell him to delete the profile for the other two signals in network connections, that way they won't autoconnect.

> It kept asking for authentication WPA key, when I clicked "connect" tab nothing happened.
BT still uses a WEP key for many routers.

---

### Post by grahammechanical on 2011-03-01
And they say a little knowledge is a dangerous thing.

Things were working fine until he switched service providers and yet everything is Ubuntu's fault. There is nothing wrong with the Ubuntu installation or the way it is using the wireless adapter.

He needs to point Network Manager at his wireless connection (BT Home Hub - mine) and when he is asked to authenticate he should enter the wireless key or pass phrase. His new ISP sould have provided him with a leaflet giving the right information. Or as someone said, it is on a label stuck on the bottom of the modem. Then he needs to make sure that the connection is set to connect automatically.

Finally, tell, him that I will be 63 years old by the time that Ubuntu 11.04 is released. I am not yet brain-dead and neither is he.

Regards.

---

### Post by Grenage on 2011-03-01
> **grahammechanical said:**
> And they say a little knowledge is a dangerous thing.

Things were working fine until he switched service providers and yet everything is Ubuntu's fault. There is nothing wrong with the Ubuntu installation or the way it is using the wireless adapter.

He needs to point Network Manager at his wireless connection (BT Home Hub - mine) and when he is asked to authenticate he should enter the wireless key or pass phrase. His new ISP sould have provided him with a leaflet giving the right information. Or as someone said, it is on a label stuck on the bottom of the modem. Then he needs to make sure that the connection is set to connect automatically.

Finally, tell, him that I will be 63 years old by the time that Ubuntu 11.04 is released. I am not yet brain-dead and neither is he.

Regards.


Considering that the wireless works intermittently, you're being unfair.

---

### Post by demonboy on 2011-03-02
> 
And they say a little knowledge is a dangerous thing.

Things were working fine until he switched service providers and yet  everything is Ubuntu's fault. There is nothing wrong with the Ubuntu  installation or the way it is using the wireless adapter...

Finally, tell, him that I will be 63 years old by the time that Ubuntu  11.04 is released. I am not yet brain-dead and neither is he.
You are being really insulting, grahammechanical. This kind of patronising response is exactly the kind of post that puts newbie, non-technical Linux users like my father off using Ubuntu altogether. Way out of line. Desist, please.

Thank you to the rest of the posters, I appreciate your patience. It's encouraging (if that's the right word) to see that many other people are having the same problem, ruling out the theory that my father is an idiot. Thanks to nickdc for that link. 

I have finally got some more information off of my dad. The first is my father's reiteration that this is a sporadic problem that seems to be happening intermittently. Secondly there does seem to be some correlation between rebooting, which a couple of you have picked up on. For the record some of what my father is talking about sounds familiar to me. I'm finding that Network Manager is connecting to wireless networks despite deleting them from NW. When I next boot up it finds the networks again and adds them, attempting to log in to any one of them. This is similar to what my father is experiencing, I think. Here's his update email:

> 
[FONT=Times New Roman][SIZE=3]As I said  Firefox came up with the following message: ([I]this is a regular feature-I  have seen this message MANY times before even when I have a strong signal up to  98%). 
[/I][/SIZE][/FONT]

 [FONT=Times New Roman][SIZE=3]Firefox  can't establish a connection to the server at [www.btopenzone.com:8443]("http://www.btopenzone.com:8443/") (*this  could also be Google or something else) I did look at the Firewall settings but  did not understand them.*[/SIZE][/FONT]

 [FONT=Times New Roman][SIZE=3]So I  switched off and re-booted. It logged me into BTFon (briefly). It fell out again  and came up with the same message as above.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]So I  clicked "disconnect" BTOpenzone. Tried clicking on the Home Hub symbol.  Connection established with 65% strength. Clicked on Google-went straight in at  1635hrs.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]I logged  out at 1640 hrs . At 1715 hrs I logged in again, it went straight into  BTOpenzone with 78% signal strength. Clicked on Firefox, it spent ages thinking  about it then fell over and, you guessed it, I got the same message as above. So  I clicked on disconnect to BTOpenzone and then clicked on Connect to the Home  Hub as it did not connect automatically. It kept asking for authentication WPA  key, when I clicked "connect" tab nothing happened. I then clicked Cancel,  disconnect. After a short time the wireless icon started flashing on its own and  a message came up "Configuring Wireless Network Connection" [Auto BTFon]. It  then disconnected and came up with the message "No Wireless Connection" . I  shut down. 
[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]At 1855hrs  I switched on and got the message "Unable to Connect". I tried to log in to BT  Home Hub-but gave up and logged out at 1900hrs after clicking on  System-Preferences-and deleted all wireless connections. I shut down at 1900hrs.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]  I then re-booted and logged in. No wireless signal came up so I chose Home Hub  but it would not log in so I gave up at 1903hrs and shut down at 1905 hrs. 
[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Now for  technical stuff:[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Default  settings:             -  Broadband user name (PPP) [EMAIL="bthomehub@broadband.com"]bthomehub@broadband.com[/EMAIL][/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Broadband  password:     none required[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Encapsulation:                  PPPoA or PPP over ATM[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Multiplexing:                    VC  based or VC Mux[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]VPI/VCI:                        0/38[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Wireless  Key:                   WPA  PSK WEP[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Wireless  interface:               wi-fi 802.11.b, g or n[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Authentication:                  WPA-PSK or WPA2-PSK (also known as WPOA personal)[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3]Encryption  type:                  AES or TKIP[/SIZE][/FONT] 
 [FONT=Times New Roman][SIZE=3]IP  address:                         86.134.72.57[/SIZE][/FONT]
 [FONT=Times New Roman][SIZE=3][I]Setup:                               Infrastructure  (not Ad Hoc) 
[/I][/SIZE][/FONT]

 [FONT=Times New Roman][SIZE=3]The last  item is mine as I discovered it when reading the help files. Why I kept  re-booting was because when I changed anything (like removing all the wireless  setups) I assumed that was the best procedure. I noticed all the  wirless settings were back again once Ubuntu could "see" the differing  hotspots. I often leave the computer in "standby or Hibernate" state, but Ubuntu  does not like this at all as it seems to remember if I have clicked "disconnect"  and  when I turn back on it does not permit me to re-connect, which is why  I have been forced to shut down each time.[/SIZE][/FONT]
 
And then he sent:

> 
By the way my theory is correct. This morning I turned it on
and it would not log in to wireless so I deleted all the
wireless settings again and shut down. Then I re-booted and
it went straight in. I then clicked "hibernate" and it
failed to log in when I turned it back on. Now have just
clicked "restart" again to see what happens...

...Right it's
come back and is seeking the wifi but is asking me for the
netkey. I clicked on netkey "connect" but it keeps flashing
up the message "wireless disconnected".
Just tried the BTFon connection but it cannot connect.Also
tried BTOpenzone but it is not connecting (Left it trying
for 5 minutes). All those three signals are giving over 80%
strength.(It can "see" 5 wireless networks within reach)

So, to pick up on what posters have been saying:

@Bölvaður - I don't see how the key can be the issue if he is able to log in with it intermittently. If he had an incorrect key then he would not be able to log in at all. See the second message - he is connecting immediately in some instances.

@Grenage - he is not able to change the channel as it is set to 'infrastructure'.

@cchhrriiss121212 - he has been deleting all connections and starting again. However I have not yet asked him to connect to the Homehub connection so I will send him those instructions, thanks. I suspect that this might be the issue, that it is trying to connect to other connections first.

@aeiah - the output for the 'sudo lshw -html' is as follows (not sure where the missing opening tags are):

```


ical</dfn>  <dfn title="twisted pair">tp</dfn> <dfn title="Media  Independent Interface">mii</dfn> <dfn  title="10MB/s">10bt</dfn> <dfn title="10MB/s (full  duplex)">10bt-fd</dfn> <dfn  title="100MB/s">100bt</dfn> <dfn title="100MB/s (full  duplex)">100bt-fd</dfn> <dfn  title="Auto-negotiation">autonegotiation</dfn>  </td></tr>
                <tr><td  class="first">configuration:</td><td  class="second"><table summary="configuration of  network"><tr><td class="sub-first">  autonegotiation</td><td>=</td><td>on</td></tr><tr><td  class="sub-first">   broadcast</td><td>=</td><td>yes</td></tr><tr><td  class="sub-first">  driver</td><td>=</td><td>r8169</td></tr><tr><td  class="sub-first">  driverversion</td><td>=</td><td>2.3LK-NAPI</td></tr><tr><td  class="sub-first">  duplex</td><td>=</td><td>full</td></tr><tr><td  class="sub-first">  ip</td><td>=</td><td>192.168.1.66</td></tr><tr><td  class="sub-first">  latency</td><td>=</td><td>0</td></tr><tr><td  class="sub-first">  link</td><td>=</td><td>yes</td></tr><tr><td  class="sub-first">  multicast</td><td>=</td><td>yes</td></tr><tr><td  class="sub-first">   port</td><td>=</td><td>MII</td></tr><tr><td  class="sub-first">  speed</td><td>=</td><td>100MB/s</td></tr></table></td></tr>
                 <tr><td class="first">resources:</td><td  class="second"><table summary="resources of  network"><tr><td class="sub-first">  irq</td><td>:</td><td>42</td></tr><tr><td  class="sub-first">  ioport</td><td>:</td><td>3000(size=256)</td></tr><tr><td  class="sub-first">  memory</td><td>:</td><td>f0510000-f0510fff</td></tr><tr><td  class="sub-first">  memory</td><td>:</td><td>f0500000-f050ffff</td></tr><tr><td   class="sub-first">  memory</td><td>:</td><td>f0520000-f053ffff</td></tr></table></td></tr>
 </tbody>             </table></div>
             </div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:0">
 <thead><tr><td class="first">id:</td><td class="second"><div  class="id">usb:0</div></td></tr></thead>
 <tbody>
              <tr><td class="first">description: </td><td  class="second">USB Controller</td></tr>
              <tr><td class="first">product: </td><td  class="second">N10/ICH 7 Family USB UHCI Controller  #1</td></tr>
             <tr><td  class="first">vendor: </td><td class="second">Intel  Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div  class="id">1d</div></td></tr>
              <tr><td class="first">bus info: </td><td  class="second"><div  class="id">pci@0000:00:1d.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">02</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
              <tr><td class="first">capabilities: </td><td  class="second"><dfn title="Universal Host Controller Interface  (USB1)">uhci</dfn> <dfn title="bus  mastering">bus_master</dfn> </td></tr>
              <tr><td class="first">configuration:</td><td  class="second"><table summary="configuration of  usb:0"><tr><td class="sub-first">  driver</td><td>=</td><td>uhci_hcd</td></tr><tr><td  class="sub-first">  latency</td><td>=</td><td>0</td></tr></table></td></tr>
              <tr><td class="first">resources:</td><td  class="second"><table summary="resources of  usb:0"><tr><td class="sub-first">   irq</td><td>:</td><td>23</td></tr><tr><td  class="sub-first">  ioport</td><td>:</td><td>1820(size=32)</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:1">
 <thead><tr><td class="first">id:</td><td class="second"><div  class="id">usb:1</div></td></tr></thead>
 <tbody>
              <tr><td class="first">description: </td><td  class="second">USB Controller</td></tr>
              <tr><td class="first">product: </td><td  class="second">N10/ICH 7 Family USB UHCI Controller  #2</td></tr>
             <tr><td  class="first">vendor: </td><td class="second">Intel  Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div  class="id">1d.1</div></td></tr>
              <tr><td class="first">bus info: </td><td  class="second"><div  class="id">pci@0000:00:1d.1</div></td></tr>
             <tr><td class="first">version: </td><td class="second">02</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
              <tr><td class="first">capabilities: </td><td  class="second"><dfn title="Universal Host Controller Interface  (USB1)">uhci</dfn> <dfn title="bus  mastering">bus_master</dfn> </td></tr>
              <tr><td class="first">configuration:</td><td  class="second"><table summary="configuration of  usb:1"><tr><td class="sub-first">  driver</td><td>=</td><td>uhci_hcd</td></tr><tr><td  class="sub-first">  latency</td><td>=</td><td>0</td></tr></table></td></tr>
              <tr><td class="first">resources:</td><td  class="second"><table summary="resources of  usb:1"><tr><td class="sub-first">   irq</td><td>:</td><td>19</td></tr><tr><td  class="sub-first">  ioport</td><td>:</td><td>1840(size=32)</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:2">
 <thead><tr><td class="first">id:</td><td class="second"><div  class="id">usb:2</div></td></tr></thead>
 <tbody>
              <tr><td class="first">description: </td><td  class="second">USB Controller</td></tr>
              <tr><td class="first">product: </td><td  class="second">N10/ICH 7 Family USB UHCI Controller  #3</td></tr>
             <tr><td  class="first">vendor: </td><td class="second">Intel  Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div  class="id">1d.2</div></td></tr>
              <tr><td class="first">bus info: </td><td  class="second"><div  class="id">pci@0000:00:1d.2</div></td></tr>
             <tr><td class="first">version: </td><td class="second">02</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
              <tr><td class="first">capabilities: </td><td  class="second"><dfn title="Universal Host Controller Interface  (USB1)">uhci</dfn> <dfn title="bus  mastering">bus_master</dfn> </td></tr>
              <tr><td class="first">configuration:</td><td  class="second"><table summary="configuration of  usb:2"><tr><td class="sub-first">  driver</td><td>=</td><td>uhci_hcd</td></tr><tr><td  class="sub-first">  latency</td><td>=</td><td>0</td></tr></table></td></tr>
              <tr><td class="first">resources:</td><td  class="second"><table summary="resources of  usb:2"><tr><td class="sub-first">   irq</td><td>:</td><td>20</td></tr><tr><td  class="sub-first">  ioport</td><td>:</td><td>1860(size=32)</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:3">
 <thead><tr><td class="first">id:</td><td class="second"><div  class="id">usb:3</div></td></tr></thead>
 <tbody>
              <tr><td class="first">description: </td><td  class="second">USB Controller</td></tr>
              <tr><td class="first">product: </td><td  class="second">N10/ICH 7 Family USB UHCI Controller  #4</td></tr>
             <tr><td  class="first">vendor: </td><td class="second">Intel  Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div  class="id">1d.3</div></td></tr>
              <tr><td class="first">bus info: </td><td  class="second"><div  class="id">pci@0000:00:1d.3</div></td></tr>
             <tr><td class="first">version: </td><td class="second">02</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
              <tr><td class="first">capabilities: </td><td  class="second"><dfn title="Universal Host Controller Interface  (USB1)">uhci</dfn> <dfn title="bus  mastering">bus_master</dfn> </td></tr>
              <tr><td class="first">configuration:</td><td  class="second"><table summary="configuration of  usb:3"><tr><td class="sub-first">  driver</td><td>=</td><td>uhci_hcd</td></tr><tr><td  class="sub-first">  latency</td><td>=</td><td>0</td></tr></table></td></tr>
              <tr><td class="first">resources:</td><td  class="second"><table summary="resources of  usb:3"><tr><td class="sub-first">   irq</td><td>:</td><td>16</td></tr><tr><td  class="sub-first">  ioport</td><td>:</td><td>1880(size=32)</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of usb:4">
 <thead><tr><td class="first">id:</td><td class="second"><div  class="id">usb:4</div></td></tr></thead>
 <tbody>
              <tr><td class="first">description: </td><td  class="second">USB Controller</td></tr>
              <tr><td class="first">product: </td><td  class="second">N10/ICH 7 Family USB2 EHCI  Controller</td></tr>
             <tr><td  class="first">vendor: </td><td class="second">Intel  Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div  class="id">1d.7</div></td></tr>
              <tr><td class="first">bus info: </td><td  class="second"><div  class="id">pci@0000:00:1d.7</div></td></tr>
             <tr><td class="first">version: </td><td class="second">02</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
              <tr><td class="first">capabilities: </td><td  class="second"><dfn title="Power Management">pm</dfn>  <dfn title="Debug port">debug</dfn> <dfn title="Enhanced  Host Controller Interface (USB2)">ehci</dfn> <dfn title="bus  mastering">bus_master</dfn> <dfn title="PCI capabilities  listing">cap_list</dfn> </td></tr>
              <tr><td class="first">configuration:</td><td  class="second"><table summary="configuration of  usb:4"><tr><td class="sub-first">  driver</td><td>=</td><td>ehci_hcd</td></tr><tr><td  class="sub-first">  latency</td><td>=</td><td>0</td></tr></table></td></tr>
              <tr><td class="first">resources:</td><td  class="second"><table summary="resources of  usb:4"><tr><td class="sub-first">  irq</td><td>:</td><td>23</td></tr><tr><td  class="sub-first">  memory</td><td>:</td><td>f0444000-f04443ff</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of pci:2">
 <thead><tr><td class="first">id:</td><td class="second"><div  class="id">pci:2</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">PCI bridge</td></tr>
              <tr><td class="first">product: </td><td  class="second">82801 Mobile PCI Bridge</td></tr>
              <tr><td class="first">vendor: </td><td  class="second">Intel Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div  class="id">1e</div></td></tr>
              <tr><td class="first">bus info: </td><td  class="second"><div  class="id">pci@0000:00:1e.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">e2</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
              <tr><td class="first">capabilities: </td><td  class="second"><dfn title="">pci</dfn> <dfn  title="">subtractive_decode</dfn> <dfn title="bus  mastering">bus_master</dfn> <dfn title="PCI capabilities  listing">cap_list</dfn> </td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node" summary="attributes of isa">
 <thead><tr><td class="first">id:</td><td class="second"><div  class="id">isa</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">ISA bridge</td></tr>
              <tr><td class="first">product: </td><td  class="second">82801GBM (ICH7-M) LPC Interface  Bridge</td></tr>
             <tr><td  class="first">vendor: </td><td class="second">Intel  Corporation</td></tr>
             <tr><td class="first">physical id: </td><td class="second"><div  class="id">1f</div></td></tr>
              <tr><td class="first">bus info: </td><td  class="second"><div  class="id">pci@0000:00:1f.0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">02</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
              <tr><td class="first">capabilities: </td><td  class="second"><dfn title="">isa</dfn> <dfn  title="bus mastering">bus_master</dfn> <dfn title="PCI  capabilities listing">cap_list</dfn> </td></tr>
              <tr><td class="first">configuration:</td><td  class="second"><table summary="configuration of  isa"><tr><td class="sub-first">  latency</td><td>=</td><td>0</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
<div class="indented">
                    <div class="indented">
           <table width="100%" class="node" summary="attributes of ide">
 <thead><tr><td  class="first">id:</td><td class="second"><div  class="id">ide</div></td></tr></thead>
 <tbody>
              <tr><td class="first">description: </td><td  class="second">IDE interface</td></tr>
              <tr><td class="first">product: </td><td  class="second">82801GBM/GHM (ICH7 Family) SATA IDE  Controller</td></tr>
             <tr><td  class="first">vendor: </td><td class="second">Intel  Corporation</td></tr>
             <tr><td  class="first">physical id: </td><td class="second"><div class="id">1f.2</div></td></tr>
              <tr><td class="first">bus info: </td><td  class="second"><div  class="id">pci@0000:00:1f.2</div></td></tr>
              <tr><td class="first">logical name: </td><td  class="second"><div  class="id">scsi0</div></td></tr>
             <tr><td class="first">version: </td><td class="second">02</td></tr>
             <tr><td class="first">width: </td><td class="second">32  bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">66MHz</td></tr>
              <tr><td class="first">capabilities: </td><td  class="second"><dfn title="">ide</dfn> <dfn  title="Power Management">pm</dfn> <dfn title="bus  mastering">bus_master</dfn> <dfn title="PCI capabilities  listing">cap_list</dfn> <dfn title="Emulated  device">emulated</dfn> </td></tr>
              <tr><td class="first">configuration:</td><td  class="second"><table summary="configuration of  ide"><tr><td class="sub-first">   driver</td><td>=</td><td>ata_piix</td></tr><tr><td  class="sub-first">  latency</td><td>=</td><td>0</td></tr></table></td></tr>
              <tr><td class="first">resources:</td><td  class="second"><table summary="resources of  ide"><tr><td class="sub-first">  irq</td><td>:</td><td>19</td></tr><tr><td  class="sub-first">  ioport</td><td>:</td><td>1f0(size=8)</td></tr><tr><td  class="sub-first">  ioport</td><td>:</td><td>3f6</td></tr><tr><td  class="sub-first">  ioport</td><td>:</td><td>170(size=8)</td></tr><tr><td  class="sub-first">   ioport</td><td>:</td><td>376</td></tr><tr><td  class="sub-first">  ioport</td><td>:</td><td>1810(size=16)</td></tr></table></td></tr>
 </tbody>          </table></div>
<div class="indented">
                          <div class="indented">
             <table width="100%" class="node" summary="attributes of disk">
 <thead><tr><td class="first">id:</td><td class="second"><div  class="id">disk</div></td></tr></thead>
 <tbody>
                 <tr><td class="first">description: </td><td  class="second">ATA Disk</td></tr>
                <tr><td class="first">product: </td><td class="second">ST9250315AS</td></tr>
                <tr><td class="first">vendor: </td><td class="second">Seagate</td></tr>
                <tr><td class="first">physical id: </td><td class="second"><div  class="id">0.0.0</div></td></tr>
                 <tr><td class="first">bus info: </td><td  class="second"><div  class="id">scsi@0:0.0.0</div></td></tr>
                 <tr><td class="first">logical name: </td><td  class="second"><div  class="id">/dev/sda</div></td></tr>
                <tr><td class="first">version: </td><td class="second">0001</td></tr>
                <tr><td class="first">serial: </td><td  class="second">5VC9QHL5</td></tr>
                <tr><td class="first">size: </td><td class="second">232GiB (250GB)</td></tr>
                 <tr><td class="first">capabilities: </td><td  class="second"><dfn title="Partitioned  disk">partitioned</dfn> <dfn title="MS-DOS partition  table">partitioned:dos</dfn> </td></tr>
                 <tr><td class="first">configuration:</td><td  class="second"><table summary="configuration of  disk"><tr><td class="sub-first">  ansiversion</td><td>=</td><td>5</td></tr><tr><td  class="sub-first">   signature</td><td>=</td><td>00098aee</td></tr></table></td></tr>
 </tbody>             </table></div>
<div class="indented">
                                <div class="indented">
                <table width="100%" class="node" summary="attributes of volume:0">
 <thead><tr><td class="first">id:</td><td class="second"><div  class="id">volume:0</div></td></tr></thead>
 <tbody>
                    <tr><td class="first">description: </td><td  class="second">EXT4 volume</td></tr>
                   <tr><td class="first">vendor: </td><td class="second">Linux</td></tr>
                    <tr><td class="first">physical id: </td><td  class="second"><div  class="id">1</div></td></tr>
                   <tr><td class="first">bus info: </td><td  class="second"><div class="id">scsi@0:0.0.0,1</div></td></tr>
                    <tr><td class="first">logical name: </td><td  class="second"><div  class="id">/dev/sda1</div></td></tr>
                    <tr><td class="first">logical name: </td><td  class="second"><div  class="id">/</div></td></tr>
                   <tr><td class="first">version: </td><td class="second">1.0</td></tr>
                   <tr><td  class="first">serial: </td><td class="second">64c4bca0-b840-4e4d-89e6-2f97d0a6e96f</td></tr>
                   <tr><td class="first">size: </td><td class="second">227GiB</td></tr>
                   <tr><td class="first">capacity: </td><td class="second">227GiB</td></tr>
                    <tr><td class="first">capabilities: </td><td  class="second"><dfn title="Primary  partition">primary</dfn> <dfn title="Bootable partition  (active)">bootable</dfn> <dfn  title="">journaled</dfn> <dfn title="Extended  Attributes">extended_attributes</dfn> <dfn title="4GB+  files">large_files</dfn> <dfn title="16TB+  files">huge_files</dfn> <dfn title="directories with 65000+  subdirs">dir_nlink</dfn> <dfn title="needs  recovery">recover</dfn> <dfn title="extent-based  allocation">extents</dfn> <dfn title="">ext4</dfn>  <dfn title="EXT2/EXT3">ext2</dfn> <dfn title="initialized  volume">initialized</dfn> </td></tr>
                    <tr><td class="first">configuration:</td><td  class="second"><table summary="configuration of  volume:0"><tr><td class="sub-first">  created</td><td>=</td><td>2010-11-12  18:11:24</td></tr><tr><td class="sub-first">   filesystem</td><td>=</td><td>ext4</td></tr><tr><td  class="sub-first">  lastmountpoint</td><td>=</td><td>/&#1764;}O&#65533;u&#65533;&#65533;&#65533;,&#65533;&#65533;&#65533;P&#65533;M&#65533;q!&#65533;&#65533;,&#65533;&#65533;@&#65533;M&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;u&#65533;&#65533;A&#65533;h&#65533;M&#65533;It!&#65533;&#65533;j</td></tr><tr><td  class="sub-first">  modified</td><td>=</td><td>2011-03-01  17:26:53</td></tr><tr><td class="sub-first">  mount.fstype</td><td>=</td><td>ext4</td></tr><tr><td  class="sub-first">  mount.options</td><td>=</td><td>rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered</td></tr><tr><td  class="sub-first">  mounted</td><td>=</td><td>2011-03-02  12:45:02</td></tr><tr><td class="sub-first">   state</td><td>=</td><td>mounted</td></tr></table></td></tr>
 </tbody>                </table></div>
                </div>
<div class="indented">
                                <div class="indented">
                <table width="100%" class="node" summary="attributes of volume:1">
 <thead><tr><td class="first">id:</td><td class="second"><div  class="id">volume:1</div></td></tr></thead>
 <tbody>
                    <tr><td class="first">description: </td><td  class="second">Extended partition</td></tr>
                    <tr><td class="first">physical id: </td><td  class="second"><div  class="id">2</div></td></tr>
                    <tr><td class="first">bus info: </td><td  class="second"><div  class="id">scsi@0:0.0.0,2</div></td></tr>
                     <tr><td class="first">logical name: </td><td  class="second"><div  class="id">/dev/sda2</div></td></tr>
                   <tr><td class="first">size: </td><td class="second">5999MiB</td></tr>
                   <tr><td class="first">capacity: </td><td class="second">5999MiB</td></tr>
                    <tr><td class="first">capabilities: </td><td  class="second"><dfn title="Primary  partition">primary</dfn> <dfn title="Extended  partition">extended</dfn> <dfn title="Partitioned  disk">partitioned</dfn>  <dfn title="Extended partition">partitioned:extended</dfn>  </td></tr>
 </tbody>                </table></div>
<div class="indented">
                                      <div class="indented">
                   <table width="100%" class="node" summary="attributes of logicalvolume">
 <thead><tr><td class="first">id:</td><td class="second"><div  class="id">logicalvolume</div></td></tr></thead>
 <tbody>
                       <tr><td class="first">description: </td><td  class="second">Linux swap / Solaris partition</td></tr>
                       <tr><td class="first">physical id: </td><td  class="second"><div  class="id">5</div></td></tr>
                      <tr><td class="first">logical name: </td><td class="second"><div  class="id">/dev/sda5</div></td></tr>
                       <tr><td class="first">capacity: </td><td  class="second">5999MiB</td></tr>
                       <tr><td class="first">capabilities: </td><td  class="second"><dfn title="No filesystem">nofs</dfn>  </td></tr>
 </tbody>                   </table></div>
                   </div>
                 </div>
             </div>
          </div>
<div class="indented">
                    <div class="indented">
          <table width="100%" class="node-unclaimed" summary="attributes of serial">
 <thead><tr><td  class="first">id:</td><td class="second"><div  class="id">serial</div></td></tr></thead>
 <tbody>
             <tr><td class="first">description: </td><td class="second">SMBus</td></tr>
             <tr><td  class="first">product: </td><td class="second">N10/ICH 7 Family SMBus Controller</td></tr>
              <tr><td class="first">vendor: </td><td  class="second">Intel Corporation</td></tr>
              <tr><td class="first">physical id: </td><td  class="second"><div  class="id">1f.3</div></td></tr>
              <tr><td class="first">bus info: </td><td  class="second"><div  class="id">pci@0000:00:1f.3</div></td></tr>
             <tr><td class="first">version: </td><td  class="second">02</td></tr>
             <tr><td class="first">width: </td><td class="second">32 bits</td></tr>
             <tr><td class="first">clock: </td><td class="second">33MHz</td></tr>
              <tr><td class="first">configuration:</td><td  class="second"><table summary="configuration of  serial"><tr><td class="sub-first">  latency</td><td>=</td><td>0</td></tr></table></td></tr>
              <tr><td class="first">resources:</td><td  class="second"><table summary="resources of  serial"><tr><td class="sub-first">  ioport</td><td>:</td><td>18a0(size=32)</td></tr></table></td></tr>
 </tbody>          </table></div>
          </div>
       </div>
    </div>
<div class="indented">
        <div class="indented">
    <table width="100%" class="node" summary="attributes of battery">
 <thead><tr><td  class="first">id:</td><td class="second"><div  class="id">battery</div></td></tr></thead>
 <tbody>
       <tr><td class="first">description: </td><td class="second">Lithium Ion  Battery</td></tr>
       <tr><td class="first">product: </td><td class="second">Intel Corporation</td></tr>
       <tr><td class="first">vendor: </td><td class="second">Intel Corporation</td></tr>
        <tr><td class="first">physical id: </td><td  class="second"><div  class="id">1</div></td></tr>
       <tr><td class="first">slot: </td><td class="second">Rear</td></tr>
       <tr><td class="first">capacity: </td><td class="second">1000mWh</td></tr>
        <tr><td class="first">configuration:</td><td  class="second"><table  summary="configuration of battery"><tr><td  class="sub-first">  voltage</td><td>=</td><td>0.0V</td></tr></table></td></tr>
 </tbody>    </table></div>
    </div>
<div class="indented">
        <div class="indented">
    <table width="100%" class="node-unclaimed" summary="attributes of remoteaccess">
 <thead><tr><td  class="first">id:</td><td class="second"><div  class="id">remoteaccess</div></td></tr></thead>
 <tbody>
       <tr><td class="first">vendor: </td><td class="second">Intel</td></tr>
       <tr><td class="first">physical id: </td><td  class="second"><div class="id">2</div></td></tr>
        <tr><td class="first">capabilities: </td><td  class="second"><dfn title="receive inbound  connections">inbound</dfn> </td></tr>
 </tbody>    </table></div>
    </div>
<div class="indented">
        <div class="indented">
    <table width="100%" class="node-disabled" summary="attributes of network">
 <thead><tr><td  class="first">id:</td><td class="second"><div  class="id">network</div></td></tr></thead>
 <tbody>
       <tr><td class="first">description: </td><td class="second">Ethernet  interface</td></tr>
       <tr><td  class="first">physical id: </td><td  class="second"><div  class="id">3</div></td></tr>
        <tr><td class="first">logical name: </td><td  class="second"><div  class="id">vboxnet0</div></td></tr>
       <tr><td class="first">serial: </td><td class="second">0a:00:27:00:00:00</td></tr>
        <tr><td class="first">capabilities: </td><td  class="second"><dfn title="">ethernet</dfn> <dfn  title="Physical interface">physical</dfn>  </td></tr>
       <tr><td  class="first">configuration:</td><td  class="second"><table summary="configuration of  network"><tr><td class="sub-first">  broadcast</td><td>=</td><td>yes</td></tr><tr><td  class="sub-first">  multicast</td><td>=</td><td>yes</td></tr></table></td></tr>
 </tbody>    </table></div>
    </div>
</body>
</html>

```

---

### Post by Grenage on 2011-03-03
I haven't used it in a while, but the alternative network manager 'wicd' might be worth a go.  A version or two ago, I used it when having issues with different connections; it had a decent GUI.

---

### Post by moody_mark on 2011-03-03
Hi,

Ive seen some issues with one machine intermittently logging into a BTHomeHub on a Dell E6400 laptop and then no problems with a Dell 610 laptop. It could be the wireless driver in Ubuntu.

Theres the connection between the machine and the hub (the wireless) and then the hub out to the internet. Im assuming the internet connection is ok. Im also assuming the HomeHub connection seems intermittent.

However try these simple steps first, if you havent already (I dont want to be 

1. Connect the ubuntu machine to the HomeHub with an ethernet cable, make sure you have an ip address (usually 192.168.0.1), make sure you can ping the HomeHub (usually 192.168.0.254)
2. Login to the HomeHub in a browser [http://192.168.0.254](http://192.168.0.254)
3. Navigate to the wireless settings, and try swapping the channel number
4. Back in ubuntu delete all the wireless connections, right click NM icon, select edit connections and delete all of them.
5. Logout / login or disable enable networking, (right click NM icon, uncheck enable networking, then recheck)
6. Select the HomeHub, and enter the wireless key, see if it connects

Hope this helps some, sorry if you already done all this though :)

---

### Post by demonboy on 2011-03-03
> **Grenage said:**
> I haven't used it in a while, but the alternative network manager 'wicd' might be worth a go.  A version or two ago, I used it when having issues with different connections; it had a decent GUI.

I've been tempted to give that one a go myself. I'll have a play with it before suggesting it to me dad. Thanks.

---

### Post by nickdc on 2011-03-04
> **demonboy said:**
> I've been tempted to give that one a go myself. I'll have a play with it before suggesting it to me dad. Thanks.

Obviously worth a try, but it hasn't worked for me, I get exactly the same problems with it as with the default NM. Btw, just to confirm what others have said: for your dad to try any of the BT signals other then the HomeHub is a distraction; I've found this many times at the homes of friends running from a BT hub. You appear to get a connection, but then there's some kind of firewall that prevents further internet progress. I'm still trying to resolve my situation. If I make any progress I'll post. Best of luck.

---

### Post by robsoles on 2011-03-04
Just regarding 'the missing opening tags' from the output of that command:


To get the full output of a command to post you can put it in a file, like this:

```
 [COLOR=Red]sudo[/COLOR] lshw -html >> ~/Desktop/this-file-should-land-on-my-desktop.txt
```<edited-in>Although, being HTML it would probably be better to make the filename "system-hardware.html" - then you could double click it on the desktop and see it as it's meant to be seen :)</edited-in>

---

