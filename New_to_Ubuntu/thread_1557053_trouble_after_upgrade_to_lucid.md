---
title: "trouble after upgrade to lucid"
date: 2010-08-20
forum: New to Ubuntu
---

### Post by KarenAK on 2010-08-20
After upgrading from karmic to lucid I have the following problems:

- system doesn't boot unless I press ESC several times which however doesn't show me the boot menu. I can log in and the desktop shows.

- screen resolution is all shot - monitor not recognized. (How is this possible when it worked ok in jaunty and karmic ??)


I did try this
[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)
but got stuck in the middle because it wouldn't accept 
xrandr --addmode VGA1 1024x768_60.00
saying that it cannot find output "VGA1"


Thanks in advance for any help :-)

---

### Post by mörgæs on 2010-08-20
Are you sure that 10.04 works well on your machine? That is, have you tried a live boot before installing?

---

### Post by KarenAK on 2010-08-20
no, I didn't....hm.... The laptop is 1 year old and like I said it worked just fine with jaunty and karmic...

---

### Post by mörgæs on 2010-08-20
Unfortunately you can not take for granted that new always means better. Best is to test first.

---

### Post by KarenAK on 2010-08-20
ok, but that doesn't really help me now, does it.

---

### Post by mörgæs on 2010-08-20
At least it should: If the live CD does not behave, best is to reinstall 9.10. If it works well, there is a point in solving your problem on 10.04.

---

### Post by KarenAK on 2010-08-20
I'm writing this using the Live-CD. It works ok.

I did the upgrade with the update manager. Now I installed the Live-CD and that is a total loss. No mouse and after initially loading the desktop and firefox everything goes haywire and I only see blinking pixels. Great.

Now, unless someone has a clever idea, I will repeat the installation, this time reformatting the partitions. And if that doesn't work, I'll go back to using Windows. I am really, really tired of this upgrade disaster they keep inflicting on unsuspecting users.

---

### Post by ezsit on 2010-08-20
Why go back to Windows? If Karmic worked well, just go back to Karmic. :-) Also, did you try 10.04.1? It is the latest release and fixed a whole mess of bugs with the initial release.

---

### Post by KarenAK on 2010-08-20
the update manager said that it did install the 10.04.1
The live CD is 10.04 - I hadn't thought of that..... *bangs head
Guess that is why it now doesn't work at all *sigh

So - does anybody have a clever idea how I can salvage this mess ? Please, anyone ?

---

### Post by Thomas Garman on 2010-08-20
I would boot in recovery mode and then do sudo aptitute update

---

### Post by KarenAK on 2010-08-20
that didn't work - after showing the desktop for a few seconds, it's all a jumble of pixels

---

### Post by mörgæs on 2010-08-20
10.04.1 is the same as 10.04.0, just with all updates applied to the installation files. Still it is best to have wired internet access during installation. 

If everything else goes wrong, staying with 9.10 is a good option. It is supported until april 2011, and then you will have 10.10 and 11.04 to choose from.

Don't hesitate to write again. There are a lot of people ready for helping.

---

### Post by KarenAK on 2010-08-20
my home folder is in a separate partition - so if I install again from the CD and format the boot partition it should work...... ? Maybe ?

I don't want to go back to 9.10 - I want lucid because it's LTS - because I will NOT make another upgrade any time soon

---

### Post by mörgæs on 2010-08-20
If you have a empty USB drive, the easiest is to copy all files from /home (including browser bookmarks) and then wipe the entire drive.

If you don't have one, you can also install without moving the /home files. You can for example boot with the live CD and delete the root partition, preserving /home. Then when you install, Ubuntu will notice the empty space and suggest to make a new partition here. 

If you do this, remember to delete all configuration files in your home folder. These are hidden files and/or folders having a name like .mozilla (with the dot in front).

---

### Post by theozzlives on 2010-08-20
> **mörgæs said:**
> If you have a empty USB drive, the easiest is to copy all files from /home (including browser bookmarks) and then wipe the entire drive.

If you don't have one, you can also install without moving the /home files. You can for example boot with the live CD and delete the root partition, preserving /home. Then when you install, Ubuntu will notice the empty space and suggest to make a new partition here. 

If you do this, remember to delete all configuration files in your home folder. These are hidden files and/or folders having a name like .mozilla (with the dot in front).

