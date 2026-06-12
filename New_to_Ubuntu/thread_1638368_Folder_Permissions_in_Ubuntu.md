---
title: "Folder Permissions in Ubuntu"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by kkpickel on 2010-12-05
I finally was able to switch the ownership of my /etc folder from 'root' to 'me' and now the permissions will not save, I can only create and delete files, I change the file access drop down for read and write, but when I try to apply the permissions and reverts back to --, and I can't edit my files....

Does anyone have some suggestions on how to solve this?

---

### Post by tgm4883 on 2010-12-05
> **kkpickel said:**
> I finally was able to switch the ownership of my /etc folder from 'root' to 'me' and now the permissions will not save, I can only create and delete files, I change the file access drop down for read and write, but when I try to apply the permissions and reverts back to --, and I can't edit my files....

Does anyone have some suggestions on how to solve this?

Why would you do that, it just seems like such a bad idea. 

Use sudo (or gksudo) when you need to edit files in that directory. You shouldn't need to do it often.

---

### Post by kkpickel on 2010-12-05
Well, I installed Ubuntu 10.10 yesterday, from the beginning my touchpad on my Sony Vaio VPCEB33FM isn't working.  I've been reading the forums and the instructions tell me to do this:

1. Edit /etc/default/grub to include GRUB_CMDLINE_LINUX=&#8221;i8042.nopnp&#8221;
2. Run: sudo update-grub
3. Reboot.

when I put the information in it would tell me: Permission Denied

So I noticed on my etc folder, I didn't have ownership, so then I changed it to my username, and now I can only delete and add files but I still can't edit them, Permission Denied, still, so I'm just trying to figure out what I need to do in order to solve this whole touchpad issue....

If you have any solutions I would really appreciate it

---

### Post by coffeecat on 2010-12-05
First thing, let's get your /etc folder and contents back to the way they should be:

```
sudo chown -R root:root /etc
```To edit the grub file. From the terminal:

```
gksudo gedit /etc/default/grub
```Now, you might want to  look at this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also - please don't  change the ownership of root-owned files to yourself. That way is a sure road to system breakage. Honestly. :)

---

### Post by kkpickel on 2010-12-05
I got everything switched back.  Still unsure about what to do about my touchpad?  I think I'm just going to give up on fixing it.  I've been trying to fix it since yesterday and it's putting me in a bad mood. haha

---

