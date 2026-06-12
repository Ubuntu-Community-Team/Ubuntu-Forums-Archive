---
title: "Belkin G f5d7050b"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by wanna be geek on 2009-11-23
My ubuntu set-up was working great untill my usb wifi dongle stopped working, so i purchased a Belkin f5d7050b a cheap one but works, well not so... 

I have tried to follow various posts and spent all my day off tring to get this bugger working, in ubuntu 9.04, I have tried ndiswrapper and installed the inf files, when i reboot hoping my wifi will work but it doesn't, "no networks" its not the adapter as it works in xp sorry to say.., 
so will a reinstall of 9.10 solve the matter? mind you that's a last resort, or is there a better way, not using Belkin's drivers..like generic ones,  
Im very new to Ubuntu so if i sound like a spoon that's why, so any help will a bonus...

---

### Post by coffeecat on 2009-11-23
You've been unfortunate. Many (most?) of the chipsets that Belkin use for their G devices work out of the box with recent versions of Ubuntu. Trouble is, Belkin have a habit of putting different chipsets in at different times without changing the model number. So you have to do a bit of detective work.

Will a new install of 9.10 be the solution? Here's how to find out without installing 9.10. Simply boot up with the live 9.10 desktop CD and with the Belkin plugged in. Click on the network manager icon. Are any wireless networks visible? If you click on yours, can you connect after you have put in your WEP/WPA key? If yes to both, then a fresh install of 9.10 would seem to be the answer.

But if not, post the terminal output of:

```
lsusb
```

and

```
sudo lshw -C network
```and that will hopefully tell us what's inside that little fella, and what the best course of action is.

---

