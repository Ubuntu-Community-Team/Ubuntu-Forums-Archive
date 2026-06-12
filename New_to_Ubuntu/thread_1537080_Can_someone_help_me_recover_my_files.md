---
title: "Can someone help me recover my files?"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by Legendary_Bibo on 2010-07-23
Well I don't know why, but I started messing with Plymouth because I was sick of the low res boot screen, so I was following some guide word for word, and I think I know where I went wrong and that was because in the guide it told me to enter a resolution that I don't think my card supported. Basically when I turn on my computer it goes to a white line (like an old terminal) which is what it always did, but now it just goes completely black. When I put in a Kubuntu Live CD I could see the files on my hard drive, but I couldn't copy any of them over onto my external HDD. Can anyone help? Is there a way I can still recover from this?

---

### Post by jtarin on 2010-07-23
Do you get a Grub prompt? No? Boot with the Live DVD and open a terminal and sudo to root then chroot to the directory you want to copy files from. Now you should be able to move or copy your files. Are you dual booting? What Linux filesystem do you use...ext2,ext3? There is a [windows application]("http://www.diskinternals.com/linux-reader/") that will allow you to access your files. [More here]("http://www.linuxjournal.com/article/9449"). [This say this one]("http://sourceforge.net/projects/ext2fsd/") **_could_** work with Windows accesing a ext4 environment

---

### Post by nothingspecial on 2010-07-23
You need to fix your display.

What guide did you use?

Boot into root recovery console

Type ```
dpkg-reconfigure -phigh xserver-xorg 
```

then ```
shutdown -r now
```

---

### Post by mapes12 on 2010-07-23
I find it's always a good idea to have /home on its own partition. If your system breaks all you need to do is reinstall /(root) and you're up and running again. Select "Manual" at the partitioning section of the install to tell the installer where everything is. Do NOT format /home in this scenario.

If your /home isn't on its own partition and you want to move it then here's a good HowTo: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

Alternatively, boot from a live Cd. Go to Terminal and launch Nautilus with sudo permissions ```
gksudo nautilus
```and then move your data to where ever you want to move it.

---

### Post by Legendary_Bibo on 2010-07-23
> **jtarin said:**
> Do you get a Grub prompt? No? Boot with the Live DVD and open a terminal and sudo to root then chroot to the directory you want to copy files from. Now you should be able to move or copy your files. Are you dual booting? What Linux filesystem do you use...ext2,ext3? There is a [windows application]("http://www.diskinternals.com/linux-reader/") that will allow you to access your files. [More here]("http://www.linuxjournal.com/article/9449"). [This say this one]("http://sourceforge.net/projects/ext2fsd/") **_could_** work with Windows accesing a ext4 environment

Ah I'll try that. I actually don't even get a Grub menu, I get nothing, just a black screen. I can still go into Live CDs so I'll try doing that. I'll have to use my Kubuntu disc because I can't seem to find my Ubuntu one.

To answer your other questions.
No I'm not dual booting
I use ext4.

I will not mess with plymouth again...

---

### Post by Legendary_Bibo on 2010-07-23
> **nothingspecial said:**
> You need to fix your display.

What guide did you use?

Boot into root recovery console

Type ```
dpkg-reconfigure -phigh xserver-xorg 
```

then ```
shutdown -r now
```

I can't boot into anything :(
and my computer is being uncooperative and won't even let me access my BIOS where I think I can reach Grub from.

I wish there was a plymouth installation CD or something. This is so dumb, why is that when plymouth doesn't work, then the whole system doesn't?! Why can't it just skip plymouth if it's not working?!

---

### Post by Legendary_Bibo on 2010-07-23
> **jtarin said:**
> Do you get a Grub prompt? No? Boot with the Live DVD and open a terminal and sudo to root then chroot to the directory you want to copy files from. Now you should be able to move or copy your files. Are you dual booting? What Linux filesystem do you use...ext2,ext3? There is a [windows application]("http://www.diskinternals.com/linux-reader/") that will allow you to access your files. [More here]("http://www.linuxjournal.com/article/9449"). [This say this one]("http://sourceforge.net/projects/ext2fsd/") **_could_** work with Windows accesing a ext4 environment

Okay, you might have to walk me through this because I don't know what to do.

---

### Post by jtarin on 2010-07-23
And what part is not clear to you?
From your post above...it sounds as if you have a hardware problem if you can't get into the bios. What make and model of computer is this?

---

### Post by Legendary_Bibo on 2010-07-24
> **jtarin said:**
> And what part is not clear to you?
From your post above...it sounds as if you have a hardware problem if you can't get into the bios. What make and model of computer is this?

Oh I just figured I could get to grub from my BIOS, I guess not.

So I followed this [guide](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml), and I don't think the resolution the person was using is supported by my video card. I have an HP dv7 laptop. It works flawless with Ubuntu, except for the low res plymouth screen which I tried to fix, and failed.

---

### Post by Wim Sturkenboom on 2010-07-24
> **Legendary_Bibo said:**
> When I put in a Kubuntu Live CD I could see the files on my hard drive, but I couldn't copy any of them over onto my external HDD.Maybe you should indicate why backing up does not work. Don't you see the external HD? Do you get errors when copying? If so, post them as I don't have a crystal ball.

---

### Post by Legendary_Bibo on 2010-07-24
> **Wim Sturkenboom said:**
> Maybe you should indicate why backing up does not work. Don't you see the external HD? Do you get errors when copying? If so, post them as I don't have a crystal ball.

It says I don't have permission, and I can't change the permissions.

---

### Post by mapes12 on 2010-07-25
- Boot from the live CD. 
- Launch nautilus like I said in my last post with super user permissions. 
- You shouldn't need to have permission in this configuration. 
- Find the stuff you want to keep. 
- Copy it some place. 
- Reinstall the OS. 
- Copy back your stuff. -
- DONE!

---

### Post by k3lt01 on 2010-07-25
If your dual booting you should see GRUB. So reboot and select recovery mode for the latest kernel, then FailsafeX, and then select low graphics mode. If this works you should be able to get into a usable configuration in which you can change your resolution back to a "normal" setting.

---

### Post by Legendary_Bibo on 2010-07-25
> **mapes12 said:**
> - Boot from the live CD. 
- Launch nautilus like I said in my last post with super user permissions. 
- You shouldn't need to have permission in this configuration. 
- Find the stuff you want to keep. 
- Copy it some place. 
- Reinstall the OS. 
- Copy back your stuff. -
- DONE!

Yep, it worked! I tried doing that with Kubuntu but it wouldn't let me (sudo dolphin). So I burnt a new copy of Ubuntu and it let me. Ah, the only problem was that I ran out of memory on my external HDD, but I got everything I actually needed.

---

