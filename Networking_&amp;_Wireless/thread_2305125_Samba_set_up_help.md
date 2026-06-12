---
title: "Samba set up help"
date: 2015-12-02
forum: Networking &amp; Wireless
---

### Post by Patrick_Costa on 2015-12-02
I live in the country and we have internet access through our cell phone hotspots.  My children have tablets and I would like for them to be able to watch videos I download for them via a simple network I'm trying to set up.  I have an old laptop running Ubuntu Mate 15.10 connected to a broadcom 2750b router (no internet access) and I want to be able to give access to vids I download via samba.  I have been trying to for over a week and I am losing my mind.  I have samba set up  but I set a password (which I know) but it is asking for a domain (?) and I have no clue what they want.  I have another laptop running manjaro.  I am losing my mind trying to figure this out.  Any help greatly appreciated


I realize I didn't give a lot of technical info but at this point I'm so lost I don't know what to provide

---

### Post by mikybee93 on 2015-12-02
What kinds of phones and tablets are you using? If android, there's this great app called 'ES File Explorer" and it has built in support for networked drives. 

As far as getting samba set up on your laptop, it's probably asking for the domain of the computer itself (the IP address). It'll likely look something like '192.168.x.x' and you can probably pinpoint it if you use this command and search for it: 'ifconfig -a'

If you're having trouble locating it, try this one: 'ifconfig -a | grep 192.168.*.*

I'm sure you've seen it before, but this is a great tutorial that goes into good detail on accessing the samba server. 
[https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way](https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20(Command-line%20interface/Linux%20Terminal)%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way)!

---

### Post by Bucky Ball on 2015-12-03
Are the kids using Windows or Ubuntu? If you are running all Linux, then you don't really need Samba. Doesn't help with your Samba issue, but just to say there are other options ...

(PS: As Manjaro is based on Arch Linux, and not supported here, any advice you get here may/will not be applicable to that machine (although you might be able to translate).)

---

### Post by Patrick_Costa on 2015-12-03
Thanks for the replies.  I'll give it a shot when I get home.  Buckyball, I have samba running off of the ubuntu laptop so I figured I would ask here.  I can translate if I need to.

---

### Post by SeijiSensei on 2015-12-03
If the kids' devices support DLNA, then I'd recommend using [**minidlna**]("https://help.ubuntu.com/community/MiniDLNA") rather than Samba for streaming videos over your local network.  It's in the repositories.  The only real configuration required is adding a line or two to minidlna.conf that identifies the directories where the media are stored.  

On Android devices you can use the [BubbleUPnP]("https://play.google.com/store/apps/details?id=com.bubblesoft.android.bubbleupnp&hl=en") app to stream the videos and [MXPlayer]("https://play.google.com/store/apps/details?id=com.mxtech.videoplayer.ad&hl=en") to watch them.  In Windows, use Windows Media Player.  On Ubuntu, [VLC]("http://codeyarns.com/2015/01/25/how-to-play-content-of-upnpdlna-server-in-vlc/") has a DLNA client.

---

