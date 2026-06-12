---
title: "Can't update through Terminal"
date: 2011-01-18
forum: New to Ubuntu
---

### Post by Dutch70 on 2011-01-18
Hi, 

 I've noticed lately that if I do an update with "sudo apt-get update" in terminal, all it does is reads the packages, even when there are updates available. Also when I update via update manager, it doesn't go through the list of "Reading packages "62 of 62" or whatever. I've included pics of both. 

 Can someone please tell me what may cause this, or better yet, how to fix it? 

 I dual boot with Ubuntu & vista and have separate / & /home partitions. I did a fresh install of Kubuntu a couple days ago, but switched back to Ubuntu(fresh install) b/c I was having trouble with the diff terminal commands, but it seems to have kept a lot of the settings I had before.

ps. In the 1st pic, I ran the terminal 1st & got nothing. In the 2nd pic, I took the pic as soon as I clicked "check" for updates. 
I'ts updating cache. :confused:

---

### Post by NightwishFan on 2011-01-18
"sudo apt-get update" only reloads the repositories. The command you want is:
```
sudo apt-get upgrade
```

As for the update-manager behaviour, I am not quite sure what you mean.

---

### Post by Elfy on 2011-01-18
> "sudo apt-get update" in terminal, all it does is reads the packages, even when there are updates availableAs it should, if you then want to install the updated packages - upgrade

```
sudo apt-get upgrade
```

The system checks when it boots for updates (I believe) - so the Update Manager is up to date, it won't check. If you have a look in there a few hours after it will say - last checked x hours ago.

If you want to get the update manager to check - use the Check button.

---

### Post by Dutch70 on 2011-01-18
> **NightwishFan said:**
> "sudo apt-get update" only reloads the repositories. The command you want is:
```
sudo apt-get upgrade
```

As for the update-manager behaviour, I am not quite sure what you mean.

Great, thank you for such a quick response. That installed my updates, but why is update manager not working like it always has? As in the 2nd pic. How would I get it back to normal?

---

### Post by NightwishFan on 2011-01-18
I really cant be sure why it fails if the terminal version is successful. Does it time out after a while and fail?

---

### Post by Dutch70 on 2011-01-18
> **NightwishFan said:**
> I really cant be sure why it fails if the terminal version is successful. Does it time out after a while and fail?

 No, it will actually install them, but I've never seen it act that way before. It used to go through a process similar to reloading synaptic.
instead of saying "downloading file 47 of 72" when checking for updates. 
Now it says "Downloaded "0B of 21B" & at the top of the window it says "updating cache" instead of "Downloading package information", or "Reading package information"

---

### Post by NightwishFan on 2011-01-18
Well the update manager in Ubuntu 10.10 uses a new more flexible back-end for dealing with packages. The user experience should be largely the same. If there are no problems with it I would just learn the way it works now as the default.

---

### Post by Elfy on 2011-01-18
Wording changed I think. It's doing the same thing though.

I understand what you are saying now :)

---

### Post by Dutch70 on 2011-01-18
Well, that makes sense, being that I've recently upgraded from Hardy. I thought it was something I done b/c I've been messing with it a lot since the upgrade. Anyhoo, I feel much better now. :tongue:
Thanks a bunch for your help guys!

---

