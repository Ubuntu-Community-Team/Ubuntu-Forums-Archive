---
title: "seamless virtualization - Jaunty - VirtualBox - XP guest"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by aharown07 on 2009-08-20
I've got some apps I have to run in Windows... and Wine can't handle them. So I have set up a VirtualBox with XP Pro in it.
So I was reading here [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization) about  going seamless... got as far as doing this in the terminal..

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" 10.0.2.15:3389 -u administrator -p password
```

Result is this...
```
Autoselected keyboard map en-us
ERROR: 10.0.2.15: unable to connect
```

I couldn't find any info on how to get the VM IP address in XP ... for Vbox 2x.
So I just did a CMD in XP and then IPCONFIG. But apparently that's not how you do it?
Much of the info I'm finding via Google is out of date.

---

### Post by whitethorn on 2009-08-20
As far as I know the ip address you get in Vbox XP is usually given to you by your router. But then it all depends on what kind of Network Interface you set up, when xp is off click on settings go to the network tab, and then under Attached to : Choose bridged adapter

which means, it'll share your connection and xp will receive it's own IP address from your router.  You should then be able to ping it from ubuntu...

---

### Post by j7%&lt;RmUg on 2009-08-20
Also make sure you have a net connection on ubuntu first, before you try getting a connection on XP.

---

### Post by MyR on 2009-08-20
Umm..

Virtualbox has a "seamless mode" option.  It worked perfectly for me.
No assembly required.

---

### Post by nmaster on 2009-08-20
try this link.  it will explain exactly what to do. 

[http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux](http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux)

---

### Post by aharown07 on 2009-08-22
Thanks! Didn't even know there was "seamless mode"! 
I believe I've got what I was after now.

---

