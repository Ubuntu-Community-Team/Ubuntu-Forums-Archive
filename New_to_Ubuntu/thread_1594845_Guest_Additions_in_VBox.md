---
title: "Guest Additions in VBox"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by vyasr on 2010-10-12
Hi,
I'm virtualizing Lucid Lynx (Ubuntu 10.04 I believe) with VirtualBox 3.2.0 and I'm trying to get the Guest Additions to work. The procedure I followed was:
1. Clicked on Install Guest Additions in the Devices Menu
2. Updated the system and installed dkms using the terminal commands as in the user guide
3. Restarted the virtual machine
4. Changed to the directory where it was using the cd command
5. Typed sudo sh ./VBoxLinuxAdditions-x86.run, executing the command as a superuser
6. Restarted again after installation completed

I should note that when I first installed the OS itself, mouse pointer integration was enabled without manually installing it, so I thought that maybe the Guest Additions were pre-installed. However, I'm still unable to access seamless and full-screen mode. I can access shared folders if I follow the instructions here.

[http://ozz314.wordpress.com/2008/05/08/virtualbox-shared-folders-between-ubuntu-guest-and-mac-host/](http://ozz314.wordpress.com/2008/05/08/virtualbox-shared-folders-between-ubuntu-guest-and-mac-host/)

Do I just need to manually change the resolution, or is there another way to get seamless and full-screen to work?

---

### Post by bodhi.zazen on 2010-10-12
You need to manually change the resolution.

What do you mean exactly by "seamless" ?

And what version of Virtualbox are you using ? A new version was released yesterday.

---

### Post by vyasr on 2010-10-12
I haven't updated to the newest version of VirtualBox yet, but I don't think that would be the problem because this functionality has been around for multiple major releases. I'm just one minor update away, and I will probably do that soon.
By seamless mode I'm referring to the capability to run applications directly over the host GUI so that Ubuntu programs appear as windows on the host desktop without the guest desktop at all. I don't particularly need this feature, I'm more interested in being able to access full-screen, but I thought that might help diagnose the problem.

---

### Post by Vaphell on 2010-10-12
does your guest system resize its desktop when you stretch its window?

---

### Post by QIII on 2010-10-12
I find seamless mode to be more confusing than helpful.

Do you have it set to change screen size when the vm is maximized or minimized?

What have you done to attempt to change your screen resolution?

---

### Post by mikodo on 2010-10-12
I was installing different distros yesterday from a Vbox Puel version I downloaded the day before yesterday virtualBox-3.2. I didn't know that a new version was coming out yesterday.. LOL!   When installing the vm's with some distros, the fullscreen mode would work with the guest additions. As examples, for me Ubuntu 10.10 would install as a vm and show the whole desktop with seamlessness with the desktops. Then again, with Debian Squeeze, I couldn't get the guest additions to work, and I couldn't enlarge the desktop and there was no seamlessness of desktops. Both of the examples were with Ubuntu 10.04 as the Host OS. So mileage seemed to be varied dependent upon the distros I was putting in as vm's.     Maybe we should try that new release that bodhi.zazen spoke of!

---

### Post by mikodo on 2010-10-12
Oh yes, another quirk was that I couldn't get SimplyMepis to install at all as a vm, and Windows 7, played as nice as pie. So, really it seemed dependent on the OS being put in as a vm. Strange...

---

### Post by scrooge_74 on 2010-10-12
I find it better to start vms from command line giving the option vrdp, then I use Remmina to what ever port I assign to that vm.

Specially useful when working over the network

---

### Post by vyasr on 2010-10-12
@Vaphell: No, the screen doesn't resize when I stretch the window, there is just blank space in between the actual window edges and the screen.

@QIII: I haven't tried to manually change the resolution at all yet, I'm not too comfortable with CL controls and I wasn't sure if that was necessary. The screen size is currently not set to change with maximizing or minimizing as far as I know, how would I go about changing that?

I probably wasn't too clear about what is and isn't enabled. When I enter the VirtualBox Machine window when the VM is running, the Enter Fullscreen and the Adjust Window Size commands are usable, while the Seamless mode is grayed out. The Disable Guest Display Auto-Resize is grayed out, but it also has a check mark next to it, so it appears to be permanently activated. Maybe that is the problem?

---

### Post by vyasr on 2010-10-12
When I looked this up online, most people with similar issues said that there was ultimately something wrong with the XOrg, but that only seems to pertain to older distributions and versions.

[http://forum.virtualbox.org/viewtopic.php?f=3&t=15679](http://forum.virtualbox.org/viewtopic.php?f=3&t=15679)

Maybe updating from 10.04 to 10.10 would help?

---

### Post by QIII on 2010-10-12
> **vyasr said:**
> 
I probably wasn't too clear about what is and isn't enabled. When I enter the VirtualBox Machine window when the VM is running, the Enter Fullscreen and the Adjust Window Size commands are usable, while the Seamless mode is grayed out. The Disable Guest Display Auto-Resize is grayed out, but it also has a check mark next to it, so it appears to be permanently activated. Maybe that is the problem?

Sounds like you didn't actually get the Guest Additions applied.

I'll be on the back side of the moon for a couple of hours.  If I can, I'll get back to you.

---

### Post by scrooge_74 on 2010-10-12
+1 Guess Additions seems not to be working or properly installed

---

### Post by CharlesA on 2010-10-12
Note: There was an update to VirtualBox this morning/afternoon (for Linux at least). When I installed Maverick on it, it loaded fine with the guest additions.

---

### Post by Quackers on 2010-10-12
> **CharlesA said:**
> Note: There was an update to VirtualBox this morning/afternoon (for Linux at least). When I installed Maverick on it it loaded fine with the guest additions.

Me too, version 3.2.10
Very, very nice :-)

---

### Post by mikodo on 2010-10-12
> **vyasr said:**
> When I looked this up online, most people with similar issues said that there was ultimately something wrong with the XOrg, but that only seems to pertain to older distributions and versions.

[http://forum.virtualbox.org/viewtopic.php?f=3&t=15679](http://forum.virtualbox.org/viewtopic.php?f=3&t=15679)

Maybe updating from 10.04 to 10.10 would help?

Nice Find!  I am guessing the problem lies with the guest vm's and not the Host.My host Ubuntu Lucid, would have no problems with newer distro vm's, with the exception of SimplyMepis, which I think is based on Debian Lenny or Squeeze anyways,not the newest releases. Where as an example,the guest additions with the Ubuntu Maverick vm worked just fine!  Mike

---

### Post by CharlesA on 2010-10-12
> **Quackers said:**
> Me too, version 3.2.10
Very, very nice :-)

Yep. That's the same version I am using.

The OSE version is still at 3.1.6 tho.

EDIT: The older version worked fine for Lucid, for me as well.

---

### Post by mikodo on 2010-10-12
I just checked, and I was using yesterday, the newest version, VirtualBox 3.2.10.  Either it came out 2 days ago, or the PPA sent me an update.

---

### Post by vyasr on 2010-10-12
OK I'll try updating both VirtualBox and Ubuntu and see if that helps.

---

### Post by vyasr on 2010-10-13
OK it works fine now. I'm guessing the Lucid Lynx OS hasn't been properly adapted yet, because I didn't need to download the newest VirtualBox update. Afterwards, though, I did download the new VirtualBox, and it was fine both ways, so that update was probably just a bug fix more than anything.
Thanks to everyone who helped!

---

### Post by omegadestroy on 2011-09-10
need help. how do you install guest additions the way you guys did it? i'm getting this "starting the virtual box guest additions ...fail"

auto resize still grayed out.

---

### Post by Perfect Storm on 2011-09-11
This is an old thread. Please find a newer one or create your own thread, thanks.


Thread closed.

---

