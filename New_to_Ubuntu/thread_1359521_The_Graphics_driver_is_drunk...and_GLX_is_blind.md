---
title: "The Graphics driver is drunk...and GLX is blind"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Glawar on 2009-12-19
Good evening Easterners, Good morning Westerners, and Good day to the rest of you!

_**Intro**_
I am a brand spanking new Ubuntu user who is very excited about Ubuntu, but also a bit disillusioned with what I'm able to do with it. I have a problem that has something to do with my graphics card, my driver, or some configuration issue.

_**My Background**_ - *So you know how to help me*
I'm a CS major who has finally decided to try out Ubuntu. I am familiar with computers (most CS majors are) and normally pick up things fast, but have only ever used Windows, except for a limited exposure to UNIX in one of my lab classes (by limited exposure, I mean I learned what the **ls** and **cd** commands do, and created a few text files). This means I know hardly anything about Ubuntu and am flying by the seat of my pants here. I am an eager, teachable, and capable learner, so don't water things down for me too much.

_**My System's Background**_ - *Anything that might be helpful in diagnosing the problem*
Two days ago, I purchased a new computer and partitioned its hard drive, and can now dual boot to either Windows 7 or Ubuntu...but I'm not sure exactly what mixture of Ubuntu versions I have. I originally installed--from a CD--Ubuntu version 8.10 Intrepid Ibex. One of the first things I did was upgrade to version 9.10 using the "Update Manager." I'm not 100% sure it was a success. A good bit of my interface changed, but I still have, for example, Pidgin as my default IM program.

_**The Problem**_ - *The Graphics driver is drunk and GLX is going blind*
Anyway, both before and after the ubuntu update, I've had a problem. I couldn't change my desktop effects. And whenever I went to "Hardware Drivers" and enabled my driver, I couldn't even get the green dot to appear. At two points in time, after trying a gazillion things, I all of a sudden realized my nvidia driver was enabled, and I could get my desktop effects to work. I moved on about my merry way, and, before I knew it, was back to the same problem. I'm sure you've all experienced this as well: I don't know what I did that made it work, and I don't know what I did that made it stop working.

Random note: my graphics card is a **NVIDIA GeForce 9300M GS**.

But this was merely a slight inconvenience for me--until I tried to install the game *BZFlag* from the "Add/Remove" program. It seems to have installed without problems, but when I double click on the icon, nothing happens. When I try to run BZFlag from the Terminal, I get this error message: "Could not set Video Mode: Couldn't find matching GLX visual." This could be a rather big difficulty, assuming other programs I install will likely have the same problem.

[U][B]What I've Tried
[/B][/U]I've looked all over the internet, and found many guides, as well as many forum posts by people with the same error I'm getting. I never found a solution that worked, although I suspect [this]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") page might be onto something: maybe I don't have the right version of linux-restricted-modules installed. I can't seem to find a good guide on how to fix that, and I don't really have much hope for it anyway.

Anyway, as I said, I'm eager, teachable, and a capable learner, so, if you have a few minutes to make a real difference in my life (making Ubuntu worth my effort), please don't hesitate to walk me through possible solutions.

---

### Post by Cheesemill on 2009-12-19
There have been alot of people having problems when upgrading to 9.10, I'd suggest doing a clean install to see if that helps, especially as you've jumped 2 versions from 8.10 to 9.10.

---

### Post by Glawar on 2009-12-19
I'll try it. Any other suggestions in the meantime?

---

### Post by 3rdalbum on 2009-12-19
I normally suggest sticking with the Nvidia driver from the Hardware Drivers program, but if you are having trouble with it then you should try installing them straight from [www.nvidia.com](www.nvidia.com).

Best to look at a HOWTO as the procedure is not 'new-user' friendly.

If you installed your driver from Nvidia's website and later installed a kernel update, then this may be why your driver is not working - it needs to be reinstalled after a kernel update. (but only if you installed the driver from nvidia.com - the one that Ubuntu provides will stay in sync with your kernel).

