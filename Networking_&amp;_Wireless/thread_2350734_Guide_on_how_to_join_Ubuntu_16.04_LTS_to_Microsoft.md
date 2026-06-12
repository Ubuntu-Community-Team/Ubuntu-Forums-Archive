---
title: "Guide on how to join Ubuntu 16.04 LTS to Microsoft Active Directory using PBIS"
date: 2017-01-27
forum: Networking &amp; Wireless
---

### Post by arsalanj123 on 2017-01-27
Hi everyone, 

Here is a guide on how to join Ubuntu 16.04 LTS to the Microsoft Active Directory using Beyond Trust's Power Broker Identity Services Open version. 

I'm using wired network, so connect your computer to the Ethernet port on the pc before attempting the following.

1. Freshly installed Ubuntu 16.04 LTS or sometimes already in production can also work but I would suggest use virtual images to check the outcomes before doing anything in production.
2. Go to softwares and updates > other updates and enable canonical partners and canonical partners (source code).
3. open terminal and do "sudo apt-get install likewise-open"
4. sudo apt-get update
5. sudo apt-get install ssh
6. sudo reboot (system restarts)
7. Login again
8. Open browser and go to [https://github.com/BeyondTrust/pbis-open/releases](https://github.com/BeyondTrust/pbis-open/releases). Download the download file for your supported architecture. Mine is **[COLOR=#0066cc]_pbis-open-8.5.2.265.linux.x86_64.deb.sh_[/COLOR]**.

9. open terminal
10. cd  /Downloads
11. sudo chmod +x pbis-open-8.5.2.265.linux.x86_64.deb.sh
12. sudo ./pbis-open-8.5.2.265.linux.x86_64.deb.sh
13. After installing it might open a gui based domain join window. If not then later enter sudo ./domainjoin-gui
14. Enter your domain name into the Domain field and press join domain.
15. You will get a warning saying restart is required to join the domain. that's good news. Close it.
16. After close all boxes that appear
17. in the terminal enter sudo nano /etc/pam.d/common-session and under the two lines enter these two lines more: "allow-guest=false" and "greeter-show-manual-login=true". Exit and Save it.
18 sudo nano /usr/share/lightdm/lightdm.conf.d/50-unity-greeter.conf
19 find the line "session optional pam..." something after pam I don't remember and replace it with "session [success=ok default=ignore] pam..." something after pam, keep that pam word the same. Save and Exit
20 sudo nano /etc/sudoers
21 Find "root ALL=(ALL:ALL) ALL" and under it put the admin account you are using "adminaccountname ALL=(ALL:ALL) ALL" and save and exit.
22. Done!
23. sudo reboot
24 You see a login option in the screen. now you login like this "domainname\domainusername" and then password in the password field. 

Done!

This should work +95% of the time. :)

Note: If your gui does not open restart the machine and try again. Sometime there is an error libglade2-0. See that you have the latest of it "sudo apt-get install libglade2-0".

If there are any issues please let me know and I might be able to help.

Arsalan
Network Engineer

---

### Post by TheFu on 2017-01-27
Welcome to the forums.  Impressive 1st post.

Lots of extra steps that aren't necessary.

2. Go to Software and Updates > Other updates and enable canonical partners and canonical partners (source code).
3. open a terminal 
4. sudo apt update   # apt is the new apt-get
5. sudo apt install ssh likewise-open fail2ban  # ssh is a metapackage with both openssh client and server
6. reboot probably not needed
....

Most instances of **sudo nano** should use **sudoedit** instead. It is safer and uses whatever EDITOR the user has defined.
Modifying the sudoers (step 20) should **always, always, always** use **visudo**.

Don't know what installing ssh has to do with this task. Not a terrible idea, just not related. Whenever ssh is installed, would be smart to also install some brute-force attack protection like **fail2ban** or **denyhosts** and configure it. The defaults for fail2ban are reasonable for ssh. Don't know about denyhosts.

I've seen SSSD used for this purpose (using AD for login authentication).  It is F/LOSS.  Requires editing a few config files as normal Unix daemons often do. 
[https://help.ubuntu.com/lts/serverguide/sssd-ad.html](https://help.ubuntu.com/lts/serverguide/sssd-ad.html) and 
[https://wiki.ubuntu.com/Enterprise/Authentication/sssd](https://wiki.ubuntu.com/Enterprise/Authentication/sssd)

More options are good. Thanks for posting.

---

