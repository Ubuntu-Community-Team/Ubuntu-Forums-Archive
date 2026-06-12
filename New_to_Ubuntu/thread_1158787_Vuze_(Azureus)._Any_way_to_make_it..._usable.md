---
title: "Vuze (Azureus). Any way to make it... usable?"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by HittingSmoke on 2009-05-14
After a bad experience with Azureus many years ago on Windows I decided that would NOT be my torrent client in Ubuntu so I looked for something more minimalistic and powerful like uTorrent. I've been happily using Deluge since the start of my Ubuntufication.

Well, the Jaunty upgrade broke Deluge. Apparently it's a known bug and has something to do with GTK.

My problem is now I'm using Vuze because Transmission just isn't powerful enough for me but holy hell I hate it. I hate it so much, oh god how I hate it.

The whole thing is bloated feeling and the UI runs sluggishly on my PC, which is by no means low end at all. Menus open and change seconds after I click them and when I try to resize columns in the torrent list that column goes nutty and starts shooting back and fourth like a rubber band until I close and restart Vuze.

Is there any way to speed up Vuze? Not the downloads, that's not a problem. Just the UI. Are there also any ways to make Vuze more usable and resemble a real torrent client instead of a non-functional version of the already bad iTunes? I've looked for themes or plugins to make it not look like such a piece of crap but I'm just coming up empty handed with people reccomending Deluge as a replacement, which isn't working right now.

*P.S. If you want to post about the Deluge breakage problem instead of how to make Vuze more usable please post it [here]("http://ubuntuforums.org/showthread.php?t=1155405")*

---

### Post by AndThenWhat on 2009-05-14
You could try going into System Monitor (System -> Administration -> System Monitor) and going to the processes tab.  There you can right-click on the vuze process and change its priority level to something higher.

---

### Post by HittingSmoke on 2009-05-14
> **AndThenWhat said:**
> You could try going into System Monitor (System -> Administration -> System Monitor) and going to the processes tab.  There you can right-click on the vuze process and change its priority level to something higher.

Well that would kinda defeat the purpose of having a torrent client running in the background all the time to keep important seeds going. Was thinking more along the lines of a way to lighten up the UI a bit.

---

### Post by kpkeerthi on 2009-05-14
What version of java do you have installed?
```
java -version
```

---

### Post by HittingSmoke on 2009-05-14
> **kpkeerthi said:**
> What version of java do you have installed?
```
java -version
```

```
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) Server VM (build 11.3-b02, mixed mode)

```

I had to manually set Azureus to use Sun Java in the config file because it was reporting an error about not being able to find OpenJDK originally. Could that be part of it's sluggish behaviour?

---

### Post by kpkeerthi on 2009-05-14
Although I don't think so, you may want to try it with open-jdk. Instructions here: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java"). Be sure to set open-jdk as the default java for your system by running ```
sudo update-alternatives --config java
```

---

### Post by lovinglinux on 2009-05-14
I don't remember exactly how to do it, but Vuze has a preference option that allows you to use just the torrent interface without the other features. It basically will look like Azureus 2.5. This might help speed the interface responsiveness.

---

### Post by HittingSmoke on 2009-05-14
> **lovinglinux said:**
> I don't remember exactly how to do it, but Vuze has a preference option that allows you to use just the torrent interface without the other features. It basically will look like Azureus 2.5. This might help speed the interface responsiveness.

Ill try to find this when I get some free time. I did read a tooltip about some special version for people who liked the "old" interface but I disregarded it and cant pull it back up

---

### Post by fridaythe14th on 2009-05-25
I did it too. Tried to change it back now just to find how but I couldn't find it.

---

### Post by kpkeerthi on 2009-05-25
I found some discussion related to this here: [http://forum.vuze.com/message.jspa?messageID=172168]("http://forum.vuze.com/message.jspa?messageID=172168")

---