---

### Post by mikewhatever on 2009-12-19
Hi and welcome,

can you please provide the useful info.
What version of Ubuntu are you running?
What version of nvidia driver is installed?

If you don't know any of that, please open Applications-<Accessories->Terminal and post the output of the following commands:

cat /etc/lsb-release
dpkg -l | grep nvidia

Please, keep it simple this time. ;)

---

### Post by Mrandersonjr on 2009-12-19
Try to get envyNG and try to install the driver for your card.

---

### Post by Glawar on 2009-12-19
> **mikewhatever said:**
> Hi and welcome,

can you please provide the useful info.
What version of Ubuntu are you running?
What version of nvidia driver is installed?

If you don't know any of that, please open Applications-<Accessories->Terminal and post the output of the following commands:

cat /etc/lsb-release
dpkg -l | grep nvidia

Please, keep it simple this time. ;)

I've attached a screenshot of my output.

---

### Post by mikewhatever on 2009-12-19
Thank you. I am not quite certain what's the status of the nvidia-glx-180 package is, but that's the driver you should be using. Apparently, 'rc' means it's been removed, but is set for reinstallation. Can you run the following from Terminal and post the output:

```
sudo apt-get install nvidia-glx-180
```

---

### Post by Glawar on 2009-12-19
Here you go. Thanks for being willing to assist!

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nvidia-180-kernel-source
The following packages will be REMOVED:
  nvidia-173-kernel-source nvidia-glx-173
