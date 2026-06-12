---
title: "Can see wireless networks - but not my own???"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by c00ch on 2008-04-28
I know I should not have clicked the upgrade button. I ruined a perfectly running Gutsy and have no a somewhat defunct Hardy on my laptop. I don't know why I did it.

Anyhow, just as many other users have experienced, after the upgrade to hardy, my wireless adapter did not work anymore. I reinstalled the drivers, but in the end used the ndiswrapper solution:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

Now the wireless adapter (seems) to work again, but lo and behold... not with my own wireless router. I can see all my neighbours' networks including signal strengths and what-have-you. But my router is gone. When in fact it isn't as my other machines (all Macs) are working. Has it something to do with the router being an Apple AirPort base station?

At any rate, it worked fine until I hit that blasted upgrade button... ](*,)

Any suggestions greatly appreciated!

---

### Post by c00ch on 2008-04-29
bump.

anyone?

---

### Post by dhysk on 2008-04-29
sorry for dumb questions, but do you hide your ssid?  Second did you try to manually config it.  I hide my sid so i have to manually put in my ssid and passphrase.

---

### Post by c00ch on 2008-04-30
Thanks for the reply. No, the SSID is not hidden. I have tried to configure the connection manually using the correct SSID and pass phrase, it still doesn't work.

I have tried everything I could think of on my Ubuntu machine. I don't think that I will try anything outside the linux box (e.g. reconfiguring the router etc.) as I don't want to mess up my perfectly running network. 

As I said, Gutsy was working like a treat. Without utilizing ndiswrapper I should mention - which I had to use to get my wireless adapter running after the upgrade.

Overall, Hardy so far has proven to be a rather unsatisfactory upgrade. Last time that I pushed the Upgrade button in Ubuntu (they should ditch it). Not to mention that with my current setup I don't have to worry about the Upgrade button considering that I don't have an internet connection anymore...:(

---

### Post by jimv on 2008-04-30
First no wireless and then it sees all the networks but yours?  Now it's just toying with you.

---

### Post by c00ch on 2008-05-01
It seems like it, doesn't it. Hardy is evil. 

I probably gonna reinstall Gutsy as I still haven't figured out what's wrong. I presume it is rooted in the access point setup somewhere, and while gutsy could handle it, Hardy can't. Or perhaps it's ndiswrapper? Ah... Linux...:rolleyes:

---

### Post by Aearenda on 2008-05-01
Just a thought - what channel does your wireless router use? Maybe Hardy is limited to the US range of channels, and so not seeing yours?

---

### Post by macroshaft on 2008-05-02
What security are you using on your network? I have just recently discovered that my copy of hardy displays only WEP networks, WPA connections do not show at all and cannot be connected to manually. I'm having trouble finding anything about it on here and it's driving me nuts!

---

### Post by Aearenda on 2008-05-02
macroshaft: 
For troubleshooting you might like to see [http://ubuntuforums.org/showthread.php?t=571194](http://ubuntuforums.org/showthread.php?t=571194) or [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

You might have the same problem as this: [http://ubuntuforums.org/showthread.php?t=713780](http://ubuntuforums.org/showthread.php?t=713780)
Or this: [http://ubuntuforums.org/showthread.php?t=737102](http://ubuntuforums.org/showthread.php?t=737102)

Is the network hidden? See the end of this thread: [http://ubuntuforums.org/showthread.php?t=172810](http://ubuntuforums.org/showthread.php?t=172810)

---

