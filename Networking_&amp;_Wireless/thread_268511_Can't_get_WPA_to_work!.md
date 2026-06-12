---
title: "Can't get WPA to work!"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by Dr.Calimero on 2006-09-30
Hi all. I am a noob who just deleted my entire windows install and switched "whole penguin" to ubuntu (6.10).  I am having a heck of a time getting my computer to connect wirelessly to the network, and I was hoping that one of you gurus could help.  I have an old (x386) dell with a linksys pci wireless card (wmp54gs).  When I load up the os, I see the card, and I can even enable it in network manager.  The problem is that I have WPA enabled on the network, and I can not seem to get the network manager to offer me WPA access as an option!  Any suggestions?  PLEASE :)
Thanks!
Calimero
](*,)

---

### Post by wieman01 on 2006-09-30
You need to install a tool called "NetworkManager" which has nothing to do with the one you have referred to. Network Manager enables you to connect to WPA1/WPA2 networks and manage these connections.

NetworkManager has a number of constraints:
1. DHCP only, no Static IP.
2. ESSID broadcast cannot be turned off otherwise the tool does not recognize the network.
3. I remember it cannot handle networks with encryption turned off.

If you don't mind these restrictions, that's the tool of your choice. If you need static IP or hidden ESSID then you need to set it up manually by editing "/etc/network/interfaces". 

If the latter applies I can help. But I would try NetworkManager first.

---

### Post by Dr.Calimero on 2006-09-30
Thanks for your reply.  I tried to do this, but the only other networkmanager I can find is knetworkmanager, and that does not seem to help the proble, either!
How do I find the *right* network manager?

---

### Post by wieman01 on 2006-09-30
This is a good howto:

