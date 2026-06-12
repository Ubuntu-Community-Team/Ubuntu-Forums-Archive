---
title: "Fatal Error With Ndiswrapper"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by blackdahliamurder on 2006-07-23
So I installed Kubuntu this morning, and after a few Grub troubles and editing my device.map, I got it to boot. I installed ndiswrapper and dhcpcd so I could get my Linksys WMP54GS card to work. So I loaded the driver fine, but when I did:

```
sudo modprobe ndiswrapper
```

I got:

```
FATAL: Module ndiswrapper not found.
```

I tried a bunch of other things I found on the forums as well as on Google, but nothing seems to work. I know this card works under Linux because I had it working under Gentoo and Knoppix.

So either I'm mising some linux-headers, something isn't compiled into the kernel, or something else I'm not aware of.

Thanks!

---

### Post by Iandefor on 2006-07-23
You have ndiswrapper-utils installed?

---

### Post by blackdahliamurder on 2006-07-23
> **Iandefor said:**
> You have ndiswrapper-utils installed?

Yes, I'm pretty sure I do.

I'll have to check, but what do I have to do if it is installed?

---

### Post by Iandefor on 2006-07-23
> **blackdahliamurder said:**
> Yes, I'm pretty sure I do.

I'll have to check, but what do I have to do if it is installed? One of the difficult questions :). 

The next step from there would be to find the driver file that Windows would use. Do you know the name of the wireless chipset you're using?

If you happen to not know, you can use the command ```
lspci -v
``` and paste the output here.

---

### Post by blackdahliamurder on 2006-07-23
I should have specified this in my original post actually. I'm not new to linux and know how to set up my wireless card. My Windows driver is already installed with ndiswrapper and I have dhcpcd installed to fetch my IP. But modprobing ndiswrapper didn't work.

---

### Post by Iandefor on 2006-07-23
> **blackdahliamurder said:**
> I should have specified this in my original post actually. I'm not new to linux and know how to set up my wireless card. My Windows driver is already installed with ndiswrapper and I have dhcpcd installed to fetch my IP. But modprobing ndiswrapper didn't work. My bad :oops:. The majority of that stuff is actually in the first post... I just ignored it. Sorry.

Regarding modprobing ndiswrapper... um. I'll look into it, assuming you don't find the answer first.

---

### Post by blackdahliamurder on 2006-07-24
Iandefor:

No need to apologize, I wasen't clear in my original post. :)

But does anyone have any other ideas? I have a feeling something is missing because it works fine in Knoppix 4.0.2.

---

### Post by blackdahliamurder on 2006-07-25
Anyone?

---

### Post by Koziasty on 2006-07-25
Hmmm. What I would do is a fresh install of ubuntu (or, actually removing the whole ndiswrapper thing you have got so far), installing ndiswrapper-utils and not even trying to play with compiling. I used to think that I cant have ndiswrapper-utils working without compilation, but that's just not true. 

Hope this will work for you.

Regards, Koziasty

p.s. if it doesnt forgive me, im new to ubuntu :F

---

### Post by mrojas73 on 2006-07-25
I was having that same problem and the only thing that solved it was reinstalling Ubuntu and stating fresh.  Sticking with one HOWTO, there are so many outthere that sometimes all they do is confuse you.

---

### Post by blackdahliamurder on 2006-07-25
Thanks, I'll be trying that tonight. :)

---

### Post by blackdahliamurder on 2006-07-25
I have to get ndiswrapper-utils and ndisgtk. If I have the alternate CD, do I still have to download all the dependencies by hand? Because that's what screwed me up last time. I was missing a bunch of dependencies.

---

### Post by blackdahliamurder on 2006-07-26
> **blackdahliamurder said:**
> I have to get ndiswrapper-utils and ndisgtk. If I have the alternate CD, do I still have to download all the dependencies by hand? Because that's what screwed me up last time. I was missing a bunch of dependencies.

Anyone?

---

