---
title: "Configuring Network Interfaces ?"
date: 2005-10-05
forum: Networking &amp; Wireless
---

### Post by emperon on 2005-10-05
Hello, I am asking the classic old question again but so far, i did not encounter any satisfying answer.

I am using my laptop at several places with wireless and wired. Each time it is booting it has a significant delay while waiting for "Configuring Network Interfaces?" Is there a smart and an elegant way to minimize this process ?

Onur

---

### Post by xristos on 2005-10-05
If you have set up your interfaces to obtain an IP by DCHP then when your laptop boots it searches for the dchp ( or dns ) server and until it gives up the try you have to wait .

You can solve this by putting static IPs to your interfaces :)

---

### Post by mlomker on 2005-10-05
> "Configuring Network Interfaces?" Is there a smart and an elegant way to minimize this process ?

You can generally press Ctrl-C at those pauses to skip them, but it might leave your network not configured of course...

---

### Post by emperon on 2005-10-06
[QUOTE=xristos]If you have set up your interfaces to obtain an IP by DCHP then when your laptop boots it searches for the dchp ( or dns ) server and until it gives up the try you have to wait .

You can solve this by putting static IPs to your interfaces :)[/QUOTE]
Ok i understood, but i am curious how windows handles this situation. It can still boot fast with a dhcp configured interface. Why not in Ubuntu ?

---

### Post by knappen on 2005-10-06
Can it not be controlled by ifplugd?

---

### Post by knappen on 2005-10-06
I forgot, but I do believe they have added a network manager in breeze that will automatically take care of your connections. 

It will select the cable if present, otherwise it will search for a wireless network. So you can plug in the cable and the manager will automatically select that connection (assumed it is the fastest one), and if you unplug the cable it will automatically search for a wireless connection.

It will also show you all available networks (provided they transmit their essid)

The NetworkManager has been implemented in Fedora and works like a charm!

Ooops, I mentioned Fedora, hopefully the paint on the wall will not curl up and fall down :-)

---

### Post by mlomker on 2005-10-06
[QUOTE=emperon]Ok i understood, but i am curious how windows handles this situation. [/QUOTE]

Does Windows actually boot faster?  Get out a stopwatch and time how long it takes to get all the way to the desktop.  The difference is that Windows just doesn't tell you what it's doing.

I do have a [write-up]("http://www.ubuntuforums.org/showpost.php?p=368604&postcount=4") on how to get ifplugd working well on Hoary.  It's mostly used by laptop users to ease switching between wireless and wired ethernet.

Knappen, I know that network manager has been packaged for Breezy but it isn't 100% and not officially supported, the last that I heard.  I know that people will be working on it, though.

---

### Post by knappen on 2005-10-06
Hi mlomker!

I think I read somewhere that it would be included and supported in Breezy, but hey, things change.

---

### Post by emperon on 2005-10-08
Hi mlomaker,

This post is slightly out of topic but i am so desperate and i will also ask you. I just wanna connect to internet through GPRS with my Bluetooth connected phone Nokia 6230.

So far i can pair the phone and my computer. So Bluetooth is working.
But no one seems knowing the next step. Theres a program called Easy GPRS connector for linux but it is somehow not working for me.

I am glad if you have any idea.

---

### Post by mlomker on 2005-10-08
> I am glad if you have any idea.

I'm afraid that I don't have any ideas.  I connectd a phone to Windows once and the performance was really bad...perhaps that'll change with EVDO in the near future.

You'll need some piece of software to make your bluetooth connection look like an ethernet interface.

---

### Post by knappen on 2005-10-08
I have done it under windows.

Have you installed the drivers for the modem?

---

### Post by emperon on 2005-10-10
Well, With same machine and phone i also have done that with windows. So technically there's no hardware missing for it. Windows is capable of doing that. But i am unaware if there's a driver for modem of Nokia 6230. If you know something about please inform me.

---

### Post by mlomker on 2005-10-10
> But i am unaware if there's a driver for modem of Nokia 6230. If you know something about please inform me.

I don't know if it's compatible with your phone, but have you read [this thread?]("http://www.ubuntuforums.org/showthread.php?t=34740")

---

### Post by emperon on 2005-10-10
[QUOTE=mlomker]I don't know if it's compatible with your phone, but have you read [this thread?]("http://www.ubuntuforums.org/showthread.php?t=34740")[/QUOTE]
Yeah i've read it and although not tried it i found it excellent. However, i saw nothing about GPRS and internet there. Its all about pairing and sending files stuff. Thus i am still stuck. Let me know if you figured it out more.

---

### Post by mlomker on 2005-10-10
> Thus i am still stuck. Let me know if you figured it out more.

Have you posted to that thread?  I suspect the readers on that thread know more than anyone.

---

### Post by emperon on 2005-10-10
[QUOTE=mlomker]Have you posted to that thread?  I suspect the readers on that thread know more than anyone.[/QUOTE]
Oh yeah, i will do so :)

---

