---
title: "WPA wireless - bizarre problems"
date: 2006-11-16
forum: Networking &amp; Wireless
---

### Post by zachtib on 2006-11-16
My university has a campus-wide WPA secured wireless network.  The configuration file that I've used to connect to it is as follows:
```

ctrl_interface=/var/run/wpa_supplicant

eapol_version=1
ap_scan=1
fast_reauth=1

network={
       ssid="**********"
       proto=RSN
       #proto=WPA
       #key_mgmt=WPA-EAP
       key_mgmt=IEEE8021X
       auth_alg=OPEN
       eap=TTLS
       pairwise=CCMP
       group=CCMP
       anonymous_identity="anonymous"


       identity="********"
       password="********"

       phase2="auth=PAP"
       priority=4
}

```

The odd part is that this doesn't work on it's own, here's what I have to do: 

0. Right-click network-manager and Disable Networking
1. Open two terminals.
2. In terminal A, run "sh wpa.sh"  (wpa.sh is a one line script that runs wpa_supplicant with the options for my config file, driver, etc.) However, this command will invariably fail to authenticate with any network.
3. in terminal B, run "sudo nano /etc/wpa_supplicant/wpa_supplicant.conf" to edit the file you see above.
4. Change ap_scan=1 to ap_scan=2 and save.
5. Alt-tab back to term A, do a ctrl-C to kill the script, then press Up and Enter to run it again.  wpa_supplicant will fail to connect again.
6. Alt-tab back to term B, where nano is still open.  Change the ap_scan line back to how it was originally, save, and exit nano.
7. Alt-tab back to term A, ctrl-C to kill the script, then press Up and Enter to run it again (note: at this point, the conf file is exactly the same as it was originally), and wpa_supplicant will now authenticate properly.
8. Finally, Alt-tab back to term B and run "sudo dhclient ath0" to request an IP address on the wireless network. Phew.


