---
title: "[SOLVED] No USB in Virtualbox"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-12-06
Hello Everybody,

I installed the personal edition of Virtualbox (2.0.6) and I can't get it to recognise USB sticks. I have already installed the guest additions, but it made no difference. I'm running 8.10. Can anybody help, please?

Thanks,

Charlie

---

### Post by lovelyvik293 on 2008-12-06
In virtual box setting u have to enable the USB and USB 2.0

---

### Post by HotShotDJ on 2008-12-06
In VirtualBox, before you start the guest OS, select the guest OS, then click on Settings in the tool bar.  In the left panel, click on USB.  Make sure "Enable USB Controller" and "Enable USB 2.0 (EHCI) Controller" are selected. Click "OK" and then start your guest OS.

---

### Post by Charlie Chick on 2008-12-06
Done all of that. Clicking on the USB in Settings gives the following error message: 

Failed to access the USB subsystem.  
Could not load the Host USB Proxy Service (VERR_FILE_NOT_FOUND). The service might be not installed on the host computer.


Result Code: 
NS_ERROR_FAILURE (0x00004005)
Component: 
Host
Interface: 
IHost {489fb370-c227-4d43-9761-ceb28484fd9f}
Callee: 
IMachine {1e509de4-d96c-4f44-8b94-860194f710ac}

---

### Post by luckydeveloper on 2008-12-06
also,

install the guest additions for the guest OS. this would make things easier in a virtual machine

---

### Post by HotShotDJ on 2008-12-06
> **Charlie Chick said:**
> Done all of that. Clicking on the USB in Settings gives the following error messageMy bad.  I left out a VERY important part... 
[LIST=1]
[*]Go to System -> Administration -> Users & Groups
[*]Unlock  "Users Settings" using the "Unlock" button near the lower right of the box (next to the close button)
[*]Click on "Manage Groups"
[*]Click on "+ Add Group"
[*]In the "Group Name" text box, type "usbuser"
[*]IMPORTANT:  Write down the Group ID number on a piece of paper... you'll need this later!
[*]Click on your user name in the "Group Members" table -- a check mark will appear in front of the user name.  Do this for each user you wish to allow USB access in VirtualBox
[*]Click OK, and then Close, then Close again.
[*]Now, open Applications -> Accessories -> Terminal
[*]Type "gksudo gedit /etc/fstab" (without the quotes)
[*]Add following lines to the end of the file:```
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=1001,devmode=664	0	0
```
[*]IMPORTANT: Replace 1001 with the Group ID number that you wrote down earlier.
[*]Save the edited file (File -> Save) and then exit gedit.
[*]Reboot your system
[*]Make sure you've enabled USB Controller in VirtualBox
[*]Enjoy USB goodness in VirtualBox
[/LIST]

---

### Post by Charlie Chick on 2008-12-06
I've just tried this and it looked like it was going to work. Windoze said "USB stick found" and then said that "your hardware may not work properly". I checked in My Computer and, indeed, the device was not showing. I then re-booted, but same thing.

You instructions were very clear apart from one thing which may have a bearing on this. When I added the 'usbuser' group you said to write the group number down which I did. It was 1001. In instrutction 12 you said to replace 1001 with the group ID number which I had written down earlier, but the two numbers were the same! Did I miss something?

---

### Post by HotShotDJ on 2008-12-06
> **Charlie Chick said:**
> You instructions were very clear apart from one thing which may have a bearing on this. When I added the 'usbuser' group you said to write the group number down which I did. It was 1001. In instrutction 12 you said to replace 1001 with the group ID number which I had written down earlier, but the two numbers were the same! Did I miss something?No, you didn't miss anything.  On a default system (that is, no groups added), then the group ID number that will be assigned to your new usbuser group will be 1001.  But not everybody has a default configuration, so I wanted to cover that possibility.

As far as the error you are getting from Windows, I really don't know what that problem is.  But lets try something (it might not work, but its worth checking out)... Open VirtualBox, but don't start Windows.  Now, plug in your USB drive.  Go to the USB settings.  You'll see a rather large box under "USB Device Filters."  Right click in that large box, and then click on "Add Filter from Device" and then select your USB stick.  Now, click OK.

From you LINUX desktop, right click on the USB stick icon and click Unmount Volume, and then remove the USB stick.

Start a virtual windows session.  When boot up is completed, insert the USB stick.  Let me know if that helps.

(OH... almost forgot, is your USB stick formated using FAT16 or FAT32 ... this is how most are shipped and is what you want.  But sometimes people reformat them using EXT2, which makes them incompatible with Windows unless you install an EXT2 driver in Windows.)

---

### Post by C. Wizard on 2008-12-06
Sorry, by saying you installed the "personal" verson do you mean you installed the PUEL version or the OSE version?

---

### Post by Charlie Chick on 2008-12-06
Thanks again for your help. I follwed your instructions to the letter, but got the same result. The one difference is that Virtualbox now reports that there is an active USB device. For some reason, it begins to show in Windoze and then fails to carry through. The stick is in FAT16.

I'm using the PUEL version.

Many thanks for your help.

---

### Post by Charlie Chick on 2008-12-06
Hotshotdj wrote:  As far as the error you are getting from Windows, I really don't know what that problem is. But lets try something (it might not work, but its worth checking out)... Open VirtualBox, but don't start Windows. Now, plug in your USB drive. Go to the USB settings. You'll see a rather large box under "USB Device Filters." Right click in that large box, and then click on "Add Filter from Device" and then select your USB stick. Now, click OK.

From you LINUX desktop, right click on the USB stick icon and click Unmount Volume, and then remove the USB stick.

Start a virtual windows session. When boot up is completed, insert the USB stick. Let me know if that helps.

I tried that again and found that, as long as I didn't remove the device in Ubuntu, Windoze recognised it. So, problem solved!

Many thanks for all your help.

Charlie

---

### Post by Xizz on 2008-12-08
HotShotDJ,

Thanks for the post!

I'm using 8.10 Intrepid Ibex, Sun xVM 2.0.6

All USB devices are now discoverable. All is working well.

I appreciate the fact that you took the time to share the knowledge with your post.

Users like you who contribute your skills and time are what keeps this forum going.
 
Good work!

---

