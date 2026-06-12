---
title: "ready to give up on 9.10"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by tzarcasm on 2010-01-16
Im brand new to Linux/9.10. Im dual-booting on a 32bit if that makes a difference. 

Ive been researching/trying to get my openvpn running for over a week now so please dont tell me to do my homework first.
Im  very near the end of my rope with Ubuntu9.10 (or ANY linux) right now.

Im not trying to set up some fancy 'server' or whatever. Im simply trying to encrypt my traffic when Im in a wifi cafe.

I signed up for 'surfbouncer' VPN service for my Windows and it works nicely on both my Widows PC's. It uses openvpn and a simple install GUI. I was hoping to utilize the same service account on Ubuntu.

However when I go to the sevice site it just redirects me to the openvpn site.And Ive followed steps there as far as I could before getting confused and trying something else.

I downloaded 'Kvpnc' manager from the repository then copied/pasted the config file from my other partition (windows7)to documents on Ubuntu.Then imported the config file into 'Kvpnc'. When I hit start I get "connection refused"
Ive been all over the internet for a week scouring forums and following instructions and installing sh/it using 'apt-get' and dont even know what it is Im installing or what the f*ck Im doing. 

Yes Im a noob and about ready to give up on this overly-complex OS. Which would be unfortunate because I really like most of it.

Thanks in advance.

---

### Post by OrangeCrate on 2010-01-16
Here's a review that pretty much mirrors my feelings on 9.10:

