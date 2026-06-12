---
title: "Help with xorg.cong"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by HNP45acp on 2009-08-18
**I need some help with xorg.conf:**
 
*(Thanks to everyone in advance)*
 
I installed Ununtu-9.04 in VBox-3.04r50677 on WinXP.  I then installed Guest Adds and installed Ubuntu Updates.  The Ubuntu updates ruinned my setup --> now Ubuntu can only load its GUI in low graphics.  It appears that it is Ubuntu Updates that are messing up things.  (I chose Install ALL updates - and I think that some X11 files were changed during the update)
 
I tried to change sequence (ie. Install Ubuntu - Install Ubuntu Updates - Install Guest Additions), but got same results.  However when I do the same on a Ubuntu Host, I dont have this problem.
 
**Here's the messages: **
 
**VBoxVideo**(**0**): **Output** **VBOX1 enabled but has no modes**
**VBoxVideo(0): initial CRT Configuration failed!**
**(EE) Screen**(**s**) **found**, **but none have a usable configuration**
 
I tried to specify modes in xorg.conf, but I just get other erros: example: Error in Parsing File.  Could my problems be due to xorg versions incompatibilities?
 
When I start in Low Graphics, it tells me that Display#0 is already in use and asks if I want to use Display#1.  If I say **YES.** Then it loads Ubuntu just fine!!! What is going on? does it load in failsafe mode this way?
[B] 
Also, a few questions[/B]
1) Why do I have to specify modes?
2) Can anyone post a xorg.conf file that works for Ubuntu-VBox-WinXP with GuestAdds?
3) What are these XServer Displays? Are these the same as Virtual Consoles (Ctrl+Alt+F#)
 
Many thanks.  I have been fooling around with xorg.conf for several days now =(

---

### Post by cariboo on 2009-08-18
You may have to extract the guest additions for linux from the guest additions iso in order to install it. Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=973756"), post #8

---

### Post by HNP45acp on 2009-08-18
That's how I installed Guest Additions. I mounted Guest Additions ISO in VBox and started Guest (Ubuntu 9.04)

Then ran Terminal: **sudo /media/cdrom/VBoxLinuxAdditions-x86.run**
 
and added a line to Section "Device" in xorg.conf: **Driver "vboxvideo"**
 
and everything seems to have intalled fine. Neither the Ubuntu Updates Install nor the Guest Additions Install seem to have changed to contents of xorg.conf

then shutdown with *sudo shutdown -P now*, unmounted ISO from VBox, and started Ubuntu 9.04 and got error messages.  
 
At this point I don't know what else to try.  It may have to do with Ubuntu Updates creating incompatibilities somewhere in /etc/X11 files, but I don't want to mess around with the other /etc/X11 files yet.  I'm hoping this is something that I can fix through xorg.conf

---

### Post by HNP45acp on 2009-08-18
Partial Fix - 

I was able to get Ubuntu to boot by adding a SubSection to **Section "Screen"** with **Modes "800x600"** without adding a DefaultDepth as I have seen it elsewhere.  It seems that 
1) I need a line for Modes to overcome the **no modes found** error, but 
2) I must keep lines for DefaultDepth out to avoid file parsing errors
 
What Works Now:
2) Mouse integration seems to wark as it should
 
What Still Doesn't Work:
1) Both Ubuntu LogIn & Ubuntu-Desktop screens are too large, even though my 800x600 should be enough for a 15 in CRT monitor. <-- However Full Screen mode (Host Key + F) works fine. 
2) Guest screen doesn't resize when I resize the VBox window, as it should.
 
Looking good so far - just hope to get it to run as it should =/
 
Thanks

---

### Post by HNP45acp on 2009-08-21
Than you for the replies!

I eventually reloaded / clonned Ubuntu (several times), and it seems that there is an issue with cloning vdi files (via VBoxmanage clonevdi).  Somehow the combination Cloning and Guest Additions seems to be problematic.  It may have something to do with changing drive UUID.

I will try to play around with it when I have more time.  I find cloning vdi files very useful, and would like to get it to work with GuestAdds.  However, it may not be possible and hence the reason we have the the Snapshot utility (which I don't know much about yet - on my list to learn soon).

Again, thanks.

---

