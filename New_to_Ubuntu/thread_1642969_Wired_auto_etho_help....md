---
title: "Wired auto etho help..."
date: 2010-12-11
forum: New to Ubuntu
---

### Post by dragon1111 on 2010-12-11
i'm absolutely new to Ubuntu...i installed ubuntu 10.10 a couple of days ago... i encountered a gnome error this morning and i think i've deleted auto etho by mistake because i dont see the auto etho icon on the tray anymore...How do i put it back....Plz help

---

### Post by gemini on 2010-12-11
I think your network cable or a port on your router went bad.  I would make sure you have a good connection that works on another computer and then try: 

```
sudo /etc/init.d/networking restart
```

---

### Post by amjjawad on 2010-12-11
> **dragon1111 said:**
> i'm absolutely new to Ubuntu...i installed ubuntu 10.10 a couple of days ago... i encountered a gnome error this morning and i think i've deleted auto etho by mistake because i dont see the auto etho icon on the tray anymore...How do i put it back....Plz help

System > Preferences > Network Connections > Wired
Click "Add" if you have to.

---

### Post by dragon1111 on 2010-12-11
i just opened my network connections and i find auto ethos in the box there...does that mean only the icon has disappeared?

---

### Post by ajgreeny on 2010-12-11
Make sure you still have the **Notification Area** in your panel, as that is what contains the Network manager applet.

---

### Post by amjjawad on 2010-12-11
> **dragon1111 said:**
> i just opened my network connections and i find auto ethos in the box there...does that mean only the icon has disappeared?

Are you trying to connect to the interent or you already connected but you're looking for the icon in your panel?

---

### Post by dragon1111 on 2010-12-11
there's absolutely no problem with the internet connection..i even checked my network connections and i can find auto ethos in the box there...i think only the tray icon has disappeared...shall i remove the network manager applet software and reinstall it?

---

### Post by amjjawad on 2010-12-11
> **dragon1111 said:**
> there's absolutely no problem with the internet connection..i even checked my network connections and i can find auto ethos in the box there...i think only the tray icon has disappeared...shall i remove the network manager applet software and reinstall it?

You may want to have a look at [this]("http://ubuntuforums.org/showthread.php?t=1471824").

---

### Post by dragon1111 on 2010-12-11
i tried exacly that....removed the nm-applet software and reinstalled it..on reboot,i still cant find the auto etho icon (the 2 arrows in opposite directions)

---

### Post by amjjawad on 2010-12-11
> **dragon1111 said:**
> i tried exacly that....removed the nm-applet software and reinstalled it..on reboot,i still cant find the auto etho icon (the 2 arrows in opposite directions)

I'm trying to search on Google and I found this:
[http://ubuntuforums.org/showthread.php?t=821028&highlight=nm-applet+panel](http://ubuntuforums.org/showthread.php?t=821028&highlight=nm-applet+panel)

---

### Post by amjjawad on 2010-12-11
This guy managed to fix it:

[http://ubuntuforums.org/showpost.php?p=9236722&postcount=16](http://ubuntuforums.org/showpost.php?p=9236722&postcount=16)

I have to go so please report back whether it worked for you or not ;)

---

### Post by dragon1111 on 2010-12-11
it still doesnt show up... there's everyting on the panel from volume to messages and from date n time to chat account...even the internet is working but those '2 arrows in opposite directions' corresponding to auto etho dont show up

---

### Post by amjjawad on 2010-12-11
> **dragon1111 said:**
> it still doesnt show up... there's everyting on the panel from volume to messages and from date n time to chat account...even the internet is working but those '2 arrows in opposite directions' corresponding to auto etho dont show up

I posted 3 links (I guess) here. Have you tired them all? did you restart your machine?

I found some threads here but one of them is totally messed up and I can't understand or find the exact solution.

I'll try to search google and find something OUTSIDE this forum. People here need to learn that they must start their own thread and not keep posting on existing threads.

P.S.
I can't stay here for too long. I hope you could start searching too ;)

---

### Post by dragon1111 on 2010-12-11
hahahhahaa...yeah i'm searching too...will surely let you know of it once i fix it...thanks for your time mate....i really appreciate it

---

### Post by amjjawad on 2010-12-11
> **dragon1111 said:**
> hahahhahaa...yeah i'm searching too...will surely let you know of it once i fix it...thanks for your time mate....i really appreciate it

One of my hobbies and interests is helping people but sometimes it's getting so ugly when you find something so messy (I mean messed up threads here - I don't mean yours) ;)
Never mind. I'll keep searching and hope you'll do the same.

I'll be on and off because I'm doing something else on another PC.

You welcome :)

---

### Post by amjjawad on 2010-12-11
Mate, how about [this]("http://ubuntuforums.org/showthread.php?t=1591270&highlight=network+manager+icon")?

---

### Post by Norm24 on 2010-12-11
Did you not try what ajgreeny suggested?

Right click on panel>click Add to Panel...>click Notification Area and then hit the Add button.

---

### Post by dragon1111 on 2010-12-11
thankyou so much amjawad...i restored panel to default...its absolutely  fine now...thanku thanku thanku thanku thanku so so much...if only you  lived nearby i'd have gotten you plenty of beer lol


[IMG]http://static.howstuffworks.com/gif/top-5-beer-making-tips-1.jpg[/IMG]t

---

### Post by dragon1111 on 2010-12-11
@norm24 - there was nothing wrong with the notification area...it was very much intact...only the nm-applet had disappeared coz there was a genome error this morning...but then i just restored my panel to default,thanks to amjawad...its absolutely fine now

---

### Post by dragon1111 on 2010-12-11
another useful link:
[http://www.webupd8.org/2010/09/how-to-reset-gnome-panels-compiz.html](http://www.webupd8.org/2010/09/how-to-reset-gnome-panels-compiz.html)

---

### Post by dragon1111 on 2010-12-11
thank you everybody for your time...i really appreciate that

---

### Post by amjjawad on 2010-12-11
> **dragon1111 said:**
> thankyou so much amjawad...i restored panel to default...its absolutely  fine now...thanku thanku thanku thanku thanku so so much...if only you  lived nearby i'd have gotten you plenty of beer lol


[IMG]http://static.howstuffworks.com/gif/top-5-beer-making-tips-1.jpg[/IMG]t


HOOOHAAA, WELL DONE :D

Hahaha, that was a lot of beer ... do you want to kill me? :P hahaha.
I'm glad you managed to fix it. You welcome, mate. No need to thank me, it's my pleasure to help everyone here. I enjoy when someone could fix his/her problem, really.

Now, do me a favor and post in details what you did exactly to fix that. I'm going to bookmark this thread and use it when someone else has the same issue. However, I just need a clear post from your side that explains/shows what were the steps you followed to fix that.

Well done and keep it up ;)

---