The following NEW packages will be installed:
  nvidia-180-kernel-source nvidia-glx-180
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/11.7MB of archives.
After this operation, 3265kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 129363 files and directories currently installed.)
Removing nvidia-glx-173 ...
Removing nvidia-173-kernel-source ...
Removing all DKMS Modules
Done.
Processing triggers for man-db ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package nvidia-180-kernel-source.
(Reading database ... 129282 files and directories currently installed.)
Unpacking nvidia-180-kernel-source (from .../nvidia-180-kernel-source_180.44-0ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-glx-180.
Unpacking nvidia-glx-180 (from .../nvidia-glx-180_180.44-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-180-kernel-source (180.44-0ubuntu1) ...
Removing all DKMS Modules
Done.
Adding Module to DKMS build system
driver version= 180.44
Doing initial module build
Installing initial module
Done.

Setting up nvidia-glx-180 (180.44-0ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

---

### Post by Roger Allott on 2009-12-19
> **Cheesemill said:**
> There have been alot of people having problems when upgrading to 9.10, I'd suggest doing a clean install to see if that helps, especially as you've jumped 2 versions from 8.10 to 9.10.

Definitely the best answer to the OP problem, although it might seem to be a bit of a cop-out.

If there's version of Ubuntu that is most suited to doing a completely fresh install, it's 9.10, because of the ext4 and grub2 aspects that don't get installed on an upgrade.

---

### Post by Zzl1xndd on 2009-12-19
> **Roger Allott said:**
> Definitely the best answer to the OP problem, although it might seem to be a bit of a cop-out.

If there's version of Ubuntu that is most suited to doing a completely fresh install, it's 9.10, because of the ext4 and grub2 aspects that don't get installed on an upgrade.

I would tend to agree there have been some major changes and starting Fresh is generally the best way to go.

---

### Post by mikewhatever on 2009-12-19
Glawar, the last output looks good, nvidia-glx-173 got removed and nvidia-glx-180 installed as expected, no errors. Try rebooting, fingers crossed.:P

---

### Post by Glawar on 2009-12-19
Rebooted. Still no luck. :( I've got the 9.10 cd downloaded and ready to go, should I fresh install?

---

### Post by mikewhatever on 2009-12-19
What are the symptoms now? No 3d effects and errors from the program you installed? How about the output of <glxinfo | head> without brackets.
Both 9.04 and 9.10 worked very well on my hardware, and if nothing works, reinstalling is always an option.

---

### Post by Glawar on 2009-12-19
Right, no 3d effects, and the error from trying to run some programs. I'm leaning towards reinstalling with a new 9.10. (My current version is upgraded from 8.10)

Running glxinfo | head gives the following:

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

---

### Post by mikewhatever on 2009-12-19
Yes, it looks like the driver is not working, not sure why.:confused: Does it appear activated in System->Admin->Hardware Drivers?

---

### Post by Glawar on 2009-12-19
Yep. It's been green before, even when it wouldn't work, and its green now, and still doesn't work. See the attachment.

---

### Post by Glawar on 2009-12-20
Well, I cleared the Ubuntu partition and fresh installed 9.10.
 
Now I'm on my Windows 7 partition (which works perfectly), because I can't even get a wireless connection on my Ubuntu side. In addition, the graphics on the Ubuntu side are blocky and jagged--even the default desktop background looks hideous.
 
Drivers again? But...how can I update my drivers...if I can't even get on the internet?
 
What does Ubuntu have against me? :(
 
(should I start a new thread now, since my problem has become much bigger than just graphics driver issues?)

---

### Post by mikewhatever on 2009-12-20
This thread or a new one, doesn't matter. It is a known issue with Karmic, that wireless works from the live cd, but needs re-enabling after the installation. We don't know anything about your wireless hardware yet, but pluggin a cable if, possible should, help. If not, the solution is to install the wireless driver from the installation cd.
Here is a good example [http://ubuntuforums.org/showpost.php?p=8090292&postcount=1](http://ubuntuforums.org/showpost.php?p=8090292&postcount=1).

You can find out what your wireless card is with <lspci | grep -i wireless>.

---

### Post by Glawar on 2009-12-20
Ok, I connected with a cord, and now have internet. On google, I have been unable to find a generic guide for how to check for and download drivers. Do you know of a good guide, or do you have any preferred method? (I checked out your link for the wireless driver installation, and will follow it, but that won't help me with my other driver problems)

I have attached a screenshot of what my loading page looks like, so you get an idea of what my graphics are like. Keep in mind that the graphics on my other partition are as good as they can get (and I've been able to run the programs there, so I know the problem is with Ubuntu, not with my computer).

After reinstalling Ubuntu, here are the symptoms I now know of:
1. No wireless connection
2. Terrible graphics.
3. When I go to System -> Admin -> Hardware Drivers, the window contains no drivers, and shows this message: "No proprietary drivers are in use on this system."
4. I still cannot enable Desktop Effects.
5. Now, I cannot even install the program that gave me the earlier message about GLX visuals. When I find it in the Software Center, it tell me: "Not available in the current data."

Finally, running that code in the terminal gives me:
```
0e:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
```

---

### Post by Glawar on 2009-12-20
I hate to double post, but this calls for a second post...

It's all working!

I followed the guide you posted to install the wireless card driver, and at the end it told me to restart. But just before I restarted, an Update Manger window popped open with 161 updates, among them some that looked very helpful. I decided not to update at that point, so that I'd be able to know exactly what helped.

So, I restarted without updating, and wireless worked. That means the guide you linked to was a success. At that point, I went to Update Manager and installed everything. Then I restarted again.

Then, I checked Admin -> Hardware Drivers, and found an NVIDIA accelerated graphics driver (version 185). I clicked enable, and, what do you know, I actually got a little loading window, and, at the end, it told me to restart. I restarted, and when the computer came up, the graphics were working swimmingly. I'm also gonna guess that the new wireless driver would've been included in the updates, if I hadn't already installed it. But hey, all's well that ends well.

In addition, I have installed and run the program that was giving me so much grief.

Thanks so much, mikewhatever! Without your assistance and encouragement, I'd have given up long ago.

---

### Post by mikewhatever on 2009-12-20
Wow, 161 updates, that's a lot. Glad it finally worked and you are welcome.

---

