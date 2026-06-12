---
title: "Upgrade to Ubuntu Mate 20.04 TigerVNC not working like vnc4server did, help!"
date: 2021-03-06
forum: Networking &amp; Wireless
---

### Post by bob-swede on 2021-03-06
I have an HP w8440 laptop on which I installed Ubuntu Mate 18.04 LTS a year ago (before 20.04 came out).
This is sitting on my wired network but with no monitor attached because I access it using SSH and VNC (PuTTY and RealVNC clients) from Windows10.
I installed vnc4server when it was set up back then and it has worked flawlessly up until I decided to accept the logon nag to upgrade to 20.04 LTS...

When that was done a week or so ago most seemed to work afterwards, but when I tried to access it via VNC as I used to there was no connection.
After some research I realized that the upgrade to 20.04 had hosed my VNC server and there was no vnc4server available on apt anymore. :(

So then I had to find a replacement and since TigerVNC is maintained by the Ubuntu folks I though that would be a good version.

I installed TigerVNC using:
```
sudo apt install tigervnc-standalone-server
``` 

But it would not allow any connectíon until I found that I had to modify the /etc/vnc.conf to enable this setting:
```
$localhost = "no";
```

Now I can connect from the RealVNC client on my main computer, but the desktop of the target does not appear as it did with vnc4server.
Just a gray rectangle is shown after the login is given.
With vnc4server I saw my normal desktop...

What should I do to get to that state again?

---

### Post by bob-swede on 2021-03-06
_**Reply to self...**_
I found that returning the xstartup file from backup to ~/.vnc/ solved the start problem.
Now the normal desktop is visible in the VNC session and my applications also appear properly.
I did have this file available from when the system was running 18.04 LTS with vnc4server, so by returning this the old desktop appeared.

---

