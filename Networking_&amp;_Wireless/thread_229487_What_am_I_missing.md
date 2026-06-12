---
title: "What am I missing??"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by Carbonfish on 2006-08-04
Hi all,

I installed DD yesterday and am trying to get wifi working, and Ubutu is seeing my wireless card, I have full signal strength in the task-bar, etc. but Firefox won't connect to the interweb.

I did an iwconfig and here is the output:

eth1   IEEE 802.11b ESSID:"springcreek"  Nickname:"Prism I"
       Mode:Managed  Frequency:2.462 GHz Acess Point: 00:11:50:OA:IE:8D 
       Bit Rate:11 Mb/s
       Retry limit:16  RTS thr:off  Fragment thr=0 B
       Power Management: off
       Link Quality=30/92 Signal level=137/153 Noise level=107/153
       Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
       Tx excessive retries:0 Invalid misc:0 Missed beacon:0

So it seems obvious to me that I am missing something simple. I am typing this from my Mac, sitting in a cafe with an open net, to try to get this wireless prob. fixed so that I can get updates, but I am stuck here.

TIA for any advice.

KC
ps. I looked at this after it posted, and I have no earthly idea why there is a  smiley in the middle of my text. I didn't stick it there!

---

### Post by Carbonfish on 2006-08-04
Just a quick update. I pinged Google from the terminal, and I am connected and have name recognition, so I don't have a clue what's going on. Everything indicates that I have a solid network connection, but Firefox won't load any web pages. I don't have any firewalls up or anything. I'm sorta stumped and I can't hang around this place drinking $3.00 cups of coffee to figure it out. 

I would be deeply grateful for any insight. I'll just have to wait until I am around an open network again to implement them.

TIA for any help.

Kent

---

### Post by Carbonfish on 2006-08-04
Well, 

Maybe I gave this thread a title that makes people shake their heads and move on, or put this in a way that people are finding offensive, or perhaps I put the post in an inappropriate forum or something, but I'll take zero responses as a bad sign.

I thoroughly read this wiki: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
and tried to follow the trouble-shooting steps, but although I'm not intimidated by the terminal, I seem to be chasing my tail.

*shrugs, sighs deeply*

I guess I'll just keep reading and hope that I stumble across the right thread or wiki page. The sad part of this is that there is no way for me to know whether an update would fix this, as I can't get on-line to use synaptic or apt_get.

I guess that I haave a steeper learning curve ahead of me than I thought.

KC

---

### Post by stormblue on 2006-08-04
If you can ping google it's not a DNS problem.  It looks like you're connected.  Have you tried other internet services like e-mail, bittorent, etc, etc?

---

### Post by Carbonfish on 2006-08-04
stormblue,

Thank you very much for the reply. I tried to set up the default E-mail client, but of course I didn't have my pop 3 or smtp info with me at the coffee shop, so I couldn't try that. I didn't think about trying a bittorrent server. Are you suggesting that I do that through my terminal the same way that I pinged Google? Firefox doesn't seem to be an option. It opens properly, and everything seem fine, but it just attempts to connect until it times out. It doesn't give me the usual "Firefox cannot find the server, check your URL, and your network settings, blah, blah...". It acts like it should be connecting, then nothing.

I realize that I am not being very helpful, but I am not sure how I can be more helpful.

EDIT: I just thought of something, would it do me any good to go buy an Ethernet cable and connect with eth0 (the ethernet connection), download and install the system patches that are available and see if that helps, or would that make a difference?

Thanks again for taking the time to try and help. :) 

Kent

---

### Post by stormblue on 2006-08-04
type the following in the terminal

```

ftp ftp.debian.org
```

---

### Post by Carbonfish on 2006-08-04
Thanks, I'll try it. But it will take me about a half-hour to get someplace with an open network (or any wireless net for that matter), I'm sort of on the edge of the sticks. Right now I'm using the dial-up connection at home. I'll jump up and zip into town and let you know what happens!

Thanks again.

Kent

---

### Post by Carbonfish on 2006-08-04
Okay, I made it to a place with a wireless network, and I have typed ftp ftp.debian.org into my terminal and I am connected to the 220 saens.debian.org FTP server.

I tried apt_get updates and got a "530 This FTP server is anonymous only."

What next?   :oops: :oops:

KC

---

### Post by stormblue on 2006-08-04
Sounds like it's an apt-get problem.   Try doing a google search for your error or search the forums.

---

### Post by Carbonfish on 2006-08-04
Is there another FTP server that I can access to get updates from? Hate to ask what are probably obvious questions, but I have searched the forums and am probably just not defining my search terms very well. Plus, it's a little frustrating that I can't try each suggestion as it is given as I am not where there is a wireless network (or ethernet) in my home.

Oh well, poco a poco, I guess.

Kent

---

### Post by stormblue on 2006-08-04
I'd repost with a better title in the begining ubuntu forum.  It's the first one on the top.  Explain what you are able to do...and the apt-get error.  A good title might be "Apt-get error: 530 This FTP server is anonymous only"

---

### Post by Carbonfish on 2006-08-04
Okay stormblue,

Thanks for your time.

KC

---

