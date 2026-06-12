---
title: "Network Neighborhood Not Displayed Correctly on Two Computers with Ubuntu 16.04"
date: 2017-01-21
forum: Networking &amp; Wireless
---

### Post by Steve R. on 2017-01-21
Recently, I noticed that when viewing the network under Nautilus on two computers that the other two home LAN computers do not show-up. Look at image for **computer3** and compare that to the image for **computer1**. **Computer3** shows the expected network neighborhood. The image for **computer1** only shows the windows network icon. I would like to have the computer network displayed again as displayed by **computer3**.

**Additional notes:** The windows network icon on **computer1** takes a very long time to appear.  Other than that, it works correctly as you click on it to display the other computers. I believe that the other network computer icons as show for **computer3** may have disappeared from **computer1** as a result of attempting to avoid having to login to access a remote computer. I didn't try that with **computer3**, and it is the only one that shows the other networked computers as shown by the attached image.

---

### Post by Steve R. on 2017-03-05
New information.
[LIST=1]
[*]I just recently installed a new router. The router is now visible in the same manner as displayed in the image "*computer3.png*" in my initial post.  However the other computers still do not show-up.

[*]Additionally, a bug report that I submitted on network discovery has been "*confirmed*" (Bug #1589975). [Ubuntu 16.04 has Networking problems]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1589975"). Whether this bug has anything to do with my current problem is unknown.
[/LIST]

---

### Post by Steve R. on 2017-03-20
Still analyzing this network display concern.  Now fully solved.  Since making this post, I located and deleted a "**.smb**" directory in my "**home**" directory. That solved the problem on one computer, but only partially on the other.

Turns out, for some unknown reason, the **fstab** file did play a role in failing to display the other computers on one computer.

# out the line below resolved the issue of the other computers not showing-up. Why I don't know.
```
//syrma/sfmagcovers /home/steve/sfmagcovers cifs file_mode=0777,dir_mode=0777,credentials=/etc/samba/credentials,sec=ntlmssp,uid=1000,gid=34,nofail,iocharset=utf8,user 0 0
```

I also tried this approach, but it did not work either.  For now, this mounting option has simply been deleted since I don't access that **fstab** mounted directory much.
```
#//syrma/sfmagcovers /media/sfmagcovers cifs file_mode=0777,dir_mode=0777,guest,sec=ntlmssp,uid=1000,gid=34,nofail,iocharset=utf8,user 0 0
```

The network now shows-up correctly.

---

