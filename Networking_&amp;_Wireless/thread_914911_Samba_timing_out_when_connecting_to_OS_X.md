---
title: "Samba timing out when connecting to OS X"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by Baza210 on 2008-09-09
Hi everyone. Sorry that my first post is a question..

Before I explain my problem I'll just describe the two machines in question.
1. Asus EEE 1000H running Hardy with Adamm's Kernel for EEE.
2. Apple iMac running OS X 10.4

Now, I enabled "Windows file sharing" on my iMac, which let me connect to my mac through the Connect to server.. option with smb://192.xxx.x.xx/username , and my iMac's harddrive was mounted on the desktop and was fully browsable. Since my EEE doesn't have an optical drive,  I've been using my iMac to rip my DVDs to mp4 and then have been transferring them to my EEE by USB key. This is annoying because my iMac only has USB 1.1 so it's painfully slow. 
With my EEE connected by Samba to the imac, I dragged and dropped the video files onto my EEE's harddrive. It started transferring the files quite rapidly -up to 350kb/s. However, after several minutes, I got an error saying that the connection had timed out. This occurred repeatedly on attempting numerous other times.

So what I'd like to ask is - Is there a fix for this issue, and, if not, is there an alternate wireless file transfer method I could use? I have SSH setup too, but that seems to use the actual internet rather than transferring just through the router, and "proper" filesharing with is a big no-no with my ISP.

Thanks in advance for any help. In fact, thanks for just reading this far..

---

### Post by matriculated on 2008-09-09
I'm on 10.5 so this may be a bit different: You could try enabling AFP on your iMac and installing Netatalk on your ASUS. AFP/Netatalk is Apple's native file sharing method while SMB/Samba is more Windows centric. It's a bit of a hassle to set up but I've found it much more stable than Samba. Here's a set of guides I used:
[http://www.zaphu.com/2008/04/30/five-guides-on-how-to-integrate-ubuntu-into-a-mac-os-x-network/](http://www.zaphu.com/2008/04/30/five-guides-on-how-to-integrate-ubuntu-into-a-mac-os-x-network/)

Also a guide right on this forum: [http://ubuntuforums.org/showthread.php?t=410274](http://ubuntuforums.org/showthread.php?t=410274)

I've a sneaking suspicion that OSX is pretty flaky with Samba - especially with Leopard.

---

### Post by Baza210 on 2008-09-09
Thanks for the links. My Linux seems to be having some other problems though..

I got as far as the fourth step, then get this:

brian@brian:~/src/netatalk$ sudo apt-get build-dep netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up netatalk (2.0.3-9) ...
Starting Netatalk services (this will take a while): ra0: disabled.
atalkd: zero interfaces, exiting.
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error processing netatalk (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netatalk
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Failed to process build dependencies
brian@brian:~/src/netatalk$ 

Any ideas?

---

### Post by Baza210 on 2008-09-09
Ok, Netatalk really doesn't seem to want to work on this computer. First I had to make a fake ethernet connection, then build-dep it or something, and it still failed. It also keeps crashing the dpkg subprocess.

---

