---
title: "NetworkManager not getting WPA"
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by wyth on 2006-11-25
Hi folks,

I've searched around for an answer to this conundrum and have come up empty.  Here's my issue: I have NetworkManager installed, and everything's working fine.  But when I switch my network over to WPA security, NetworkManager only offers me WEP options, and doesn't recognize the secured network as WPA.

I have my network secured as WPA TKIP, and it works via Windows.  I can also connect to the network in Ubuntu when I disable WPA security.  My understanding is that NetworkManager is supposed to pick up WPA automatically (yes wpasupplicant is installed).  

Any ideas here?

---

### Post by CSMatt on 2006-11-26
I have a similar problem.  Please fix NetworkManager so that it works with WPA and WPA2 encryption.

---

### Post by wyth on 2006-11-26
bump

---

### Post by Jamie Jackson on 2006-11-26
The next question you're going to be asked (by smarter people than me) is what wireless card you're using. That will enable the smart people to tell you whether the driver you're using supports WPA or not, etc.

Jamie

---

### Post by wyth on 2006-11-26
Heh.  Nice one (and right).

I'm using a Netgear WG511; it's an older wireless card, and has been natively supported by Ubuntu and linux in general for a couple years now.  The router is a Linksys WMP54G, the old standard.

---

### Post by Jamie Jackson on 2006-11-26
Well, while no smarter folks are answering, I'll throw some dumb stuff at you.

[I don't have WPA actually connecting yet]("http://ubuntuforums.org/showthread.php?t=307326"), but I do seem to be farther along than you, so maybe there's a nugget here that you're missing: Maybe the part about commenting out things in your /etc/network/interfaces file, or maybe the part about ENABLED=0 (/etc/default/wpasupplicant file).

See what I mean [here]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html").

Jamie

---

### Post by wyth on 2006-11-29
I may be getting somewhere here; it seems the Netgear WG511 (which uses the prism54 driver) doesn't come with WPA capabilities.  It can be done through ndiswrapper, but good luck finding the .inf file for it.

If this is the same problem you're having, Jamie Jackson, it may be that your card works, but WPA isn't figured into the linux driver being used.

I'm still looking for a way around this.

---

### Post by Jamie Jackson on 2006-11-29
Ohhh, my card doesn't work at all natively, so I already *am* using ndiswrapper.

I still haven't gotten WPA to work (the option's there in NM, but can't connect yet).

Since you're already running that card under Windows, too, you should be able to yank the driver out of your Windows installation, no? (As long as that particular driver works with ndiswrapper.) 

I guess you'd also have to blacklist the native driver.

Jamie

---

### Post by Jamie Jackson on 2006-11-30
I got mine (though it's a different card than yours) going with WPA, NetworkManager, and NDISWrapper. I modified [this wiki]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29#preview") to document what I did.

Thanks,
Jamie

---

### Post by wyth on 2006-12-02
AAAARRRGGGHHH!

Okay Jackson, so I went through the page you referenced, and a few others, installed ndiswrapper, and got nowhere.  I thought the problem was something to do with prism54 being enacted over ndiswrapper, so ndiswrapper just wasn't handling my Netgear WG511 card.  I searched some more, found some real voodoo that supposedly worked for some, but not me -- perhaps because I was running NetworkManager this whole time, and the card being managed through that.  So I was about to give up and post my failing here, when I sez to myself, I sez self, I'm gonna give this another try.

I still don't know what happened, but when I went to put my network back on WEP thinking WPA just wasn't going to work, WPA showed up as an option... (!)  This was what I wanted all along.  Why?  How?  I have no idea, but it's working.

For what it's worth, I got a little more help [here]("http://www.ubuntuforums.org/archive/index.php/t-141180.html") and [here]("http://www.linuxquestions.org/linux/answers/Networking/Netgear_WG511_with_WPA_on_SuSE_10_0").

---

### Post by Jamie Jackson on 2006-12-03
Man, do I hate the voodoo stuff (it happens to me way too often), but cheers to getting it working. :D

---

### Post by iClouseau88 on 2006-12-03
I got both network-manager and network-manager gnome installed as shown in Synaptic Package Manager. Also installed is wpasupplicant.  It appears to me that wpasupplicant is put on Ubuntu 6.06 merely as a place holder, so that it can be updated later to truly include WPA.  I am speculating this because I only get WEP when I click on the Network Manager icon and the file has no content when I execute the following to edit wpasupplicant file (as suggested in "Beginning Ubuntu-Linux" by Keir Thomas, page 89):

sudo gedit /etc/default/wpasupplicant

I could be wrong.  Any comments?

---

### Post by wyth on 2006-12-03
Just two quick comments:

1.) The file that needs the wpa input is at /etc/wpa_supplicant.conf.  Although with NetworkManager, I'm not sure that's even necessary

2.) If NetworkManager is only giving you WEP options (which was my problem), it's because of the card.  Some linux drivers don't yet offer WPA, but you can get it to work through ndiswrapper instead of letting Ubuntu handle it.  That's what I did, and I got WPA support.

---

