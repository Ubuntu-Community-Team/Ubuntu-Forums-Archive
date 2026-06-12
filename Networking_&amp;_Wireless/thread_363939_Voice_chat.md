---
title: "Voice chat"
date: 2007-02-17
forum: Networking &amp; Wireless
---

### Post by ali780 on 2007-02-17
Hello everybody
How can I have a voice chat in ubuntu?
Thank you

---

### Post by aa.ivanov on 2007-02-17
Well, the most well-known voice-over-internet applications seem to be ekiga (was gnome-meeting before) and skype.
The first one is free software, but is more a phone than a chat app IMHO. Chances are that it is already installed.
The second is commercial software (that could be used free of charge) and is the preffered way of many people to keep in touch. Take a look at the skype.com site for a linux package. [The debian package]("http://skype.com/download/skype/linux/") should work... I hope. It worked the last time I used it. Or you can [set APT's repository]("http://skype.com/download/skype/linux/repositories.html").
Hope someone will correct me if I'm forgetting something.

---

### Post by ali780 on 2007-02-17
thank you I will try to use them

---

### Post by ali780 on 2007-02-17
I want to know can I use my Yahoo account and use it for voice chat?

---

### Post by aa.ivanov on 2007-02-18
I'm not sure whether this can be done. 
The standard protocols for VoIP telephony (SIP, IAX etc.) are relatively well supported. As long as the both parties use sip phones (for example) they can talk.

The proprietary protocols are not that well supported. I have no experience with voice over icq or yahoo, or anything alike and I have not done any research on this issue. There are some programs like phonegaim, wengophone and tapioca that offer IM and voice integration, but I don't know if they can do what you want them to.

If I'm to speculate, I'd say that chances are that you won't be able voice-chatting over the yahoo unless yahoo has released a version of their software for linux. Even if they did so it doesn't necessarily mean it'll support all the functionality of the windows versions. Skpe for example does not offer video chat for linux, and the linux version is still 1.x while windows users have 2.x versions. I'm sorry but Desktop Linux is still not that attractive for these companies :(

I'd also speculate that support for Jabber voice chat (e.g. Google Talk) wold be easier to implement that ICQ/MSN/Yahoo/etc - it's an open protocol by its nature. 

All I can say for sure is that gaim, the default IM application for GNOME will support voice chat in version 3.x... whenever it is ready. I hear that Koppete, the IM application of KDE is more advanced in this field, but I'm using Ubuntu, not Kubuntu.

Feel free to investigate all applications I've mentioned as well as the other posts on this matter on the forums.

---

