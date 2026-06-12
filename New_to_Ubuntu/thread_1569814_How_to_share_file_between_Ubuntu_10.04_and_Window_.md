---
title: "How to share file between Ubuntu 10.04 and Window 7 by using Virtual Machine(VM)?"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by Jian0203 on 2010-09-07
Can anyone help me with this ?

I am trying to share the file between Ubuntu and Window 7 but the Window 7 just can't read the shared file of Ubuntu .

Because I am still new to Linux so can anyone provide me a detail solution ? I have refer to many sites and forum but their solutions don't work for me .

Thanks a lot for helping ~

---

### Post by bredman on 2010-09-07
On the Ubuntu machine...

1. Open the directory you want to share (for example use the main menu Places/Documents)
2. Move up one level, by clicking on the up arrow next to "Forward"
3. Right-click on the directory you want to share
4. Select "Sharing options"
5. Tick "Share this folder"
6. If this is your first time to share a folder, you may be asked to select a sharing type. Select "Samba" and allow any needed software to install.
7. Tick "Guest access" if you are on a private network and don't want to bother with passwords.
8. Remember the name of the shared folder for later steps, I will use the name "MyShare" in example below.
9. Click on "Create share"
10. Press CTRL-ALT-t to open a terminal
11. enter the command
ifconfig
12. Look for your IP address. It should look like
eth0 inet addr:192.168.1.99

On the Windows machine...
1. Open "My Computer" or any similar file browser.
2. In the address bar at the top, type in
\\192.168.1.99\MyShare
(remember to substitute your Ubuntu IP address and your shared folder name)
3. You may be asked for your Ubuntu username and password, depending on the settings in step 7 above.

Windows should now be able to access your Ubuntu shared folder.

---

