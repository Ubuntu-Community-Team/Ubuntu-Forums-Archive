---
title: "No internet after upgrade"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by Shrimply on 2009-01-24
Hi, sorry i really have no idea what I'm talking about so if you need any extra information you'll have to ask.

I just updated my ubuntu to 8.10, its a dual boot with XP but I'm hoping to make it my main operating system.

The problem is it now won't connect to the internet.  I had previously installed the correct software so that it could use my wireless card and it was working fine.

But now although it can find the the network and other computers on the network I can't actually seem to connect to the internet.  So the Windows network is visible in the network folder.

I also have previously shared an internet connection through a ethernet cable from my vista laptop but I'm getting pretty much the same result, local connection but no internet.

Thanks in advance for any help.

---

### Post by jemate18 on 2009-01-24
> **Shrimply said:**
> Hi, sorry i really have no idea what I'm talking about so if you need any extra information you'll have to ask.

I just updated my ubuntu to 8.10, its a dual boot with XP but I'm hoping to make it my main operating system.

The problem is it now won't connect to the internet.  I had previously installed the correct software so that it could use my wireless card and it was working fine.

But now although it can find the the network and other computers on the network I can't actually seem to connect to the internet.  So the Windows network is visible in the network folder.

I also have previously shared an internet connection through a ethernet cable from my vista laptop but I'm getting pretty much the same result, local connection but no internet.

Thanks in advance for any help.

Try to ping a website

Applications -> Accessories -> Terminal

type
```
ping www.google.com
```

If it responds then you should be able to connect to internet,

If not, maybe it is a DNS problem or something else....

Check your network settings.

---

### Post by Shrimply on 2009-01-24
Hi if I try to ping something I get unknown host,

Sorry but what should my network settings be, I've tried chaging varies things in varies places but its made very little difference.

---

### Post by jemate18 on 2009-01-24
> **Shrimply said:**
> Hi if I try to ping something I get unknown host,

Sorry but what should my network settings be, I've tried chaging varies things in varies places but its made very little difference.


OK.. so are you connected via wireless? do you use a router to connect to the internet? Or is it that you just plug the ethernet cable and then it automatically detects the settings and lets you go to the internet?

---

### Post by Shrimply on 2009-01-24
Hi, sorry your going to have to bare with me a bit.

Yes I am connected to wireless, I have no other access point where I am.

When I initially installed Ubuntu my wireless card didn't work, but I shared the internet connection from my vista laptop so that I could install "windows wireless drivers".  If I open this now my wireless card, mrv8000c, is still displayed but if I click on configure network I get "could not find a network configuration tool"

The strange thing is though it is no longer accepting the internet connection from my laptop either.

---

### Post by theozzlives on 2009-01-24
If Vista and Ubuntu won't connect it must be hardware or ISP. You have everything set to obtain a IP and DHCP automatically right?

---

### Post by Shrimply on 2009-01-24
Sorry if I din't make myself clear, the vista laptop is connected to the wireless but previously i'd been able to provide Ubuntu with an internet connection via ethernet cable from the vista laptop.

---

