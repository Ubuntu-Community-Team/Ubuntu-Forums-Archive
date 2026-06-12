---
title: "Can't connect to samba shares since Feisty upgrade"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by benn333 on 2007-05-06
Since upgrading from Kubuntu Edgy to Feisty, other computers have been unable to connect to the shares on the Kubuntu machine. The Kubuntu machine can connect to my Windows machine via samba. Also, the Windows machine can connect to the root of the Kubuntu machine's share, displaying the share names, but if I try opening a share folder, I get the following error:

"\\[IP ADDRESS]\[SHARE NAME] is not accessible. You might not have permission to use this network resource. Contact the administrator of this server to find out if you have access permissions.

The network path was not found."

I've gone through the Samba troubleshooting guide below, and things stop working at step 6:
[http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html)

Step 6 only returns the Kubuntu machine's IP, though the IP, broadcast, and subnet settings look correct for all machines. 

Step 7 also returns odd results (smbclient //[SAMBA MACHINE]/[SHARE NAME]). The share name comes back with odd characters in the name:

"Domain=[LUNIA] OS=[Unix] Server=[Samba 3.0.24]
Connection to l&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;(O&#65533; failed"

From here, I'm not sure what to do to fix it. Any suggestions? Thanks.

---

### Post by dmizer on 2007-05-06
try mounting with unicode (utf8) ... directions can be found in the second link in my sig.

---

### Post by benn333 on 2007-05-07
Thanks dmizer, that looks like a well-written guide. I may have not been clear enough, however. I can connect *to* Windows shares from my Kubuntu machine just fine. (If I shared files this way often, I'd be sure to use your guide to set up mounted shares.) The problem I'm having is connecting to my Kubuntu machine *from* the others.

---

### Post by benn333 on 2007-05-07
Lol. Well, I took a look at the first guide in your sig. Low and behold, it did the trick, at least for one of my machines. (I didn't bring my work machine home tonight, so I can't say it's 100% fixed yet.) Thanks for the help dmizer, albeit you provided the solution inadvertently. ;)

---

### Post by dmizer on 2007-05-07
sorry for the misunderstanding ... glad you found the answer though ;)

---

