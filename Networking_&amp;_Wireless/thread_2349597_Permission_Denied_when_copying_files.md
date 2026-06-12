---
title: "Permission Denied when copying files"
date: 2017-01-16
forum: Networking &amp; Wireless
---

### Post by peyre on 2017-01-16
I have two Xubuntu computers; both are running 64-bit Xubuntu 16.10, and I recently wiped the hard drives and reinstalled from scratch because they had gotten a little messed up with time.  Now they're running fine, except if I try to copy a file from my laptop to my desktop I get "Permission Denied".  The user name and password are the same on both computers, and I can copy files from the desktop to the laptop, just not the other way around.  And I can read from my desktop share from the laptop, but not write to it.  Very strange!

I used the Samba link in Settings on both machines.  I set both shares to be Writable and Visible, and Allowed access to everyone, so I'm kind of puzzled why I'm having trouble sending files...and in only one direction, at that!  Any ideas?

---

### Post by SeijiSensei on 2017-01-16
Install openssh-server on both machines and use scp or rsync to transfer files.  

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

You can then use sshfs to share folders between the machines rather than Samba.  

[https://www.digitalocean.com/community/tutorials/how-to-use-sshfs-to-mount-remote-file-systems-over-ssh](https://www.digitalocean.com/community/tutorials/how-to-use-sshfs-to-mount-remote-file-systems-over-ssh)

That will let you drag-and-drop files between the machines.

Actually, with Kubuntu, I can create an sshfs connection between two machines on-the-fly by entering a fish://server/share URL in the file manager, Dolphin.  I have little experience with Xubuntu, so I don't know whether its file manager offers similiar functionality.

---

