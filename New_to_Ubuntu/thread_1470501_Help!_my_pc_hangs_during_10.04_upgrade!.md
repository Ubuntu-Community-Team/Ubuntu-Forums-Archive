---
title: "Help! my pc hangs during 10.04 upgrade!"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by kramer65 on 2010-05-02
Hello,


Today I decided to upgrade to Ubuntu 10.04 so I fired up the update manager, updated everything there was to update, and then started the 10.04 upgrade. Since it takes a long time I left my pc, and I just came back to it.

But what happened? It now hangs! I see some screen about configuring the grub-pc. The button "next" is highlighted but nothing works anymore (no mouse or keyboard works). In the background I see that it takes 13 more minutes to upgrade, so it wasn't finished yet!

What should I do now? Hit reboot? Will the whole system be messed up then?

---

### Post by TheNerdAL on 2010-05-02
How long have you waited?

---

### Post by kramer65 on 2010-05-02
Well, i started the upgrade about 5 hours ago and after the files were downloaded, it said it would take about an hour. If that is so, it hangs for about 4 hours now..

---

### Post by TheNerdAL on 2010-05-02
> **kramer65 said:**
> Well, i started the upgrade about 5 hours ago and after the files were downloaded, it said it would take about an hour. If that is so, it hangs for about 4 hours now..

Hmm, I don't know then, sorry. :/

