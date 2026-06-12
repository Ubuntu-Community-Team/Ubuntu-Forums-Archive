---
title: "NETGEAR Wireless PCI Adapter WPN311"
date: 2008-08-13
forum: Networking &amp; Wireless
---

### Post by Shadow-Sleeper on 2008-08-13
Hello All

I am in a bit of a jam, i installed Ubuntu Hardy Heron last week, or the week before. And my wireless was working 100%.

Then i decided to do updates, but i got impatient and stopped the updates in the middle of it. And switched of my pc.
When i logged in again my wireless icon, has a esclamtion mark, and is not working.

Now i have done some troubleshooting, and realized that some how
my driver has been deleted or gone?

Where can i find a driver? i really dont want to reinstall, because that means, i have to reinstall Apache and mysql, with my DB's etc..

Please help...

---

### Post by chili555 on 2008-08-13
I believe your card uses the Atheros 5212 chipset. The drivers are included in *linux-restricted-modules*. I suggest opening System -> Administration -> Synaptic and find the latest version of it and Mark for Reinstallation. Click Apply and let it hum. Does that bring your wireless to life?

You might also check System -> Administration -> Hardware Drivers and see if your Atheros is listed and enabled.

If none of these steps help, post back.

---

### Post by Shadow-Sleeper on 2008-08-13
Its on my home pc, so will try it as soon as i am there.
Do i need internet access for it? if so.. that might be a problem, seeing that i dont have connection without the wireless.

Thanks for your help! :)

---

### Post by chili555 on 2008-08-13
> Do i need internet access for it? if so.. that might be a problemIt will want internet connectivity. 

When you boot the computer, there is a GRUB countdown for three seconds. If you press 'Esc,' you will be presented with the GRUB menu. If you select an earlier kernel, not 'recovery mode,' you will probably be able to connect and then reinstall *linux-restricted-modules.* Just to be a little obssessive, I'd reinstall *linux-image* for the latest version that's installed, signified by a green box. 

When you reboot, it will boot into the latest kernel and see if your wireless works.

Post back if you get stuck.

---

### Post by Shadow-Sleeper on 2008-08-13
Well i saw that it needed internet connectivity. hehe.
So i then well played around.. and did as you just discribed! and Allas i am connected!

So to my suprise when i logged on here, you explained exactly what i did.
wow. anyhow. so i noticed i have 2kernels now... what do you recommmend i do now?

I just wanna say thank you for your help! i really do appreciate it. 
I want to stick with linux.

---

### Post by chili555 on 2008-08-13
> i am connected!Excellent!> so i noticed i have 2kernels now... what do you recommmend i do now?About two kernels? Nothing. A spare is like a safety belt. If you tinker with your system so much that it no longer runs, you can always boot into an earlier kernel and reinstall the later kernel, hopefully correcting your unwise tinkering. (If your tinkering is in /etc I hope and pray you will make backups: *sudo cp /etc/somefile /etc/somefile.bak*) Call me obssessive if you must, but I have *five* kernels on my system!> I want to stick with linux.Wonderful! I hope you will love it as much as I do,

---

### Post by Shadow-Sleeper on 2008-08-14
Again thank you very much for your help!!
I am gona ask a silly question, to well update / reinstall my kernel, should i just run the updates? or should i do it from the terminal or the synaptic package manager?

And when i do the update, will it remove my current working kernel?

I am surely doing a backup today, as you suggested, i really dont want to loose my data in /etc.. that could just be reallly bad. :)

---

### Post by chili555 on 2008-08-14
I have, perhaps, not been clear. If your system is running correctly, there is no need to reinstall your kernel. However, when a newer kernel is released by the developers, it will come to all of us by the normal update system. The little update icon will be glowing in your panel and when you click it, it will offer a number of updates. One will be *linux-image*, which is Ubuntu-speak for a newer kernel. After you accept and the updates run, you will be prompted to reboot to finalize the change. That's the change from 2.6.24-19 to 2.6.24-new. There is no need to do anything proactive to update your kernel; the system will spoon feed you.> And when i do the update, will it remove my current working kernel?No, it wants you to have that safety belt I referred you to, and I do, too. As to how many it will retain, I really don't know. I have five or so. You can always remove the really ancient ones in Synaptic, but I would keep a couple of safety belts on hand.

Also, I never meant to suggest you back up your entire /etc directory, although it's certainly an interesting idea. What I meant to suggest is that if you are reading some tutorial and it suggests you amend a file to do some magical, mystical thing; that it's smart to back up the file first so you can restore it in case it brings tragedy and not magic. To back up:```
sudo cp /etc/somefile /etc/somefile.bak
```To restore, simply reverse the process:```
sudo cp /etc/somefile.bak /etc/somefile
```This is especially helpful when the changes involve several steps that would be hard to reverse one step at a time.

One of the wonderful things about Linux and Ubuntu is that you can make your system uniquely yours.

---

### Post by Shadow-Sleeper on 2008-08-14
Great thank you!

---

