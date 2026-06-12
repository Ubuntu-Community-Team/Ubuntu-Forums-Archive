---
title: "How to uninstall gnome network manager?"
date: 2018-03-05
forum: Networking &amp; Wireless
---

### Post by Silhorn on 2018-03-05
Hello,

I have installed wicd and would like to uninstall gnome network manager.

I tried to mark the network-manager-gnome package to be removed in synaptic but that will also remove gnome desktop and control centre so that can't be the package to remove.
I tried to mark network-manager to be removed but when clicking apply to says to fix broken packages. Network manager gnome has an exclamation mark.

How to properly replace network manager of Ubuntu 17.10 with wicd?

Also, does wicd have it's own tray icon? I can't see it but I remember when using mint mate it was there.

---

### Post by monkeybrain20122 on 2018-03-05
Why do you nee wicd? Is gnm not working?

---

### Post by kerry_s on 2018-03-05
your best bet is to just stop it loading, but leave it installed.

sudo stop network-manager
echo "manual" | sudo tee /etc/init/network-manager.override

for the icon:
wicd-client --tray

i think, run it from term first see what it does, if it works add to startup.

---

### Post by Silhorn on 2018-03-06
Reason for wanting to move to wicd is 2 reasons:
One is it allows me to see each access point using same SSID and which channel they are using. This is great so I can connect to the specific access point I like and also acts as a wifi analyzer app. So I don't need to use linssid app.

Second reason is when I am using in home streaming with a steam game, I have high quality image during streaming which means bandwidth is enough but every now and then I get a big lag spike. I search the internet and at least 1 other person has had a similar problem and fixed it by moving to wicd.
[https://steamcommunity.com/groups/homestream/discussions/0/540735426854884989/](https://steamcommunity.com/groups/homestream/discussions/0/540735426854884989/)
I think something to do with scanning
[https://ubuntuforums.org/showthread.php?t=2163994](https://ubuntuforums.org/showthread.php?t=2163994)

I try the things mentioned and will report back.

---

### Post by Silhorn on 2018-03-07
ok so I have tried 
sudo stop network-manager
But it says command not found.
I tried a command someone posted in the 2nd link someone posted and seems to have worked. Command was:
sudo killall -STOP NetworkManager

Now the command 
wicd-client --tray
Does not seem to work, this is the readout:
Has notifications support True
Loading...
Connecting to daemon...
Connected.
displaytray True
Done loading.

---

