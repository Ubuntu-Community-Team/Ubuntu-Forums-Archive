---
title: "Have to switch password type from &quot;hexidecimal&quot; to &quot;plain&quot;"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by timmyblog on 2007-01-28
For some strange reason every time I restart Ubuntu I have to reset the wireless so to speak. The wireless will not work unless I double click on the wireless icon and click configure to open up the Wireless Config dialog. My network has no security, except that it does not broadcast the SSID, so I have that saved int he config just fine, except that it will not work unless I go in and change the password type from hexidecimal to plain. (And vice versa if it is set to plain first) only then will the network get picked up and recognize.

Now I don't mind doing this, but there has to be some way that it will auto configure every time I restart without me having to manually go in and change this setting in order to get the network working. The 3 screenshots are attached so you can see what I'm talking about.

---

### Post by timmyblog on 2007-01-31
Anyone else have a similiar problem?

Hell I'll even post the solution to my blog if someone knows it.

---

### Post by Floppyjoe on 2007-01-31
I am curious to know which version of Ubuntu you are using and what your /etc/network/interfaces file contains. Do you use Network Manager to connect to the internet?

```
sudo gedit /etc/network/interfaces
```

---

