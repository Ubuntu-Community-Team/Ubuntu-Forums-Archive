---
title: "Thinkpad R60 Wireless"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by linuxWombat on 2008-11-22
Hello,

My issue is that my newly installed xubuntu on my Thinkpad R60 can SEE wireless networks just fine, but I cannot connect to any of them.  I've tired both at my home and my friends home, I put in the WEP code correctly, it thinks for a while, and then it fails and prompts me for the code again. 

I've tried both 40/128 and 128.  The Wifi LED is not illuminated on my laptop, eventhough the wifi 'works' to identify hotspots.

What should I do?

Thanks!

---

### Post by linuxWombat on 2008-11-22
I know thinkpads have some issues with wireless, is this even possible??

I have to work on a group project for school which requires our group to set up a web application for a major networking company and I would like to be able to deploy it on my linux machine first before it touches their redhat server.  Thanks!

---

### Post by Olivier2371 on 2008-11-22
sorry to drop in, i have an acer laptop and i am using unbuntu8.04. 

My wireless led is always off under unbutu, whatever the version, but my wireless works prefectly.

I tried in the beginning to press the button of the wireless which lit but the connection didn't work.

I guess it might be because the wireless led is design to work with specific windows or for my case acer software.

---

### Post by linuxWombat on 2008-11-22
Yeah thats what I figured, it's just weird that I can see my home network, exchange packets with the router, and just am completely unable to connect with a correct WEP code

---

### Post by Olivier2371 on 2008-11-22
I am glad I could help. If your problem is resolved would you be kind enough to mark the thread as solved.

---

### Post by linuxWombat on 2008-11-22
I still can't connect to anything, eventhough it appears to be functioning.

I see this problem all over the internet and I see no working solution...

I've tried NDISWRAPPER and NDISGTK.

---

### Post by Olivier2371 on 2008-11-22
What chipset is your wireless adapter?

Are you sure that your router is set for WEP and not for WPA?

---

### Post by linuxWombat on 2008-11-22
Intel 3945 a/b/g

WEP - 128 - Open System

---

### Post by Olivier2371 on 2008-11-22
Hi,

I found this thread maybe it could help.
[http://ubuntuforums.org/showthread.php?t=477181](http://ubuntuforums.org/showthread.php?t=477181).

---

### Post by linuxWombat on 2008-11-22
Well, I tried that.  I made those changes to those three files, rebooted, and I was able to connect to my network for about 10 seconds, navigated to google.com at what had to be 5kb/s, then the connection was dropped and I havn't been able to connect since =(

---

### Post by linuxWombat on 2008-11-22
I made another change, any instance of a different interface I changed to wifi0 which is the interface for my wifi card (under ifconfig that matches based on MAC address)and the best I can do is connect for maybe 20 seconds before I am booted.

edit: It seems like there's no distro where everything works... this feels like windows 95.  Solaris network worked out of the box and video was like 3fps with no drivers available, debian I had no keyboard, forget about Arch, and now no network on *ubuntu...

I really appreciate any help though, I think If I can somehow get this working it will definately benefit our project's rollout

---

### Post by Olivier2371 on 2008-11-22
Ubuntu is based on debian!!

Don't despair I will look around for you, and try to find something that works.

I have forgotten to ask you which version of ubuntu you are using.

---

### Post by linuxWombat on 2008-11-22
The newest downloadable Xubuntu (Linux kernel 2.6.27, Xubuntu 8.10)

It ran like a dream, everything was sooo fast!!

edit: what's really bothering me is I already switched to Fedora, hoping maybe it would work, and the wireless worked flawlessly when I ran Fedora as a LIVE cd, but as soon as I installed it I am completely unable to connect to anything.

And I meant it 'felt like win95' cause it had that whole 'plug n play' but it was horrible because you basically spent hours looking for drivers which never ended up working anyway.

---

### Post by Olivier2371 on 2008-11-22
Have you tried your wireless adapter with ubuntu hardy 8.04?

---

### Post by linuxWombat on 2008-11-22
I think I'm going to try that.  I read a lot of posts how a more recent version of *ubuntu caused issues with my card.  I'm downloading 8.04.* now.

Thx so far =)

---

### Post by Olivier2371 on 2008-11-22
Just make sure before to enable any restricted drivers to do an update.

goto System->Administration->Software Sources.
I put some pictures to let you know what to change before updating.

[ATTACH]93774[/ATTACH]

[ATTACH]93775[/ATTACH]

[ATTACH]93776[/ATTACH]


Then the icon update manager should come up. if it doesn't,
System->Administration->Update Manager

then reload, update.

Restart you computer.

Check under
System->Administration->Hardware Drivers.
You should find your wireless adapter driver.

---

### Post by linuxWombat on 2008-11-23
Wireless still pinwheels and doesn't connect =(

I got fedora to work but the KDE environment is just hideous.  I guess I'll have to deal with that until the project is over =\

Thanks a lot for the help though!!

---

### Post by Olivier2371 on 2008-11-23
Try this link, it might help:

[http://linuxwireless.org/en/users/Drivers]("http://linuxwireless.org/en/users/Drivers")

---

