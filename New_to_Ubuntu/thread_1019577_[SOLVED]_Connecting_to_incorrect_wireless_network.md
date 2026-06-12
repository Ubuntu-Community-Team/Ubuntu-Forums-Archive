---
title: "[SOLVED] Connecting to incorrect wireless network"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by Scunnered on 2008-12-23
[s]I have been looking at this post with interest from the reverse.  What I experience is that on start up I sometimes automatically connect to someone elses wireless network. [/s]

When I left click on my wireless network icon I can see at the moment 2 other items in addition to my own.  Of the two one has what would appear to be an icon which I assume is an indication that security is applied and it is the other network that I access which has no icon showing.

Naturally I dont wish to act in an inappropriate fashion and ask what can I do to eliminate this problem?

Thanking you in anticipation

---

### Post by jespdj on 2008-12-23
Ubuntu shows the wireless networks that it detects. That does not mean it automatically connects to those networks. So you don't have a problem that you have to eliminate.

And ofcourse Ubuntu certainly never automatically cracks and connects to a secured network.....

---

### Post by wieman01 on 2008-12-23
Connecting to "open" networks in Europe is legal. So you ought to be fine from my perspective. As jespdj has pointed out, Ubuntu does not crack WEP keys and then connects, therefore there shouldn't be any breach.

You can always remove specific wireless networks from NM's list of trusted networks. Then it should connect automatically any longer.

---

### Post by Scunnered on 2008-12-23
jespdj & wieman01

Firstly thanks very much for your replies. Contrary to what jespdj said when I booted up to check the forum I automatically connected to the unsecured network and had then to change settings to ensure proper connection.

Could you advise how I can remove the offending network as it will save a lot of bother at start up.

Once again thanks

---

### Post by dmizer on 2008-12-23
I split these posts out into a new thread, as there is a legitimate request for help, but it was off topic.

---

### Post by wieman01 on 2008-12-23
Scunnered, 

I am on Kubuntu so naturally Network Manager looks a little different, however, I believe you can delete "trusted" networks by opening the settings dialogue and removing them from there. 

Can you find something similar there?

---

### Post by Maverick1712 on 2008-12-23
It just looks like it is automatically connecting to the open network, since it does not require any input from the user. What you can do is right click on the nm-applet and select "edit connections", from there, you should be able to tell nm to connect to your prefered network and it will connect to that one on startup. (Sorry I cannot say exactly where, I am currently at work so don't have access to my Ubuntu machine. I hope to edit this post when I get home).

Cheers,
Adam

---

