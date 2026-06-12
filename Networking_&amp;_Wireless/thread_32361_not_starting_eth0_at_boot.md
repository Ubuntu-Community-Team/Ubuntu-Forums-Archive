---
title: "not starting eth0 at boot"
date: 2005-05-07
forum: Networking &amp; Wireless
---

### Post by Alexander Kirillov on 2005-05-07
Hi,
sorry for a question which is probably a FAQ, but I couldn't find an answer: 

How do I configure Ubuntu so that network interface (eth0) is not brought up at boot time? Most of the time my laptop is not plugged in, so it makes little sense to bring eth0 up at every boot. 

Reading docs (man interfaces, man ifup), it seems that Ubuntu is only supposed to start at boot  those intefaces that have "auto" in /etc/network/interfaces. I removed "auto" from eth0 interface in this file, yet Ubuntu tries to start eth0. Am I missing something?

I know I can press Ctrl-C when I reach this stage in boot process to skip it, but it leaves eth0 up, even though it is not actually connected to anything - hardly an optimal solution. And I hate to press Ctrl-C every time. Anyone has a better solution?

---

### Post by nad on 2005-05-07
Remove the 'networking' script from /etc/rcS.d and add it only to the runlevel of your choice.

---

### Post by defkewl on 2005-05-07
Open /etc/network/interfaces

Comment this line:
# iface eth0 auto

---

### Post by Alexander Kirillov on 2005-05-08
[QUOTE=defkewl]Open /etc/network/interfaces

Comment this line:
# iface eth0 auto[/QUOTE]
As I mentioned in my original post, I had already removed this line. 
[QUOTE=nad]
Remove the 'networking' script from /etc/rcS.d and add it only to the runlevel of your choice.
[/QUOTE]

Thanks! I tried it, but it still tries to activate eth0. It just does it in the background, after starting X and gdm, so I can login wihtout waiting for it to finish. However, if I switch to console 1, I see that it still trying to activate eth0 and waits for a long time before timing out. And when it does time out, it leaves eth0 active - even though there is no cable plugged into it. So it is not a perfect solution either. 

What I would want to do is somehow prevent it from even trying to activate eth0 at boot, before or after starting X...

---

### Post by nad on 2005-05-09
You could try disabling the hardware in the bios and/or add the driver module to your blacklist. I was trying to suggest a conditional solution that could be chosen at run time. If something is still trying to connect (think hal? gnome-desktop?) you may continue to experience this problem until you can figure out out to disable/deactivate eth0 in gnome through restarts. Play with 'Networking' gui.

---

### Post by dukeinlondon on 2005-05-09
Looks to me like a bug if an interface that's not listed in the 'auto' section is still brought up automatically.. 

I've commented out eth0 from the /etc/network/interface file.

---

### Post by elsewhere on 2005-05-09
FWIW, I had the same issue and it drove me nuts.  All I saw everywhere was to disable the eth0 auto.

I also had the following three lines in my initial interfaces file, couldn't figure out exactly why they were there, so I commented them out.

#mapping hotplug
#    script grep
#    map eth0

Now it bypasses eth0 and my boot time is absolutely smokin', it's literally a fraction of what it was.  I just ifup eth0 or wlan0 manually after login, depending on whether I'm at home or at work.  That's an extra step I don't like, but I'm still basking in the glow of my new "turbo" boot and can live with it for now.
 
Maybe worth a shot if you've got a similar config ?

Hope this helps...

Cheers,
KV

---

### Post by Alexander Kirillov on 2005-05-10
[QUOTE=elsewhere]FWIW, I had the same issue and it drove me nuts.  All I saw everywhere was to disable the eth0 auto.

I also had the following three lines in my initial interfaces file, couldn't figure out exactly why they were there, so I commented them out.

#mapping hotplug
#    script grep
#    map eth0

Now it bypasses eth0 and my boot time is absolutely smokin', it's literally a fraction of what it was.  I just ifup eth0 or wlan0 manually after login, depending on whether I'm at home or at work.  That's an extra step I don't like, but I'm still basking in the glow of my new "turbo" boot and can live with it for now.
 
Maybe worth a shot if you've got a similar config ?

Hope this helps...

Cheers,
KV[/QUOTE]
 Thanks for the tip - it did the trick!

AFAIK, these lines are supposed to bring up eth0 when a network cable is plugged in - which should be detected by hotplug system. Apparently, it does not work as expected. Seems like  a bug to me - I'll look in bugzilla and file it unless it is already reported.

---

### Post by elsewhere on 2005-05-10
Sweet !  I'm glad to hear it worked for you as well.  

There is an app called ifplugd, it's supposed to detect when a cable is plugged in and fire up the interface then, brings it down when it's unplugged.  It conflicts with the regular network config scripts so interfaces needs to be config'd to work alongside ifplugd (ie. interfaces shouldn't be activating a network port if ifplugd is trying to as well).

Having said all that, I haven't gotten around to really trying it yet myself, but it's on my list of things to do...  

Cheers !
KV

---

