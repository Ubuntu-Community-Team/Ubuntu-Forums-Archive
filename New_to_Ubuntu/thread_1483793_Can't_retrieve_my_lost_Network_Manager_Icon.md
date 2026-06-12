---
title: "Can't retrieve my lost Network Manager Icon"
date: 2010-05-15
forum: New to Ubuntu
---

### Post by MildlyInsane on 2010-05-15
I am trying a different forum to get an answer to why it was easy as pie to accidently erase my network mgr icon from the top panel of my desktop but extremely difficult to get it back. 
Installed brand new Ubuntu last night with Gnome. Im not able to get on line without it. Wasting lots of time trying to recover that tiny little thing.

---

### Post by garvinrick4 on 2010-05-15
Here is the Code:

```
sudo apt-get install network-manager-gnome
```

Or right click on toolbar where it is suppose to be and remove the other couple will go away.

Right click on toolbar and add to panel, select notification area and they will all be replaced.
The sound the envelope and the network applets I am talking about. Notification area is where they all appear in other words.

---

### Post by Ozymandias_117 on 2010-05-15
Right click Add to panel Notification area, if that doesn't work try
```
sudo service network-manager restart
```

---

### Post by Ozymandias_117 on 2010-05-15
> **garvinrick4 said:**
> The sound the envelope and the network applets I am talking about. Notification area is where they all appear in other words.

Sound and envelope are part of Indicator Applet, Network Manager is part of Notification Area

---

### Post by fms8424 on 2011-07-08
Thank you!
I've been trying to get my network manager back for _months_.

---

### Post by shibu_sawyer on 2011-07-08
> **MildlyInsane said:**
> I am trying a different forum to get an answer to why it was easy as pie to accidently erase my network mgr icon from the top panel of my desktop but extremely difficult to get it back. 
Installed brand new Ubuntu last night with Gnome. Im not able to get on line without it. Wasting lots of time trying to recover that tiny little thing.

its very simple,the n/w manager icon is present under notification area, simply right click the top panel,then select add to panel,in the list of options you see in the dialog ,select notification area and you can see the applet displayed again in the top panel.

---