NO NEED to delete your conf files and directories!!! You'll lose ALL your settings. I install "fresh" everytime and leave my /home partition alone. Everything works fine.

---

### Post by mörgæs on 2010-08-20
I delete them every time just to be sure, since I might (unknowingly) have  made a mess in the configuration. Well, let's see what works for original poster.

---

### Post by ezsit on 2010-08-20
> I don't want to go back to 9.10 - I want lucid because it's LTS - because I will NOT make another upgrade any time soon

What is the problem with using 9.10 for as long as you want? Use it for two years, use it for three years, it should still work if your hardware does. 

If you are not running a server, most (if not all) security updates relate to server software, especially after a couple of years, so your "protection" is very, very, very, minimal. 

Best bet, put a hardware firewall/router between you and the net and you should be fine for years to come. I have friends running three to four year old installations and their computer are far safer than most, especially anything running Windows.

---

### Post by KarenAK on 2010-08-21
ok, the solution is:

when upgrading to lucid, DO NOT use the update manager

install from CD and make sure the system partition (or whatever the linux name for it is) is formatted.

install hardware drivers - e.g. nvidia

reactivate repos

reinstall software (configuration on home partition is recognized, so not much trouble there)



Thanks everybody for your support :D

---

### Post by mörgæs on 2010-08-21
> **ezsit said:**
> What is the problem with using 9.10 for as long as you want? Use it for two years, use it for three years, it should still work if your hardware does. 

If you are not running a server, most (if not all) security updates relate to server software, especially after a couple of years, so your "protection" is very, very, very, minimal. 

Best bet, put a hardware firewall/router between you and the net and you should be fine for years to come. I have friends running three to four year old installations and their computer are far safer than most, especially anything running Windows.

I have to disagree on this one. A hardware firewall is good, but it is not an excuse for not having an updated system. Use whichever of the four supported versions, but using an unsupported one is a security hole.

---

### Post by mörgæs on 2010-08-21
> **KarenAK said:**
> ok, the solution is:

when upgrading to lucid, DO NOT use the update manager

install from CD and make sure the system partition (or whatever the linux name for it is) is formatted.

install hardware drivers - e.g. nvidia

reactivate repos

reinstall software (configuration on home partition is recognized, so not much trouble there)



Thanks everybody for your support :D


You are welcome. It is a classical error: Updating from version to version gives problems, and a clean install solves them. You wouldn't believe how many times this happens in the fora.

---

### Post by KarenAK on 2010-08-21
But then I wonder why they do not remove the upgrade option from the update manager.....

---

### Post by mörgæs on 2010-08-21
I would also like it to be removed. In my experience it makes more trouble than benefit. 

Compare the number of posts saying A) 'I upgraded and now I have this error...' and B) 'I made a clean install (having wired internet access while installing) and now I have this error...'

---

### Post by philinux on 2010-08-21
[http://ubuntuforums.org/showthread.php?t=1539882](http://ubuntuforums.org/showthread.php?t=1539882)

[http://ubuntuforums.org/showthread.php?t=1555197](http://ubuntuforums.org/showthread.php?t=1555197)

---

### Post by ezsit on 2010-08-21
> **mörgæs said:**
> I have to disagree on this one. A hardware firewall is good, but it is not an excuse for not having an updated system. Use whichever of the four supported versions, but using an unsupported one is a security hole.

Unless you are running a server, with ports open, there is no more of a risk running an unsupported version than any other version. 

Running a desktop, where all ports are closed by default, and sitting behind a firewall, poses no security risks (no more than usual), no matter how old the system is. The behavior and intelligence of the user is always more of a risk than software.

If you are not using a piece of software, and your system is not accepting connections on any ports, than it does not matter in the least whether that piece of software is ever updated. After a couple of years, the only security updates that come down the line are for server software. Running an unsupported desktop is fine. The only reason most people believe that unsupported versions are riskier is because distro developers always promote the release cycle roller coaster.

---

### Post by mörgæs on 2010-08-22
The closed ports of course blocks attacks coming from the outside, but today most attacks come from the inside: The user is clickling on an infested PDF file or otherwise executing unwanted code on his machine. 

If the machine is not updated, clicking on this infested file can trigger the attack. On an updated machine this does not happen.

---

