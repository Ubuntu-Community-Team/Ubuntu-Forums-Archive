---
title: "[SOLVED] Request static ip from dhcp server"
date: 2008-02-03
forum: Networking &amp; Wireless
---

### Post by curtlee2002 on 2008-02-03
I live in a college dorm. I want to request a specific ip address from the dhcp server. The schools network is very complex and if I don't register with the dhcp server I can NOT locate my computer from others on the the schools network by simply typing the HOSTENAME.DOMAINNAME . But I must have a static ip for mythtv-backend to work properly. 

NOTE: I am not using NetworkManager. 

With Gentoo after reading the network conf manual I simply had to add a single line to my network conf file. Worked like a charm.

---

### Post by stalker145 on 2008-02-03
Even though it might not be the best thing to do on a DHCP network that you do not own, the easiest way to set your computer up static is to:```
sudo nano /etc/network/interfaces
``` and substitute your device for the following ```
auto ath0
iface ath0 inet static
address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx
``` where x is the appropriate IP information.

Remember that since this is a DHCP network, there may come a time that the DHCP server gives away your IP address and messes up this perfect world.

Either that or you have have the network admin assign you a static IP...

---

### Post by curtlee2002 on 2008-02-04
Sorry, I do understand how to set a static ip. That is not what I want. I must registrar with the DHCP server or other computers on the network can NOT find me by hostname.domainname, only by ip address. It is very possibly to request an specific ip from the DHCP; It works great in Gentoo. I just need to know the Debian or Ubuntu way to do this.

Thank You for your post stalker145

---

### Post by rickyjones on 2008-02-04
> **curtlee2002 said:**
> Sorry, I do understand how to set a static ip. That is not what I want. I must registrar with the DHCP server or other computers on the network can NOT find me by hostname.domainname, only by ip address. It is very possibly to request an specific ip from the DHCP; It works great in Gentoo. I just need to know the Debian or Ubuntu way to do this.

Thank You for your post stalker145

Easiest thing that I can see happening is contact the network admin and request a reserved DHCP address. Give him/her your MAC address and if they cooperate you should be golden without making any changes to your PC.

-Richard

---

### Post by curtlee2002 on 2008-02-04
Thank You for your comment rickyjones.

Contacting network admin is not needed. I do not want to depend on them and wait for them to make a change every time I decide to make a change.

I only want my DHCP client to request a specific ip address from the DHCP server. This is very easy and well documented in Gentoo. I just want to know how it is done in Ubuntu.

---

### Post by curtlee2002 on 2008-02-13
I am really starting to think this forum is useless unless you are ask some stupid simple gui question. I don't understand why no one has the info I need. Why the HELL is Ubuntu's documentation so very limited. Thank You for creating a distro that is as documented as windows.

---

### Post by discodan on 2008-02-13
just curious,

if it works in gentoo, why not use it?  I'm new to linux and have no prefernce for one distro over another.  So, no disrespect or anything. I'm just curious why all the fuss over this if you had it working before?  

Why did you switch to ubuntu?

sincerely,

-disco-

---

### Post by curtlee2002 on 2008-02-13
Ubuntu is gaining in popularity and I thought I would give it a try. So far I have been very locked to defaults. Documentation and help are almost none existent. This forum seems to be a NEW TO LINUX forum. If anyone know how to get detailed documents or help from Knowledgeable people please tell me. 

I know new to GNU/Linux people are going to need help. I have been in their shoes. That is great that they are learning to be less Windows dependent. 

Where is the advance documentation and help?

---

### Post by rickyjones on 2008-02-13
> **curtlee2002 said:**
> I am really starting to think this forum is useless unless you are ask some stupid simple gui question. I don't understand why no one has the info I need. Why the HELL is Ubuntu's documentation so very limited. Thank You for creating a distro that is as documented as windows.

No offense, but with that kind of attitude no one will want to help you. I certainly don't after reading that.

EDIT:

Here is a link to the DHCPCD manpage - I believe that this is the DHCP client that Ubuntu uses. You may wish to read this file and see if there are options you can add to the configuration file to request a certain IP. I'm in a good mood today.

