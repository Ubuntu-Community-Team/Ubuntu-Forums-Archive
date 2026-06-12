---
title: "Error during shutdown Ubuntu 9.04"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by babloo75 on 2009-05-30
I recently upgraded my Ubuntu 8.10 to 9.04 version. Have also installed Avant window navigator. 
When ever I shut down my ubuntu 9.04 it says waiting time of 60 seconds. When I don't wait for 60 seconds and shut down before this waiting time it gives a error message for a fraction of a second which I am not able to read and then produces some sound and then shuts down. This occurs even if i wait for 60 seconds too. 
Why this new version of Ubuntu has been bundled with the wait time... don't understand.
and what could be the error message, and how to get rid of this error message. 
Please help..........

---

### Post by steeleyuk on 2009-05-30
The wait time is optional, for those people that want to click Shut Down on the menu and walk away. If you want to shut down the computer immediately then you need to click Shut Down again to confirm it.

Not a clue what the error is though.

---

### Post by babloo75 on 2009-05-30
Is there any way to know the error from terminal?
If theres one, I can know what the error report and post it here to get some help from the community.

---

### Post by babloo75 on 2009-05-31
This time I gave the command to "Restart" and the error window stayed there for a fraction of second and I could read the first few words. It said:
"Screen isn't composited........"
and then the computer restated. Thats all i could read.
Please guide.

---

### Post by nandemonai on 2009-05-31
Check 'messages' in System -> Administration -> Log File Viewer.

Should have something in there around the time of your last shutdown or reboot.

---

### Post by babloo75 on 2009-05-31
> **nandemonai said:**
> Check 'messages' in System -> Administration -> Log File Viewer.

Should have something in there around the time of your last shutdown or reboot.

Could not understand anything there. Let me restart once again and put the screenshot of the same here.
Thanks

---

### Post by nandemonai on 2009-05-31
> **babloo75 said:**
> Could not understand anything there. Let me restart once again and put the screenshot of the same here.
Thanks

Run this in terminal:

```
cat /var/log/messages > ~/messages.txt
```

That will save a txt file in your home directory with all the messages contained. Go to [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and copy / paste the contents of the file and provide us a link.

---

### Post by babloo75 on 2009-05-31
> **nandemonai said:**
> Run this in terminal:

```
cat /var/log/messages > ~/messages.txt
```

That will save a txt file in your home directory with all the messages contained. Go to [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and copy / paste the contents of the file and provide us a link.

Last time I restarted my computer at 23:48 HRS on 31st May. 
I have copied and pasted the required content as you said. The link is here:
[http://paste.ubuntu.com/185147/](http://paste.ubuntu.com/185147/)

---

### Post by nandemonai on 2009-05-31
Hmm, doesn't appear to be in there. Where are you actually seeing this error? In the GUI or when the screen goes black with text?

---

### Post by babloo75 on 2009-05-31
It appears at the desktop screen itself just after the window for "60 seconds shut down command" disappears. 
As i said the error window stays there for a fraction of a second only so am not able to read it properly. But it says something like "screen isn't composited....... etc etc"
It occurs at the time of system shut down beep sound. One more thing I have noticed with Ubuntu 9.04 that even if my speakers are off, the machine makes this beep sound while shutting down. I think earlier it was not there.
I hope this is not causing any damage to my machine.

---

### Post by steeleyuk on 2009-05-31
Are you running Compiz?

If you are, try to turning it off and see if the same message appears.

---

### Post by nandemonai on 2009-05-31
> **babloo75 said:**
> It appears at the desktop screen itself just after the window for "60 seconds shut down command" disappears. 
As i said the error window stays there for a fraction of a second only so am not able to read it properly. But it says something like "screen isn't composited....... etc etc"

Ohh right now I'm with you. It sounds like compiz (desktop effects) is being taken down just before the rest of the GUI is. If that's the case I wouldn't worry about it too much. That's provided you have desktop effects enabled.

---

### Post by blastbar on 2009-05-31
i too am having errors shutting down, not quite the same i get the beep from my computer but no real shut down screen just goes all red then the machine turns off any clues what this is or how to fix it? thanks

---

### Post by babloo75 on 2009-05-31
Yes yes......... I was talking about this message mentioned in the bottom part of the screenshot.
I disabled the desktop effects. and got the same error message like this... (see screenshot- the bottom half of the screen).

 Please guide me.. is it harmful for my machine. what should I do now... I mean what should be the best configuration for Compiz.
Thanks in advance.

---

### Post by nandemonai on 2009-05-31
> **blastbar said:**
> i too am having errors shutting down, not quite the same i get the beep from my computer but no real shut down screen just goes all red then the machine turns off any clues what this is or how to fix it? thanks

The beep is normal. It's a broadcast that tells other users logged into the system that it's shutting down.

You can disable it if you wish by blacklisting the pcspkr module. Many threads on the forum about it lately if you search.

As far as the screen going all red? No idea I'm afraid. It should show the splash screen while the system is shutting down.

---

### Post by blastbar on 2009-05-31
sorry i didnt search, i can't work out what it could be either because its the official ubuntu disk that they send out....

---

### Post by nandemonai on 2009-05-31
> **babloo75 said:**
> Yes yes......... I was talking about this message mentioned in the bottom part of the screenshot.
I disabled the desktop effects. and got the same error message like this... (see screenshot- the bottom half of the screen).

 Please guide me.. is it harmful for my machine. what should I do now... I mean what should be the best configuration for Compiz.
Thanks in advance.

Harmful? No. Why you're getting that message though I'm not sure. Could be you're running something that requires or at least wants compiz enabled.

So you get this message on shutdown even when desktop effects is enabled? Again I believe this is because compiz is being shutdown before whatever is wanting it loaded when you shutdown.

Safe to ignore though in my opinion.

---

### Post by nicoverbking on 2009-05-31
It's nothing to worry about. But if you want the message to be gone...

This is what I understood from your screenshot:

It's Avant Window Navigator complaining that compiz is not on and it can't start without compiz.

Do you use Avant Windows Navigator? If you do, it's quite possible that it starts and fails to start or shuts down when you turn compiz off (in this case, when you turn your computer off) - if you don't, it is most likely running automatically (or trying to run) without you actually needing it.

So, if you want to keep using Avant Window Navigator, I'd say: ignore it - else, remove AWN (Avant Windows Navigator) from the startup-programs - or remove it completely from your system.

---

### Post by babloo75 on 2009-05-31
Yes, I am using Avant Window Navigator also. I think that is causing this problem.
But I love this beautiful thing......
If it doesn't harm my computer, i would like to continue with this...
Thanks to all of you...

---

### Post by vitaraq1962 on 2009-09-11
I had this one myself, this is how i fixed it...


Alt-F2 &#8594; gconf-editor &#8594; /apps/avant-window-navigator/show_dialog_if_non_composited

Uncheck it.

Hope this helps

Gary
:P

---

### Post by babloo75 on 2009-09-16
Yes. it works. Thanks a lot

---

### Post by carnagex420x on 2009-12-25
thnx

---

