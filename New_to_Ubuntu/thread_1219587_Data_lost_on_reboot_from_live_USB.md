---
title: "Data lost on reboot from live USB"
date: 2009-07-21
forum: New to Ubuntu
---

### Post by KakDela on 2009-07-21
I am using a live USB to boot ubuntu, and each time I reboot, all (or it seems like all) settings are reset and data is erased: firefox history, game scores, which driver is active, etc...

any ideas? I am new to linux (only started yesterday), so keep that in mind in your answer.

Thanks in advance.

---

### Post by LookTJ on 2009-07-21
a live USB is like a live CD, meaning it only boots to RAM. 

RAM is temporary storage unlike a HDD, which is read/write.

---

### Post by HotShotDJ on 2009-07-21
Because it is a CD distribution. Every time your reboot a live cd, it is exactly like doing a destructive reinstallation.  Live CD's are for the purpose of testing/experiencing Linux before committing yourself to a full install.  To get a fully functioning system, including retaining settings across boots, you'll need to install Ubuntu.

There are many options available... you can install it on top of your current system (effectively removing your current OS), you can dual-boot, you can create a USB drive with Ubuntu on it and run it from that.  Start with this handy Installation Guide: [https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)

---

### Post by KakDela on 2009-07-21
Hmm... I was under the impression that for live USBs, as oppose to live CDs, settings (at least system settings) were stored to the flash drive... I could have sworn that I read somewhere that when there were only live CDs, people would carry CDs to boot from and flash drives to load settings and files off of, but with the introduction of live USBs, everything could be stored on one flash drive.

I thought that the whole point of a live USB was that the operating system could be booted on any computer; if all data is erased, that would destroy the point, wouldn't it?

I'm not quite ready yet to fully install ubuntu.

I also tried to open the flash drive from which I'm booting, and realized I can't. why is this? Another thing; can additional data be stored on a live USB without affecting booting from it?

---

### Post by Toadinator on 2009-07-21
> **KakDela said:**
> Hmm... I was under the impression that for live USBs, as oppose to live CDs, settings (at least system settings) were stored to the flash drive... I could have sworn that I read somewhere that when there were only live CDs, people would carry CDs to boot from and flash drives to load settings and files off of, but with the introduction of live USBs, everything could be stored on one flash drive.

I thought that the whole point of a live USB was that the operating system could be booted on any computer; if all data is erased, that would destroy the point, wouldn't it?

I'm not quite ready yet to fully install ubuntu.

I also tried to open the flash drive from which I'm booting, and realized I can't. why is this? Another thing; can additional data be stored on a live USB without affecting booting from it?
Oh oh oh... I see your problem. What program did you use to install ubuntu on to your flash drive, if any? If it was unetbootin then no wonder you have this problem. unetbootin doesn't configure Live USBs with Persistent Storage (aka the ability to store personal data on it, such as documents, programs, and configurations).

---

### Post by Toadinator on 2009-07-22
Speaking of which, I found a neat little program that'll save you here: its called [cd2usb]("http://hacktolive.org/wiki/Cd2usb") (google's amazing, isn't it?). It'll make a live usb with persistent storage ^_^.

Oh and also, once you're running Ubuntu (if you're a newbie to the whole ubuntu thing) then might I suggest [Ubuntu Tweak]("http://ubuntu-tweak.org/")? Once you install the .deb file on the website, you can enable some very good repositories (some of which are official, like Wine, Pidgin, and Ubuntu Tweak itself) which will provide you with helpful updates to your installed programs, as well as provide new ones (such as Skype and OOo 3.1). Have fun!

---

### Post by t0p on 2009-07-22
Are you using jaunty?  If so, under System > Administration you will find **USB Startup Disk Creator** which will enable you to make a persistent (I believe) USB.

---

### Post by zeroseven0183 on 2009-07-22
> **t0p said:**
> Are you using jaunty?  If so, under System > Administration you will find **USB Startup Disk Creator** which will enable you to make a persistent (I believe) USB.


No, but this can help him: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

