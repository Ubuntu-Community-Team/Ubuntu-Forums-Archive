---
title: "[SOLVED] WiFi Radar only works sometimes"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by tugh on 2007-03-10
Hi,

I have a Sony Vaio laptop which I've installed Ubuntu 6.10 recently. I'm having problems with the WiFi Radar. The issue is that most of the time it doesn't connect to my wireless router at home automatically. Occasionally it does, though. Usually it says it's "connected" but cannot get an IP address. So, what I do is, I go to "Edit" and select another "Mode" under "Wifi Options", save it, and click on "Connect". If it doesn't work, try another "Mode". After several times, it finally connects. It sometimes works when I select "Managed", sometimes "Master", sometimes "Secondary" etc. Sometimes I can connect after my first attempt, sometimes my 10th. I haven't found any pattern yet. Another way to connect is to disable and then enable the box under Networking>Wireless>Properties.

It's really annoying to go through this almost everytime I turn on my laptop. Does anybody out there who has any opinion why this is happening? Or, is there any alternative application that I can use?

Thank you.

---

### Post by mabelrxu on 2007-04-22
since you're using ubuntu and not xubuntu, u might want to think about using nm-applet ... there's a guide available @ debianadmin.com ... there isn't even any setting up you have to do, just
[HTML]sudo apt-get install nm-applet[/HTML]
and restart the computer, then it automatically shows up in your tray panel so that u can left click and select a network to connect to ... u do need to know your network's password, though, and i'll probably ask you for your keyring password so that it can add the network password to the keyring

---

