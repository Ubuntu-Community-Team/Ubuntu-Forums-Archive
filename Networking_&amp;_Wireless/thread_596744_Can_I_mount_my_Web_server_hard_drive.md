---
title: "Can I mount my Web server hard drive?"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by hipnerd on 2007-10-29
I do a little Web design and I am trying to completely divorce myself from Windows. I'm pretty close, but one of the programs I miss is HTML-Kit, which allowed me to edit files directly on the Web server using a graphical editor, rather than downloading, editing, saving, then re-uploading.

HTML-Kit is not coming to Linux anytime soon, I think. So I was looking for a way to duplicate that functionality. I thought that the best solution would be if could mount the remote system as a drive on my home box. This sounds like the sort of thing I should be able to do. but I don't know how to do it. 

I'm not a network-administrating type of guy.

My home box is running Gutsy.
My Web server is running Red Hat (not sure what version) It also has Plesk 8 installed.

Anyone have ideas on how I can do this?

---

### Post by MrFSL on 2007-10-29
I would recommend SSH

Properly configured SSH would be a secured was to connect to your remote system. Using gnome you can mount the remote system in the form of:
```
ssh://remote_ip
```


To get started:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by hipnerd on 2007-11-06
This worked great. Thank you. My only remaining question is:

Is there a way to automate the process? I'd like to mount this remote directory each time the computer boots.

---

### Post by MrFSL on 2007-11-06
> **hipnerd said:**
> This worked great. Thank you. My only remaining question is:

Is there a way to automate the process? I'd like to mount this remote directory each time the computer boots.

Well, it isn't actually ***_mounted_*** in the traditional sense. Nautilus file browser just makes it appear to be (similar to how Internet Explorer handles ftp). You can make a link to this, or you can go to **Places > Connect To Server** and enter all the information for ssh.

To avoid password prompts you will need to get your keys straight. For further information please read:

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

If you insist on mounting then read this:

[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

### Post by hipnerd on 2007-11-08
Worked like a charm and brought the ease of use for Web editing up to a level that surpasses my old Windows box with HTML-Kit.

Now if we can get Adobe to make PhotoShop for Linux, I'll be done with Windows for good.

---

### Post by MrFSL on 2007-11-08
Photoshop?

What can Photoshop do for a web designer that The Gimp 2 can't do?

---