[http://www.phystech.com/download/dhcpcd_man.html](http://www.phystech.com/download/dhcpcd_man.html)

---

### Post by KCPokes on 2008-02-13
> **curtlee2002 said:**
> I am really starting to think this forum is useless unless you are ask some stupid simple gui question. I don't understand why no one has the info I need. Why the HELL is Ubuntu's documentation so very limited. Thank You for creating a distro that is as documented as windows.

Easy solution, find out how you can do it period and implement it.  Linux versions are not different enough that if it works for one it'll usually work for th other.  That said, your research, once you do it, will show that you cannot register a static IP with a DHCP server, unless you work through the network admin.  What you can do, with a DHCP server, is reserve an IP address, as someone tried to tell you above, such that it is set up as DHCP on your side but you'll always be assigned the same IP address, thus it is as static as it gets.  

Request for you now.  You tell me how you'd do this in Windows, since apparently it is simply the missing documentation on either that is stopping it from being done.  Why do people come on here and yell when they don't hear the answer they want?  This is not the end-all-be-all of information, so if you can find out how to do it, period, then work backwards to accomplish it with Ubuntu.

---

### Post by curtlee2002 on 2008-02-13
rickyjones,
I did try to be nice to you. Your answer just didn't fully help me. I tried to be very thorough with my question. The documents for /etc/network/interfaces and DHCP clients are simply lacking info.

---

### Post by curtlee2002 on 2008-02-13
KCPokes you are wrong. Next time think before you post

---

### Post by KCPokes on 2008-02-13
> **curtlee2002 said:**
> KCPokes you are wrong. Next time think before you post

Boy that is informative.  Seems to be the common attitude around here lately and a lot of the reason people quick assisting others.  Wonderful approach to asking others for their time with your issue.

[EDIT]  Actually, for the sake of curiosity, I looked into this a bit more and it can be done, in theory.  Different implementations may choose to ignore, but you can set the hostname in the dhcp connection (/etc/dhcp3/dhclient.conf):
```

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

This may work.  Of course there are different scenarios that will stop this from happening.  You should not be able to assign a static IP within the range of dynamically assigned addresses, or at least you shouldn't attempt as a conflict can occur at any time.  Still always a better approach to speak with the network admin and have them assign a static ip on the dhcp server, as you can be assured your address stays the same and there will be no conflicts.

---

### Post by mozetti on 2008-02-13
LIke others have said, your attitude means this thread is probably going to die unresolved. Don't be a complete jerk and more people will likely try to help. The support offered here is completely voluntary by anyone that might have the answer. For advanced topics (which this is one), there is the chance that no one knows the answer. This isn't the official Canonical support site. For official support you need to pay, so keep that in mind when you're putting down the people trying to help you.

That being said, I must be in a good mood, too. 

So, why don't you start by telling us how you accomplished this in Gentoo? Then we might be able to figure out how to do it in Ubuntu.

By the way, found this on Linuxquestions.org > The client cannot request an IP, however, the server can be setup to assign a specific IP to a specific client. One way is by having the server identify the hardware ethernet id number for a client, and assign a specific number to that ethernet card.

This echoes what others have mentioned, and is also my understanding of how DHCP works in every implementation I've come across. Although I did find this on Wikipedia: [http://en.wikipedia.org/wiki/Udhcpc](http://en.wikipedia.org/wiki/Udhcpc) -- and a reference to it on a Gentoo forum using Google. > On 1/6/06, Sergio Polini <sp_rm_it.RemoveThis@yahoo.it> wrote:
> I can't understand how to ask dhcp for a static address.
> I've read /etc/conf.d/net.example, but using
> Any hints?
>

I know that you can do this with udhcpc using the "-r" option:

" -r ADDRESS, --request=ADDRESS
Request IP address ADDRESS."

If this is what you're referring to, then you need to install udhcpc on your system and then hope it works with the school's DHCP server.

---

### Post by curtlee2002 on 2008-02-13
I have tried editing /etc/dhcp3/dhclient.conf but nothing happens. It is like that file is being bypassed. I looked in  /etc/init.d/networking and the  /etc/network/if-* 's. I can't find where this is being bypassed. I am sorry I am a little short with people. I can't stand people telling me I can't do something I have done before and explained that I have done before. When you look at the /etc/dhcp3/dhclient.conf file what I am wanted to do is right there in the file, but it isn't working.

With Gentoo I used dhcpcd instead of dhcp-client. I tried installing dhcpcd on Ubuntu but even less info is documented. Gentoo's /etc/conf.d/net is setup a little different. Ubuntu's is simpler, but a little lacking in documentation. Ubuntu should be very proud of it's easy "install and use". I just would like for more info on the advanced side of things.

---

### Post by KCPokes on 2008-02-13
Which options are you setting in your dhclient.conf file?  Everything I've found points to needing to set send host-name HOSTNAME.  If that is set, and its still not working, may take a bit more digging.  Most set it at the interface level, which I was messing with, but it seems to ignore it at that level, thus I thought the dhclient may be the best route.  It is all trial and error at this point, as this is not something I've done in the past.

---

### Post by curtlee2002 on 2008-02-13
Below I just listed the setting that I have change from default.  Setting the hostname seems a little redundant, but I tried it.  These settings just don't seem to be doing anything different.  

```
send host-name "georgedesktop";

lease {
  interface "eth0";
  fixed-address 10.192.16.200;
}

```

---

### Post by KCPokes on 2008-02-13
I don't really have much else to offer, as I don't have an opportunity to try it out right now, but there is also an option under the lease itself :

```

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;

```

Otherwise the other option is setting hostname in /etc/network/interfaces:
```

iface eth0 dhcp 
hostname georgedesktop

```

---

### Post by curtlee2002 on 2008-02-13
I have my /etc/hostname set and with regular /etc/network/interfaces dhcp setting, I have no hostname or domain problems. 

Only if I manually set the network like below, do I have problems with my domain and hostname being recognize on the network.

 ( I am hiding my dns's for security )
```
iface eth0 inet static
        address         10.192.16.200
        netmask         255.255.254.0
        broadcast       10.192.17.255
        network         10.192.16.0
        gateway         10.192.17.254
        dns-search      parker.rl
        dns-nameservers ___.___.___.___ ___.___.___.___
```

---

### Post by mozetti on 2008-02-14
As I mentioned in my previous post, the only documentation I've found that states you can specify the IP address you want from the DHCP server is the udhcpc daemon. Ubuntu uses dhcpd.

As far as I can tell, if you want the option of requesting a specific IP you need to install udhcpc as your dhcp client and hope that the dhcp server honors the request. 

I don't think there's any amount of editing you can do to the dhcpd/networking conf files to get this functionality in plain-vanilla Ubuntu.

---

### Post by KCPokes on 2008-02-14
Also keep in mind that you cannot specify "static" if you plan on using the dhclient configuration.  You need to specify dhcp but specify an IP address in the client config.  That will give you a "static" IP address but still utilize dhcp.

---

### Post by curtlee2002 on 2008-02-15
> As I mentioned in my previous post, the only documentation I've found that states you can specify the IP address you want from the DHCP server is the udhcpc daemon. Ubuntu uses dhcpd.

Default Ubuntu uses dhcp3-client from [http://www.isc.org/sw/dhcp/]("http://www.isc.org/sw/dhcp/") not dhcpcd.  That is why I ignored your previous mentioning.  The file /etc/dhcp3/dhclient.conf is owned by the dhcp3-client package.  So it makes sense that changes to this file should change the way dhcp3-client works.  Changes to the "alias" part of the file does work just change to the "lease" part seem to cause no change.

I only posted the static to show complexity of the network for only my building and to explain that I must use dhcp to get the hostname and domainname problem fixed.  Each building or section of the buildings on campus has its own dhcp-server.  For my full domainname to be recognized across campus I must use the dhcp-server.

---

### Post by curtlee2002 on 2008-02-15
If I was using dhcpcd,  -s is the option that I would use. 

       -s ipaddr
              Sends  DHCP_REQUEST  message  requesting  to  lease  IP  address
              ipaddr.    The   ipaddr   parameter   must   be   in   the  form
              xxx.xxx.xxx.xxx.  This effectively doubles the  timeout  period,
              as  if  we  fail  to  get this IP address then we enter the INIT
              state and try to get any IP address.

dhcpcd is what gentoo suggest and is what I was using with it. I am going to experiment with dhcpcd on ubuntu.

---

### Post by curtlee2002 on 2008-02-15
I GOT IT!!!!!!!!!!!!!!!

I installed dhcpcd, removed all of dhcp3-client, and edited a configuration file.

/etc/default/dhcpcd
```
# Add other options here, see man 8 dhcpcd-bin for details.
OPTIONS='-s 10.192.16.200'

```

Thank Guy's for all the effort

---

