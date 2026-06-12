---
title: "no more wireless after update"
date: 2007-04-11
forum: Networking &amp; Wireless
---

### Post by jputman01 on 2007-04-11
alright i have seen a couple of these threads around, but none the had a solution

my wireless was working just fine, then update-manager said i needed updates, i installed them as usual and poof no more wireless, the light still comes on but when i click on network manager it doesnt list wireless as an option.

ifconfig states:
```
eth0      Link encap:Ethernet  HWaddr 00:16:36:EF:6B:91  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:feef:6b91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:92 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50529 (49.3 KiB)  TX bytes:20901 (20.4 KiB)
          Interrupt:10 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:1A:73:21:9E:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:9 Memory:b8000000-b8004000 

eth1:avah Link encap:Ethernet  HWaddr 00:1A:73:21:9E:29  
          inet addr:169.254.4.169  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:9 Memory:b8000000-b8004000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:556 (556.0 b)  TX bytes:556 (556.0 b)
```

which is weird because i dont remember having and eth1 and an eth1:avah, anyone have an idea?

iwconfig states:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

in network configuration i can click on wireless and then on properties, i can see available networks but i cant connect to any of them. i can scan thru terminal and find networks but cant connect to any, anybody have any ideas how to get this working again. thanks for your help!!

---

