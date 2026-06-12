---
title: "Installing a US Robotics MAXg Wireless card"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by Redbelt on 2007-03-20
Hello guys
I installed ubunto just days ago. Always dreamt that I could migrate to Linux and felt that Ubuntu was good.
I install it, and it doesn't recognize my wireless card. Its US Robotics (USR) MaxG PCI model.
How do I go about introducing it to my system? I am a noob when it comes to anything Linux so I appreciate detailed steps. I am using Windows again because an OS with no connectivity nowadays is useless.
Help!

---

### Post by Redbelt on 2007-03-21
First they tell me ubuntu works...
Then they said great support.

Maybe I should go back to windows until I afford a mac.

---

### Post by Unhindered on 2007-03-23
I am having the same problem myself. If you search the forums, you may find, as I did, that with just a moment of checking, others are already discussing, resolving, and sharing solutions about your question. I searched for "US Robotics Wireless" your post was #1. #2 had solutions. [Here's a direct link to what I'm looking at: http://ubuntuforums.org/showthread.php?t=389162&highlight=us+robotics+wireless]("http://ubuntuforums.org/showthread.php?t=389162&highlight=us+robotics+wireless")

I'm with you in being frustrated and feeling lost, but you and I as noobs need to take a minute to see what solutions are already out there so we don't ask everyone to repeat what they've already typed before.

I'll be trying the solutions from the forum post I linked to this weekend. Will let you know.

---

### Post by ffxr on 2007-03-23
you have to find out what chipset is in the wireless card and then find a guide to install it, all the information you need is out there,, a bit of perseverance & poking around will get it installed...

---

### Post by ffxr on 2007-03-23
i had a look around for your card.. what model of MaxG is it?

---

### Post by Jouke74 on 2007-03-23
Try to go through these steps if you haven't already:

Check if the wireless card is supported by NDISWRAPPER on their website.

Then follow:

[http://www.ubuntuforums.org/showthread.php?t=391416&highlight=Asus+Wl-138g+wireless](http://www.ubuntuforums.org/showthread.php?t=391416&highlight=Asus+Wl-138g+wireless)

You need the 32 bits US robotics Windows drivers for Ubuntu 6.10 Edgy version i386, or the 64 Bits Windows drivers for the Ubuntu 6.10 AMD64 version. Forget it for Ubuntu 6.06 Dapper and DONT use the Asus drivers mentioned in this post. Instead replace the drivers in step 1 (SYS + INF) with the drivers from your US robotics wireless card which must be on a CD somewhere you got with the PCI card.

If it fails to work, check if Ubuntu did not add a driver for the US robotics card already. If so you need to remove (blacklist) this driver first.

---

### Post by Unhindered on 2007-03-24
Thanks for the info - I'm eager to try out Ubuntu, especially since installing it caused the default OS on my new comp (vista) to stop booting, even from the "system restore" dvds.

My US Robotics Wireless MaxG adapter model number is is USR5421

I'll be trying out the information linked to above and I'll report back.

---

### Post by tomiu on 2007-05-16
> **Unhindered said:**
> 
I'll be trying out the information linked to above and I'll report back.

Plss report back..did u find any solution???

---

### Post by Unhindered on 2007-05-16
Sorry, since this post I haven't used the wireless card on my Ubuntu PC. I will post back here if/when I have a chance to try this again. I ended up just moving my router next to my computer so I could connect with a cable because I had to be using the net and didn't have time to experiment at the time.

I did get Ubuntu working on my pre-loaded Vista, though.

---

### Post by parsellhouse on 2008-03-02
I followed the exact steps here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

With no problems. I checked the ndiswrapper list for my USR805411 802.11g MaxG PC Card and downloaded the windows installer and allowed it to extract to program files\us rebotics\ and put those files on my ubuntu machine. From there I used the ndiswrapper instructions to insert it and make lsmod and /etc/modules load on reboot. Wasn't much trouble at all. Remember to disable bcm43xx like the instructions tell you first.

---