[http://www.ubuntuforums.org/showthread.php?t=125150&highlight=network+manager+howto]("http://www.ubuntuforums.org/showthread.php?t=125150&highlight=network+manager+howto")

Don't follow the steps for "ipw2xxx" if you happen to have another wireless network adapter.

As for KNetworkManager & GNetworkManager... These are GUIs for NetworkManager (thus depend on it) for KDE (K) & GNOME (G). No more, no less.

---

### Post by chele on 2006-09-30
The package you want is network-manager-gnome. 

You will need disable the wireless connection in System > Administration > Networking and run the nm-applet. You also may need to remove everything but the lo interface from the /etc/network/interfaces file.

---

### Post by Dr.Calimero on 2006-09-30
hmmm I am trying.... how do I run the nm applet? I can't fin network-manager-gnome under synaptic or any of the other update managers!  *groan* I feel like an idiot.

---

### Post by wieman01 on 2006-09-30
Could be a problem with your respositories. Run this command line from a terminal window:
> sudo gedit /etc/apt/sources.list
Make sure these lines are there:
> # Ubuntu 'Main' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

# Ubuntu 'Universe' Repository
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse
Then save and run the command again:
> sudo apt-get install network-manager network-manager-gnome
That installs NetworkManager and the GUI (= network-manager-gnome).

---

### Post by Dr.Calimero on 2006-10-01
so I tried the sudo you suggested and recieved:

@ubuntu-desktop:~$ sudo apt-get install network-manager network-manager-gnome 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
network-manager is already the newest version.
network-manager-gnome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

apparently I have it, but can't call it up.... even more fustrating! so close, but so far away :)

---

### Post by Dr.Calimero on 2006-10-01
One other thing, that may be contributing: I am using the edgy eft pre-release.  Can I still use the dapper repositories?

what I have in my sources .list is 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by wieman01 on 2006-10-01
You should be able to open NetworkManager from a terminal windows to begin with. Try mn... and press tab. You should be given a list of option afterwards.

As for the repositories... I am pretty sure the Dapper ones won't help you. I have no idea where to find the ones for Edgy.

---

### Post by Dr.Calimero on 2006-10-01
I opened a terminal window, and typed:
mn[TAB]
and my computer just sat there and beeped at me.
I think my computer is possesed by the spirit of evil beeps.
but apparently not nmanager! argh,

---

### Post by chele on 2006-10-01
You can run the applet by typing: **nm-applet** from the command line.

---

### Post by Dr.Calimero on 2006-10-01
now I have 2 instances of the applet running in my upper right hand corner of the screen, but it still won't offer me any WPA options.
(baby steps please.... I am really a beginer at this!)

---

### Post by chele on 2006-10-01
OK, I guess Edgy Eft uses network-manager already. You can remove one of the applets. (right-click > remove)

What WPA options are you looking for? When I selected the network, up popped a window asking for my WPA password. There are no options to configure. It just worked.

---

### Post by Dr.Calimero on 2006-10-01
that does not happen for me.  the #$%#$% network manager can see my  wireless card, but refuses to offer me ANY security options.  Olny ASCII or hex
is there something else I should be doing?

---

### Post by chele on 2006-10-01
What exactly happens when you select the desired wireless network from the list presented by network-manager?

---

### Post by Dr.Calimero on 2006-10-01
> **chele said:**
> What exactly happens when you select the desired wireless network from the list presented by network-manager?
ummmm, it never presents to me a list of networks. so I guess there is a problem before that step.

---

### Post by wieman01 on 2006-10-01
You probably need to install another package: wpa_supplicant.

---

### Post by chele on 2006-10-01
Can we assume that your wireless network does not use a hidden ESSID?

Is the /etc/network/interfaces file controling the wireless card?

Try:** sudo gedit /etc/network/interfaces**

Comment out everything except the bits about **lo**:

[B]auto lo
iface lo inet loopback[/B]

# lines with the # character are commented out
#iface ath0 inet dhcp
#wireless-essid libre

---

### Post by Dr.Calimero on 2006-10-01
> **chele said:**
> Can we assume that your wireless network does not use a hidden ESSID?

Is the /etc/network/interfaces file controling the wireless card?

Try:** sudo gedit /etc/network/interfaces**

Comment out everything except the bits about **lo**:

[B]auto lo
iface lo inet loopback[/B]

# lines with the # character are commented out
#iface ath0 inet dhcp
#wireless-essid libre

Before I go any further, I have to say how greatful I am that you folks are taking the time to help me!  It is amazing.  Thanks.

re: WPA-supplicant.  I seem to have that, per synaptic
re: commenting things out. ok-doeky
here is what the file looks like.
now what?


auto lo
iface lo inet loopback


#iface eth0 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp
#iface eth1 inet dhcp
#wireless-essid Monster
#wireless-key s:
#auto eth0

---

### Post by chele on 2006-10-01
try a: [B]sudo /etc/init.d/networking restart

[/B]I can't seem to find the command for simply restarting network-manager. If all else fails, reboot the computer should work, though that seems like such a regression!

---

### Post by Dr.Calimero on 2006-10-01
I restarted the computer and now it is attempting to connect!  Vast improvement.  but it does not recognize any of the existent networks (which are not hidden). So close, I can taste it!
Thanks again for all the help :)

---

### Post by Dr.Calimero on 2006-10-01
ok. Clearly I am still missing something.  What do I have to do to have NM actually recognize my network?  It is offering me WAP options, but refusing to connect.

---

### Post by chele on 2006-10-01
If you are selecting the right Wireless Network from the list and entering the correct WPA passowrd, it should just work.

You could try disabling WPA on your network in order to test if your network card is compatable with your router. You can even leave that way, if your neighbours are not so nasty as to to abuse the open network.

Once connected to the open router, go back into the router setup and set the **WPA personal** option (not WEP, not Radius). The network should then appear with a shield beside it in the list from NM. Selecting it will then pop up the password prompt. Give it a few minutes to set everything up, then it should be working.

---

### Post by Dr.Calimero on 2006-10-01
> **chele said:**
> If you are selecting the right Wireless Network from the list and entering the correct WPA passowrd, it should just work.