### Post by christian.convey on 2007-04-11
It's a long shot, but this is possibly related to a bug I reported today:
[https://bugs.launchpad.net/ubuntu/+bug/105707](https://bugs.launchpad.net/ubuntu/+bug/105707)

I say that because my system has started freezing somewhat frequently, and I've noticed that it correlates with some WiFi oddity I've had today as well.

I'm running a Centrino-based laptop with Intel WiFi.  Here's the relevant line from my "lspci" output:

06:05.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

Are you running similar WiFi hardware?

---

### Post by pgroover on 2007-04-12
I'm having almost the same problem but without the unknown network device.  After the update I haven't been able to connect to any wireless network at all.  What I have noticed is that, like christian.convey, NetworkManager does not display any facet of wireless ability at all.

iwconfig displays the correct information for the connection(s) that I try to connect to but nothing I do can get me connected.  I've looked at dmesg and don't see anything irregular but I haven't really scrutinized it either.

Just to post this message I have to boot into windows so I'll jump back over here in a bit and give it another shot before I call it a night.

Hopefully there will be a solution to this soon.

---

### Post by christian.convey on 2007-04-12
I'm actually starting to conclude that this is a hardware problem, because I've seen similar problems in Windows.  I'm bringing the laptop in for repair tomorrow.

---

### Post by pgroover on 2007-04-12
Maybe so in your case, however I've just booted back into windows and have yet to have a problem at all.

Oh well, I'll just keep "playing around" with it and more than likely end up using it as a stand alone system until it's "cured"...

---

### Post by ugurdy on 2007-04-12
I have exactly same problem both my laptop and desktop. I have open the protection of my router and I am able to connect internet now.But it is not secure and also my network management tool is gone, too.Hopefully it will be ok soon.

---

### Post by k5cqb on 2007-04-12
Yup, I just did the updates and whenI restarted network-manager started but didn't recognize any wireless options.  It allowed me to click on the static address option but when I checked the wireless configuration on networking, network manager disappeared.  I reinstalled it via synaptic manager but still no wireless capability.

---

### Post by jputman01 on 2007-04-12
yes i can click on network manager and it will not display anything about wireless at all, if i go to system->admin->network i can click properties for wireless and see networks there but not connect to any!!!! i hope this get fixed

---

### Post by pgroover on 2007-04-12
You're lucky you can see networks.  The only way I can see them is by using iwlist as I get nothing from the GUI at all.

---

### Post by Mr Squiddy on 2007-04-12
Exactly the same problem for me with an Intel Pro 2200 card.  I can see networks but can't connect to them and there is no wireless option in nm-applet.

I have another laptop with Feisty and the Intel card - can someone confirm precisely what is broken here so I can avoid updating it - is is nm-applet?

---

### Post by jputman01 on 2007-04-12
> **pgroover said:**
> You're lucky you can see networks.  The only way I can see them is by using iwlist as I get nothing from the GUI at all.

are you using gnome? if so can you not go to system->admin->network then click on wireless (make sure its checkbox is checked) then click properties, from there you should see a spot for the essid if you click the drop arrow next to it you should see some networks available, what happens if you go there?

---

### Post by jputman01 on 2007-04-12
> **Mr Squiddy said:**
> Exactly the same problem for me with an Intel Pro 2200 card.  I can see networks but can't connect to them and there is no wireless option in nm-applet.

I have another laptop with Feisty and the Intel card - can someone confirm precisely what is broken here so I can avoid updating it - is is nm-applet?

in not exactly sure which update killed it because the update had somewhere around 160 updates in it, wish i knew which one, im afraid im going to have to reinstall and start fresh to get it working again unless anyone can help:(

---

### Post by Mr Squiddy on 2007-04-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105825](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105825) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				It looks like the bug has been recorded already:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105825](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105825)

It seems that network-manager 0.6.4-6ubuntu6 is the culprit.  Obvious question:  is there any way to downgrade to the previous version whilst this bug is fixed?

---

### Post by pgroover on 2007-04-12
> **jputman01 said:**
> are you using gnome? if so can you not go to system->admin->network then click on wireless (make sure its checkbox is checked) then click properties, from there you should see a spot for the essid if you click the drop arrow next to it you should see some networks available, what happens if you go there?

Yes, I am using gnome but I rarely use NetworkManager as I'm typically at the command line for connections.  I'll have to check it when I get home since I'm at work right not. Based on what you say it's just a "feature" that I didn't know it had. :)

---

### Post by Mr Squiddy on 2007-04-12
Well I seemed to have fixed the issue but it's a bit of a hack and I can't guarantee that you won't get into a whole world of pain with it!!  For a start it upsets the Update Manager which tells you that the 'Software index is broken'.  But if you are desperate you might be able to live with that.

In /var/cache/apt/archives/ there is the previous network-manager .deb file, in this case it is called network-manager_0.6.4-6ubuntu4_i386.deb .  I simply ran dpkg to install this older package:

sudo dpkg -i /var/cache/apt/archives/network-manager_0.6.4-6ubuntu4_i386.deb

After a restart the wireless is now working.  Clearly if you assiduously clean the old packages off every time you do an upgrade then you will not be able to use this option.

---

### Post by jputman01 on 2007-04-12
> **Mr Squiddy said:**
> Well I seemed to have fixed the issue but it's a bit of a hack and I can't guarantee that you won't get into a whole world of pain with it!!  For a start it upsets the Update Manager which tells you that the 'Software index is broken'.  But if you are desperate you might be able to live with that.

In /var/cache/apt/archives/ there is the previous network-manager .deb file, in this case it is called network-manager_0.6.4-6ubuntu4_i386.deb .  I simply ran dpkg to install this older package:

sudo dpkg -i /var/cache/apt/archives/network-manager_0.6.4-6ubuntu4_i386.deb

After a restart the wireless is now working.  Clearly if you assiduously clean the old packages off every time you do an upgrade then you will not be able to use this option.

that may be worth a shot, i wish i would have looked through all of the updates before i hit install!!

---

### Post by ajmctaggart on 2007-04-12
it works, revising to archived n-m did work, it'll show that you have no connection but click on n-m applet and your cool, just a big red x all the time on the applet.

I am just really getting into feisty, but if a fix to this n-m release is made available, will running a "sudo apt-get install -f" pull me the right update?  right now i think ill have to do w/o anymore feisty updates...

---

### Post by MrFalcon on 2007-04-12
hmmm, It seems that I have the same problem .. but here is one thing .. when I stoped the restricted Device, which is the ATI Radion X700, I got back my wireless network to work .. I don't know if it is the exact same problem though.  I wish it can help in any ways. :(

---

### Post by k5cqb on 2007-04-12
I have the same symptoms.  I checked and couldn't find that version of network manager in my archives.  So I uninstalled network manager via synaptic manager and connected right up.  Well I am doing another update but I checked and didn't see a network manager in there so here goes.  So try and uninstall net-manager and see if that helps, look for more that one, I had two.  Good Luck.

---

### Post by ajmctaggart on 2007-04-12
Great, Thanks- I may try to uninstall all n-m's and reinstall later, would that take away my archived copy as well?  Just in case it doesn't work...

Im just glad to be up and running for work right now, my Powerbook is in my bag, Terminal Services client is faster to connect to my Windoze box than Microsoft's own RDP for Mac...go figure

---

### Post by jputman01 on 2007-04-12
> **k5cqb said:**
> I have the same symptoms.  I checked and couldn't find that version of network manager in my archives.  So I uninstalled network manager via synaptic manager and connected right up.  Well I am doing another update but I checked and didn't see a network manager in there so here goes.  So try and uninstall net-manager and see if that helps, look for more that one, I had two.  Good Luck.

I tried reinstalling network manager last night and that didnt work, if i uninstall network manager do you just connect thru the terminal??

---

### Post by pgroover on 2007-04-12
> **Mr Squiddy said:**
> Well I seemed to have fixed the issue but it's a bit of a hack and I can't guarantee that you won't get into a whole world of pain with it!!  For a start it upsets the Update Manager which tells you that the 'Software index is broken'.  But if you are desperate you might be able to live with that.

In /var/cache/apt/archives/ there is the previous network-manager .deb file, in this case it is called network-manager_0.6.4-6ubuntu4_i386.deb .  I simply ran dpkg to install this older package:

sudo dpkg -i /var/cache/apt/archives/network-manager_0.6.4-6ubuntu4_i386.deb

After a restart the wireless is now working.  Clearly if you assiduously clean the old packages off every time you do an upgrade then you will not be able to use this option.

Thanks for the tip, I'll definitely give that a shot when I get back to my system.  If it turns out that I can't find it then I'll just go with the uninstall option and see where that puts me.  I wonder how long it will be before we see a fix to this one, my guess is not too long as it seems to have affected quite a few different people with varying hardware.

---

### Post by reauthor on 2007-04-12
Hy guys I have the same problem.After update network-manager-gnome doesnt work in Feisty(wireless problem)...I tried so many combination and nothing...So, I was reinstalling my system and update again except network-manager & network-manager-gnome and all works fine...Maybe this can be helpfull...

---

### Post by paddygman on 2007-04-12
hey guys dunno if my prob is the same i've got network manager uninstalled but my network card rt2500 does not show up in system>administration>networking. This only happened recently as before some updates dunno which (probably network manager) it worked fine. I realise that NM has issues with the rt2500 and WPA but it should still show up as a connection in system>administration>networking as its listed in device manager. Any ideas anyone, think this may be unrelated to the bug discussed here as I'm still on edgy but wi some updates.
Anyone??

---

### Post by pgroover on 2007-04-13
Well, I got my wireless to work without uninstalling NetworkManager or lowering my security settings (at least for the time being).  As a punting maneuver I enabled Roaming mode" within NM and connected immediately to my network.

I don't know if anyone else had it disabled or not, but it's definitely worth a shot.

---

### Post by jputman01 on 2007-04-13
> **pgroover said:**
> Well, I got my wireless to work without uninstalling NetworkManager or lowering my security settings (at least for the time being).  As a punting maneuver I enabled Roaming mode" within NM and connected immediately to my network.

I don't know if anyone else had it disabled or not, but it's definitely worth a shot.

ill give it a shot, i got some more updates this morning and one of them said new "network manager," I was excited because I thought it would fix my issue, however I still cannot connect via wireless and network manager still isnt listing wireless as an option

also it looks like there was a kernal update in this mornings update and it wouldnt download, it kept saying "error: restricted" anyone know why?

---

### Post by pgroover on 2007-04-13
> **jputman01 said:**
> ill give it a shot, i got some more updates this morning and one of them said new "network manager," I was excited because I thought it would fix my issue, however I still cannot connect via wireless and network manager still isnt listed wireless as an option

also it looks like there was a kernal update in this mornings update and it would download it, it kept saying "error: restricted" anyone know why?

The only thing I can guess about the update being restricted may have to do with the kernel update causing boot failures.  If you are able to update and can't boot afterwards  you either boot into an older kernel or rename the overwritten version of it (2.6.20-14-generic.bak -> 2.6.20-14-generic) within your boot directory.

Alternatively, you could simply update your menu.lst file to point to the old one...

As for the wireless fix I made, so far so good... :)

---

### Post by jputman01 on 2007-04-13
geez my sorry about my previous post, must have been typing too fast, i corrected most of it.

there were a bunch of updates and all of them downloaded and installed just fine except for the new kernal, im going to try roam mode when i get home and see what happens

---

### Post by jputman01 on 2007-04-13
IM BAAACK!!!! thanks for the tip pgroover on the roaming mode. 
 
so i came home from work and started messing with this thing. i uninstalled NM. after that i could not even scan for networks via terminal. i messed with it for a little while and nothing would work. so i reinstalled NM, still no go. then i remembered that pgroover said it worked on roam mode so i tried it and bam! there is a list of networks in NM now, sooo happy, but then it wouldnt stay connected, it connected for a few seconds then disonn and reconn. then i remembered that i had been messing with my /etc/network/interfaces so i had to go back and make sure everything was commented out except lo and eth1 and now i stay connected.

one more question, i never had this before the update that killed my wireless, what is the difference in eth1 and eth1:avah it was in my terminal when i did ifconfig before i switched to roam mode

---

### Post by Bert Mariën on 2007-04-13
When I upgraded Edgy to Feisty bèta a few days ago I also could not connect wireless. I uninstalled the Network Manager, but that didn't seem to do the trick.
I DID have Wifi-Radar installed. I ran it, configured the connection and everything went smooth from there on.
So I suggest people with wireless network problems to try to use Wifi-Radar to establish their connection. It worked for me anyhow, and... no fuss at all.

---

### Post by pgroover on 2007-04-14
> **jputman01 said:**
> IM BAAACK!!!! thanks for the tip pgroover on the roaming mode. 
 
so i came home from work and started messing with this thing. i uninstalled NM. after that i could not even scan for networks via terminal. i messed with it for a little while and nothing would work. so i reinstalled NM, still no go. then i remembered that pgroover said it worked on roam mode so i tried it and bam! there is a list of networks in NM now, sooo happy, but then it wouldnt stay connected, it connected for a few seconds then disonn and reconn. then i remembered that i had been messing with my /etc/network/interfaces so i had to go back and make sure everything was commented out except lo and eth1 and now i stay connected.

one more question, i never had this before the update that killed my wireless, what is the difference in eth1 and eth1:avah it was in my terminal when i did ifconfig before i switched to roam mode

No problem, just glad it worked for you! :D

---

### Post by pak33m on 2007-06-18
Anybody know if this is an issue still in Feistyl? 

Or where I can download a copy of network-manager_0.6.4-6ubuntu4_i386.deb becasue I don't have it in my apt archives?

I recetly upgraded my System76 laptop from Edgy to Feisty bu the problem did not start until after I installed network-manager-vpnc.

---

