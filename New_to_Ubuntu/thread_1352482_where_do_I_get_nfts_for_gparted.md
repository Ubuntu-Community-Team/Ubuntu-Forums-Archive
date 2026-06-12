---
title: "where do I get nfts for gparted"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by john1066 on 2009-12-11
In a moment of  Vista madness I used their disc manager and somehow ended up with an partition on my disc which is not visible from  Vista/explorer. I wanted to use gparted to make it visible in Ubuntu 9.10 but it can't handle nfts. So my question is - how do I get nfts support into gparted?

Thanks,
John

---

### Post by synapsys on 2009-12-11
```
sudo apt-get install ntfsprogs
```

---

### Post by john1066 on 2009-12-11
Doesn't do it. Sudo asks for a password but then won't take any keyboard input. See below

jjs@jjs-laptop:~$ sudo apt-get install ntfsprogs
[sudo] password for jjs: 
Sorry, try again.
[sudo] password for jjs: 

Got me stumped.

John

---

### Post by leef on 2009-12-11
the password prompt in the console doesn't show input (it doesn't add *s like you would expect it to). How about installing using this apt url; [apt://ntfsprogs]("apt://ntfsprogs").

---

### Post by john1066 on 2009-12-11
Clicking on that url then I get a launch application pop up asking me for an application tp open the link?

Guess I'm not quite getting what you mean.

John

---

### Post by john1066 on 2009-12-11
And then after a couple of minutes i worked anyway - mysterious. Anyway I've got the stuff and managed to label the partition thanks.

John

---

### Post by leef on 2009-12-11
Rats I was thinking that you were more than likely using the firefox that comes with ubuntu (which would have installed the app) might be best if you searched for "ntfsprogs" in synaptic, using the following command "gksudo synaptic".

---

### Post by tom66 on 2009-12-11
Sudo has a security feature. It won't show what you are typing (not even stars) - you end up typing 'blind' into it. Just type your password & press enter.

---

