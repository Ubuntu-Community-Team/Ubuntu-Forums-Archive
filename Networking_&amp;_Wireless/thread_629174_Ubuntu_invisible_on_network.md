---
title: "Ubuntu invisible on network"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by de_valentin on 2007-12-02
Hello Everyone,

I've done a lot of searches on this and it appears not to have been solved untill now (hopefully) and it starts to become very annoying. 

The problem is that we have a windows home network and with the ubuntu machines we can explore the network and all the windows shares including the server. We can copy/paste etc, just as it is supposed to work. But here it comes the ubuntu computers do not show in the home network. The ubuntu pc's can't see each other as well.

I installed xp in virtualbox and when that is turned on it shows in the network with the default windows shared folders.

When I go to “Places>network>Windows network>Thuis” it only shows windows pc's, so not even the pc I'm working from at that moment. 

This also is a problem getting the printer to work that is on the other ubuntu computer, it's no problem on the pc it is hooked up to.

I've tried this HOWTO
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) 
and many others I can't seem to find right now. None of them got the job done.

In System>admin> Network>connections
wired connection 
this network interface is not configured.

>General
host name: valentin (this is the computername)
domain name: THUIS (this is the name of the network)

>DNS
DNS servers: 192.168.1.1
search domains: empty

System>admin>Shared Folders
Shared folders (tab) it shows the folders I want to share
General Properties(tab)
Domain/Workgroup: THUIS
this computer is a WINS server (box) not ticked
WINS server:192.168.1.1

System>preferences>Network proxy
all default settings

I hope this is enough information, if not just ask.
Thanks in advance for helping out.

---

### Post by tact on 2007-12-02
Have you tried to share a folder on the ubuntu boxes?   The first time you share a folder to the windows network (SMB) you are asked to allow the system to install some software.   Obviously this software is what makes your share available to the windows network and equally logical: until its installed you wont be sharing anything to windows network.

If you haven't tried to do so... just pick a folder and right click on it and select share folder.  Let the system install software and configure...  after that your ubuntu systems will be seen by windows PCs.

Note:  By default ubuntu sets up windows network sharing in such a way that that it demands a few levels of security more than windows machines do on a windows network.

 - for remote users to access files/folders on your ubuntu PC (with default settings) firstly they will need to have a user account ON the ubuntu machine.   

- secondly you need to ensure that the shared folder/files have permissions set that allow the kind of access you want others to have (i.e. read, read./write) etc.

You can change the default behaviour so that ubuntu acts as insecurely as windows and just shares to all and sundry without needing username/password/account etc...

---

### Post by de_valentin on 2007-12-02
Yes I did make shared folders and I did install the 2 pieces of software samba and NFS.

I unchecked the box for read only in the shared folders.

In the howto I had to make a user, but that didn't help either.

I wouldn't mind to change the default to be as unsafe as windows is.

---

### Post by tact on 2007-12-02
Ok - a few more ideas to toss out there....

1.  Do you have the windows boxes and ubuntu boxes all on the same "workgroup"?
(you have to edit /etc/samba/smb.conf to change ubuntu machines from the default "mshome" to whatever workgroup the windows boxes are using)

Back up your smb.conf before touching it...
sudo cp /etc/samba/smb.conf  /etc/samba/smb.conf.original  

Then edit it
```
gksudo gedit /etc/samba/smb.conf
```

you will find a line in that file "workgroup = mshome".   Change "mshome" to whatever is same as your windows machines.

you might like to add a line (if it does not already exist) 
netbios name = your_ubuntu_box's_hostname

And to make it so that any one browsing your network can see and access shares... find a line that says ";   security = user"   -  remove the semicolon and change it to read "security = share"

(this may be convenient like in windows but not the best way to do things... your own risk).

You will need to restart samba to have the changes take effect 
```
sudo /etc/init.d/samba restart
```

2.  no fault of ubuntu or linux - microsoft networking, how it works, can mean that it MAY take a long time before shares/pc's show up in network neighbourhood/network places etc....talking from a minute to 40 minutes.

To check if your config is working at all and be sure that its not just the time dependency that windows networking sometimes has - on the windows box, open your network places, click on find a computer, and type in the ubuntu computer's name (or IP address)...  and see if windows can "find" the computer even if it doesnt show up in the network browser already.

3.   hmmm I forgot what I was going to write as no3.   ;)

---

### Post by tact on 2007-12-02
just re-reading your original post - sorry for asking if you had tried sharing folders before, stupid Q - you said you had.

I note you have 192.168.1.1 listed as DNS and WINS server in your ubuntu configs...  is that machine really able to act as WINS and DNS server?

I also note that your "PC1" and "PC2" are on a different subnet to the NAS box you are using as a router....  does it have to be that way?   
192.168.2.131 and 192.168.2.132 are on the same subnet.  But 192.168.1.1 and 192.168.1.10 are not.

