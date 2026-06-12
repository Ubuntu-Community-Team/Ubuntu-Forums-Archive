---
title: "Wireless interference?"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by mwacky on 2008-10-13
I'm having issues with my wireless network dropping connections and not being able to connect at times.  I've experienced this since I moved into a new apartment complex, the issue is with both my laptop and desktop regardless of windows or linux on either box.  I had this exact network setup at my last place without any problems at all.  Now my neighbor is saying he and his friend both with their wireless networks, none of us have problems being wired.  Are their any good tools out their for analyzing this problems?  Any suggestion other than the usual change channels etc.

---

### Post by iponeverything on 2008-10-13
> **mwacky said:**
> I'm having issues with my wireless network dropping connections and not being able to connect at times.  I've experienced this since I moved into a new apartment complex, the issue is with both my laptop and desktop regardless of windows or linux on either box.  I had this exact network setup at my last place without any problems at all.  Now my neighbor is saying he and his friend both with their wireless networks, none of us have problems being wired.  Are their any good tools out their for analyzing this problems?  Any suggestion other than the usual change channels etc.

It does sound like its an RF interference issue. Do the drops correspond, with someone using the microwave ;)

---

### Post by hyper_ch on 2008-10-14
can you run
```

iwconfig

```
and post the output here?

---

### Post by mwacky on 2008-10-14
Doesn't correspond with microwave or any other device that I can tell.  It starts working everytime I reset the factory defaults of my router, redo the settings.  Generally will work for a day or two, then unable to connect.


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Mickey"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:17:3F:55:E7:94   
          Bit Rate=9 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=90/100  Signal level=-14 dBm  Noise level=-70 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth2      no wireless extensions.

---

### Post by PMahoney on 2008-10-14
Although no expert in Linux...have you tried using your laptop elsewhere (i.e. university, cafe, friends, etc.)?  This might narrow it down to either your router or boxes.

Although unlikely in your case, I've recently experienced similar problems with my MadWifi HAL for my Atheros card...I haven't fixed it yet via a patch, but their appears to a bug with the attenuator in high noise environments.

Sorry, hope this helps some,
P

---

### Post by cariboo on 2008-10-14
I had a problem with my wireless connection dropping every time the cordless phone rang I replaced them SMC router I was using with a Linksys router and the problem was solved. The SMC is out in my garage working as an access point with no problems, as there is only a wired phone out there.

Jim

---

### Post by mwacky on 2008-10-15
Thanks for the replies, the problem is with both of my boxes regardless of whether I'm booted into Linux or Windows and they worked fine where I lived before.  The only new things since i moved is a new microwave, which I don't use very often and a new dvr/cable box, but I doubt that has anything to do with it.  No cordless phones.

Once in a while the Linux boxes will see two wireless networks hda1 and hda2, but these are never visible with windows...

---

### Post by hyper_ch on 2008-10-15
well, there's a "bug" that sets a lot of wifi card to transfer rate 1mb/s and I thought you'd have been a victim of it also. But yours set to 9m. You could still try to correct it and run at 54m

```

sudo iwconfig eth1 rate 54M && sudo /etc/init.d/networking restart

```

It's also strange that your wifi is called eth1

---

### Post by mwacky on 2008-10-15
> **hyper_ch said:**
> well, there's a "bug" that sets a lot of wifi card to transfer rate 1mb/s and I thought you'd have been a victim of it also. But yours set to 9m. You could still try to correct it and run at 54m

```

sudo iwconfig eth1 rate 54M && sudo /etc/init.d/networking restart

```

It's also strange that your wifi is called eth1

Thanks for this, I did actually have this bug with my desktop, but unfortunately it doesn't solve the problem.  

The thing that makes me think something weird is going on and it is not pure interference with a phone or microwave is that every time I reset the routers factory defaults it works fine for a day or two, then the problem comes back....

---

### Post by hyper_ch on 2008-10-16
if your desktop gets reset regurarly to 1 Mb/s then please report that here:
[https://bugs.launchpad.net/ubuntu/+bug/282053](https://bugs.launchpad.net/ubuntu/+bug/282053)

---

### Post by mwacky on 2008-10-17
Still having issues, almost convinced that someone or something is jamming our networks.  The key is that once I reset my defaults it works fine for a while and then starts the behavior.  Any Ideas?

---

### Post by mwacky on 2009-01-28
The cable company is going to rewire my building, I haven't had full wi-fi (on Windows, Linux, PS3, Ipod) in months...  Hope this solves it.

---

### Post by mwacky on 2009-04-07
That didn't work, when I moved out of that apartment I took the exact same network setup and now I have no issues.  I think that there were way too many wireless networks in that area and the channels were getting jammed....

---