If this process seems long and involved, that's because it is, although I've gotten it down pretty well at this point (oddly, though, I've only ever had to do this on Edgy.  Dapper and Breezy worked better, but still had a few quirks), and I can do the entire process in about 30 seconds.


What makes it annoying, however, is the fact that the connection remains fairly unstable, and is prone to drop randomly. Sometimes the connection will stay open for close to an hour, sometimes only a few minutes, and I have to repeat the entire process over again.

If someone has some insight into why this happens, or anything that may help resolve the problem, please tell me, this is driving me nuts.  I'm out around campus for about 4 hours a day, every day Monday-Friday, and with the connection dropping every 20 to 30 minutes on average, it get extremely annoying.  Particularly because I get no indication the connection has dropped, except things stop working, and it usually takes me a minute to notice.  Plus, everytime I do this, I have to close and restart most networking applications that keep a constant connection, such as Gaim and XChat.

Thanks for reading, and thanks for any help you can provide,

Zach

---

### Post by notebook_ftw on 2006-11-16
Yeah, the wpa_supplicant.conf file that they give us (I go to your university btw, in your physics class...) isn't working well with Edgy.  I have yet to be successful connecting to the campus' wireless networks, and am trying to find some way to do so.  The problem I have is that I have the Intel 3945 wireless card, and I'm not sure if it's supported by wpa_supplicant yet.  But any insight anyone can give would be greatly appreciated.

---

### Post by zachtib on 2006-11-16
> **notebook_ftw said:**
> Yeah, the wpa_supplicant.conf file that they give us 
They actually give us one?  I sort of reverse-engineered mine through trial and error.
> I have yet to be successful connecting to the campus' wireless networks, and am trying to find some way to do so.  The problem I have is that I have the Intel 3945 wireless card

Like I said, I've pulled it off, but its annoying (along with several other little quirks in Edgy)
I usually go out of my way to get an Atheros card, as I've always had better luck with them

---

### Post by notebook_ftw on 2006-11-16
Yeah, there's a Linux group here at the university, and they have a sample wpa_supplicant.conf file in their wiki page.  Just search for "linux" at the university's home page and it will be the first link.  It's called SLUG or something like that (Student Linux User Group?).  

Anyways, yeah, I didn't really have the option for an Atheros card in my laptop.  It was either the Intel 3945 or the Dell 1390.  Obviously, the Intel was the much better decision between those two.  And this laptop only has an ExpressCard slot, so I can't use an PCMCIA wireless cards, but I don't want to.  I want to get it working like this.

And yeah, I've had quite a few problems with Edgy myself.  The upgrade process completely trashed my old laptop.  I can't do anything on that computer anymore.  And there have been a lot of uphill struggles trying to get things to work in Edgy.  I find it really sad how my wireless went from working perfectly out of the box with Dapper to not at all in Edgy.

---

### Post by zachtib on 2006-11-16
> **notebook_ftw said:**
> Yeah, there's a Linux group here at the university, and they have a sample wpa_supplicant.conf file in their wiki page.  Just search for "linux" at the university's home page and it will be the first link.  It's called SLUG or something like that (Student Linux User Group?).
Oh yeah, Speed ACM has the conf on their wiki, I thought you were referring to an 'official' one from the university.> Anyways, yeah, I didn't really have the option for an Atheros card in my laptop.  It was either the Intel 3945 or the Dell 1390.  Obviously, the Intel was the much better decision between those two.  And this laptop only has an ExpressCard slot, so I can't use an PCMCIA wireless cards, but I don't want to.  I want to get it working like this.

The ipw3945 should be pretty well supported, I'd think.  Maybe somethings set up wrong, but I'm almost positive that it should be possible to get it working with your card.  I almost threw that wifi card into my next laptop, but decided against it because of the 'binary blob' driver situation.

---

### Post by notebook_ftw on 2006-11-16
Well, the card works fine with Network-Manager, and I can connect to open networks pretty easily.  But Ubuntu's built-in Networking Manager doesn't do anything with the wireless, and according to the wpa_supplicant's output, the only Intel drivers supported are the ipw2200 and ipw2100, not ipw3945.  But I don't know.  The university's wireless is so screwed up anyway, it's hard to say.  I wish they would give an official way for Linux users to connect.  Of course they have it for Mac, but no love for the Linux.  I'd be willing to be that there are more Linux users on campus than Mac users too.

---

### Post by zachtib on 2006-11-16
bump

does anyone have any idea as to the original question?

---

### Post by DavidTangye on 2006-11-16
I installed wpa_supplicant only to get its utility to create an encrypted key for me, then place it into the /etc/network/interfaces file.

I found that the best info on this topic, that got me up and going, was in these forum threads:
 - [http://www.ubuntuforums.org/showthread.php?t=202834&highlight=8B2A](http://www.ubuntuforums.org/showthread.php?t=202834&highlight=8B2A)
 - [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

---

### Post by zachtib on 2006-11-28
bump.

back to my original question, I'm still curious as to why wpa_supplicant may be behaving this way, it's very odd.

---

### Post by randomnumber on 2006-11-29
I am at a different school (UWF) but we use wpa too.
I connect with network-manager, not originally installed with ubuntu.
Network-manager uses wpa-supplicant. To use network-manager you have to disable the network devise in the original network manager (System-> Administration-> networking).

You may try looking at wpa-supplicant's gui (wpagui). I suspect that you are having root issues. For example, I have to type sudo before I get the wpagui to work correctly. Without "sudo" it opens the gui but will not work with active wpa_supplicant. I only used the wpagui to see that wpa-supplicant is working. I also only use wpa-supplicant through network-manager.

I am curious if you have tried to connect to the network by selecting the network and connecting with network-manager. It should request more information after failure to connect. One of the problems I had was changing "Key Type" to "DyNamic WEP" from "auto..". I find that I do not need to create any config files. 

Our school only had how to connect guides for windows and mac systems so I spent about a semester figuring out how to connect. I am by no means an expert but I thought that some of my experiences may help you. I realize that your network maybe different.

-Some history-
I originally had troubles determining if my settings allowed a connection because I dual boot. When XP would connected, my laptop would be able to connect for a day or more without having settings that would really allow a connection without the XP connection preexisting. After this I have been reluctant to say I can connect with my setting but it has been over a month without booting XP.

---

