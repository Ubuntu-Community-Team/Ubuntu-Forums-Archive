---
title: "Gutsy not retaining WPA shared key"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by mjezell on 2007-11-05
I've been able to get the wireless on my Aspire 5000 laptop to work but don't know why the WPA shared key is not being retained in system>network>properties.  When I reboot the system I have to go in and re-enter the key before the the wireless nic will connect to my router.  I do not have network-manager installed because all of the ip addresses on my network are static.  Any suggestions would be appreciated.

---

### Post by clflyer on 2007-11-05
Same problem here. I have to reenter the WPA password each time I boot Ubuntu.
I have noticed that the password appears to have doubled in size...

---

### Post by mjezell on 2007-11-05
Thanks for the reply.  I noticed the same thing but thought it was do to the encryption process.

---

### Post by cml21 on 2007-11-06
bump...    (I'm having the same problem)

---

### Post by xshakakee on 2007-11-07
You all are going to have to bite the bullet and go into the terminal.  Right now, no one can help you because you have not posted code ```
like this
```

Anyway, first, go to Applications --> Accessories --> Terminal.  A little window should open up that looks like:```

me@mydomain:~$
```

You will want to type in the following command, starting from after the $:```

 me@mydomain:~$ gedit /etc/network/interfaces
```

This will open up another window, this one with a bunch of text inside.  Just Select All (CTRL+A) and paste (CTRL+V) the results in the Message thread here when you get ready to post again.

We'll be able to help you, I think, if you just post the contents of the interfaces file, or modify it yourself.

If you want to modify it, without us telling you what to do, you'll have to use:```

me@mydomain:~$ **sudo** gedit /etc/network/interfaces
```
and type in your password when it prompts you.

You can make modifications to this file, and save, using CTRL+S.
If I were you, I'd copy the original interfaces file to a backup, in case something goes horribly wrong and you cannot recover.  The best way to do that is to use```

sudo cp  /etc/network/interfaces  /etc/network/interfaces.bak
```
Also, I would check out this post:
[http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

These folks, and the forum moderators can set you up with a way to permanently lock in your WPA password.

Ya gotta make changes in the console, though.

---

### Post by tvphil on 2007-11-07
It may not be necessary or work, but try this. If you have a workgroup name on your network that is different than the SSID (network name), try entering the workgroup name as the SSID. Then, if necessary, enter the network key. This worked on one of my computers that didn't have intel centrino for a wireless nic. Ubuntu's wireless connections seem to work much better with Centrino.By the way,  I'm using WPA 2 encryptiion through a D-Link Wireless N router.

---

### Post by mjezell on 2007-11-07
Thanks for the reply  xshakakee.  
Should have given more information.  I'm very comfortable using the command line and prefer to.  I have set-up wireless on several Ubuntu systems successfully and have it currently running on a feisty box without problems.   This is a problem that I have not ran into until doing a clean install of Gutsy after running several tribe releases successfully with wireless.  Interfaces, iwconf, iwlist scan, lspci and route -n show no irregularities.  My post was an attempt to find people with the same problem in Gutsy and any solutions they had to it.  I was hoping to find a change in the way wpa_supplicant is handling the share key in Gutsy.  

Thanks for the link. 
I've used wieman01's post in past trouble shooting sessions on earlier versions of Ubuntu.  Such things as wpa_supplicant being including with Gutsy by default have me thinking there maybe other things have changed and are different from wieman01's post. 

I'll keep looking and appreciate any other suggestions you may have.

---

### Post by mjezell on 2007-11-07
Hi tvphil
My workgroup name and SSID name are different.  As I explianed in the last post, I do have another system, Ubuntu Feisty, running wirelessly on my network without any problems.  My laptop is a dual boot with XP (work slave) and it continues to work without problems.  

Thanks for the suggestion and I appreciate any other possible solutions you run across.

---