Ideally all should be on 192.168.2.x or all on 192.168.1.x  -  not some on one subnet and some on another.  (Windows networking does not traverse subnets unless you have WINS servers working properly.  I am not sure you have WINS set up properly (you have winbind installed and edited /etc/nsswitch.conf at some time before?).  Even if you have whether that will work when the WINS server is on one subnet and the PC's on another...)

Are PC1 and PC2 representative of both windows and ubuntu machines?  Are the windows machines and ubuntu machines on the same subnet?

---

### Post by tact on 2007-12-02
Just looking over your diagram...  maybe try to simplify what you have and see its all working.

adsl modem is 192.168.1.1  
NAS/router is 192.168.1.10  (are you using DHCP to give the other PC's IP addresses?)

whether manual or DHCP have your PC's on the same subnet:
PC1   192.168.1.132
PC2  192.168.1.133

Netmask everywhere is 255.255.255.0
default gateway for PC1 & PC2 is 192.168.1.10

See if that solves why the windows boxes cannot see the ubuntu boxes and why the ubuntu boxes cannot see each other.  (I cannot imagine why the ubuntu boxes can see the winboxes at the moment)   :)

---

### Post by tact on 2007-12-02
just did some googling....
here is a website that may be helpful as far as general info on windows networking...
[http://www.pccitizen.com/windowsnetworking.htm](http://www.pccitizen.com/windowsnetworking.htm)

This is all for windows machines doing windows networking with other windows machines and shows some of the traps they face...  getting linux on a windows network can hardly be expected to be easier.  :)

note the comments about the time it sometimes takes for network resources to show in browse lists, and also having all PC's on the same subnet.

---

### Post by de_valentin on 2007-12-03
After trying out everything I could find, I found myself without internet acces or email. and I thought of just reinstalling the entire system I know that is not the way. But for me it was the easiest way to get everything back up again. 
During the proces of reinstalling I checked to see if the ubuntu-pc was showing on the network, and it did...??? So I was happy although I couldn't get to see what was on the pc.  The next morning this morning I thought lets check it out and see if I can change the smb.conf so i could get easy acces. Unfortunately the ubuntu pc doesn't show on the network anymore so even if I would change the smb.conf I could't see the damn thing.

But on the other hand I have a completly blanc system rightnow so time to try it all again.

by the way the windows pc and the nas are visible and accesable on the network without changing a single setting.

---

### Post by tact on 2007-12-03
> **de_valentin said:**
> After trying out everything I could find, I found myself without internet acces or email. and I thought of just reinstalling the entire system I know that is not the way. But for me it was the easiest way to get everything back up again. 
During the proces of reinstalling I checked to see if the ubuntu-pc was showing on the network, and it did...??? So I was happy although I couldn't get to see what was on the pc.  The next morning this morning I thought lets check it out and see if I can change the smb.conf so i could get easy acces. Unfortunately the ubuntu pc doesn't show on the network anymore so even if I would change the smb.conf I could't see the damn thing.

But on the other hand I have a completly blanc system rightnow so time to try it all again.

by the way the windows pc and the nas are visible and accesable on the network without changing a single setting.

How are you configuring your networking?  Is the ubuntu box getting its IP address automatically via DHCP?   Or are you manually pre-setting IP address?  (to what?).

---

### Post by edm1 on 2007-12-03
I'm guessing you have firestarter installed? Alot of people are having alot of problems with firestarter making their computers invisible even after opening the supposedly necessary ports. If this is the problem sorry but i havent got a fix, if you find one please share as i'm not happy with my lack of firewall at the moment.

---

### Post by de_valentin on 2007-12-03
Hi

Thanks for all the answers, I am not configuring anything at this point. At this point the layout of the network is unfortunately not something I can change. The adsl router is crappy but there is no alternative at this point. And because of the router, the nas has a fixed IP and it gives out the pc ip-adresses that have to be 192.168.2.2-255 or it won't work at all.
So this must mean that the ubuntu box is getting the ip-adres automatically right?
According to the nas it is via DHCP.

At this point I have no firewall installed so unless its in the package by default(Gutsy) no firewall

---

### Post by tact on 2007-12-04
The router part of your NAS should be configurable in way it gives out IP addresses (DHCP).  Do you know how to go into the NAS setup and configure it?  Where it comes to DHCP you should be able to choose what addresses it gives out.

Alternatively you can manually set up IP addresses for each computer on your LAN.  Just take care you never give two machines the same IP address.

Either way would result in all the machines on the LAN having addresses in the same subnet and simplify "windows networking".

---

### Post by de_valentin on 2007-12-04
That is the problem it is not possible to change that, because of the cheap adsl(multimedia) modem provided by the provider and not to be replaced (partly because there aren't that many alternatives.

here is what the NAS says about  the DHCP

Subnetmask: 255.255.255.0
gateway:192.168.2.1
DNS server:192.168.1.1
IP-adres range:192.168.2.100-200

and about the LAN
IP-adress:192.168.2.1
subnetmask: 255.255.255.0
Workgroup: THUIS (HOME)
Routername: FSG

---

### Post by tact on 2007-12-04
dont worry about the adsl modem...its fine.   But the NAS device should let you change the address range it uses for DHCP.  COrrect??

instead of x.x.2.x make it x.x.1.x

---

