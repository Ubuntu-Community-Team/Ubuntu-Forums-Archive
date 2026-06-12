---
title: "Oops no USB in my WINE for my phone"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by mikee55 on 2010-10-25
Hi, Downloaded my phone's software manager, thinking me can run it in me WINE. It didn't work and gave a message
Failed FsUsbExService, No existing FsUsb Device 

Now eveytime I launch a Win.exe in WINE, I get this message after my App runs for several seconds,and it closes.

A search says 0 matches, Google gave nothing. Thats rare???

Mike:confused:

---

### Post by arochester on 2010-10-25
Phone? Make? Model?

---

### Post by mikee55 on 2010-10-25
Hi Samsung B2100 on O2 Network
[http://www.samsung.com/uk/consumer/mobile-phones/mobile-phones/bar/GT-B2100SRAXEU/index.idx?pagetype=prd_detail](http://www.samsung.com/uk/consumer/mobile-phones/mobile-phones/bar/GT-B2100SRAXEU/index.idx?pagetype=prd_detail)

And their software
[http://www.samsung.com/uk/consumer/mobile-phones/mobile-phones/bar/GT-B2100SRAXEU/index.idx?pagetype=prd_detail&tab=support](http://www.samsung.com/uk/consumer/mobile-phones/mobile-phones/bar/GT-B2100SRAXEU/index.idx?pagetype=prd_detail&tab=support)

PC Studio.

Thank you
Mike:)

---

### Post by anewguy on 2010-10-25
Maybe wine has changed since I last checked, but it never has supported USB devices.  I know devices such as keyboards, mice and I think at least some printers are supported, but access to "normal" USB access is not a part of wine.

Dave ;)

---

### Post by mikee55 on 2010-10-25
Ooops! What do I do?

Mike

---

### Post by HotShotDJ on 2010-10-25
Mikee55:

I know this doesn't help you now, but for future, here is what I do BEFORE modifying my Wine setup: copy my .wine to .wine~ (to create a backup).  Now, go ahead and install new software or make other changes.  If things fail miserable, just delete your current .wine directory and rename .wine~ to .wine to completely restore your known-working wine configuration and applications.

---

### Post by mikee55 on 2010-10-25
Hi Hot Shot DJ,

> copy my .wine to .wine~  

Can I not delete this and create a new one, I only have two Win32 progs installed, and I can re-install them.

Mike:)

---

### Post by anewguy on 2010-10-25
Still won't do you any good since wine doesn't support USB.  You won't get a USB device like that working in wine unless something has drastically changed.

Not sure what you want to do - perhaps there is a native ubuntu app that might work as well.

I would suggest closing this post since USB isn't happening in wine, and open a new thread asking for help on a native app to do what you want.  There are a lot of people out there with cell phones working with native ubuntu programs.

Dave ;)

---

### Post by mikee55 on 2010-10-25
No wait, don't close this post. I can't revert back to how Wine was before I installed this program. I tried to un-install it, but it won't un-install. I removed and re-installed Wine itself, in Synaptic. And still it remains.

Okay so USB don't go in Wine, But please, how do I repair Wine?:confused:

Thank you

Mike

---

### Post by anewguy on 2010-10-25
When you uninstalled wine with synaptic it removed the package, but doesn't remove the folder in your home folder that contains your wine drive image and config files.  The folder is hidden - ~/.wine  .  Remove wine with the package manager, then go in using "Places", change the view to show hidden files and folders, then delete the .wine folder.  You may need to delete the files first - it will give an error if you need to.  When that's done reinstall wine and you'll be back to a completely clean slate as if you just installed it (because that's what we did).

Dave ;)

---

### Post by mikee55 on 2010-10-26
At last, Thanks everyone. Its fixed.

Mike:)

---

### Post by anewguy on 2010-10-26
Your welcome.

Dave ;)

---

### Post by vene-ubu on 2010-11-09
Hey I just had this issue and worked it around differently:

I am using Ubuntu 9.04 too with Wine 1.0.1:

I got this error after I Installed Samsmung's New PC Studio. Which I downloaded from a non-official website. After next Wine application start the problem appeared.

It is being caused by the file "C:Windows\System32\FsUsbExService.ex" is being executed gives this error.

I read around that this may be a virus. I just tried reinstalling Wine and truly this software is not there on the original install. 

To solve it you can delete such file, or better what I did was edited the registry entry:
- HKEY_LOCAL_MACHINE/System/Services/Eventlog/FsUsbExservice/ImagePath, 
And cleared the entry.

(The registry editor in Wine can be opened browsing C drive on applications->Wine, Windows/regedit.exe.).

@mikee55:  Where did you get the phone software from?

---