You could try disabling WPA on your network in order to test if your network card is compatable with your router. You can even leave that way, if your neighbours are not so nasty as to to abuse the open network.

Once connected to the open router, go back into the router setup and set the **WPA personal** option (not WEP, not Radius). The network should then appear with a shield beside it in the list from NM. Selecting it will then pop up the password prompt. Give it a few minutes to set everything up, then it should be working.

The problem here is that I can not see any of the open networks in my bldg.  I know the card works, and the network is running because up until yesterday it was perfectly happy letting windows connect wirelessly.  But then I erased windows to install ubuntu... and now I have a problem.  I can still see the network up, and am using a mac to connect to it to type this. So I think the problem may be in the way linux is trying to talk with my wireless card (linksys).  
Any thoughts?

---

### Post by almax00 on 2006-10-01
can you tell what id ubuntu sees your card as ?
it looks like it might be eth0 or eth1 ?
try:
auto eth1
iface eth1 inet dhcp
if that doesn't work substitute eth0 for eth1

i have a wireless card that dapper sees as ath0
and i had the same problem until i changed to:
auto lo
iface lo inet loopback
auto ath0
iface ath0 inet dhcp

good luck --

---

### Post by Dr.Calimero on 2006-10-01
tried to change the comenting as per your suggestion, and I get these errors

Sending on   LPF/eth1/00:0f:66:6d:6f:35
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down

even though the network is clearly up (I am writing to you on it at this very moment).
Is ubuntu not seeing my card?

---

### Post by almax00 on 2006-10-02
will ubuntu connect if you turn WPA off ?

---

### Post by chele on 2006-10-02
OK, I thought when you said that you can see the network is up, it was from the linux computer, not from another computer (a mac). You know the card was working under windows, so the card is physically functional.

What we don't know is if linux has drivers for the card. What make and model of network card is it?

---

### Post by chele on 2006-10-02
> a linksys pci wireless card (wmp54gs)OK. From other forum posts, I see that this card is not well supported under linux, there are not good solid drivers for the card. You should replace it with a card that is well supported. This laptop has a card from Atheros, which has always worked well, it always Just Worked. I hear that the Intel wireless cards are also well supported. Perhaps someone using a good, solid pci wireless card can give a specific recommendation. Something which Just Works, without any special configuration.

---

### Post by Dr.Calimero on 2006-10-02
> **chele said:**
> OK, I thought when you said that you can see the network is up, it was from the linux computer, not from another computer (a mac). You know the card was working under windows, so the card is physically functional.

What we don't know is if linux has drivers for the card. What make and model of network card is it?

chele, I think you have hit the nail on the head. I think that linux and wmp54gs cards do not like each other.  from reading those other posts, however, it appears that I can get a workaround with ndiswrapper.  the only problem is that I commented the heck out of my interface file (and I am not unix savy enough to know what the stuff I commented out MEANS...yet).  Is there a way for me to call up NDiswrapper by network manager?  and or from my network interface file?  Also, who do I pull the driver off the windows CD that came with the card.  (yes, I know I caould buy another card, but that option is a lot more expensive, and less satisfying). 
Thanks!

-DC

---

### Post by chele on 2006-10-02
ndiswrapper is a way to load a driver/module for the card. Once/if it is setup, you can go back to NM or the interfaces file to get the wireless networking working. 

Note that NM and the interfaces file are incompatable. You use one or the other, not both. NM always easy WPA setup, it just works, assuming you have a supported wireless card. Neither of these has anything to do with the module for your card

I suggest you start a new post in the Edgy Eft section about getting a working module loaded for the wmp54gs card. The details may be quite different on Edgy then on Dapper.

I think buying a mac to browse wirelessly is a bit more expensive then buying a decent wireless card for x86 Linux! ;-)

I guess it depends on ones objective. If you just want to get it working as quickly as possible, buy a supported card. If you want to learn a bit about work-arounds to load a module, then go the ndiswrapper route. Then you could dump that OS X junk of the mac, and install Linux there as well!

---