This might help: [https://help.ubuntu.com/7.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-troubleshooting.html)

---

### Post by kramer65 on 2010-05-02
> **TheNerdAL said:**
> Hmm, I don't know then, sorry. :/

This might help: [https://help.ubuntu.com/7.04/installation-guide/i386/boot-troubleshooting.html](https://help.ubuntu.com/7.04/installation-guide/i386/boot-troubleshooting.html)

That link doesn't work. Well it could be because I'm internetting on my phone now, but it simply says that the website doesn't exist...

No other ideas? No other option than rebooting?

---

### Post by GSF1200S on 2010-05-02
> **kramer65 said:**
> That link doesn't work. Well it could be because I'm internetting on my phone now, but it simply says that the website doesn't exist...

No other ideas? No other option than rebooting?

No mouse or keyboard works on the 9.10 install currently running? You should be able to select "Keep existing grub" and move on. If the computer isnt responding at all, try hitting this keyboard combination:

left ALT key + Sysrq (or print screen on some computers) + k

That should reset X in case it froze and the kernel is responding. DO NOT REBOOT at this point. You need to let APT get you up to date or it probably wont boot. After X comes back up, run the update manager again and see if it carries on (which it should). If that doesnt work, you can try updating APT from the command line:
```
sudo -i
apt-get update
apt-get dist-upgrade
```

If you dont get any response from anything and its just frozen, well then I guess you have no choice but to force shutdown. Try to use other Sysrq commands first- Check out some of them on this Wikipedia page:
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

If it doesnt boot when you try to reboot, then perhaps we can use a liveCD, chroot into the partition and fix it that way. Let me know..

---

### Post by TheNerdAL on 2010-05-02
> **kramer65 said:**
> That link doesn't work. Well it could be because I'm internetting on my phone now, but it simply says that the website doesn't exist...

No other ideas? No other option than rebooting?

Do you have a live CD?

---

### Post by kramer65 on 2010-05-03
Alright, so after trying all these SysRq options (tried Alt+SysRq+all the letters on the keyboard), I finally hit the reboot button, and indeed it doesn't start. I took two pictures of the screen which I hereby share with you. After this shows for about 10 minutes the screen goes blank, and that's the end..

So I just downloaded the new live cd from Ubuntu.com which I'm now burning on a cd. What should I do once I booted into the live environment?

---

### Post by Ed209 on 2010-05-03
Hi, I'm sure you've already tried this one, but have you checked your install disc for errors? I had problems with install discs unless I burned at x4 speed. Currently I'm running Ubuntu Studio 10.04 on a dual boot system alongside XP on a dell GX260. Installed with no problems, but having difficulties with the screensaver. when it kicks in, it locks up the system.:D

---

### Post by kramer65 on 2010-05-03
Hi Ed, I don't have a problem with the live CD. The problem was that I upgraded my 9.10 installation to the 10.04 when it all of a sudden hung in the middle of the process. Now my pc doesn't boot the installation anymore so I just downloaded the live cd so I hope I can still fix it. 

Does anybody have any idea of how I cn fix my half-upgraded 9.10/10.04 system?

---

### Post by GSF1200S on 2010-05-03
> **kramer65 said:**
> Hi Ed, I don't have a problem with the live CD. The problem was that I upgraded my 9.10 installation to the 10.04 when it all of a sudden hung in the middle of the process. Now my pc doesn't boot the installation anymore so I just downloaded the live cd so I hope I can still fix it. 

Does anybody have any idea of how I cn fix my half-upgraded 9.10/10.04 system?

Depends on whats broken really.. The best way to try and fix your install from a LiveCD is to chroot in.

So, lets say Ubuntu is installed on /dev/sda1, you would do:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
```
Then, you are logged in as root in your install. From here you can try to fix it with apt. For example:
```
dpkg-reconfigure apt
apt-get update
dpkg --configure -a
apt-get install -f
apt-get dist-upgrade
apt-get install ubuntu-desktop
update-initramfs -u
update-grub2

```
Then, exit the chroot (type exit and hit enter) and unmount:
```
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /dev/sda1
```
and reboot.

Be prepared though- 10.04 has had some issues with people booting, so the nightmare may not be over :(

---

### Post by kramer65 on 2010-05-03
Wow! Thanks for the enormous effort of helping me with this! I ran all your commands up till "dpkg --configure -a". I then got a prompt (or how do you call it), saying I need to configure grub. I clicked ok and I now have some options. 

I attached two screenshots of what I see. The second one also shows gparted, in which you see the partitions of my primary hard drive. The first one (sda1) is indeed where I installed the system. The second one (sda2) is my home folder. 

I think I need to select sda1 and hit ok. Am I right?

---

### Post by GSF1200S on 2010-05-03
> **kramer65 said:**
> Wow! Thanks for the enormous effort of helping me with this! I ran all your commands up till "dpkg --configure -a". I then got a prompt (or how do you call it), saying I need to configure grub. I clicked ok and I now have some options. 

I attached two screenshots of what I see. The second one also shows gparted, in which you see the partitions of my primary hard drive. The first one (sda1) is indeed where I installed the system. The second one (sda2) is my home folder. 

I think I need to select sda1 and hit ok. Am I right?

Are you dual booting with Windows by chance? Some people have had issues with not being able to boot windows after this prompt. Im really trying to get a definitive answer on this. 

I really hope im not wrong here, but I suggest /dev/sda, NOT /dev/sda1.

**EDIT** I installed 10.04 from scratch, so I didnt deal with this prompt. I install grub to /dev/sda (it depends on your partition scheme). If it doesnt work, we can fix it on the live cd.

---

### Post by klytu on 2010-05-03
> **kramer65 said:**
> Wow! Thanks for the enormous effort of helping me with this! I ran all your commands up till "dpkg --configure -a". I then got a prompt (or how do you call it), saying I need to configure grub. I clicked ok and I now have some options. 

I attached two screenshots of what I see. The second one also shows gparted, in which you see the partitions of my primary hard drive. The first one (sda1) is indeed where I installed the system. The second one (sda2) is my home folder. 

I think I need to select sda1 and hit ok. Am I right?

NO. You want /dev/sda ...

---

### Post by kramer65 on 2010-05-03
I&#7743; not dual booting windows so that won't be a problem. So if I select sda and it's wrong we can still fix it lateron..?

---

### Post by GSF1200S on 2010-05-03
> **kramer65 said:**
> I&#7743; not dual booting windows so that won't be a problem. So if I select sda and it's wrong we can still fix it lateron..?

Yes we can, but im confident that /dev/sda is right. I have grub installed to /dev/sdb (which is where all my OS' are installed), and I have no issues. The only reason I asked is due to some problems other people have had with Windows 7/Vista (unless im confused by their issues). Some of them cant get grub to detect Windows on the same hard drive as Ubuntu and the MBR, and yet others get a black screen and nothing happens when they select Windows from grub.

Anyways, /dev/sda should do it. Continue on and well see how it goes...

---

### Post by kramer65 on 2010-05-03
Alright thanks! I just did, and it did a lot of more stuff and it ended again. Do I now just continue with the commands you gave? So apt-get install -f, apt-get dist-upgrade.. etc..?

---

### Post by GSF1200S on 2010-05-03
> **kramer65 said:**
> Alright thanks! I just did, and it did a lot of more stuff and it ended again. Do I now just continue with the commands you gave? So apt-get install -f,
apt-get dist-upgrade.. etc..?
Correct.

---

### Post by kramer65 on 2010-05-03
Alright, so I proceeded with all the commands. It often said it didn't have anything to upgrade. And I finally concluded with the last part (I think closing everything). I then tried to close the terminal window to restart, but it says a process is still running. But I don't see anything running in that window. 

Attached is another screenshot..

[SIZE="1"]ps. I am so grateful that you guys are helping me with this![/SIZE]

---

### Post by GSF1200S on 2010-05-03
> **kramer65 said:**
> Alright, so I proceeded with all the commands. It often said it didn't have anything to upgrade. And I finally concluded with the last part (I think closing everything). I then tried to close the terminal window to restart, but it says a process is still running. But I don't see anything running in that window. 

Attached is another screenshot..

[SIZE="1"]ps. I am so grateful that you guys are helping me with this![/SIZE]

You can type 'exit' to leave chroot, then close the terminal ;)

Closing the terminal wont really hurt anything though...

---

### Post by kramer65 on 2010-05-03
GSF1200S, you are a hero! After some disc checking everything works again! You do not realise how grateful I am to you. Tonight I will go out here in Amsterdam and (although I'll have a hard time to pronounce it) I'll cheers to your name!

If there's anything I can make you happy with, just let me know!

---

### Post by GSF1200S on 2010-05-03
> **kramer65 said:**
> GSF1200S, you are a hero! After some disc checking everything works again! You do not realise how grateful I am to you. Tonight I will go out here in Amsterdam and (although I'll have a hard time to pronounce it) I'll cheers to your name!

If there's anything I can make you happy with, just let me know!

:D Glad it works for you man! No need to do anything for me- you just made my day :)

Enjoy!

---

