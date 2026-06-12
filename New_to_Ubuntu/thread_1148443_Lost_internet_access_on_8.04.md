---
title: "Lost internet access on 8.04"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by namreg on 2009-05-04
Hi

I installed 8.04 on an old desktop to evaluate it. The desktop has no wireless card so I'm using a Belkin USB wireless adapter. Ubuntu recognised this and mousing over the wireless icon on the top panel shows the tooltip "*Wireless network connection to "Virgin Home" (100%)*"

However, I had no acess to the internet until I went into BIOS and changed the OS to "*Other*" from whatever Windows OS was previously entered (can't remember what it was now). This was recommended in a previous thread I posted. This seemed to fix the problem and I had access. This enabled me to set up my email and generally fart about!

However, last night, I lost access again. The only thing I had done to the system since gaining access was to change a few Appearance settings - nothing I would have thought that would affect internet access.

I ran the command **iwconfig **(found in a previous thread) and this returns:

[I]lo        no wireless extensions.

eth0    no wireless extensions.

eth1    IEEE 802.11b/g  ESSID:"Virgin Home"  Nickname:"zd1211"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1E:2A:0C:FC:84   
          Bit Rate=24 Mb/s   
          Link Quality=99/100  Signal level=43/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

[/I]Which suggests to me that the machine at least thinks it has a wireless connection. I've also tried the USB adapter on an old laptop without a wireless card, and it works fine.

I'd appreciate some help, as I don't know where to go from here. Please bear in mind that I **did** have access, so the machine is capable, but then lost it for no apparent reason.

Thanks in advance

---

### Post by ptn107 on 2009-05-04
I have the same adapter.  It should work with absolutely no configuration whatsoever, sometimes restarting helps.  It does require that linux-ubuntu-modules-#-generic be installed but it should already be.

---

### Post by namreg on 2009-05-04
Hi ptn

It was working fine then just gave up the ghost. I've rebooted several times since losing connection and it makes no difference unfortunately

---

### Post by namreg on 2009-05-04
Don't know if this helps, but I've just gone into **System>Administration>Network Tools **and on the **Devices **tab, **Network Device** selected **eth1. **There is an IP address shown, plus other information, but **Reception errors **is currently 442556 and rising by the second, which seems to suggest a problem. But I don't know where to look to solve it! :-(

---

### Post by namreg on 2009-05-04
bump

---

### Post by benj1 on 2009-05-04
just i thought,(im guessing not because you you don't seem to have installed your own drivers)
anyway, i just had a kernel upgrade which messed up my hso drivers, so i have to use an older kernel module, why don't you try booting up using your previous kernel, assuming it has just been upgraded?

---

### Post by namreg on 2009-05-04
Hi benj1

No, I haven't upgraded - this is my first installation of Ubuntu

---

### Post by namreg on 2009-05-04
Anyone think an upgrade from 8.04 to 8.10 will make any difference? Very frustrating this - a computer without internet is like a fish without...something a fish needs very badly! :)

---

### Post by benj1 on 2009-05-04
> **namreg said:**
> Hi benj1

No, I haven't upgraded - this is my first installation of Ubuntu

kernel upgrades come as normal updates, not just distro updates.

---

### Post by namreg on 2009-05-04
So how would I boot up using the previous kernel, assuming there is one?

---

### Post by namreg on 2009-05-04
I've just reinstalled the system, just in case there was something in the updates I downloaded that may have affected connectivity. I checked the BIOS to make sure the Installed OS still says "Other", which it does. The system can see my USB adapter, and is connected to my router, as it was before, but I still have no internet access.

As this installation was for evaluation purposes, I'd say it's probably served its purpose.

---

### Post by nothingspecial on 2009-05-04
Did you take previous advice and do ```


sudo apt-get install linux-backports-modules-jaunty-generic
```?

You have to reboot.

---

### Post by namreg on 2009-05-04
Hi nothingspecial

Haven't seen that suggestion yet. What exactly does that command do? Does the word "jaunty" in there assume installation of 9.04? If so, I have 8.04 installed

---

### Post by Scunnered on 2009-05-04
**namreg**

I was running 8.10 and it was hell to initially set up and every now and again it kept dropping off from **Virgin Media**.  What I had to do was to re-enter my password for the wireless security and when it refused to activate the connection and again asked for the password completely shut down the system. A restart will not do the job you must completely shut down and start over again.

Perhaps you have something similar with your connection.  It may be worth a try. Additionally for what it is worth Jaunty (9.04) worked immediately I downloaded it.  My wireless connection was immediately identified and has worked a treat since then.
This could also be something you can consider.  Only caveat with Jaunty as far as I am concerned is the problems with Inter graphics.

Hope this may be of assistance

---

### Post by namreg on 2009-05-04
Hi Scunnered

Thanks for that. I'm with Virgin as well - the only difference is my machine recognises my wireless and appears to be connected, until I open Firefox!

I'm actually in the process of downloading 9.04 now - must have read your mind!

---

### Post by nothingspecial on 2009-05-05
> **namreg said:**
> Hi nothingspecial

Haven't seen that suggestion yet. What exactly does that command do? Does the word "jaunty" in there assume installation of 9.04? If so, I have 8.04 installed

Hi, you`re quite right, my mistake.

The command installs a collection of packages including some drivers that don`t ship with a default Ubuntu installation. If you still have problems after installing jaunty try installing it. The original advice was earlier in the thread from ptn107.

> I have the same adapter. It should work with absolutely no configuration whatsoever, sometimes restarting helps. It does require that linux-ubuntu-modules-#-generic be installed but it should already be.

Hope everything works first time though.
_______

---

### Post by namreg on 2009-05-05
Ah. I wondered what linux-ubuntu-modules-#-generic meant?! :P
 
I downloaded 9.04 last night and will install it hopefully this evening - fingers crossed!

---

### Post by triunenature on 2009-05-05
> **namreg said:**
> So how would I boot up using the previous kernel, assuming there is one?

Restart your computer, there should be multiple versions in your Grub

Just use the one 3rd from the top (second from the top is safe mode)

---

### Post by Lemuel111 on 2009-05-05
I'm having the same problem connecting to the internet. I have looked at the BIOS settings & I can't find anywhere where it says which OS is in use, so as to change to 'other'. Any suggestions?

---

### Post by namreg on 2009-05-05
On mine I have a menu along the top. Second option is Advanced - it's in there and says "Installed O/S"

---

### Post by namreg on 2009-05-05
OK. This isn't going very well

I've installed 9.04, having understood that the wireless side of things is improving all the time, and it can't even SEE my USB wireless adapter, which at least 8.04 could, even if I had no internet access.

I've tried *linux-backports-modules-jaunty-generic* and I get: [I]

E: Couldn't find package linux-backports-modules-jaunty-generic

[/I]I didn't try booting from a previous kernel whilst I still had 8.04 installed, as suggested by triunenature, as I had re-installed 8.04 and hadn't downloaded any updates, for obvious reasons, so assumed that only one kernel was available to me.

Any suggestions guys? Getting a little desperate now.

Thanks

---

