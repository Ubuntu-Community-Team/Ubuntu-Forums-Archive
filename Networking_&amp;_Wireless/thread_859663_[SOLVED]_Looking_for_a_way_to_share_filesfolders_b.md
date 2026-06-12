---
title: "[SOLVED] Looking for a way to share files/folders between two Ubuntu machines."
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by fullmetalgerbil on 2008-07-14
I have a desktop and a laptop both running Ubuntu 8.04, and the internet connection is shared via a wireless router. I need to know how to create share folders on the desktop that can be accessed from the laptop and vice versa. When I'm browsing my network on the desktop the laptop appears, only the only folder that shows up is a shared printing folder. I'm looking to create other share folders that can be accessed by either computer, or to gain the ability of browsing all folders of either machinefrom either machine.

---

### Post by dmizer on 2008-07-14
see the 4th link in my sig.

if you want to share files to and from both computers, both computer will have to be configured as both a server and a client.

---

### Post by fullmetalgerbil on 2008-07-14
dmizer, I followed the link. It looks way more complicated than I think I can handle. For serious, I dont think I can do it. I'm so effing stupid when it comes to Linux I cant even find my own IP address via the terminal. Really, I read that post and was lost like halfway through.
I'll try it, I just hope I don't totally screw things up...

---

### Post by dmizer on 2008-07-14
believe me when i say, it's way easier than attempting to do the same with samba.

just give it a shot, and if you run into problems we'll get you straightened out.

---

### Post by Yuki_Nagato on 2008-07-14
I share files with the SSH Protocol.

```
sudo apt-get install ssh-server ssh-client
```

After that, I can use a terminal to run remote scripts or I can use a GUI interface for easy click-and-drag.

---

### Post by fullmetalgerbil on 2008-07-14
Ok, thanks. I managed to get the NFS server support installed, but when I went to edit /etc/exports per the guides next step, I entered sudo vi /etc/exports and got this in the terminal:
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/etc/exports" 10 lines, 321 characters"
The guide says I'm now supposed to add permissions to my /etc./exports, but I have no idea how-like where would I enter /files 192.168.1.1/24(rw,no_root_squash,async)in that terminal output and is the example ip range given for that command (192.168.1.1 through 192.168.1.255) an umbrella range or do I have to enter my own ip?

---

### Post by fullmetalgerbil on 2008-07-14
I'm already started into configuring for NFS, so if I cant pull it off then I'll try SSH. Thanks though.

---

### Post by dmizer on 2008-07-14
> **fullmetalgerbil said:**
> The guide says I'm now supposed to add permissions to my /etc./exports, but I have no idea how-like where would I enter /files 192.168.1.1/24(rw,no_root_squash,async)in that terminal output and is the example ip range given for that command (192.168.1.1 through 192.168.1.255) an umbrella range or do I have to enter my own ip?
actually, the howto is wrong here (but not so wrong that it won't work), it should read 192.168.1.[COLOR="Red"]0[/COLOR]/24(rw,no_root_squash,async)

you should use your own ip range.  so 192.168.1.0/24 means that any computer with an ip of 192.168.1.x will be able to access the share.

if you only want one computer to access the share, then you should enter the ip address of the computer for which you wish to allow access like so:
```
/files 192.168.1.100(rw,no_root_squash,async)
```

assuming that 192.168.1.100 is the ip address of the computer wishing to access files.

---

### Post by fullmetalgerbil on 2008-07-14
OK, two things- First, I still have no idea how to enter anything when my terminal just says, again,:
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
~                                                                               
"/etc/exports" 10 lines, 321 characters
And second, I don't even know how to find my ip range for either computer.

---

### Post by fullmetalgerbil on 2008-07-14
Never mind. I'm going to try ssh.

---

