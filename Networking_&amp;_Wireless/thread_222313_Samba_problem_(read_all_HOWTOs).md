---
title: "Samba problem (read all HOWTOs)"
date: 2006-07-24
forum: Networking &amp; Wireless
---

### Post by ammarr on 2006-07-24
Hello,

I have to join a windows workgroup (i.e. be able to browse the workgroup, though I dont necessarily want to share any folders off my own PC). I dont have access to the other windows PCs.

Yesterday, it seemed to work when I simply (after a fresh install, from what I remember) went into /etc/samba/smb.conf and changed workgroup = my_workgroup and rebooted the PC. However, after that I made some other changes (i was trying to connect through a proxy), and today I cant access the workgroup at all (i.e. from places ->.. ) I cant access any windows PC directly using smb:// either.

I tried installing samba and smbfs using sudo apt-get install samba, and that didn't solve anything. I made sure smbd and nmbd were running. (read this in other HOWTOs)

I tried a fresh install and changing only the /etc/samba/smb.conf file, but thats not working either.

What else would I have to do to be sure that I can join this workgroup? There is simply no other configuration I can think of other than my pc name (netbios name = .. in smb.conf) and the workgroup name (workgroup = .. in smb.conf), because these are all the details I've ever had to use in windows.

I'm not sure if it matters, but I am assigned a static IP and connect through a proxy, but dont think that should matter with the workgroup configuration. Also, the proxy rejects the connections if i'm not part of the workgroup. Meaning, I cant access the net unless I join the workgroup. (And both the workgroup and the net were working fine yesterday, so I'm sure this can be done, and I'm also quite sure that nothing has changed at the server or other windows PCs).

Apologies for the long post! :???:

---

### Post by foolishchild on 2006-07-25
Read ALL the Howto's?

The samba howto contains a fantastic checklist here [http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/diagnosis.html) which always sorts me out. It gives you a step by step method for finding your samba problem.

I notice apt-get install samba also stores it as /usr/share/doc/samba/diagnosis.html.

---

### Post by ammarr on 2006-07-25
All those i could find through google and on ubuntuforums :-)

Thanks for the link, I'll check it out.

---

