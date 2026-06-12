---
title: "Key ring prompt very annoying."
date: 2007-08-22
forum: Networking &amp; Wireless
---

### Post by Scrib on 2007-08-22
Hi,

   When I log into UBuntu I get the keyring prompt - which I find really :mad: annoying :mad: .

I read somewhere that if I set the keyring to the same as my log password then the prompt will not appear. 

I've just rebuilt my system so I thought I'd try it. Guess what it doesn't work.

Anyone know how to get rid of the prompt?

---

### Post by ddrichardson on 2007-08-22
If you are running 7.07 then there is a useful section [here]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo?highlight=%28wpa%29").

---

### Post by Scrib on 2007-08-27
OK Thanks - this works - sort of.

Now when I log in I do not get the password knagg. However, my Wireless network does not connect. 

Network manager 0.6.4 tries to connect but fails (after a minute or so). If I then click on the NM icon and choose my network from the list it then reattempts to connect and works.

Is there a way to get it to connect on its own without the second attempt? I appears to be a timing issue as the second attempts works fine, wthout having to change any settings or enter any passwords, etc.

---

### Post by ddrichardson on 2007-08-27
I've never experienced this, perhaps someone else has?

---

### Post by Scrib on 2007-08-29
It does seem to be a timing thing. If I oot the box and then leave it a few mins before logging on everything works ok and no knaggs.

If I log on as soon as the log on screen appears it fails to conect to the wirless network and I have to simply reselect it in netowkr manager.

No big deal i guess.

---

### Post by chriswyatt on 2007-08-30
You could try creating a script which would contain the sleep command (however much time you need to wait before you login I suppose) and the path of the WiFi manager.

The file could be called, say, WiFiLaunch.sh and it could contain

Sleep (Whatever)
nm-applet --sm-disable

After saving it you would need to make it executable, you can do this by right clicking on the file and going through the properties dialogue box.  Then make it run at startup by going to System, Preferences, Sessions and changing Network Manager to point to this script instead of directly to nm-applet.

I know this is quite long-winded and not the best solution, but it's an idea.

---

### Post by Scrib on 2007-09-01
hummm after some more time looking at this it does not seem to be timing. It seems to be totally intermittent.

Sometimes it connects to my wireless wpa network at log in, and some times it does not.

When it does not connect automtically I can manually connect (clicking nw manager and selecting my network) and even then it some times takes a couple of attempts before it connects. 

I'd blame my network, however my windows boxes connect fine first time every time.

---

