---
title: "wifi and wired connetion"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by mafi127 on 2011-05-13
I need to share my wifi whit my other computer what dont have wifi anten. I need to make my laptop to share the wifi what I am connected to whit another computer whit wired connection. I have configured auto eth but when I plug the internet cabble whit my laptop then the wiffi connection get lost how can I fix this?

---

### Post by mafi127 on 2011-05-13
In windows I can make two connections. What I mean is I have one pc connected whit my TV and I want that this computer connects to my laptop whit wired so I can transfer movies faster to media center.

I have readed this tutorial [http://davidzhang.webs.com/apps/blog/show/5725746-how-to-bridge-an-ethernet-connection-with-a-wireless-connection-on-linux](http://davidzhang.webs.com/apps/blog/show/5725746-how-to-bridge-an-ethernet-connection-with-a-wireless-connection-on-linux) , and seend on net the same tutorials but when I connect my cable whit laptop I get disconnected from wifi and I cant selecet any wifi networks, to reconnect.

---

### Post by mafi127 on 2011-05-13
I found out in this post that it is possible to make two connections, [http://ubuntuforums.org/showpost.php?p=3855326&postcount=11](http://ubuntuforums.org/showpost.php?p=3855326&postcount=11) but I cant find whre can I cange the raming mode in network manager. some help me plz :(

---

### Post by varunendra on 2011-05-14
> **mafi127 said:**
> I found out in this post that it is possible to make two connections, [http://ubuntuforums.org/showpost.php?p=3855326&postcount=11](http://ubuntuforums.org/showpost.php?p=3855326&postcount=11) but I cant find whre can I cange the raming mode in network manager. some help me plz :(
Which version are you using? I think "Enable Roaming Mode" is same as "Connect Automatically" checkbox in newer NetworkManager interface. Just clear one checkbox (either in wired or in wireless network settings).

I've seen a few laptops that have an inbuilt BIOS setting (enabled by default) to automatically switch off wifi as soon as an ethernet cable is plugged in. This is done to save battery power (although it works even if the laptop is on ac power). So if the above trick does not work, you may also wish to check whether the wifi remains 'on' when the ethernet is plugged in.

---

### Post by wep940 on 2011-05-14
I've even had desktops that do that same disconnect.  Just curious - does the wired connection need to be set to adhoc (if that's even possible on a wired connection)?

---

### Post by varunendra on 2011-05-14
> **wep940 said:**
> I've even had desktops that do that same disconnect.  Just curious - does the wired connection need to be set to adhoc (if that's even possible on a wired connection)?
I think there is the "Link-Local only" option in NetworkManager for the adhoc mode. But I can't say if this can be a solution.

---

