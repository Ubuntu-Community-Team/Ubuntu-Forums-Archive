---
title: "My Windows Network disappeared?!"
date: 2007-07-03
forum: Networking &amp; Wireless
---

### Post by herbster on 2007-07-03
So I click on Places > Network and then open Windows Network which of course showed my "mshome" just fine, but suddenly nothing is showing. Hit reload 100 times, restarted both machines, nothing.

I can remote desktop into my networked XP machine just fine but can't seem to browse it on network, what the heck??

---

### Post by limbourg31 on 2007-07-03
are you trying to enter the network?

---

### Post by herbster on 2007-07-03
> **limbourg31 said:**
> are you trying to enter the network?

Sorry what exactly do you mean?

I typically use Places > Network, then Windows Network is there so I doubleclick and see MSHOME, doubleclick that and then can browse the networked PC right there.

What's happening is after I doubleclick Windows Network, it's empty :(

---

### Post by limbourg31 on 2007-07-03
oh sorry, i thought you were trying to be on the network. so do you have a working internet connection on ubuntu? if so then i would think the other computer is probably not recieving any signals, so you might want tocheck that wireless card

---

### Post by herbster on 2007-07-03
Yeah that's the thing, my internet is working perfectly, like I said I can even remote desktop into the XP machine just fine from this Ubuntu box. The only thing not working is being able to browse my windows network in Places > Network. It doesn't show up.

And I am using a Linksys router, no wireless stuff :)

---

### Post by lisati on 2007-07-03
Internet connectivity is no guarantee that you'll be able to see shared folders from another machine.
[LIST=1]
[*]You might want to run the "Network setup wizard" on your Windoze machine.
[*]You might need to set up "file and printer sharing"
[/LIST]

---

### Post by herbster on 2007-07-03
That's the thing, it's all setup. It has been working perfectly for the longest time, I have changed no settings. :confused:

---

### Post by Fitzcarraldo on 2007-07-03
Looks like you've discovered the dreaded 'missing Windows Network in Nautilus' phenomenon. The Ubuntu forums are littered with many threads from people who have experienced or are still experiencing this infuriating problem. Some people have managed to find a fix, but none of the fixes have worked for me or several other 'sufferers'. The problem was reported as a bug in Ubuntu 6.06 and is still unresolved as far as I know. From what I read in these forums, the KDE browser Konqueror does not exhibit the problem, whereas the GNOME browser Nautilus does for some people. The best I have been able to achieve is to find a couple of workarounds that I read about in threads in these forums: one is to create a shortcut icon on the Desktop for each of the other PCs on the network, and the other is to launch Nautilus as root in which case I can browse the network perfectly. See the following thread for details of the latter workaround:

[http://ubuntuforums.org/showthread.php?t=430806](http://ubuntuforums.org/showthread.php?t=430806)

If you search these forums for key words such as "samba", "shares", "nautilus", "windows network", "browse" etc. you will find many threads about this problem. I think I have tried every suggestion but never managed to get it working again. Like you, it just stopped working one day. A couple of weeks ago it suddenly worked *once* -- I nearly fell off my chair -- and then stopped working again after I closed the Nautilus browser window and reopened it having changed absolutely *nothing* on my PC or the network or the other PCs on the network.

---

### Post by herbster on 2007-07-03
FItzcarraldo,

Hot damn I'm in your boat, I had it happen on Edgy, then had reinstalled for other reasons and it was fine forever since, but now a recently new Feisty install I had forgotten about that bug since it was working so well but here it goes again! I'm not sure to what degree the linux minds out there are working on it but one would think this is a pretty serious/important "bug" that should be worked out as asap I'm sure many people use Windows shares and clearly have experienced this :mad:

I just tried your recommendation:

```
sudo nautilus --browser
```

I went Go > Network and I see Windows Network, but when I try double clicking on it nothing happens, it just stays exactly as is, but in terminal I saw this happen everytime I double clicked it:

```
Couldn't get main dbus connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

Not sure if it means anything or if I'm just doomed to never have access to my XP box shares again :( This is going to be a huge pain in the butt if it's the case!!

**EDIT: Whoops I got my own answer, I just did Connect to Server in Places and can access my windows share just fine. This is just too wierd!**

---

### Post by craigsn on 2007-07-05
For me it is the same thing, except I cannot get the connect to places to work. 

On the other hand, I have also been trying to get a samba server up and running so I can go from windows to linux as wel. So maybe I screwed something up there.

Other suggestions to solve my network problem would be helpful.

---

### Post by herbster on 2007-07-05
craigsn,

You mean Places > Connect to Server does not function? When you click it nothing happens, or does it show up and not connect to the location you input? If the former, indeed strange, but the latter should have a solution.. let us know.

---

### Post by craigsn on 2007-07-05
> **herbster said:**
> craigsn,

You mean Places > Connect to Server does not function? When you click it nothing happens, or does it show up and not connect to the location you input? If the former, indeed strange, but the latter should have a solution.. let us know.

Actually, connect to server brings up the dialog box, so that is fine. But I have read some other threads in the meantime, and find I cannot ping my windows box. Linux is 192.168.2.3 and windows is 192.168.2.2. Can not figure that one out. Both are set to be my network name of cdp.

Thanks for the response.

---

