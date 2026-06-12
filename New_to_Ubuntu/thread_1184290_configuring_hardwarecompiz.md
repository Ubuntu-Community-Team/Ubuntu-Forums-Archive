---
title: "configuring hardware/compiz"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by omss on 2009-06-11
Hi,

I've just installed Ubuntu using the dual-boot option. However, I don't think my hardwares were configured by default. For example, under the Visual effects, I am not able to select neither the "Normal" nor the "Extra" settings. I believe it has something to do with my video card configuration. I installed Ubuntu on my Sony VAIO VGN-NR160E laptop which has Vista for the other boot option, and I know that Windows doesn't have anything to do with Ubuntu, but what do I do?

Also, I need help to configure my sound card. Whenever I plug my headphones in I can listen through them, but I noticed that the sound ALSO comes out my laptop's speakers. *Confused*

I installed Ubuntu Jaunty 9.04 and I am fairly new to this. I really wanted to test drive Beryl which I found is Compiz now and that it is a default program that gets installed with the newer Ubuntu versions. I installed the CompizConfig Settings Manager, and if I select an effect, I don't get any notification on whether the change in effect was made or not, which led me to think that something is up with my video card configuration. So any help regarding this matter will be highly appreciated. THANKS GUYS!!

-o

---

### Post by omss on 2009-06-11
any ideas yet? I am dumbfounded.

Also, how do I find out what my graphics driver/other hardwares are? just in case I need to find the latest driver and install it.

---

### Post by keplerspeed on 2009-06-11
Ok to get some visual effects, we need to install the 'accelerated' graphics driver.

So got to system>administration>hardware drivers. If a driver appears there for your graphics card, enable it, reboot and try to enable visual effects then.

If there is not drivers avaliable in 'hardware drivers', go to applications>accessories>terminal and enter this code into the terminal:
```

lspci | grep VGA

```

---

### Post by omss on 2009-06-11
So I just came home from work, and I checked under my Hardware Driver settings, and there were no available drivers. So I typed the command in the terminal, and it gave me the following:

omss@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
omss@ubuntu:~$ 

what do I do now?:???:

---

### Post by synapsys on 2009-06-11
It appears your graphics controller by default is blacklisted by Compiz. Here's the link for a fix.

[http://www.rudkin.me.uk/2009/04/22/how-to-get-your-intel-gm965gl960-working-with-compiz-on-ubuntu-jaunty-jackalope/](http://www.rudkin.me.uk/2009/04/22/how-to-get-your-intel-gm965gl960-working-with-compiz-on-ubuntu-jaunty-jackalope/)

Also....check this out for the sound issue.....

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

### Post by omss on 2009-06-11
i tried the command:

     root@ubuntu:~# ~/.config/compiz/compiz-manager

and this came up:

     bash: /home/omss/.config/compiz/compiz-manager: No such file or directory

apparently it cannot find my compiz manager configuration settings?

---

### Post by juanoleso on 2009-06-11
> **omss said:**
> i tried the command:

     root@ubuntu:~# ~/.config/compiz/compiz-manager

and this came up:

     bash: /home/omss/.config/compiz/compiz-manager: No such file or directory

apparently it cannot find my compiz manager configuration settings?

From that link you need to edit the file:
```

omss@ubuntu:~$mkdir ~/.config/compiz/
omss@ubuntu:~$echo -e 'SKIP_CHECKS=yes' > ~/.config/compiz/compiz-manager

```

will put "SKIP_CHECKS-yes" into that file.  Or just do it from the file browser.

let us know if it works.  ;-D

---

### Post by omss on 2009-06-11
Thank you to all you guys. I have both my video card, and sound card configured properly. This feeling of satisfaction is great.

However, I do have one more question. Since I have the dual-boot option, I figured I can access my Windows files from Ubuntu. But that is not the case, I researched on it and I am assuming it's got something to do with the way my drive was partitioned??

Since I installed Ubuntu inside Windows, and I only had one partition (where I installed Ubuntu by allocating a certain amount of free space). So is there any way to go AROUND reformatting my hard disk and partitioning it and then putting windows on one and Ubuntu on the other? Or, is there any way I can access my Windows files on Ubuntu? Eagerly waiting. . . 

and I can't thank you guys enough!!!! This place is great!

---

### Post by juanoleso on 2009-06-12
I haven't tried WUBI myself (which is installing ubuntu in windows), but from what I read you should be able to access your windows files no matter how Ubuntu is installed.

From here, [[COLOR="Blue"]https://wiki.ubuntu.com/WubiGuide[/COLOR]]("https://wiki.ubuntu.com/WubiGuide"):

> How do I access the Windows drives?

The Windows partition where you installed Wubi is available as /host within Ubuntu (places > computer > file system > host) All the other partitions will be available under places > removable media 

if ubuntu is installed on another partition (where you installed ubuntu while windows wasn't running), then it should be under the places folder and then just clicking the right drive it should auto mount it for access.

Hopefully very easy. :-)

---

