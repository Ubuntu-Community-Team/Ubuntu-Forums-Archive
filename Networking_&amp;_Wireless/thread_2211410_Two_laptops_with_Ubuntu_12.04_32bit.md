---
title: "Two laptops with Ubuntu 12.04 32bit"
date: 2014-03-15
forum: Networking &amp; Wireless
---

### Post by Joe_Johnston on 2014-03-15
Hi All,

I just convinced two users to switch to Ubuntu for their older laptops but something is not right with the networking. His computer can see hers but she cannot see him and they are on the same wireless home router. They are both on workgroup and I am using Samba to set up the sharing but when clicking the browse network I can only see her laptop from his and not vise versa. Can you give any insight? I thought two Ubuntu laptops would easily see each other without any configuring but I am new to Ubuntu and still learning and appreciate the feedback. Thank you.

---

### Post by Joe_Johnston on 2014-03-16
I am hoping this is a simple solution as it seems Linux would make it easier than Windows to share data. I hope someone has some input.

---

### Post by Joe_Johnston on 2014-03-17
I will be heading back over to look at these laptops today, does anyone have any input? Thank you.

---

### Post by oldfred on 2014-03-17
Are you connecting the two with just Linux or to the other as Windows?

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
Howto: Fix Windows share browsing issues 
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)
Sharing issues
[http://ubuntuforums.org/showthread.php?t=1374369](http://ubuntuforums.org/showthread.php?t=1374369)
See posts by Morbius1
[http://ubuntuforums.org/showthread.php?t=1649380](http://ubuntuforums.org/showthread.php?t=1649380)
[http://ubuntuforums.org/showthread.php?t=1872904](http://ubuntuforums.org/showthread.php?t=1872904)

I do not know Samba anymore.
Years ago I had Linux on desktop and XP on laptop. I only wanted to copy data once or twice a year when i travelled. In that time my Ubuntu install often was new, XP had new firewall, secuity system and other updates and it always seems like a major task. I just gave up on Samba, installed Ubuntu on laptop and configured NFS. I was able to script configuration so after a new install I could easily reinstall.

---

### Post by rogergantner on 2014-03-17
When I installed 12.04 32 bit on my laptop yesterday SAMBA did not automatically install. I went onto the Software Centre and installed SAMBA from there. Other than the horrible slow speed due to the opensource iwl3945 driver for the intel 3945ABG wireless card network discovery now works properly.

---

### Post by Joe_Johnston on 2014-03-17
Yes, I had to manually install Samba and they are both using Ubuntu 12.04 32 bit and no Windows of any kind. I am just wanting to get both laptops to be able to see each other and share files. They also have an external HD and he wants to share that drive so they can both use it for backup. I believe I set that up correctly but cannot tell since she cannot see his laptop when Browsing Network.

---

### Post by rogergantner on 2014-03-17
Another thing I've done is create a folder under Home called 'Shared', and when I right clicked to share this folder I was prompted by Nautilus that permissions have to be set up to share this folder and that it could do that automatically. I clicked to do it automatically and everything is working.

---

### Post by Joe_Johnston on 2014-03-17
Wonderful, thank you all for the input! I am heading over and hope to have success.

---

### Post by rogergantner on 2014-03-17
good luck. post back. lol
sometimes it can be stubborn.

---