[http://www.tomshardware.com/reviews/ubuntu-karmic-koala,2484-13.html](http://www.tomshardware.com/reviews/ubuntu-karmic-koala,2484-13.html)

(I've posted the Conclusions first. You can backtrack to the beginning from there.)

IMO, the latest version of Ubuntu is simply snake bit. (If you cruise around the forums, you'll find many who agree with me.)

Personally, I have reinstalled 9.04 (a very good release), bought a big bag of Doritos, and a 12 pack, and I'm now quietly sitting here waiting for Lucid to be released in April.

You might try that, rather than giving up completely.

---

### Post by kenuf on 2010-01-16
I'm a noob too...  so this may or may not be an issue....
But the VPN you installed is for a KDE desktop, if you are using a Gnome desktop you might try another VPN app...

Also... Could the windows config file be different from the one needed for Linux?

Maybe entering the settings instead of copying the file over...  

Like I said I'm a noob too..  but just some thoughts.

---

### Post by OrangeCrate on 2010-01-16
> **tzarcasm said:**
> Im brand new to Linux/9.10. Im dual-booting on a 32bit if that makes a difference. 

Ive been researching/trying to get my openvpn running for over a week now so please dont tell me to do my homework first.
Im  very near the end of my rope with Ubuntu9.10 (or ANY linux) right now.

Im not trying to set up some fancy 'server' or whatever. Im simply trying to encrypt my traffic when Im in a wifi cafe.

I signed up for 'surfbouncer' VPN service for my Windows and it works nicely on both my Widows PC's. It uses openvpn and a simple install GUI. I was hoping to utilize the same service account on Ubuntu.

However when I go to the sevice site it just redirects me to the openvpn site.And Ive followed steps there as far as I could before getting confused and trying something else.

I downloaded 'Kvpnc' manager from the repository then copied/pasted the config file from my other partition (windows7)to documents on Ubuntu.Then imported the config file into 'Kvpnc'. When I hit start I get "connection refused"
**Ive been all over the internet for a week scouring forums and following instructions and installing sh/it using 'apt-get' and dont even know what it is Im installing or what the f*ck Im doing. **

Yes Im a noob and about ready to give up on this overly-complex OS. Which would be unfortunate because I really like most of it.

Thanks in advance.

(Caught this on a second read of your post...)

Seriously?

See here:

VPN Clients

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#VPN_clients](http://ubuntuguide.org/wiki/Ubuntu:Karmic#VPN_clients)

---

### Post by CharlesA on 2010-01-16
Huh, what?

[http://www.surfbouncer.com/linux_download.htm](http://www.surfbouncer.com/linux_download.htm)

---

### Post by ankspo71 on 2010-01-16
Hi tzarcasm,
Sorry to hear about your experience with Karmic so far. I just noticed you mentioned openvpn. If you search Synaptic Package Manager for ' gadmin ' you will find a nice collection of GUIs for various server applications, including for the openvpn server and client. I don't have any expereince with openvpn, but I do for the gui for proftpd.
Hope this helps.

---

### Post by Marvin666 on 2010-01-16
You may have better luck with jaunty.

---

### Post by HermanAB on 2010-01-16
Howdy,

If it will make you feel better... I have been using UNIX since 1984 and I have never been able to get OpenVPN to work either.  So it is not easy, despite what other people may tell you.

When I need a VPN, I use SSH and Socks.

---

### Post by distortedecho on 2010-01-16
My advice would be: If you can't get the same app in Windows working in Linux, use an alternative.

So like how Flashget won't work for me (via WINE) I use Tucan or Jdownloader instead.

If you can't work OpenVPN, do as HermanAB suggested and try SSH and Socks instead...

---

### Post by tzarcasm on 2010-01-16
> **CharlesA said:**
> Huh, what?

[http://www.surfbouncer.com/linux_download.htm](http://www.surfbouncer.com/linux_download.htm)


This is one of the 1st things Ive tried,but thanks.

I'll research other suggestions in this thread,as I said Im a noob and dont know sh/it from ssh socks.

Thanks I'll keep trying.

---

### Post by arvevans on 2010-01-16
Crudely obscured or implied cursing is a turn-off for those of us already using virtual networking via Linux.

---

### Post by tzarcasm on 2010-01-16
> **ankspo71 said:**
> Hi tzarcasm,
If you search Synaptic Package Manager for ' gadmin 

I installed "Gadmin-openvpn-client 0.0.3" and tried to import config file from my documents that I copied over from my Widows partition.

But I get *"Error: Import package should be a compressed .tar.gz package."*

So how and where do I get this? If I found it online and installed, wouldnt it have the wrong keys?

As I mentioned I have tried many things from other forums-and my apologies for not listing what I did so far. I dont understand what I was doing otherwise I'd list what I did.

IOW if I understood it I'd remember better but trying to remember obscure commands that I copied/pasted to terminal from a message board 3days ago is not possible for me.My feelings on that are if I screw up Ubuntu by doing such things I'll just wipe it from HDD and be done with it for good-thats where Im at with all of this.

---

### Post by nothingspecial on 2010-01-16
I know nothing of your issue.

However, I suggest being less hostile (or demanding of help, whilst swearing about the os people are trying to help you with).

A couple of pointers -

If you open a terminal and press the up arrow, it will cycle through the last (I`m not sure, but) hundreds of commands you have used.

If you type history it will list the last (I don`t know how many, because I restart bash so often) commands.

If you know a bit of the command you typed, try
```

history | grep [COLOR="Red"]bit_you_know[/COLOR]
```

substituting the red bit_you_know with the actual bit you know.

Also I suggest you change your post title to "Help with encryption and vpn" or something similar so the people who know how to help don`t skip past....... and maybe put it in the server section.

Anyway no offence meant, just trying to help you get the right help.

---

### Post by tzarcasm on 2010-01-16
> **arvevans said:**
> Crudely obscured or implied cursing is a turn-off for those of us already using virtual networking via Linux.
  

Not obscured nor 'implied', I outright cursed. If you enter sh/it without the slash you get ****.

---

### Post by tzarcasm on 2010-01-16
> **nothingspecial said:**
> I know nothing of your issue.

However, I suggest being less hostile (or demanding of help, whilst swearing about the os people are trying to help you with).



If thats how it comes off,my sincere apologies. Its more frustration. I'll refrain from cursing from here out.


And thanks all.

---

### Post by MarkC502 on 2010-01-16
9.10 has caused me headaches too and I now have rolled several boxes back to 9.04 to save frustration. My advice is to install 9.04 and turn off upgrades of Ubuntu ( not updating but upgrading as in versions ). 

I think for new Linux users the new version upgrades hurt more than they help as when they break things the people have no idea how to fix them get mad since it was working 30 minutes ago before the "Upgrade" and they rarely fix someone's problem on a system they have long since been using as those were fixed after install or they would have abandoned Linux back to windows long ago. In short I think they should carry a warning label like a cigarette pack "Warning this version upgrade may torque your sound and video, If you are a Jedi fear not else be scared"

Sometimes the stablest release beats the newest release.

---

### Post by doublewitt on 2010-01-16
Oh well, it's too bad to here that. It runs smoothly for me. It just gets better all the time... I enjoy Ubuntu 9.10 and I'm not about ready to switch to something else...

---

### Post by arvevans on 2010-01-16
A read through the information at these URLs will give you a better idea of what is happening, what needs to happen, and how to make it happen:

    <http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch35_:_Configuring_Linux_VPNs>

    <http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html>

    <http://articles.techrepublic.com.com/5100-10878_11-6038003.html>

    <http://tldp.org/HOWTO/VPN-HOWTO/>

    <http://www.linuxhelp.net/guides/vpn/>

    <://www.faqs.org/docs/Linux-HOWTO/VPN-HOWTO.html>
 
    <http://pptpclient.sourceforge.net/>

All these information sources provide some part of the methodology.  There is specific instruction for how to connect between Linux and Microsoft VPN structures, which I suspect might be the problem.

_._

---

### Post by tzarcasm on 2010-01-16
> **arvevans said:**
> A read through the information at these URLs will give you a better idea of what is happening, what needs to happen, and how to make it happen:


Thanks for the links, but those pages are a deadly morass of confusion to me.Also I always seem to come to a dead end such as when I followed the steps in the 'cyberciti' link you provided:

[I]"After this operation, 1,307kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)'
in the drive '/cdrom/' and press enter"
[/I]
I dont have a cdrom on this box and probably could install it from my usb stick if I knew what it is thats supposed to be installed. (I installed my 'bwcm' wireless driver from usb.)

Also I thought there was a distinction between setting up a 'server' and 'client'. The openVPN has downloads for 'server'.I also thought there was a difference between 'VPN'(cisco?) and 'openVPN'.

---

### Post by NFblaze on 2010-01-16
> **tzarcasm said:**
> Thanks for the links, but those pages are a deadly morass of confusion to me.Also I always seem to come to a dead end such as when I followed the steps in the 'cyberciti' link you provided:

[I]"After this operation, 1,307kB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu-Netbook-Remix 9.10 _Karmic Koala_ - Release i386 (20091028.4)'
in the drive '/cdrom/' and press enter"
[/I]
I dont have a cdrom on this box and probably could install it from my usb stick if I knew what it is thats supposed to be installed. (I installed my 'bwcm' wireless driver from usb.)

Also I thought there was a distinction between setting up a 'server' and 'client'. The openVPN has downloads for 'server'.I also thought there was a difference between 'VPN'(cisco?) and 'openVPN'.

Hey if you dont have the disk what you can attempt to do download the [Ubuntu Netbook Remix iso]("http://www.ubuntu.com/getubuntu/download-netbook"), and mount it as a virtual CDROM drive using something like:

sudo mount -o loop /wherever/you/downloaded/ubuntu_netbook.iso /media/cdrom0

Also, about the VPN. I used a VPN with Ubuntu 9.04, unfortunately I had to reinstall, but the website was BlackLogic, and they had some somewhat decent (a bit outdated at the time, and even more so now) instructions on how to install their particular VPN. I do remeber using Synaptic to search for VPN, and I installed each one pptp. openvpn, and ciscovpn. I believe I ended up using OpenVPN. 

[Here is the guide I kinda used back then. ]("http://pptpclient.sourceforge.net/howto-ubuntu.phtml")

Edit:Apparently the article says it used PPTP, so scratch that I didnt use openvpn I suppose, I used pptp.

---

### Post by tzarcasm on 2010-01-17
Thanks all Im getting is "could not find" I have the .iso on my desktop.

Just to re-iterate Im just trying to tunnel my traffic while on an open wifi. Having said that can anyone tell me if [this]("http://hackertarget.com/2009/07/guide-to-openvpn-on-ubuntu-904-jaunty-jackalope/") is what I need?-I thought that was for connecting to a remote computer.
Also Im in terminal & Im following directions from 'openVPN' website that seems to be leading me to setting up a 'server':

[I]"Once you provide a few initial configuration settings,
OpenVPN Access Server can be configured by accessing
its Admin Web UI using your Web browser.

Please specify the network interface and IP address to be
used by the Admin Web UI:
(1) all interfaces: 0.0.0.0
(2) eth1: 192.168.x.xxx
Please enter the option number from the list above (1-2).
> Press Enter for default [2]:" 
[/I]
The above isnt what Im needing to do ,correct??

Thanks

EDIT: Could I set up an access server using the above method and tunnel through something like domain.com??

---

### Post by kary21 on 2010-01-27
Shoot the guys at Surfbouncer a note. I have one of their virtual machine images that I run and it's a full implementation of Ubuntu 9.10. If nothing else it will give you a side by side comparison to a working version.

---

