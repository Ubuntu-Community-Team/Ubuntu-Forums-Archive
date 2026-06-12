---
title: "Can't reach max download speed on linux."
date: 2009-02-19
forum: New to Ubuntu
---

### Post by gidra on 2009-02-19
I'm using linux mint which is a very similar distro to ubuntu up to my knowledge. I ran some speed tests on the machine and managed to get a max of 478 KiloBytes per second on linux. Now my connection allows up to 512KBps, which i manage to achieve if i boot back to windows (dual booting that is not in a virtual environment). I don't reckon it has to do with my Realtek 8139 driver. Ipv6 seems to be disabled as well on my system. Don't know what else to tweak. Any suggestions welcome. Thanks

---

### Post by Mark Phelps on 2009-02-19
Actually, given that MS Windows and Linux use different network card drivers, it has A LOT to do with your drivers.  

As an alternative, do an "lspci", find out the chipset that your network interface uses, go to the manufacturer's website for that chipset, and see if they have a Linux-specific driver.  If they do, they usually have instructions about how to install their driver.

Apart from that, there's not much you can do about the network throughput performance.

---

### Post by superprash2003 on 2009-02-19
try downloading a file from the internet , that would give you a better idea!!

---

### Post by philinux on 2009-02-19
> **gidra said:**
> I'm using linux mint which is a very similar distro to ubuntu up to my knowledge. I ran some speed tests on the machine and managed to get a max of 478 KiloBytes per second on linux. Now my connection allows up to 512KBps, which i manage to achieve if i boot back to windows (dual booting that is not in a virtual environment). I don't reckon it has to do with my Realtek 8139 driver. Ipv6 seems to be disabled as well on my system. Don't know what else to tweak. Any suggestions welcome. Thanks

The difference between 478 and 512 would hardly be noticable. With some websites and downloads you may get even less. Some ubuntu updates come through my system at 200 kbs other times 600 or higher. I'm on an up to 8meg line too.

---

### Post by gidra on 2009-02-19
I went to Realtek website and it says linux driver is built-in the kernel, the current one i'm using right now i suppose. Downloading files from the internet gives me the same result as the test or less. :(

---

### Post by sydbat on 2009-02-19
You can try testing your bandwidth speed [here]("http://www.dslreports.com/tools"). I find that it is faster on Ubuntu than it ever was on XP.

---

### Post by Kareeser on 2009-02-19
Can you run two speed tests, one on Ubuntu, and one on Windows, just so we can verify your statement?

---

### Post by sydbat on 2009-02-19
> **Kareeser said:**
> Can you run two speed tests, one on Ubuntu, and one on Windows, just so we can verify your statement?Are you asking me? If so, I cannot run anything XP anymore, as I no longer have XP on any computer I own. However, before removing XP, I was getting about 700 - 800 Kb/s in XP and 1000+ in Ubuntu. I know it's not the fastest line, but it does the job.

---

### Post by gidra on 2009-02-19
> **sydbat said:**
> You can try testing your bandwidth speed [here]("http://www.dslreports.com/tools"). I find that it is faster on Ubuntu than it ever was on XP.

If you're asking me i already tried a couple of tests and a bunch of download managers each giving out the same result : Windows Speed > Linux Speed. Mentioning download managers nothing beats that damn Internet Download Manager in windoze. I download nearly from every server with max speed using IDM, download the same file with downthemall and it's about half that speed. But that's not exactly what i'm trying to tweak right now.

---

### Post by jerome1232 on 2009-02-19
> **gidra said:**
> I'm using linux mint which is a very similar distro to ubuntu up to my knowledge. I ran some speed tests on the machine and managed to get a max of 478 KiloBytes per second on linux. Now my connection allows up to 512KBps, which i manage to achieve if i boot back to windows (dual booting that is not in a virtual environment). I don't reckon it has to do with my Realtek 8139 driver. Ipv6 seems to be disabled as well on my system. Don't know what else to tweak. Any suggestions welcome. Thanks

Your talking about a difference of ~30KB's here, not very much of a difference ;) Most probably due to fluctuating Internet speeds or maybe the Linux driver for your network adapter just isn't as good as the Windows one.

---

### Post by LowSky on 2009-02-19
Serioiusly 30KB os like arguing about 30 cents of $100 it isn't that significant.
Many things can cause a slower speed to register. for one the way Windows and Linux estimate the actual connection speed, to how the website or server connect to your computer, and then the drivers and modems involved. I see if you were arguing over 1.5Mbps when you should be getting 5Mbps, but your agueing 30KBps on a 512KB connection is about a 5% difference. which would equate to an extra 3 minutes to a hour long download, whereas my 1.5 to 5MBps analogy would considerably worse with an extra 20 minutes added to a hour download.

---

### Post by gidra on 2009-02-19
Yep, honestly it doesn't make that much difference but still i was hoping to tweak into something and learn on my way. But i'll leave it if there are no solutions available, thanks for your input guys

---

### Post by traetron on 2009-07-28
well in my case it does make a big difference. On windows XP my maximum download speed reaches 5.9MB/s almost every time but on Ubuntu Intrepid Ibex it only reaches up to 1,54MB/s when downloading the same file from the same source. Is there a way to fix this ? This is really annoying because i'm loosing my 4.4MB/s while using Linux and i'm actually paying for that speed. Please tell me if there is a way to fix this.

---

### Post by XCan on 2009-07-29
You could try tweaking your settings in sysctl as described in [http://ubuntu-unleashed.com/tag/sysctl](http://ubuntu-unleashed.com/tag/sysctl) . On my home computer, it didn't help at all. But on my high-speed dedicated server, it made a world of difference transferring to a high-latency source.

---

### Post by Arup on 2009-07-29
Totally reverse situation here for me and my friends using both Windows and Linux, every Linux distro outdoes Win with ease, Win starts with same speed as Linux but within hours of doing heavy downloads, P2P, it slows down, thats the TCP stack in Windows, no such issues in Ubuntu where it keeps going full steam for the whole day.

---

