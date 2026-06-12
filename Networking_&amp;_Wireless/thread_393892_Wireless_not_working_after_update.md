---
title: "Wireless not working after update"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by Larken on 2007-03-26
I just installed Ubuntu on my IBM T30 laptop last night.  After the install, I was amazed to see that everything, even wireless ethernet, was working great.  I was prompted to apply 128 updates to the system, which I did.  After the update, I no longer have wireless connectivity.  Has anyone else seen this behavior?

---

### Post by chili555 on 2007-03-26
Yessir. You probably got an updated kernel, or linux-image as it's called now, in the 128 updates. Sometimes a fix here makes a problem over there. That's why there is a team of people feverishly working on kernel development.

Open a terminal and do:```
lspci -v | grep -i Network
```and tell us what kind of wireless card you have. I'm pretty sure it's a quick, easy fix.

Prism? Aironet? Or...?

---

### Post by Larken on 2007-03-26
prism 2.5 wavelan chipset

---

### Post by chili555 on 2007-03-26
See if the new kernel inserted too many modules and they are fighting for domination of your computer instead of downloading mp3s and torrents, like they are supposed to. Let's open a terminal and issue a command:```
lsmod | grep prism
```If you see that prism2_whoever is loaded, we'll need to expel him from school for fighting. sudo gedit /etc//modprobe.d/blacklist to add:```
blacklist  prism2_<whatever>
```Use the module you found, something like prism2_pci or prism2_cs or otherwise. Leave off the .ko extension. Save and close gedit.

Reboot and post back.

---

### Post by cboebel on 2007-04-21
Chili555 -

Thank you for the most welcome information. I used the fix that you described above and it worked perfectly.

Being a new user, i now have to look back at the steps of your fix and learn about what I did. 

Thank you.

Chris

---

### Post by stinkpadnlinux on 2007-04-21
I actually have the same exact problem, with my T30 as well, with a WG511 netgear card. I tried to run the lspci -v | grep -i Network, and it did nothing at all, just went back to the prompt, so I just ran lspci -v and saw nothing about the card anywhere listed. Obvoiusly this is probably a big problem :)

any ideas?

---

### Post by shanerdaner on 2007-04-21
I had the same problem I have an HP N5495 (ancient) lol When I installed it the pc saw it right away after reboot the card is not working.  After I unplug it from the wall and pull out the battery then reboot using the sleep button the card works I think I need to get the driver to install in the boot up ...any ideas?  thanks!

---

### Post by shanerdaner on 2007-04-21
I am using a WG511T netgear card

---

### Post by nyy3321 on 2007-04-24
> **cboebel said:**
> Chili555 -

Thank you for the most welcome information. I used the fix that you described above and it worked perfectly.

Being a new user, i now have to look back at the steps of your fix and learn about what I did. 

Thank you.

Chris




I have a prism 2.5 wavelan chipset and this worked without a hitch... but i dont really get what i did. Can anyone explain why it worked?

---

### Post by chili555 on 2007-04-24
Often, three modules load, orinoco, hostap and prism2. Instead of downloading 128 updates, mp3's and torrents, they fight for world domination. If you expel prism2_xx from school for fighting, the other two sit down and get to work. The blacklist file simply means don't ever load this module, ever.

Other posts on the forum report success blacklisting prism2_xx *and* orinoco_xx, but in my experience, prism_xx is enough.

You must go through the lsmod process to determine if you need to blacklist prism2_usb or prism2_pci or otherwise.

---

### Post by chili555 on 2007-04-24
shanerdaner-
Your problem is really not related to prism2 cards. Please check here: [http://ubuntuforums.org/showthread.php?t=420627&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=420627&highlight=madwifi)

---

### Post by ponx on 2007-04-24
I had the same problem on my laptop at the weekend.  Wireless was flawless 'out of the box', but after many upgrades later, it wasn't working by the end of the day..!?

Mine is using the rt73usb driver, does anyone know of any conflicts with this one..?

(I'm suer there was a kernel ugrade, but the grub menu doesn't list any others other than the latest, so I can't revert back)

ponx.

---

### Post by npcomplete on 2007-04-25
> **chili555 said:**
> Often, three modules load, orinoco, hostap and prism2. Instead of downloading 128 updates, mp3's and torrents, they fight for world domination. If you expel prism2_xx from school for fighting, the other two sit down and get to work. The blacklist file simply means don't ever load this module, ever.

Other posts on the forum report success blacklisting prism2_xx *and* orinoco_xx, but in my experience, prism_xx is enough.

You must go through the lsmod process to determine if you need to blacklist prism2_usb or prism2_pci or otherwise.

Thank you very much!  I fixed the wireless problem on my laptop.

---

### Post by npcomplete on 2007-04-25
> **ponx said:**
> I had the same problem on my laptop at the weekend.  Wireless was flawless 'out of the box', but after many upgrades later, it wasn't working by the end of the day..!?

Mine is using the rt73usb driver, does anyone know of any conflicts with this one..?

(I'm suer there was a kernel ugrade, but the grub menu doesn't list any others other than the latest, so I can't revert back)

ponx.

Ponx, 
  A guy posted his solution in a Chinese forum. I am trying to make the points clear:
1. you need a driver from  [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz)
2. and you are refered to [http://www.linuxquestions.org/questions/showthread.php?t=539889](http://www.linuxquestions.org/questions/showthread.php?t=539889) , see what aquayol says.
3. you may also need to add rt73usb&#12289;rt2570&#12289;rt2x00lib to /etc/modprobe.d/blacklist 
just as chili555 pointed out.

---

### Post by ponx on 2007-04-25
Thanks for that ncomplete.

I have, however, already been down that route with feisty beta.  It's just that when I installed the final release of feisty everything worked ok.  But upgrading packages, etc, breaks it again..!?

Was just looking to see if anyone knew how to 'gracefully' repair it again (so I don't have to do the serialmonkey thing again)...

If not then I guess I have no choice...

ponx.

P.S.  I hope it gets fixed properly soon, I quite like the roaming feature of network manager.

---

